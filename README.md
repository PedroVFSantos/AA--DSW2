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

## Responsividade (media queries)

O layout é pensado primeiro para celular (*mobile first*) e usa dois tipos de breakpoint:

1. **Prefixos do Tailwind no HTML** (`xs:`, `sm:`, `md:`, `lg:`), que geram media queries de `min-width`. Além dos padrões, criamos `xs` (480px) e `3xl` (1792px) no `@theme`.
2. **Media queries escritas à mão** na seção 3 de `tailwindInput.css`:

| Media query | O que muda |
|---|---|
| `max-width: 47.99rem` (celular) | Menu vira barra fixa no rodapé; degradê do hero vem de baixo; filtros rolam na horizontal |
| `min-width: 48rem` (tablet+) | Degradê do hero passa a ser lateral |
| `48rem` a `63.99rem` (tablet) | Saídas em 2 colunas |
| `min-width: 64rem` (desktop) | Hero mais alto; coluna lateral fica fixa (*sticky*) ao rolar |
| `min-width: 112rem` (telas largas) | Conteúdo mais largo |
| `orientation: landscape` e `max-height: 30rem` | Celular deitado: hero compacto e menu não fixo |
| `hover: hover` e `pointer: fine` | Efeitos de hover só em aparelhos com mouse |
| `prefers-reduced-motion` | Animações desligadas para quem pediu menos movimento |
| `print` | Impressão sem menu e sem sombras |

Tudo continua sem JavaScript: os cards de opção do formulário usam `:has(:checked)` e as animações de entrada usam CSS (incluindo `animation-timeline: view()` onde o navegador suporta).

## Como rodar

```bash
npm install
npm run tailwind-watch
```

Com o comando acima rodando, abra o `index.html` no navegador (por exemplo, com a extensão Live Server do VS Code). Para gerar o CSS uma única vez:

```bash
npm run build
```

Os estilos ficam em `tailwindInput.css` e o resultado gerado em `tailwindOutput.css`. O `npm install` também instala o Basecoat (`basecoat-css`), que o CSS importa.

## Próxima fase: AA2 (React)

Lógica do app com React, acesso à rede (back-end simulado), geolocalização para "trilhas perto de mim" e localStorage para favoritos.

## Equipe

- Pedro Vinicius
- Lucas Crempe
- Vinicius Massuda
