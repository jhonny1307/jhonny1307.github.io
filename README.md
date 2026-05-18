## in work progress
- Última atualização: **17/03/2026**

<script>
(function () {

  function gerarPDFDaSecao(h1) {

    // Guarda o conteúdo original da página.
    // Porque humanos adoram destruir o DOM temporariamente e depois fingir que nada aconteceu.
    const bodyOriginal = document.body.innerHTML;
    const tituloOriginal = document.title;

    // Cria container da seção
    const container = document.createElement("div");

    // Clona o H1 atual
    container.appendChild(h1.cloneNode(true));

    // Pega tudo até o próximo H1
    let atual = h1.nextElementSibling;

    while (atual && atual.tagName !== "H1") {
      container.appendChild(atual.cloneNode(true));
      atual = atual.nextElementSibling;
    }

    // Estilo de impressão
    const estilo = document.createElement("style");
    estilo.innerHTML = `
      @media print {
        body {
          margin: 1.5cm;
          font-family: sans-serif;
        }

        button {
          display: none !important;
        }
      }
    `;

    // Define título do PDF
    document.title = h1.innerText.trim() || "documento";

    // Substitui página temporariamente
    document.body.innerHTML = "";
    document.head.appendChild(estilo);
    document.body.appendChild(container);

    // Imprime
    window.print();

    // Restaura página
    setTimeout(() => {
      document.body.innerHTML = bodyOriginal;
      document.title = tituloOriginal;

      // Recria os botões depois de restaurar
      adicionarBotoes();

    }, 100);
  }

  function adicionarBotoes() {

    const h1s = document.querySelectorAll("h1");

    h1s.forEach((h1) => {

      // Evita duplicar botão
      if (h1.nextElementSibling?.classList?.contains("pdf-section-button")) {
        return;
      }

      const botao = document.createElement("button");

      botao.innerText = "📄 Baixar esta seção";
      botao.className = "pdf-section-button";

      botao.style.cssText = `
        background-color: black;
        color: white;
        border: none;
        padding: 10px 20px;
        border-radius: 999px;
        cursor: pointer;
        margin: 10px 0 25px 0;
        font-size: 15px;
        transition: 0.2s;
        display: block;
      `;

      botao.onmouseover = () => {
        botao.style.backgroundColor = "#333";
      };

      botao.onmouseout = () => {
        botao.style.backgroundColor = "black";
      };

      botao.onclick = () => gerarPDFDaSecao(h1);

      h1.insertAdjacentElement("afterend", botao);
    });
  }

  // Inicializa
  adicionarBotoes();

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
