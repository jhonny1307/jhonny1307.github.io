# Currículo

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

<!-- Botão que NUNCA MAIS VAI TE FAZER SOFRER -->
<style>
  /* Esconde o botão no PDF */
  @media print {
    .no-print {
      display: none !important;
    }
    
    /* Quebra de página antes de h1 e h2 */
    h1, h2 {
      page-break-before: always;
    }
    
    /* Evita quebra no meio de parágrafos ou imagens */
    p, img, pre, table {
      page-break-inside: avoid;
    }
    
    /* Ajustes opcionais de margem */
    body {
      margin: 1.5cm;
    }
  }
</style>

<div style="text-align: center; margin: 20px 0;" class="no-print">
  <button onclick="gerarPDF()" 
          style="background-color: #4CAF50; color: white; padding: 12px 24px; 
                 border: none; border-radius: 4px; font-size: 16px; cursor: pointer;
                 box-shadow: 0 4px 6px rgba(0,0,0,0.1);">
    🖨️ Salvar como PDF (título, quebras, sem botão)
  </button>
</div>

<script>
function gerarPDF() {
  // 1. Define o título da página como nome sugerido do PDF
  const titulo = document.title || 'documento';
  document.title = titulo; // já existe, mas garantimos
  
  // 2. (Opcional) Se quiser remover acentos e espaços pro nome do arquivo
  const nomeArquivo = titulo
    .normalize('NFD')
    .replace(/[\u0300-\u036f]/g, '')
    .replace(/[^a-zA-Z0-9]/g, '_')
    .toLowerCase() || 'documento';
  
  // 3. Dispara a impressão
  window.print();
  
  // 4. Restaura o título original (se tiver mudado)
  //    Mas não precisa, porque o título já era esse.
}
</script>
