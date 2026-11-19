# Ficha do Enxame â€” /swarm do Google Antigravity sem bagunÃ§a

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="48" />
  <p><strong>Arckhé AI</strong></p>
</div>


[![Ficha do Enxame](guia/assets/banner.jpg)](https://inematds.github.io/enxame-antigravity/guia/)

**ðŸ‡§ðŸ‡· [PortuguÃªs](README.md) Â· ðŸ‡ºðŸ‡¸ [English](README.en.md) Â· ðŸ‡ªðŸ‡¸ [EspaÃ±ol](README.es.md)**

## O que Ã©

VocÃª ainda pede tudo para um agente sÃ³? O `/swarm` do Google Antigravity (app e CLI, em prÃ©via para Google AI Pro e Ultra) divide uma tarefa entre vÃ¡rios agentes com nome, que trabalham ao mesmo tempo, e pÃµe um verificador para revisar e testar. Ele sÃ³ funciona bem se as partes nÃ£o se atropelarem. A **Ficha do Enxame** Ã© uma folha curta que vocÃª escreve antes de digitar `/swarm`: quem Ã© dono de quÃª, o que cada um nÃ£o toca, quando estÃ¡ pronto, quem verifica e quando parar. Este kit traz o modelo, um conferidor que dÃ¡ nota de 0 a 8 e monta o texto para colar, e um ajudante que diz se o caso Ã© mesmo de enxame. Precisa sÃ³ de Python 3.

> **Importante:** este kit **nÃ£o testou o /swarm**. O Antigravity nÃ£o estÃ¡ instalado na mÃ¡quina onde ele foi feito. Tudo sobre o `/swarm` vem da [documentaÃ§Ã£o oficial](https://antigravity.google/docs/swarm). As "saÃ­das reais" deste repositÃ³rio sÃ£o do `checar.py`, que sÃ³ lÃª o Markdown da ficha.

## ðŸ“– Guia de uso

Guia completo (landing + passo a passo): **https://inematds.github.io/enxame-antigravity/guia/**

ðŸŽ¬ VÃ­deo: em breve no guia.

## O processo, do inÃ­cio ao fim

Quem faz: ðŸ§  vocÃª Â· âš™ï¸ script deste kit Â· ðŸ¤– o `/swarm` no Antigravity

| # | Passo | Comando | Quem |
|---|---|---|---|
| 1 | Ver se o caso Ã© de enxame (ou de subagente, `/boost`, `/teamwork`) | `python3 escolher.py` (perguntas) ou `python3 escolher.py --divide-limpo sim` | ðŸ§  + âš™ï¸ |
| 2 | Copiar o modelo e preencher: tarefa, como verificar, peÃ§as, verificador, limites | `cp modelos/FICHA.md minha-ficha.md` | ðŸ§  |
| 3 | Conferir a ficha: 8 itens, nota 0â€“8, com o motivo e como corrigir | `python3 checar.py minha-ficha.md` | âš™ï¸ |
| 4 | Corrigir os âœ˜ e conferir de novo atÃ© nota 7 ou 8 | `python3 checar.py minha-ficha.md` | ðŸ§  |
| 5 | Gerar o texto pronto para colar (PT; `--en` monta o esqueleto em inglÃªs). SÃ³ sai com nota â‰¥ 7; abaixo disso mostra o que corrigir e sai com cÃ³digo 1 | `python3 checar.py minha-ficha.md --prompt` | âš™ï¸ |
| 6 | No Antigravity, colar a linha inteira (ela jÃ¡ comeÃ§a com `/swarm`). Se o comando colado nÃ£o for reconhecido, digitar `/swarm`, Tab, e colar o resto | `/swarm â€¦` | ðŸ§  |
| 7 | O coordenador divide, cria os workers com o brief de cada um e o `@verifier` | â€” | ðŸ¤– |
| 8 | Acompanhar o quadro e responder aprovaÃ§Ãµes | app: painel Swarm (Board, Members, Graph) Â· CLI: `/swarm board`, Alt+S, Alt+J | ðŸ§  |
| 9 | O verificador lÃª os diffs e roda o comando; o coordenador reporta | â€” | ðŸ¤– |
| 10 | Rodar vocÃª mesmo o comando de "Como verificar" e pedir ao coordenador para remover quem terminou | o comando da sua ficha | ðŸ§  |

ManutenÃ§Ã£o do kit (quando mudar `checar.py` ou um exemplo):

```bash
python3 -m unittest -v
for d in calculadora-roi landing-page investigacao-lenta testes-por-pacote; do
  python3 checar.py exemplos/$d/ficha.md --prompt    > exemplos/$d/prompt.txt
  python3 checar.py exemplos/$d/ficha.md --prompt --en > exemplos/$d/prompt.en.txt
done
```

## O que tem aqui

| Arquivo | Para quÃª |
|---|---|
| `modelos/FICHA.md` | Modelo da ficha (Markdown simples, em PT) |
| `checar.py` | Confere 8 itens, nota 0â€“8; `--prompt` (sÃ³ com nota â‰¥ 7), `--en`, `--json`; sai com 0 se a nota for â‰¥ 7 |
| `escolher.py` | Subagente, `/boost`, `/swarm` ou `/teamwork`, pela tabela oficial; flags ou perguntas |
| `exemplos/` | 4 fichas nota 8 (calculadora de ROI com 4 entradas, landing page, investigaÃ§Ã£o lenta, testes por pacote), uma ficha ruim, os `prompt.txt` gerados e `saidas.txt` |
| `CUIDADOS.md` | Cota, prÃ©via, worker sem cota, remover Ã© permanente, relato de bloqueio de conta |
| `tests/` | `python3 -m unittest -v` |

## Os 8 itens do `checar.py`

1. Tarefa escrita.
2. "Como verificar" com um comando entre crases.
3. Pelo menos 2 peÃ§as (com uma sÃ³, use um agente sÃ³ ou um subagente).
4. Toda peÃ§a tem dono (arquivos e pastas entre crases, ou uma pergunta, para investigaÃ§Ã£o).
5. Donos nÃ£o se sobrepÃµem: mesmo arquivo, pasta que contÃ©m arquivo de outro, glob simples (padrÃ£o com `*`, como `src/*.js`).
6. Toda peÃ§a tem "nÃ£o mexe" e "pronto quando".
7. Verificador com "roda"; avisa se faltar proporÃ§Ã£o (1 para cada 2â€“4 peÃ§as) ou se o modelo nÃ£o for diferente do dos workers.
8. Limites de cota e de parada, e nenhuma frase pedindo laÃ§o sem supervisÃ£o (a negaÃ§Ã£o, "nada de laÃ§o", passa).

SaÃ­da real (do `checar.py`, nÃ£o do `/swarm`) no exemplo ruim:

```text
âœ˜ 5. Donos nÃ£o se sobrepÃµem â€” colisÃ£o: @design `site/` Ã— @textos `site/index.html`
   â†’ como corrigir: DÃª cada arquivo a uma peÃ§a sÃ³. Se duas precisam do mesmo arquivo, quebre o arquivo em partes, junte as duas peÃ§as numa sÃ³, ou peÃ§a cÃ³pias de trabalho (working copy) para cada worker.
Nota: 2/8 â€” ainda nÃ£o: corrija os âœ˜ antes do /swarm
```

Todas as saÃ­das: [`exemplos/saidas.txt`](exemplos/saidas.txt).

**Sobre o `--en`:** sÃ³ o esqueleto do texto ("Give each piece its own worker", "Add 1 verifierâ€¦") sai em inglÃªs; o que vocÃª escreveu na ficha vai como estÃ¡.

## Fontes

- DocumentaÃ§Ã£o oficial do `/swarm`: https://antigravity.google/docs/swarm
- Comandos (`/boost`, `/teamwork` e outros): https://antigravity.google/docs/slash-commands
- `/teamwork`: https://antigravity.google/docs/teamwork

Kit aberto e grÃ¡tis do [INEMA.CLUB](https://inema.club). LicenÃ§a MIT.

---

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="32" />
  <p><strong>Arckhé AI</strong></p>
</div>