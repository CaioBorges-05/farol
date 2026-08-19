# Farol — Identidade Visual

Direção: instrumento de aviação, não farol marítimo. A ideia central é "painel de voo do seu crescimento" — cockpit, radar, torre de controle, não litoral/navio. A copy precisa reforçar isso ativamente (ver `docs/positioning.md`), porque o nome sozinho puxa pra farol de navio.

## Conceito

HUD (heads-up display) noturno de cockpit: fundo quase-preto com viés frio (azulado, não neutro), leitura em mono como instrumento digital, um único acento ciano (a "luz do painel"), e cor semântica de alerta separada do acento de marca (âmbar de aviso, vermelho de crítico, verde de "tudo certo") — porque no produto real essas cores význam coisas diferentes (status de anomalia) e não podem se confundir com a cor de marca.

## Cores

| Token | Valor | Uso |
|---|---|---|
| `--bg` | `#0A0D12` | Fundo base — preto com viés azul frio, não neutro |
| `--surface` | `#12161D` | Cards, painéis |
| `--surface-2` | `#171C25` | Elementos elevados |
| `--border` | `#232A35` | Bordas padrão |
| `--border-subtle` | `#1A1F28` | Divisórias discretas |
| `--text` | `#E4E8ED` | Texto principal (branco frio) |
| `--text-sec` | `#8791A0` | Texto secundário |
| `--text-muted` | `#525B69` | Texto terciário/labels |
| `--accent` | `#3ED6C4` | Cor de marca — ciano de instrumento/HUD. CTAs, destaques, ativo |
| `--accent-dim` | `rgba(62,214,196,0.10)` | Fundo suave de destaque |
| `--accent-mid` | `rgba(62,214,196,0.22)` | Borda de destaque |
| `--warn` | `#FFB020` | **Semântico** — alerta/atenção (luz âmbar de cockpit). Nunca usar como cor de marca. |
| `--critical` | `#FF4D4D` | **Semântico** — crítico/urgente |
| `--good` | `#34D399` | **Semântico** — status ok/dentro da meta |

`--warn`/`--critical`/`--good` são as cores que o produto real vai usar pra sinalizar status de anomalia (CAC subiu, funil caiu) — deliberadamente diferentes do `--accent` de marca, pra não virar ambíguo quando o dashboard existir de verdade.

## Tipografia

- **Display/headings:** `Sora` (600–800) — geométrica, técnica, sem ser o clichê de "Space Grotesk". Títulos, números grandes de métrica.
- **Corpo:** `IBM Plex Sans` (400–600) — família técnica, combina com a mono abaixo.
- **Dados/labels/mono:** `IBM Plex Mono` (400–600) — leitura de instrumento: labels, timestamps, números de métrica, badges de status.

Import: `https://fonts.googleapis.com/css2?family=Sora:wght@600;700;800&family=IBM+Plex+Sans:wght@400;500;600&family=IBM+Plex+Mono:wght@400;500;600&display=swap`

Em ambientes que bloqueiam fonte externa (preview de artifact), cai numa pilha de sistema desenhada de propósito (peso pesado + tracking apertado nos títulos, mono nas leituras) — não é fallback acidental.

## Padrões de componente

- **Leitura tipo instrumento**: números-chave em mono com `font-variant-numeric: tabular-nums`, label acima em caixa alta pequena — como um readout de cockpit, não um card de app genérico.
- **Radar/varredura**: elemento único de assinatura visual no hero (varredura de radar sutil, respeita `prefers-reduced-motion`) — um momento, não decoração espalhada pela página inteira.
- **Cards de instrumento**: painel com borda fina, cantos levemente technical (não totalmente arredondado, mais "display de vidro" que "app fofo").
- **Badge de status semântico**: pequeno indicador colorido (âmbar/vermelho/verde) + label mono uppercase — pensado pra já parecer o componente real de alerta do produto.

## Aplicação no Farol

- Wordmark: `Farol` em Sora 700-800.
- Diferente do Winlist (lima em preto neutro), aqui é ciano frio em preto azulado — precisa ler como "instrumento sério", não "app de dropshipping animado".
