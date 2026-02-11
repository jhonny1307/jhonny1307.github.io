# Currículo

### Informações Pessoais

Nome: **João Mayer Mendes Cordeiro**\
Data de nascimento: **13/07/2009**\
Email: **joao.mayer.m.c@gmail.com**\
Telefone: **(61) 99415-2099**\
Situação atual: **Estudante**

### Sobre mim

Estudante interessado em tecnologia, programação e criação de projetos digitais. Tenho facilidade para aprender ferramentas novas, resolver problemas e trabalhar com lógica e criatividade. Busco oportunidades para desenvolver experiência prática e crescer profissionalmente.

### Formação

+ Ensino Médio incompleto
  Colégio Católica de Brasília
  Previsão de conclusão: 2027
+ Estudo autodidata em programação

### Experiências

**Projetos pessoais em tecnologia**
• Desenvolvimento e testes de projetos próprios
• Aprendizado prático de programação e lógica computacional
• Exploração de ferramentas digitais e criação de conteúdo

<!-- html2pdf CDN -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js"></script>

<button onclick="baixarPDF()" style="
padding:10px 16px;
background:#24292e;
color:white;
border:none;
border-radius:6px;
cursor:pointer;
font-weight:bold;
">
📄 Baixar PDF
</button>

<script>
function baixarPDF() {
    const element = document.body; // pega a página toda

    html2pdf()
        .set({
            margin: 10,
            filename: 'README.pdf',
            image: { type: 'jpeg', quality: 0.98 },
            html2canvas: { scale: 2 },
            jsPDF: { unit: 'mm', format: 'a4', orientation: 'portrait' }
        })
        .from(element)
        .save();
}
</script>
