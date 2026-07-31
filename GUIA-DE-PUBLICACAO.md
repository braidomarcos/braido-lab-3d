# Braido Lab 3D — Guia definitivo (site, painel, domínio e manutenção)

Este é o guia único e completo — do zero até a manutenção do dia a dia.
Segue as partes em ordem na primeira vez; depois disso, use o
**Índice** abaixo pra pular direto pra parte que precisar.

## Índice

1. [Glossário rápido](#glossário-rápido)
2. [O que você recebeu](#o-que-você-recebeu)
3. [Criar conta no GitHub](#parte-1--criar-conta-no-github)
4. [Criar o repositório](#parte-2--criar-o-repositório)
5. [Subir os arquivos do site](#parte-3--subir-os-arquivos-do-site)
6. [Publicar na Netlify](#parte-4--publicar-na-netlify)
7. [Escolher o endereço gratuito](#parte-5--escolher-o-endereço-gratuito-domínio)
8. [Ativar o painel visual](#parte-6--ativar-o-painel-visual-cms)
9. [Manutenção do dia a dia](#parte-7--manutenção-do-dia-a-dia-adicionar-editar-remover)
10. [Textos que ficam fora do painel](#parte-8--textos-que-ficam-fora-do-painel)
11. [CI/CD — atualizações estruturais](#parte-9--cicd-para-atualizações-estruturais)
12. [Se algo der errado](#se-algo-der-errado)
13. [Checklist antes de divulgar](#checklist-antes-de-divulgar)

---

## Glossário rápido

- **Repositório**: a pasta que guarda os arquivos do site, dentro do GitHub.
- **GitHub**: onde essa pasta fica guardada e com histórico de tudo que muda.
- **Netlify**: quem pega os arquivos do GitHub e coloca o site no ar, de graça.
- **Deploy / publicar**: o momento em que a Netlify atualiza o site no ar com os arquivos mais recentes.
- **Domínio / subdomínio**: o endereço do site (ex: `braidolab3d.netlify.app`).
- **Painel (CMS)**: a página em `/admin` onde você adiciona fotos e textos sem editar código.
- **Commit**: "salvar uma alteração" dentro do GitHub.
- **Branch**: uma "cópia paralela" do site pra testar mudanças sem afetar o que está no ar. A branch principal se chama `main`.
- **CI/CD**: o processo automático que pega uma alteração salva e publica ela sozinho, sem você precisar fazer nada manualmente além de salvar.

---

## O que você recebeu

Dentro do arquivo `braido-lab-3d.zip`:

- `index.html` — o site
- `favicon.png` — o ícone da aba do navegador (recortado da sua logo real)
- `admin/` — o painel visual (arquivos `index.html` e `config.yml`)
- `data/catalogo.json` e `data/portfolio.json` — os itens do catálogo e portfólio (editáveis pelo painel)
- `images/uploads/` — suas fotos reais já organizadas
- `images/logo-full.png` — sua logo real, otimizada para o site
- `images/logo-full.svg` e `images/logo-icon.svg` — versões vetorizadas (bônus, caso precise em tamanho grande/impressão no futuro)

---

## Parte 1 — Criar conta no GitHub

1. Acesse **github.com**
2. Clique em **Sign up**
3. Preencha e-mail, senha e nome de usuário (ex: `braidolab3d`)
4. Confirme o e-mail que o GitHub enviar

## Parte 2 — Criar o repositório

1. Logado, clique no **+** (canto superior direito) → **New repository**
2. Em **Repository name**, digite `braido-lab-3d`
3. Deixe marcado **Public**
4. Clique em **Create repository**

## Parte 3 — Subir os arquivos do site

1. Na página do repositório, clique em **uploading an existing file**
   (ou **Add file → Upload files**)
2. Selecione **todos** os arquivos e pastas do zip que você recebeu
   (`index.html`, `favicon.png`, e as pastas `admin`, `data`, `images`)
3. Arraste tudo pra área de upload
4. Role até o final e clique em **Commit changes**

> Confira se `admin`, `data` e `images` aparecem como **pastas** clicáveis
> no GitHub, não como arquivos soltos. Se o navegador não deixar
> arrastar pastas inteiras, entre em cada pasta local e repita o
> upload, escrevendo o caminho completo no nome do arquivo (ex:
> `images/uploads/bebedouro-pet.jpg`).

## Parte 4 — Publicar na Netlify

1. Acesse **app.netlify.com** → **Sign up with GitHub**
2. Autorize o acesso
3. Clique em **Add new site → Import an existing project**
4. Escolha **Deploy with GitHub** → selecione `braido-lab-3d`
5. Não mude nada — clique em **Deploy site**

Em cerca de 1 minuto o site está no ar, com um link tipo
`nome-aleatorio-123.netlify.app`.

## Parte 5 — Escolher o endereço gratuito (domínio)

1. No painel do site, clique em **Site configuration → Domain management**
2. Ao lado do endereço, clique nos três pontinhos (**Options**) → **Edit site name**
3. Digite o nome que quiser, ex: `braidolab3d`
4. Clique em **Save**

Se disponível, seu site passa a ser **braidolab3d.netlify.app** — fixo e grátis.

## Parte 6 — Ativar o painel visual (CMS)

Feito uma única vez.

**6.1 — Criar as chaves no GitHub**

1. No GitHub: foto de perfil → **Settings → Developer settings → OAuth Apps → New OAuth App**
2. Preencha:
   - **Application name**: `Braido Lab 3D`
   - **Homepage URL**: `https://braidolab3d.netlify.app` (seu endereço real)
   - **Authorization callback URL**: `https://api.netlify.com/auth/done`
3. Clique em **Register application**
4. Copie o **Client ID**
5. Clique em **Generate a new client secret** e copie o valor (só aparece uma vez)

**6.2 — Colar as chaves na Netlify**

1. No painel do site: **Site configuration → Access & security**
2. Procure **OAuth → Install provider → GitHub**
3. Cole o **Client ID** e o **Client Secret**
4. Salve

**6.3 — Apontar o painel pro seu repositório**

1. No GitHub, abra `admin/config.yml` → clique no lápis ✏️ (**Edit**)
2. Troque `repo: SEU-USUARIO/SEU-REPOSITORIO` pelo seu usuário/repositório real
   (ex: `repo: joaobraido/braido-lab-3d`)
3. Clique em **Commit changes**

**6.4 — Testar**

1. Acesse `braidolab3d.netlify.app/admin`
2. **Login with GitHub** → autorize
3. Confira se aparecem as opções **Catálogo** e **Portfólio**

---

## Parte 7 — Manutenção do dia a dia (adicionar, editar, remover)

Tudo isso é feito em `/admin`, sem editar nenhum código.

### Adicionar um item novo

1. Entre em `/admin` → **Catálogo** ou **Portfólio**
2. Clique em **catalogo** ou **portfolio** (o nome do arquivo) pra abrir a lista
3. Clique em **Add "Itens"** (ou **+**) no final da lista
4. Preencha título, descrição/legenda, preço e clique no campo de foto pra enviar a imagem
5. Clique em **Publish**

### Editar um item existente

1. Entre em `/admin` → abra **Catálogo** ou **Portfólio**
2. Clique no item que quer mudar (ele expande a lista)
3. Altere o campo que quiser (texto, preço, ou clique na foto pra trocar por outra)
4. Clique em **Publish**

### Remover um item

1. Entre em `/admin` → abra o item dentro da lista
2. Procure o ícone de lixeira 🗑️ (ou **Remove**) no canto do item dentro da lista
3. Clique para remover
4. Clique em **Publish**

### Reordenar itens

Dentro da lista, cada item tem um "alça" (ícone de setas ⠿) — clique e
arraste pra cima ou para baixo pra mudar a ordem em que aparecem no site.

Em todos os casos, o site atualiza sozinho no ar em cerca de 1 minuto
depois do **Publish**.

---

## Parte 8 — Textos que ficam fora do painel

Esses campos vivem direto no `index.html` (não no painel) — edite pelo
GitHub: abra o arquivo, clique no lápis ✏️, altere, e **Commit changes**
no final da página.

- `[SEU-NOME]` e `[ANO]` — seção Sobre e rodapé
- Os preços do catálogo (`R$ —`)
- Os links de WhatsApp, Instagram, TikTok, YouTube, Facebook e e-mail (hoje `href="#"`)
- Os links das lojas: Shopee, Shein, TikTok Shop, Mercado Livre (hoje `href="#"`)
- O link das avaliações do Google (seção Avaliações)
- O `shortname` do Disqus (crie uma conta grátis em disqus.com pra pegar o seu)

## Fotos ainda pendentes de confirmação

Duas fotos (porta-canetas de dragão, e o par preto/branco do suporte
PS5) ainda não entraram — tinham cara de foto de catálogo, não de foto
caseira. Se forem suas mesmo, suba pelo painel normalmente.

---

## Parte 9 — CI/CD para atualizações estruturais

Boa notícia: **você já tem CI/CD funcionando, de graça**. Todo esse
fluxo GitHub → Netlify que você acabou de montar é exatamente isso:
sempre que um arquivo muda no GitHub (seja pelo painel, seja por você
editando direto), a Netlify detecta sozinha e publica a versão nova.
Não existe passo manual de "clicar em publicar o servidor" — é automático.

Isso cobre bem o dia a dia (fotos, textos, preços). Mas se um dia você
quiser mudar algo **estrutural** — um novo bloco no site, uma seção
inteira nova, uma mudança de layout — vale um cuidado a mais pra não
arriscar o site que está no ar. Duas opções, gratuitas:

### Opção simples: branch + Deploy Preview (recomendada)

Isso já vem incluso na Netlify, sem configurar nada extra.

1. No GitHub, dentro do repositório, clique no menu que mostra **main**
   (canto superior esquerdo da lista de arquivos) → digite um nome novo,
   ex: `teste-novo-layout` → **Create branch**
2. Faça as alterações **nessa branch** (edite os arquivos com ela
   selecionada, em vez de `main`)
3. A Netlify cria sozinha um link de pré-visualização só dessa branch
   (visível em **Deploys**, na Netlify, como "Deploy Preview") — você
   testa por lá, sem afetar o site principal
4. Gostou do resultado? No GitHub, abra um **Pull Request** dessa
   branch para `main`, e clique em **Merge** — só aí a mudança vai pro
   site principal

### Opção avançada: GitHub Actions

Se um dia você (ou alguém que contratar) quiser automatizar checagens
antes de publicar — por exemplo, validar se o HTML não tem erro antes
de ir pro ar — o **GitHub Actions** é gratuito para repositórios
públicos e se conecta direto ao mesmo repositório. É mais técnico, e
não é necessário pro funcionamento do site hoje — só mencionando caso
o projeto cresça e precise.

Pra manutenção normal (fotos, preços, textos), você não precisa mexer
em nenhuma dessas duas opções — é só o painel mesmo.

---

## Se algo der errado

- **O site não atualizou**: espere 1–2 minutos e dê F5. Na Netlify, veja
  em **Deploys** se o último deploy está com bolinha verde (sucesso) ou
  vermelha (erro).
- **Não consigo logar no `/admin`**: revise a Parte 6 — Client ID/Secret
  colados certinho, e a linha `repo:` no `config.yml` no formato exato
  `usuario/repositorio`.
- **Subi uma foto e ela não aparece**: confira o tamanho do arquivo
  (ideal menos de 5 MB) e espere o novo deploy terminar.
- **Editei algo e "sumiu" um pedaço do site**: no GitHub, toda alteração
  fica no histórico — entre no arquivo, clique em **History**, e você
  consegue ver e restaurar qualquer versão anterior.

---

## Checklist antes de divulgar

- [ ] Nome, ano e preços preenchidos (Parte 8)
- [ ] Links de WhatsApp / Instagram / TikTok / YouTube / Facebook reais
- [ ] Links das lojas (Shopee, Shein, TikTok Shop, Mercado Livre) reais
- [ ] Google Perfil da Empresa criado e link colado no site
- [ ] Disqus configurado (área de comentários)
- [ ] Pelo menos uma foto real em cada categoria do catálogo
- [ ] Testado o formulário de orçamento (envie um teste pra si mesmo)
- [ ] Conferido o site no celular, não só no computador
