<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Doces com Morango</title>
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: #fff0f6;
      color: #7a1f2f;
      margin: 0;
      padding: 20px;
      display: flex;
      flex-direction: column;
      align-items: center;
    }
    header {
      text-align: center;
      margin-bottom: 25px;
    }
    header h1 {
      font-size: 2.8rem;
      margin: 0;
    }
    header p {
      font-size: 1.2rem;
      font-style: italic;
      color: #a63a4d;
    }
    .strawberry-img {
      max-width: 200px;
      margin-top: 15px;
      border-radius: 15px;
      box-shadow: 0 4px 10px rgba(122,31,47,0.3);
      transition: transform 0.3s ease;
      cursor: pointer;
    }
    .strawberry-img:hover {
      transform: scale(1.05);
    }
    /* Efeito pulsar */
    .pulse {
      animation: pulse 0.6s ease;
    }
    @keyframes pulse {
      0% { transform: scale(1); }
      50% { transform: scale(1.15); }
      100% { transform: scale(1); }
    }
    main {
      max-width: 600px;
      background: #ffe6ea;
      border-radius: 15px;
      padding: 20px;
      box-shadow: 0 6px 12px rgba(122,31,47,0.15);
    }
    h2 {
      color: #a63a4d;
    }
    ul {
      list-style-type: none;
      padding: 0;
    }
    li {
      background: #fff0f6;
      margin-bottom: 12px;
      padding: 12px 15px;
      border-radius: 10px;
      box-shadow: 0 3px 6px rgba(122,31,47,0.1);
      cursor: pointer;
      transition: background 0.3s;
    }
    li:hover {
      background: #f9c8d6;
    }
    .description {
      margin-top: 15px;
      font-size: 1.1rem;
      font-weight: 600;
      color: #7a1f2f;
    }
    .recipe {
      margin-top: 15px;
      background: #fff0f6;
      padding: 15px;
      border-radius: 12px;
      box-shadow: 0 2px 5px rgba(122,31,47,0.1);
      font-size: 1rem;
      line-height: 1.4;
      white-space: pre-line;
    }
  </style>
</head>
<body>
  <header>
    <h1>Doces com Morango</h1>
    <p>Delícias que conquistam qualquer paladar!</p>
    <img class="strawberry-img" id="strawberryPhoto" src="https://upload.wikimedia.org/wikipedia/commons/2/29/PerfectStrawberry.jpg" alt="Morangos frescos" />
  </header>
  <main>
    <h2>Escolha um doce para saber mais:</h2>
    <ul id="sweetList">
      <li data-desc="Clássico bolo feito com camadas de morango fresco e chantilly."
          data-recipe="Ingredientes:
           3 ovos
           2 xícaras de farinha
           1 xícara de açúcar
           1 colher de fermento
           Morangos frescos
           Chantilly
           Modo de preparo: Bata os ovos com açúcar até formar um creme. Acrescente a farinha e o fermento e misture. Asse em forno pré-aquecido a 180°C por 30 minutos. Corte o bolo em camadas, recheie com chantilly e morangos. Decore com mais chantilly e morangos por cima.">Bolo de Morango</li>
      
      <li data-desc="Sobremesa gelada feita com morangos frescos e creme chantilly."
          data-recipe="Ingredientes:
          300g de morangos
          1 lata de leite condensado
          1 lata de creme de leite 
          1 pacote de gelatina sem sabor
          Chantilly para decorar
          Modo de preparo:
          Hidrate e dissolva a gelatina conforme instruções. Bata os morangos no liquidificador. Misture o leite condensado, creme de leite e a gelatina. Acrescente o purê de morangos e misture. Leve à geladeira por 4 horas. Decore com chantilly antes de servir.">Mousse de Morango</li>
      
      <li data-desc="Tortinha crocante recheada com creme e coberta com morangos."
          data-recipe="Ingredientes:
         Massa pronta para torta
         300ml de creme de leite
         1 lata de leite condensado
         Morangos frescos
         Modo de preparo:
         Forre a forma com a massa e asse conforme instruções. Misture o creme de leite com leite condensado para o recheio. Despeje o recheio na massa e leve para gelar. Decore com morangos fatiados antes de servir.">Torta de Morango</li>
      
      <li data-desc="Smoothie refrescante feito com morangos e iogurte natural."
          data-recipe="Ingredientes:
          200g de morangos
          1 copo de iogurte natural
          1 colher de mel
         Gelo a gosto
         Modo de preparo:
        Bata todos os ingredientes no liquidificador até ficar cremoso. Sirva gelado.">Vitamina de Morango</li>
      
      <li data-desc="Picolé saudável feito com morangos e suco natural."
          data-recipe="Ingredientes:
          300g de morangos
          1 xícara de suco de laranja natural
          Modo de preparo:
          Bata os morangos com o suco no liquidificador. Despeje em formas de picolé. Leve ao congelador por pelo menos 6 horas. Desenforme e aproveite.">Picolé de Morango</li>
    </ul>
    <div class="description" id="descArea">Clique em um doce para ver a descrição.</div>
    <div class="recipe" id="recipeArea"></div>
  </main>

  <script>
    const sweetList = document.getElementById('sweetList');
    const descArea = document.getElementById('descArea');
    const recipeArea = document.getElementById('recipeArea');
    const strawberryPhoto = document.getElementById('strawberryPhoto');

    // Ao clicar no doce
    sweetList.addEventListener('click', (e) => {
      if (e.target && e.target.nodeName === 'LI') {
        const desc = e.target.getAttribute('data-desc');
        const recipe = e.target.getAttribute('data-recipe');
        descArea.textContent = desc;
        recipeArea.textContent = recipe;
      }
    });

    // Ao clicar na foto do morango
    strawberryPhoto.addEventListener('click', () => {
      strawberryPhoto.classList.add('pulse');
      alert("🍓 Você clicou no morango! Humm... já bateu a vontade de um docinho?");
      setTimeout(() => strawberryPhoto.classList.remove('pulse'), 600);
    });
  </script>
</body>
</html>
