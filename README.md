<style> 
  @media print {
    .no-print, button {
      display: none !important;
    }
    
    html, body {
      margin: 0 !important;
      padding: 0 !important;
    }
    
    h1 {
      page-break-before: always;
    }
    
    h1:first-of-type {
      page-break-before: avoid;
    }
    
    body {
      margin: 1.5cm !important;
    }
  }
</style>

<div style="text-align: center; margin: 20px 0;">
  <button onclick="gerarPDFPerfeito()" 
          style="background-color: #000000; color: white; padding: 14px 28px; 
                 border: none; border-radius: 50px; font-size: 18px; cursor: pointer; 
                 box-shadow: 0 4px 6px rgba(0,0,0,0.1); transition: 0.2s;"
          class="no-print"
          onmouseover="this.style.backgroundColor='#333333'"
          onmouseout="this.style.backgroundColor='#000000'">
    Download PDF
  </button>
</div>

<script>
  function gerarPDFPerfeito() {
    const tituloOriginal = document.title;
    const primeiroH1 = document.querySelector('h1');
    const nomePDF = primeiroH1 
      ? primeiroH1.innerText.trim() 
      : document.title || 'documento';
    document.title = nomePDF;
    window.print();
    
    setTimeout(() => {
      document.title = tituloOriginal;
    }, 100);
  }
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
	- (EV) Evasão 
	- (BL) Bloqueio 
- (VL) Volume 
- (FL) Carga 
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
|1|Batom|
|2|Habilidade|
|3|Atributo|
|4|Batom|
|5|Habilidade|
|6|Atributo|
|7|Batom|
|8|Habilidade|
|...||
|20|Habilidade|

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
