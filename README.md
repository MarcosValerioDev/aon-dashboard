# AON Dashboard — Painel de Evolução do Aluno

Painel web de página única que mostra a evolução de um aluno ao longo das sessões de treino, no estilo de um painel de instrumentos (cockpit), em tema escuro.

## O que o painel mostra

- **Cabeçalho e KPIs** com os indicadores principais do aluno.
- **Curva de aprendizagem**: desempenho (% de acertos) sessão a sessão.
- **Critério de aprovação**: meta de 85% de acertos mantida por 3 sessões seguidas.
- **Posição na turma**: comparação com os colegas (primeira sessão e platô).
- **Velocidade × precisão**: relação entre tentativas e acertos.
- **Fadiga e pausas**: efeito de várias sessões no mesmo dia e de intervalos longos sem treino.
- **Composição dos erros**: proporção de erros por tipo (ex.: alvos perdidos).
- **Leitura para o instrutor**: resumo textual dos achados.
- **Registro de sessões**: tabela com o histórico completo.

## Estrutura

```
aon-dashboard/
├── index.html.html   # Painel completo: HTML, CSS e JavaScript em um só arquivo
└── README.md
```

Não há dependências nem etapa de build. Os gráficos são desenhados em SVG com JavaScript puro, e as fontes (IBM Plex Sans, IBM Plex Mono e Saira Semi Condensed) vêm do Google Fonts.

## Como usar

Abra o arquivo `index.html.html` diretamente no navegador. Para servir localmente:

```bash
npx serve .
```

## Dados

Os dados atuais são **fictícios**, gerados de forma determinística (gerador `mulberry32` com semente fixa) dentro do próprio script: 20 sessões a partir de 21/09/2026 e uma turma simulada de 27 colegas. As constantes principais ficam no topo do script:

| Constante       | Valor | Significado                                   |
|-----------------|-------|-----------------------------------------------|
| `TARGET`        | 85    | % de acertos exigida para aprovação           |
| `STREAK_NEEDED` | 3     | Sessões seguidas acima da meta para aprovar   |
| `LAST_N`        | 5     | Janela das últimas sessões usada nos indicadores |

Para usar dados reais, substitua a geração do array `sessions` (e das listas da turma) por dados vindos de um arquivo JSON ou de uma API, mantendo os mesmos campos: `n`, `at`, `attempts`, `correct`, `errors`, `missed` e `perf`.

## Próximos passos sugeridos

- Renomear `index.html.html` para `index.html`.
- Carregar dados reais em vez dos dados simulados.
