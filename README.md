# meu.painel

Painel administrativo simples para acompanhar os números do portfólio (visitas, cliques, vídeos vistos e mensagens de contato), lendo direto do Supabase. Feito em HTML, CSS e JavaScript puro, sem build e sem Node, para abrir direto no navegador ou publicar como site estático.

## Estrutura

- `login.html`: tela de login.
- `painel.html`: painel interno protegido (menu lateral com as abas Menu Principal e Portfólio).
- `js/auth.js`: cliente Supabase e funções de autenticação compartilhadas.
- `setup.sql`: script para criar as tabelas e permissões no Supabase.
- `README.md`: este arquivo.

## Passo a passo

1. **Rode o `setup.sql` no Supabase.** No painel do seu projeto, vá em SQL Editor > New query, cole o conteúdo de `setup.sql` e clique em Run. Isso cria as tabelas `portfolio_events` e `portfolio_leads`, liga o Row Level Security e libera a leitura para usuários autenticados.

2. **Crie seu usuário de login.** No painel do Supabase, vá em Authentication > Users > Add user, informe seu e-mail e uma senha. Esse é o e-mail e senha que você vai usar em `login.html` (o painel usa Supabase Auth de verdade, não é preciso configurar mais nada).

3. **Teste localmente.** Como os arquivos usam `fetch` para carregar fontes e o script do Supabase, abra a pasta com um servidor local simples em vez de abrir o `login.html` direto com duplo clique (alguns navegadores bloqueiam certas chamadas em `file://`). Duas opções fáceis:
   - Com Python instalado: `python -m http.server 8080` dentro da pasta do projeto, depois acesse `http://localhost:8080/login.html`.
   - Com a extensão "Live Server" do VS Code: clique com o botão direito em `login.html` e escolha "Open with Live Server".

4. **Publique no GitHub Pages.** Crie um repositório no GitHub, suba os arquivos desta pasta (`git init`, `git add .`, `git commit`, `git push`), depois vá em Settings > Pages, escolha a branch principal e a pasta raiz. Em alguns minutos o site fica disponível em `https://seu-usuario.github.io/nome-do-repo/login.html`.

5. **Ou publique na Vercel.** Crie uma conta na Vercel, clique em "Add New Project", importe o mesmo repositório do GitHub e não altere nenhuma configuração de build (é um site estático, não precisa de comando de build nem de diretório de saída especial). Em poucos segundos você recebe uma URL pública.

6. **Acesse e faça login.** Abra a URL publicada apontando para `login.html`, entre com o e-mail e a senha criados no passo 2, e você cai direto no `painel.html` com os números do seu portfólio.

## Resumo rápido

- **Testar localmente:** suba um servidor estático simples (`python -m http.server` ou Live Server) e abra `login.html` por `http://localhost`.
- **Criar seu usuário:** no Supabase, em Authentication > Users > Add user, cadastre seu e-mail e senha.
- **Publicar:** suba os arquivos para um repositório GitHub e ative o GitHub Pages, ou importe o repositório na Vercel como projeto estático.
