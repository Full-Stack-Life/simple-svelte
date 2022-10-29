<script>
  let name = "world";
  const src = "https://images.unsplash.com/photo-1666812272845-c5dcaae45453?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=387&q=80";
</script>

<h1>Hello {name.toUpperCase()}!</h1>
<p>
  "Os estilos aplicados dentro de um componente Svelte alteram apenas o seu
  escopo"
</p>
<!--
    Ao criar uma constante/váriavel com o mesmo nome do atributo pode-se apenas passar o valor
    como o exemplo abaixo
-->
<img {src} alt="arvore" />

<style>
  p {
    color: purple;
    font-family: 'Comic Sans MS', cursive;
    font-size: 2em;
  }
</style>
