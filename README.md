# Centro de Documentação

Centro de documentação pessoal em HTML estático — arquivos auto-contidos, densos e fáceis de navegar e compartilhar, no espírito do artigo da Anthropic [_The unreasonable effectiveness of HTML_](https://claude.com/blog/using-claude-code-the-unreasonable-effectiveness-of-html).

---

## O que é

Um hub _hub-and-spoke_: uma página-índice (`index.html`) que lista e dá acesso a documentos independentes, cada um um único arquivo HTML. Sem framework, sem etapa de build — cada documento abre direto no navegador e pode ser compartilhado por link.

Por que HTML em vez de Markdown: densidade de informação (tabelas, SVG, código destacado, interação), leitura confortável em documentos longos e compartilhamento simples (o navegador renderiza nativamente).

---

## Estrutura do repositório

| Arquivo | Conteúdo |
|---|---|
| `index.html` | **Hub** — página-índice do centro. Cards de documentos agrupados por categoria, com busca client-side (atalho `/`). Adicionar um doc é copiar o template de card comentado no próprio arquivo. |
| `opencode.html` | Documentação técnica completa do [OpenCode](https://github.com/sst/opencode): Visão Geral, Arquitetura, Instalação, Configuração (`opencode.json`, carregamento e precedência), Modelos e Provedores, Agentes, Permissões, Servidores MCP, Comandos, Formatter & LSP, Schema, Tools Nativas, Tutoriais de Plugin e Custom Tool, Catálogo de Hooks, Referência de CLI e Glossário. |
| `agent-persistence.html` | Artigo "Onde os agentes guardam memória" — como agentes de IA (Claude Code, OpenCode, Codex, entre outros) persistem sessões em disco: event log append-only (JSONL) vs. document store normalizado. |
| `opencode-runtime.svg` | Diagrama do runtime do OpenCode, usado na seção de Arquitetura de `opencode.html`. |

---

## Como visualizar

### Direto no navegador

```bash
xdg-open index.html        # Linux
open index.html            # macOS
```

### Servindo localmente (recomendado)

Servir via HTTP garante que os CDNs (Tailwind, PrismJS, Lucide, Google Fonts) carreguem e que as âncoras de navegação funcionem sem as restrições de `file://`:

```bash
python3 -m http.server 8080      # depois acesse http://localhost:8080
```

Alternativas: `npx serve .` ou `php -S localhost:8080`.

---

## Pré-requisitos

- Navegador moderno com suporte a ES2020+ (Chrome, Firefox, Edge, Safari recentes).
- Conexão com a internet para os CDNs externos:
  - Tailwind CSS Play CDN (`cdn.tailwindcss.com`)
  - PrismJS (`cdn.jsdelivr.net`)
  - Lucide Icons (`unpkg.com`)
  - Google Fonts (`fonts.googleapis.com`)

Não há dependências locais nem etapa de instalação.

---

## Adicionar um documento

1. Crie o novo arquivo, ex.: `meu-doc.html` (use `agent-persistence.html` como ponto de partida — já traz o design system).
2. Em `index.html`, copie o bloco `<!-- TEMPLATE DE CARD -->` e preencha título, descrição, categoria, tags e `href` apontando para o novo arquivo.
3. Recarregue o navegador.

Convenções do projeto:

- Estilo via classes Tailwind (Play CDN); sem arquivo CSS separado.
- Highlight de código via PrismJS — especifique a linguagem na classe do `<code>`.
- Ícones via Lucide (`data-lucide="nome-do-icone"`).
- Cada documento traz um link "← Centro de Docs" de volta ao hub.
- O diagrama `opencode-runtime.svg` pode ser editado em qualquer editor SVG (Inkscape, Figma, etc.).

---

## Publicação

Servido como site estático via **GitHub Pages** (branch `main`, raiz `/`). Com o Pages ativo, cada documento fica acessível por link público — ex.: `https://<usuario>.github.io/opencode-example-html/opencode.html`.

---

## Referência oficial

- Repositório do OpenCode: [https://github.com/sst/opencode](https://github.com/sst/opencode)

---

## Licença

Licença não definida. Consulte os mantenedores antes de reutilizar o conteúdo.
