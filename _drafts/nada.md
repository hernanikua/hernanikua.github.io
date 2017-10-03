---
published: false
---

Las direcitvas de Angular son una parte fundamental del Framework. De hecho los componentes son diretivas con un template asociado.

Existen tres tipos de directivas:

1. **Componentes**, directivas con un template.
1. **Directivas estructurales**, crean y destruyen elementos del DOM.
1. **Directivas de atributo**, cambian la apariencia o comportamiento de un elemento, componente u otra directiva.

Para crear una directiva estructural propia, habitualmente, se utilizan las etiquetas <ng-content> y <ng-template>. <ng-content> da soporte al html que compone la directiva. el contenido de <ng-template> no se renderiza en al navegador y puede contener html que insertaremos en <ng-content> según nuestras necesidades.


<iframe
  src="https://embed.plnkr.co/OUi5LevpIstJYVwXrOVn/?t=run"
  frameborder="0"
  width="100%"
  height="480px"
  allowfullscreen="allowfullscreen"
  frameborder="0"
>
Cargando Plunk...
</iframe>
