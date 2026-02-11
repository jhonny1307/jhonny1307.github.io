# Jhonny projects

Todos os meus projetos em um só lugar, em caso de repositorios dedicados o README.md tanto se encontra aqui quanto no repositorio dedicado, e aqui você encontrará um link te redirecionando ao repositorio escolhido

## Índice
- [md2pdf](https://jhonny1307.github.io/#md2pdf)

### md2pdf

Adiciona um botão a pagina que transforma toda a pagina em pdf, ignora o botão (ele mesmo) e funciona totalmente client-side, utilizando a função ```window.print()```

<style>
  @media print {
    .no-print, button {
      display: none !important;
    }
    
    html, body {
      margin: 0 !important;
      padding: 0 !important;
    }
    
    h1, h2 {
      page-break-before: always;
    }
    
    h1:first-of-type, h2:first-of-type {
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
          onmouseover="this.style.backgroundColor='#B71C1C'"
          onmouseout="this.style.backgroundColor='#D32F2F'">
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
