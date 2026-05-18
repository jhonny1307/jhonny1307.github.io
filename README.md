## in work progress
- Última atualização: **17/03/2026**

<script>
(function () {

  function criarBotoesPDF() {

    const h1s = document.querySelectorAll("h1");

    h1s.forEach((h1, index) => {

      const botao = document.createElement("button");

      botao.innerText = "Baixar seção em PDF";

      botao.style.cssText = `
        background: #000;
        color: white;
        border: none;
        padding: 10px 18px;
        border-radius: 999px;
        cursor: pointer;
        margin: 10px 0 25px 0;
        font-size: 14px;
        transition: 0.2s;
      `;

      botao.onmouseover = () => {
        botao.style.background = "#333";
      };

      botao.onmouseout = () => {
        botao.style.background = "#000";
      };

      botao.onclick = () => {
        gerarPDFDaSecao(h1, index);
      };

      h1.insertAdjacentElement("afterend", botao);
    });
  }

  function gerarPDFDaSecao(h1Atual, indexAtual) {

    const h1s = [...document.querySelectorAll("h1")];
    const proximoH1 = h1s[indexAtual + 1];

    const container = document.createElement("div");

    container.style.padding = "1.5cm";
    container.style.background = "white";

    let elemento = h1Atual;

    while (elemento && elemento !== proximoH1) {

      container.appendChild(elemento.cloneNode(true));

      elemento = elemento.nextElementSibling;
    }

    const janela = window.open("", "_blank");

    const titulo = h1Atual.innerText.trim() || "documento";

    janela.document.write(`
      <!DOCTYPE html>
      <html>
      <head>
        <title>${titulo}</title>

        <style>
          body {
            margin: 0;
            background: white;
            font-family: Arial, sans-serif;
          }

          button {
            display: none !important;
          }

          @media print {
            body {
              margin: 0;
            }
          }
        </style>
      </head>

      <body>
        ${container.innerHTML}

        <script>
          window.onload = () => {
            window.print();

            setTimeout(() => {
              window.close();
            }, 300);
          };
        <\/script>
      </body>
      </html>
    `);

    janela.document.close();
  }

  document.addEventListener("DOMContentLoaded", criarBotoesPDF);

})();
</script>

# sRPGAV

Um sistema de rpg moldado para investigação e ação


# Ficha

## Info

Nome\
Jogador\
AV\
Trilha\
Antecedente

Aparencia\
Personalidade\
Historico

## Atributos (teste: pass, (atributo)d20[apenas maior] >= DT(x))

(FOR) Força\
(AGI) Agilidade\
(INT) Intelecto\
(VIG) Vigor\
(PRE) Presença
- (HP) Vida 
- (CA) Defesa 
	- (BL) Bloqueio 
- (VL) Volume 
- (PA) Pontos de Areia
- (SAN) Sanidade 
- (RIP) Caido 

## Pericias (teste: pass, (atributo)d20[apenas maior]+pericia >= DT(x)) 

|| Pericia | Valor | Bonus |
|-|-|-|-|
|agi| Acrobacia |  |  |
|for| Atletismo |  |  |
|int| Conhecimento |  |  |
|agi| Crimes |  |  |
|pre| Enganação |  |  |
|agi| Furtividade |  |  |
|pre| Intimidação |  |  |
|int| Investigação |  |  |
|for| Luta |  |  |
|int| Medicina |  |  |
|int| Ocultismo |  |  |
|agi| Percepção |  |  |
|int| Pilotar |  |  |
|agi| Pontaria |  |  |
|pre| Persuasão |  |  |
|int| Profissão |  |  |
|vig| Sobrevivência |  |  |
|int| Tecnologia |  |  |

## Tabelas importantes

- Subindo de Nivel

|AV|Efeito|
|-|-|
|1|+1 Slot de Batom|
|2|Habilidade de Trilha|
|3|+1 em um Atributo|
|4|+1 Slot de Batom|
|5|Habilidade de Trilha|
|6|+1 em um Atributo|
|7|+1 Slot de Batom|
|8|Habilidade de Trilha|
|...||
|20|Habilidade de Trilha|

- Limite de atributos e pericias

||Max: Valor|Max: Bonus|Minimo|
|-|-|-|-|
|Atributos|5|3|0|
|Pericias|15|10|0|

|Min:|Valor|
|-|-|
|Atributos|0|
|Pericias|0|

- Dificuldades de Testes (DTs)

|Dificuldade|DT|
|-|-|
|Irrelevante|5|
|Muito fácil|10|
|Facil|15|
|Medio|20|
|Dificil|30|
|Insana|35|
|Quase Impossivel|45|

*a DT* **Quase Impossivel** *é usavel apenas com pericia no maximo e bonus na pericia do teste em 10 (maximo de pericia base e maximo de bonus)*

# cartas

| n° | content | = |
| ---: | :--- | ---: |
| 1° | a qualquer momento o jogador que te entregou essa prenda pode falar `congela' e você deve ficar parado nessa posição, caso se mova, pegue outra prenda | =
=
=
=
= |
