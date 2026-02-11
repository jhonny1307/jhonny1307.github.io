# Currículo

- teste 3

### Informações Pessoais

Nome: **João Mayer Mendes Cordeiro**\
Data de nascimento: **13/07/2009**\
Email: **joao.mayer.m.c@gmail.com**\
Telefone: **(61) 99415-2099**\
Situação atual: **Estudante**

### Sobre mim

Estudante interessado em tecnologia, programação e criação de projetos digitais. Tenho facilidade para aprender ferramentas novas, resolver problemas e trabalhar com lógica e criatividade. Busco oportunidades para desenvolver experiência prática e crescer profissionalmente.

### Formação

+ Ensino Médio incompleto\
  Colégio Católica de Brasília\
  Previsão de conclusão: 2027
+ Estudo autodidata em programação

### Experiências

**Projetos pessoais em tecnologia**
- Desenvolvimento e testes de projetos próprios
- Aprendizado prático de programação e lógica computacional
- Exploração de ferramentas digitais e criação de conteúdo

<button onclick="gerarPDFRelativo(this)">📄 Baixar PDF</button>

<script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>

<script>
async function gerarPDFRelativo(botao) {

  const { jsPDF } = window.jspdf;

  const pdf = new jsPDF({
    unit: "mm",
    format: "a4"
  });

  const pageHeight = pdf.internal.pageSize.getHeight();
  const pageWidth = pdf.internal.pageSize.getWidth();

  let y = 10;

  function novaPaginaSePreciso(altura = 10){
    if(y + altura > pageHeight - 10){
      pdf.addPage();
      y = 10;
    }
  }

  // Pega o container pai
  const parent = botao.parentElement;

  // Pega todos os elementos antes do botão
  const elementos = [];

  for(const el of parent.children){
    if(el === botao) break;
    elementos.push(el);
  }

  for(const el of elementos){

    // HEADERS
    if(/^H[1-6]$/.test(el.tagName)){
      const tamanho = {
        H1:22, H2:18, H3:16, H4:14, H5:12, H6:11
      }[el.tagName];

      pdf.setFontSize(tamanho);

      const linhas = pdf.splitTextToSize(el.innerText, pageWidth - 20);
      novaPaginaSePreciso(linhas.length * 6);

      pdf.text(linhas, 10, y);
      y += linhas.length * 6 + 4;
    }

    // PARÁGRAFO
    else if(el.tagName === "P"){
      pdf.setFontSize(12);

      const linhas = pdf.splitTextToSize(el.innerText, pageWidth - 20);
      novaPaginaSePreciso(linhas.length * 5);

      pdf.text(linhas, 10, y);
      y += linhas.length * 5 + 4;
    }

    // LISTA
    else if(el.tagName === "UL" || el.tagName === "OL"){
      pdf.setFontSize(12);

      for(const li of el.children){
        const linhas = pdf.splitTextToSize("• " + li.innerText, pageWidth - 20);
        novaPaginaSePreciso(linhas.length * 5);

        pdf.text(linhas, 10, y);
        y += linhas.length * 5 + 2;
      }
      y += 4;
    }

    // IMAGEM (único lugar que usa html2canvas)
    else if(el.tagName === "IMG"){

      const canvas = await html2canvas(el, {
        useCORS:true,
        scale:2
      });

      const imgData = canvas.toDataURL("image/png");

      const imgWidth = pageWidth - 20;
      const imgHeight = canvas.height * imgWidth / canvas.width;

      novaPaginaSePreciso(imgHeight);

      pdf.addImage(imgData, "PNG", 10, y, imgWidth, imgHeight);
      y += imgHeight + 6;
    }

  }

  pdf.save("README.pdf");
}
</script>
