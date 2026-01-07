---
layout: default
title: Categorias
permalink: /categorias/
---

<div class="periodic-table-wrapper">
  
  <div class="intro-text">
    <h2>Tabela de Categorias</h2>
    <p>Selecione um elemento para filtrar os posts.</p>
  </div>

  <div class="chem-grid">
    {% for category in site.categories %}
      {% assign cat_name = category[0] %}
      {% assign cat_slug = cat_name | downcase %} 
      {% assign post_count = category[1].size %}
      
      <a href="{{ site.baseurl }}/category/{{ cat_slug }}" class="element-card">
        
        <span class="atomic-number">{{ post_count }}</span>
        
        <div class="symbol">{{ cat_name | slice: 0, 2 }}</div>
        
        <div class="element-name">{{ cat_name }}</div>
        
      </a>
    {% endfor %}
  </div>

</div>

<style>
  /* Wrapper para centralizar tudo */
  .periodic-table-wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 40px 20px;
    max-width: 1200px;
    margin: 0 auto;
  }

  .intro-text {
    text-align: center;
    margin-bottom: 50px;
  }

  .intro-text h2 {
    font-size: 2.5em;
    background: var(--grad-chem);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    margin-bottom: 10px;
  }

  /* Grid Responsivo */
  .chem-grid {
    display: grid;
    /* Cards com largura mínima de 150px, preenchendo o espaço */
    grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
    gap: 25px;
    width: 100%;
    justify-content: center;
  }

  /* O Card "Elemento Químico" */
  .element-card {
    position: relative;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    aspect-ratio: 1 / 1; /* Garante que seja quadrado perfeito */
    
    background: rgba(255, 255, 255, 0.7);
    backdrop-filter: blur(10px);
    border: 2px solid rgba(255, 255, 255, 0.8);
    border-radius: 8px; /* Bordas levemente arredondadas mas ainda quadradas */
    box-shadow: 0 4px 15px rgba(0,0,0,0.05);
    
    text-decoration: none;
    transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
    cursor: pointer;
    overflow: hidden;
  }

  /* Efeito Hover */
  .element-card:hover {
    transform: translateY(-8px) scale(1.05);
    border-color: var(--chem-orange);
    background: #fff;
    box-shadow: 0 15px 30px rgba(255, 107, 53, 0.2);
  }
  
  /* Quando passa o mouse, o texto fica rosa */
  .element-card:hover .symbol,
  .element-card:hover .element-name {
    color: var(--chem-pink);
  }

  /* Detalhes do Card */
  .atomic-number {
    position: absolute;
    top: 10px;
    left: 12px;
    font-size: 0.9em;
    color: var(--text-medium);
    font-family: monospace;
  }

  .symbol {
    font-family: var(--header-font);
    font-size: 3.5em;
    font-weight: 700;
    line-height: 1;
    color: var(--text-dark);
    margin-top: 10px;
    transition: color 0.3s;
  }

  .element-name {
    font-size: 1em;
    font-weight: 500;
    color: var(--text-medium);
    margin-top: 5px;
    text-transform: capitalize;
    transition: color 0.3s;
  }

  /* Ajuste Mobile */
  @media (max-width: 600px) {
    .chem-grid {
      grid-template-columns: repeat(2, 1fr); /* 2 colunas no celular */
    }
    .symbol {
      font-size: 2.5em;
    }
  }
</style>