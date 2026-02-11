# Currículo

- teste 4

![vampeta](https://veja.abril.com.br/wp-content/uploads/2025/07/vampeta-tvpop.jpg?quality=70&strip=info&w=672&h=416&crop=1)

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

<!-- Botão com abordagem híbrida: jsPDF para texto + html2canvas só para imagens -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>

<div style="text-align: center; margin: 20px 0;">
  <button onclick="gerarPDFHibrido()" 
          style="background-color: #2196F3; color: white; padding: 12px 24px; 
                 border: none; border-radius: 4px; font-size: 16px; cursor: pointer;">
    🖼️ PDF com imagens (híbrido)
  </button>
</div>

<script>
async function gerarPDFHibrido() {
  const pdf = new jspdf.jsPDF();
  let y = 20; // posição vertical inicial

  // --- CAPTURAR TÍTULO PRINCIPAL (jsPDF puro) ---
  const titulo = document.querySelector('h1')?.innerText || 'Documento';
  pdf.setFont('helvetica', 'bold');
  pdf.setFontSize(22);
  pdf.text(titulo, 20, y);
  y += 15;

  // --- CAPTURAR PARÁGRAFOS COM FORMATAÇÃO ---
  const paragrafos = document.querySelectorAll('p');
  for (const p of paragrafos) {
    // Detecta se o parágrafo contém imagem
    const temImagem = p.querySelector('img');
    
    if (temImagem) {
      // CASO 1: Parágrafo com imagem → usa html2canvas SÓ NESTE ELEMENTO
      const canvas = await html2canvas(p, {
        scale: 2, // melhor qualidade
        logging: false,
        allowTaint: false,
        useCORS: true
      });
      const imgData = canvas.toDataURL('image/png');
      
      // Calcula largura proporcional no PDF (máx 170mm)
      const imgWidth = 170;
      const imgHeight = (canvas.height * imgWidth) / canvas.width;
      
      pdf.addImage(imgData, 'PNG', 20, y, imgWidth, imgHeight);
      y += imgHeight + 10;
    } else {
      // CASO 2: Só texto → jsPDF puro com formatação
      const texto = p.innerText;
      
      // Detecta se é negrito/itálico pelo CSS ou tags
      const isBold = window.getComputedStyle(p).fontWeight >= 600;
      const isItalic = window.getComputedStyle(p).fontStyle === 'italic';
      
      let fontStyle = 'normal';
      if (isBold && isItalic) fontStyle = 'bolditalic';
      else if (isBold) fontStyle = 'bold';
      else if (isItalic) fontStyle = 'italic';
      
      pdf.setFont('helvetica', fontStyle);
      pdf.setFontSize(12);
      
      // Quebra de linha automática
      const linhas = pdf.splitTextToSize(texto, 170);
      pdf.text(linhas, 20, y);
      y += linhas.length * 7;
    }
  }

  // --- CAPTURAR IMAGENS ISOLADAS (fora de parágrafos) ---
  const imagensSoltas = document.querySelectorAll('img:not(p img)');
  for (const img of imagensSoltas) {
    const canvas = await html2canvas(img, {
      scale: 2,
      backgroundColor: '#ffffff'
    });
    const imgData = canvas.toDataURL('image/png');
    
    // Tenta pegar dimensões originais da imagem
    const imgWidth = 80; // largura fixa ou você pode calcular
    const imgHeight = (canvas.height * imgWidth) / canvas.width;
    
    pdf.addImage(imgData, 'PNG', 20, y, imgWidth, imgHeight);
    y += imgHeight + 10;
  }

  // Salva o PDF
  pdf.save('documento_com_imagens.pdf');
}
</script>
