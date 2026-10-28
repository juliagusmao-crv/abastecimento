# Abastecimento da Frota · CRV Industrial

Site para acompanhar a % de combustível e o horímetro das colhedoras e tratores, por frente.
Hospedado no **GitHub Pages**; login com e-mail e senha e banco de dados no **Firebase** (plano gratuito).

## Arquivos

| Arquivo | Para que serve |
|---|---|
| `index.html` | O site inteiro |
| `config.js` | Os dados do seu projeto Firebase (você preenche uma vez) |
| `firestore.rules` | Regras de segurança do banco (você cola no Firebase) |
| `dados-iniciais.json` | Frentes, frotas e lançamentos do site antigo. **Não suba este arquivo para o GitHub**: ele é importado uma vez pela aba *Frentes e frotas* |
| `.nojekyll` | Arquivo vazio exigido pelo GitHub Pages |

## Parte 1 · Firebase (banco e login)

1. Entre em **console.firebase.google.com** com seu Gmail › **Adicionar projeto** › nome `abastecimento-crv` › pode desligar o Google Analytics › **Criar projeto**.
2. Menu **Criação › Authentication** › **Vamos começar** › em *Provedores de login* escolha **E-mail/senha** › ative a primeira chave › **Salvar**.
3. Ainda em Authentication › aba **Usuários** › **Adicionar usuário** › coloque **o seu e-mail** e uma senha. Esse será o login da administradora.
4. Menu **Criação › Firestore Database** › **Criar banco de dados** › local `southamerica-east1 (São Paulo)` › **modo de produção** › **Criar**.
5. No Firestore, aba **Regras** › apague tudo › cole o conteúdo de `firestore.rules` › troque `EMAIL_DA_ADMINISTRADORA` pelo seu e-mail do passo 3 (entre as aspas) › **Publicar**.
6. Clique na **engrenagem › Configurações do projeto** › em *Seus apps* clique no ícone **`</>`** (Web) › apelido `site` › **Registrar app**. Vai aparecer um bloco `firebaseConfig = { apiKey: ..., ... }`. Copie os 6 valores para o arquivo `config.js`, no lugar de cada `COLE_AQUI`.

## Parte 2 · GitHub (o site no ar)

1. Entre em **github.com** › **New repository** › nome `abastecimento` › **Public** › **Create repository**.
2. Clique em **uploading an existing file** › arraste `index.html`, `config.js`, `firestore.rules`, `README.md` e `.nojekyll` (não arraste o `dados-iniciais.json`) › **Commit changes**.
   - Se o `.nojekyll` não aparecer para arrastar, crie pelo botão **Add file › Create new file** com esse nome e sem conteúdo.
3. No repositório › **Settings › Pages** › *Source*: **Deploy from a branch** › *Branch*: **main** e **/(root)** › **Save**.
4. Em 1 a 2 minutos o site fica no ar em **https://SEU-USUARIO.github.io/abastecimento/**.
5. Volte ao Firebase › **Authentication › Configurações › Domínios autorizados** › **Adicionar domínio** › `SEU-USUARIO.github.io`.

## Parte 3 · Primeiro acesso

1. Abra o link do site e entre com o e-mail e a senha do passo 3 da Parte 1.
2. Aba **Usuários** › clique em **Renomear** na sua linha e coloque seu nome.
3. Aba **Frentes e frotas** › *Importar dados* › escolha `dados-iniciais.json` › **Importar arquivo**.
4. Cadastre a equipe na aba **Usuários** (nome, e-mail, senha inicial e função) e mande para cada pessoa o link, o e-mail e a senha.

## Atualizar o site depois

Para trocar o `index.html` por uma versão nova: no GitHub, abra o arquivo › ícone de lápis ou **Add file › Upload files** › envie o arquivo novo › **Commit changes**. Em 1 ou 2 minutos o site atualiza. Os dados ficam no Firebase e não são afetados.
