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

## Como rodar

```bash
npm install
npm run tailwind-watch
```

Com o comando acima rodando, abra o `index.html` no navegador (por exemplo, com a extensão Live Server do VS Code). Para gerar o CSS uma única vez:

```bash
npm run build
```

Os estilos ficam em `tailwindInput.css` e o resultado gerado em `tailwindOutput.css`.

## Próxima fase: AA2 (React)

Lógica do app com React, acesso à rede (back-end simulado), geolocalização para "trilhas perto de mim" e localStorage para favoritos.

## Equipe

- Pedro Vinicius
