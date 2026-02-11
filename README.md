# Currículo

- teste 1

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

<!-- Botão -->
<button onclick="gerarPDF()">📄 Baixar PDF</button>

<!-- jsPDF CDN -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>

<script>
async function gerarPDF() {
    const { jsPDF } = window.jspdf;

    const pdf = new jsPDF();

    // Pega TODO o conteúdo renderizado da página
    const texto = document.body.innerText;

    // Divide texto em linhas que cabem na página
    const linhas = pdf.splitTextToSize(texto, 180);

    pdf.text(linhas, 10, 10);

    pdf.save("README.pdf");
}
</script>
