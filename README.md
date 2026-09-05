# Desafio das Economias — R$1 a R$500

App estático que guarda o progresso do desafio direto num arquivo `data.json`
dentro deste repositório, via API do GitHub. Só quem tiver um token com
permissão de escrita neste repo consegue marcar valores.

## Publicar

1. Crie um repositório **público** no GitHub (ex: `desafio-500`).
   Precisa ser público para o GitHub Pages funcionar no plano gratuito.
2. Suba estes três arquivos (`index.html`, `data.json`, `README.md`) para a
   raiz do repositório, na branch `main`.
3. Em **Settings → Pages**, em "Source" escolha a branch `main` e a pasta `/root`.
   O GitHub te dará uma URL tipo `https://seu-usuario.github.io/desafio-500/`.
4. Abra `index.html` e ajuste as três primeiras constantes do script:
   ```js
   const GH_OWNER  = 'seu-usuario';
   const GH_REPO   = 'desafio-500';
   const GH_BRANCH = 'main';
   ```
   Suba a alteração.

## Criar um token (cada um cria o seu)

1. Acesse **github.com → Settings → Developer settings → Fine-grained tokens → Generate new token**.
2. Em "Repository access", escolha **Only select repositories** e selecione
   apenas o `desafio-500`.
3. Em "Permissions", dê **Contents: Read and write**. Nenhuma outra permissão é necessária.
4. Defina uma validade (ex: 1 ano) e gere o token.
5. Copie o token — ele só aparece uma vez.

Sua esposa repete os mesmos passos na conta dela, gerando o próprio token
com acesso só a esse repositório.

## Usar

Ao abrir a página pela primeira vez, ela pede um nome e o token. Isso fica
salvo só no navegador de quem entrou (`localStorage`), nunca é enviado a
lugar nenhum além da API do GitHub. Qualquer pessoa sem token só veria a
tela de entrada — não dá pra ler nem marcar nada sem ele.

Se dois toques acontecerem quase ao mesmo tempo, o app detecta o conflito,
busca o estado mais recente do `data.json` e tenta salvar de novo
automaticamente.

## Observação sobre privacidade

O repositório precisa ser público para o Pages gratuito funcionar, então
o `data.json` (a lista de valores marcados) é tecnicamente visível a
qualquer pessoa que souber o link direto do arquivo. Ninguém além de quem
tem um token consegue *alterar* nada, mas não é um cofre — é só uma trava
de escrita, não de leitura. Se isso for um problema, dá pra usar um
repositório privado com o GitHub Pages pago, ou trocar por um backend
próprio.
