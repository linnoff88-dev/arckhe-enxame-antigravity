ï»¿# Ficha do Enxame ê¢â¬â /swarm do Google Antigravity sem bagunêÂ§a

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="48" />
  <p><strong>Arckhé AI</strong></p>
</div>


[![Ficha do Enxame](guia/assets/banner.jpg)](https://linnoff88-dev.github.io/arckhe-/guia/)

**ê°Å¸â¡Â§ê°Å¸â¡Â· [PortuguêÂªs](README.md) êÂ· ê°Å¸â¡Âºê°Å¸â¡Â¸ [English](README.en.md) êÂ· ê°Å¸â¡Âªê°Å¸â¡Â¸ [EspaêÂ±ol](README.es.md)**

## O que êÂ©

VocêÂª ainda pede tudo para um agente sêÂ³? O `/swarm` do Google Antigravity (app e CLI, em prêÂ©via para Google AI Pro e Ultra) divide uma tarefa entre vêÂ¡rios agentes com nome, que trabalham ao mesmo tempo, e pêÂµe um verificador para revisar e testar. Ele sêÂ³ funciona bem se as partes nêÂ£o se atropelarem. A **Ficha do Enxame** êÂ© uma folha curta que vocêÂª escreve antes de digitar `/swarm`: quem êÂ© dono de quêÂª, o que cada um nêÂ£o toca, quando estêÂ¡ pronto, quem verifica e quando parar. Este kit traz o modelo, um conferidor que dêÂ¡ nota de 0 a 8 e monta o texto para colar, e um ajudante que diz se o caso êÂ© mesmo de enxame. Precisa sêÂ³ de Python 3.

> **Importante:** este kit **nêÂ£o testou o /swarm**. O Antigravity nêÂ£o estêÂ¡ instalado na mêÂ¡quina onde ele foi feito. Tudo sobre o `/swarm` vem da [documentaêÂ§êÂ£o oficial](https://antigravity.google/docs/swarm). As "saêÂ­das reais" deste repositêÂ³rio sêÂ£o do `checar.py`, que sêÂ³ lêÂª o Markdown da ficha.

## ê°Å¸ââ Guia de uso

Guia completo (landing + passo a passo): **https://linnoff88-dev.github.io/arckhe-/guia/**

ê°Å¸Å½Â¬ VêÂ­deo: em breve no guia.

## O processo, do inêÂ­cio ao fim

Quem faz: ê°Å¸Â§Â  vocêÂª êÂ· ê¢Å¡â¢ê¯Â¸Â script deste kit êÂ· ê°Å¸Â¤â o `/swarm` no Antigravity

| # | Passo | Comando | Quem |
|---|---|---|---|
| 1 | Ver se o caso êÂ© de enxame (ou de subagente, `/boost`, `/teamwork`) | `python3 escolher.py` (perguntas) ou `python3 escolher.py --divide-limpo sim` | ê°Å¸Â§Â  + ê¢Å¡â¢ê¯Â¸Â |
| 2 | Copiar o modelo e preencher: tarefa, como verificar, peêÂ§as, verificador, limites | `cp modelos/FICHA.md minha-ficha.md` | ê°Å¸Â§Â  |
| 3 | Conferir a ficha: 8 itens, nota 0ê¢â¬â8, com o motivo e como corrigir | `python3 checar.py minha-ficha.md` | ê¢Å¡â¢ê¯Â¸Â |
| 4 | Corrigir os ê¢ÅË e conferir de novo atêÂ© nota 7 ou 8 | `python3 checar.py minha-ficha.md` | ê°Å¸Â§Â  |
| 5 | Gerar o texto pronto para colar (PT; `--en` monta o esqueleto em inglêÂªs). SêÂ³ sai com nota ê¢â°Â¥ 7; abaixo disso mostra o que corrigir e sai com cêÂ³digo 1 | `python3 checar.py minha-ficha.md --prompt` | ê¢Å¡â¢ê¯Â¸Â |
| 6 | No Antigravity, colar a linha inteira (ela jêÂ¡ comeêÂ§a com `/swarm`). Se o comando colado nêÂ£o for reconhecido, digitar `/swarm`, Tab, e colar o resto | `/swarm ê¢â¬Â¦` | ê°Å¸Â§Â  |
| 7 | O coordenador divide, cria os workers com o brief de cada um e o `@verifier` | ê¢â¬â | ê°Å¸Â¤â |
| 8 | Acompanhar o quadro e responder aprovaêÂ§êÂµes | app: painel Swarm (Board, Members, Graph) êÂ· CLI: `/swarm board`, Alt+S, Alt+J | ê°Å¸Â§Â  |
| 9 | O verificador lêÂª os diffs e roda o comando; o coordenador reporta | ê¢â¬â | ê°Å¸Â¤â |
| 10 | Rodar vocêÂª mesmo o comando de "Como verificar" e pedir ao coordenador para remover quem terminou | o comando da sua ficha | ê°Å¸Â§Â  |

ManutenêÂ§êÂ£o do kit (quando mudar `checar.py` ou um exemplo):

```bash
python3 -m unittest -v
for d in calculadora-roi landing-page investigacao-lenta testes-por-pacote; do
  python3 checar.py exemplos/$d/ficha.md --prompt    > exemplos/$d/prompt.txt
  python3 checar.py exemplos/$d/ficha.md --prompt --en > exemplos/$d/prompt.en.txt
done
```

## O que tem aqui

| Arquivo | Para quêÂª |
|---|---|
| `modelos/FICHA.md` | Modelo da ficha (Markdown simples, em PT) |
| `checar.py` | Confere 8 itens, nota 0ê¢â¬â8; `--prompt` (sêÂ³ com nota ê¢â°Â¥ 7), `--en`, `--json`; sai com 0 se a nota for ê¢â°Â¥ 7 |
| `escolher.py` | Subagente, `/boost`, `/swarm` ou `/teamwork`, pela tabela oficial; flags ou perguntas |
| `exemplos/` | 4 fichas nota 8 (calculadora de ROI com 4 entradas, landing page, investigaêÂ§êÂ£o lenta, testes por pacote), uma ficha ruim, os `prompt.txt` gerados e `saidas.txt` |
| `CUIDADOS.md` | Cota, prêÂ©via, worker sem cota, remover êÂ© permanente, relato de bloqueio de conta |
| `tests/` | `python3 -m unittest -v` |

## Os 8 itens do `checar.py`

1. Tarefa escrita.
2. "Como verificar" com um comando entre crases.
3. Pelo menos 2 peêÂ§as (com uma sêÂ³, use um agente sêÂ³ ou um subagente).
4. Toda peêÂ§a tem dono (arquivos e pastas entre crases, ou uma pergunta, para investigaêÂ§êÂ£o).
5. Donos nêÂ£o se sobrepêÂµem: mesmo arquivo, pasta que contêÂ©m arquivo de outro, glob simples (padrêÂ£o com `*`, como `src/*.js`).
6. Toda peêÂ§a tem "nêÂ£o mexe" e "pronto quando".
7. Verificador com "roda"; avisa se faltar proporêÂ§êÂ£o (1 para cada 2ê¢â¬â4 peêÂ§as) ou se o modelo nêÂ£o for diferente do dos workers.
8. Limites de cota e de parada, e nenhuma frase pedindo laêÂ§o sem supervisêÂ£o (a negaêÂ§êÂ£o, "nada de laêÂ§o", passa).

SaêÂ­da real (do `checar.py`, nêÂ£o do `/swarm`) no exemplo ruim:

```text
ê¢ÅË 5. Donos nêÂ£o se sobrepêÂµem ê¢â¬â colisêÂ£o: @design `site/` êâ @textos `site/index.html`
   ê¢â â como corrigir: DêÂª cada arquivo a uma peêÂ§a sêÂ³. Se duas precisam do mesmo arquivo, quebre o arquivo em partes, junte as duas peêÂ§as numa sêÂ³, ou peêÂ§a cêÂ³pias de trabalho (working copy) para cada worker.
Nota: 2/8 ê¢â¬â ainda nêÂ£o: corrija os ê¢ÅË antes do /swarm
```

Todas as saêÂ­das: [`exemplos/saidas.txt`](exemplos/saidas.txt).

**Sobre o `--en`:** sêÂ³ o esqueleto do texto ("Give each piece its own worker", "Add 1 verifierê¢â¬Â¦") sai em inglêÂªs; o que vocêÂª escreveu na ficha vai como estêÂ¡.

## Fontes

- DocumentaêÂ§êÂ£o oficial do `/swarm`: https://antigravity.google/docs/swarm
- Comandos (`/boost`, `/teamwork` e outros): https://antigravity.google/docs/slash-commands
- `/teamwork`: https://antigravity.google/docs/teamwork

Kit aberto e grêÂ¡tis do [ARCKHÉ AI](https://ARCKHÉ AI). LicenêÂ§a MIT.

---

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="32" />
  <p><strong>Arckhé AI</strong></p>
</div>