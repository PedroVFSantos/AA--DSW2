# TrilhaBR

Aplicativo web para descobrir trilhas e percursos de corrida e marcar saídas em grupo.

Projeto da disciplina **Desenvolvimento de Software para Web 2** (DC - UFSCar, 02/2026).

## Fase atual: AA1 (HTML + CSS)

Layout e telas com Tailwind CSS, sem lógica. Requisitos atendidos: R1 (identidade visual), R2 (mais de uma tela) e R3 (layout responsivo).

| Página | Descrição |
|---|---|
| `index.html` | Explorar trilhas e corridas, com busca e filtros |
| `trilha.html` | Detalhe da trilha: números, altimetria, avaliações e previsão |
| `saidas.html` | Saídas em grupo |
| `criar.html` | Formulário para criar uma saída |
| `perfil.html` | Perfil, conquistas, próximas saídas e favoritas |
| `login.html` | Entrar |

## Design

- **Componentes shadcn/ui**: como o shadcn/ui é feito para React, na AA1 usamos o [Basecoat](https://basecoatui.com), que implementa o mesmo design system em HTML + Tailwind puro. Botões (`.btn`), cards (`.card`), selos (`.badge`), campos (`.field`) e avatares (`.avatar`) vêm dele. As variáveis do shadcn (`--primary`, `--ring`, `--radius`...) foram trocadas pela paleta do TrilhaBR em `tailwindInput.css`, então na AA2 dá para usar o shadcn/ui de verdade com as mesmas cores.
- **Paleta**: verde floresta (primária), laranja brasa (chamadas para ação) e areia (fundo), com fonte Manrope e ícones Lucide (os mesmos do shadcn).
- **Fotos reais**: fotos de trilhas brasileiras do Wikimedia Commons, em WebP, com duas versões (720px e 1600px) servidas via `srcset`. Autores e licenças estão em [`img/CREDITOS.md`](img/CREDITOS.md).

## Responsividade (mobile first)

O estilo base é o do celular, que é onde a maioria das pessoas vai usar o app. A partir dele, os prefixos do Tailwind (`sm:`, `md:`, `lg:`) só acrescentam o que muda quando a tela cresce. Todos geram media queries de `min-width`; não há nenhuma de `max-width`.

| Tela | Prefixo (media query) | O que muda |
|---|---|---|
| Celular | sem prefixo (base) | Menu fixo no rodapé; hero com o texto embaixo; filtros rolam na horizontal; tudo em 1 coluna |
| Tablet | `md:` (`min-width: 48rem`, 768px) | Menu sobe para o cabeçalho; degradê do hero passa a ser lateral; saídas em 2 colunas |
| Desktop | `lg:` (`min-width: 64rem`, 1024px) | Hero mais alto; saídas em 3 colunas; coluna lateral fixa (*sticky*) ao rolar |

O `tailwindInput.css` guarda só a identidade visual (fonte, cores e a animação de entrada). O resto do estilo está nas classes do Tailwind direto no HTML, e na AA2 cada bloco repetido (link do menu, filtro, card) vira um componente React.

Tudo continua sem JavaScript: os cards de opção do formulário usam `has-checked:` (`:has(:checked)`) e as animações de entrada são feitas só com CSS.

## Como rodar

```bash
npm install
npm run tailwind-watch
```

Com o comando acima rodando, abra o `index.html` no navegador (por exemplo, com a extensão Live Server do VS Code). Para gerar o CSS uma única vez:

```bash
npm run build
```

As cores ficam em `tailwindInput.css` e o CSS gerado em `tailwindOutput.css`. O `npm install` também instala o Basecoat (`basecoat-css`), que o CSS importa.

## Próxima fase: AA2 (React)

Lógica do app com React, acesso à rede (back-end simulado), geolocalização para "trilhas perto de mim" e localStorage para favoritos.

## Equipe

- Pedro Vinicius
- Lucas Crempe
- Vinicius Massuda
