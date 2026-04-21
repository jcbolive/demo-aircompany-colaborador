# AIR Help Center Theme (Zendesk Guide)

Tema customizado da Central de Ajuda para o ambiente Zendesk Guide, com identidade visual AIR.

## Estrutura do tema

- `manifest.json`: metadados do tema e variáveis configuráveis no Guide.
- `templates/`: páginas e blocos da Central de Ajuda (Curlybars).
- `assets/`: imagens SVG do projeto.
- `style.css` e `script.js`: estilo e comportamento global.

## Personalizações incluídas

- Header com marca AIR.
- Hero principal com título/subtítulo configuráveis via settings do tema.
- Links rápidos para pesquisa, abertura de ticket e categorias.
- Cards de atalhos para conteúdos de suporte.
- Footer com ano dinâmico.

## Como publicar no Zendesk (via GitHub)

1. Garanta que o `manifest.json` está na raiz do repositório.
2. Suba o tema para um repositório GitHub dedicado (um tema por repositório).
3. No Zendesk Guide, acesse: **Administrador do Conhecimento → Painel de personalização → Adicionar tema → Adicionar do GitHub**.
4. Informe URL do repositório (e branch opcional) e importe.
5. Faça preview e publique no Guide.

## Referências

- Zendesk Developer Docs (customização de temas): https://developer.zendesk.com/documentation/help_center/#customizing-help-center-themes
- Integração GitHub com tema do Guide (PT-BR): https://support.zendesk.com/hc/pt-br/articles/4408832476698-Configura%C3%A7%C3%A3o-da-integra%C3%A7%C3%A3o-do-GitHub-com-seu-tema-do-Guide

## Troubleshooting de importação

Se aparecer o erro `manifest.json` com **"additional properties ['private']"**, remova a chave `private` do arquivo. O schema de tema do Guide não aceita essa propriedade.

Se o importador reclamar de template ausente (por exemplo `templates/community_post_list_page.hbs`), inclua também os templates padrão de Community/Requests/Profile exigidos pelo Guide.

Se aparecer erro de variável inexistente como `locale` ou `page_title`, use objetos válidos do templating atual (ex.: `help_center.locale`) e título estático/compatível no `document_head.hbs`.


Para máxima compatibilidade com validação do importador, os templates `category_page.hbs`, `section_page.hbs` e `search_results.hbs` foram simplificados sem iterações de coleções.

## Abordagem atual

O tema mantém os recursos nativos da Zendesk (busca e chamados) usando helpers oficiais como `search`, `request_form` e `request_list`, enquanto a customização fica concentrada no visual (CSS e assets).

Se o importador indicar erro em `settings.instant_search`, remova o parâmetro `instant=settings.instant_search` do helper `search` (ou declare essa setting no `manifest.json`).

A setting `instant_search` foi adicionada ao `manifest.json` para compatibilidade com ambientes que ainda usem `instant=settings.instant_search` no helper de busca.
