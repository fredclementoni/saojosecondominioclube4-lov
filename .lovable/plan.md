## Objetivo

Exibir o `index-2.html` (landing page do São José Condomínio Clube) no preview do Lovable, mantendo o nome do arquivo intacto.

## Diagnóstico

Hoje o projeto contém apenas `index-2.html` na raiz — não há `package.json`, nem Vite/TanStack Start configurados. O preview do Lovable precisa de um servidor de desenvolvimento rodando na porta padrão (8080) para mostrar qualquer coisa. Por isso o preview aparece vazio: não há nada sendo servido.

## Solução

Subir um servidor estático mínimo (Vite em modo estático) cujo único papel é servir o `index-2.html` como página inicial do preview, sem mexer no conteúdo da landing page.

### Passos

1. **Criar `package.json`** mínimo com Vite como dependência e script `dev` rodando na porta 8080.
2. **Criar `vite.config.ts`** apontando a raiz pública para a pasta do projeto e configurando um rewrite para que a URL `/` carregue `index-2.html` (mantendo o nome do arquivo).
3. **Criar um `index.html` enxuto na raiz** apenas com um `<meta http-equiv="refresh" content="0; url=/index-2.html">` (redirecionamento instantâneo). Isso garante que abrir `/` no preview exiba o `index-2.html` sem renomear o original.
4. **Instalar dependências** (`bun install`) e o dev server sobe automaticamente.
5. **Validar no preview**: confirmar que a landing page aparece com fontes, imagens e animações funcionando.

### O que NÃO muda

- O conteúdo de `index-2.html` permanece exatamente como está (HTML/CSS/JS puro, 809 linhas).
- Nenhuma alteração em textos, paleta, seções ou scripts da landing.
- O arquivo continua se chamando `index-2.html` — você continua editando o mesmo arquivo.

## Resultado esperado

Ao abrir o preview, a landing page do São José Condomínio Clube é renderizada na URL raiz, e qualquer edição que você (ou eu) fizer em `index-2.html` reflete imediatamente no preview via hot reload do Vite.
