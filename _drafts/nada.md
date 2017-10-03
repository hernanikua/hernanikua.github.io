---
published: false
---

Las direcitvas de Angular son una parte fundamental del Framework. De hecho los componentes son diretivas con un template asociado.

Existen tres tipos de directivas:

1. **Componentes**, directivas con un template.
1. **Directivas estructurales**, crean y destruyen elementos del DOM.
1. **Directivas de atributo**, cambian la apariencia o comportamiento de un elemento, componente u otra directiva.

Para crear una directiva estructural propia, habitualmente, se utilizan las etiquetas <ng-content> y <ng-template>. <ng-content> dará soporte al html que compone la directiva. El contenido de <ng-template> no se renderiza en al navegador y puede contener html que posteriormente podemos insertar en <ng-content>, según nuestras necesidades. Mediante <ng-template> facilitamos la configuración de la directiva.

{% highlight ts %}

<button class="btn-abrir" [tooltip]="{posicion:'abajo'}">

	<ng-container #vc></ng-container>

      <ng-template>
        ><span class="tip">Abrir menú</span>
      </ng-template>

      <ng-template>
        X<span class="tip">Cerrar menú</span>
      </ng-template>
      
 </button>

{% endhighlight %} 

Necesitamos diferentes decoradores para construir la directtiva.

Utilizaremos **@Hostlistener** para recoger el evento "click" sobre el elemento al que hemos asociado la directiva. Además necesitamos otros decoradores, **@ContentChild** para obtener una referencia a <ng-container> y **@ContentChildren** para acceder al contenido de todos los <ng-template>. Utilizaremos **@HostBinding** para acceder al elemento en el que hemos definido la directiva y poder incluir una nueva clase al mismo.

Para construir la directiva necesitamos utilizar el "lifecycle hook" **ngAfterContentInit()**.

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

**@ContentChildren** devuelve un objeto de tipo **QueryList** que almacena una lista de items que se pueden recorrer.

## QueryList API

### Propiedades

- **first:** obtiene el primer elemento.
- **last:** obtiene el último elemento.
- **length:** obtiene el número de elementos.


### Métodos

**map(), filter(), find(), reduce(), forEach(), some()**.

- **toArray():** Devuelve los elementos como un Array.
- **changes():** Los cambios pueden observarse suscribiendo al Observable "change" que implementa QueryList. Cada vez que un elemento hijo es añadido, borrado o movido, el QueryList se actualizará, y el Observable "change" emitirá un nuevo valor.

{% highlight ts %}

@ContentChildren(ListItem) items: QueryList<ListItem>;

  ngAfterContentInit() {
    this.items.changes.subscribe(() => {
       // Se ejecutará cada vez que un elemento se añada o borre
    });
  }

{% endhighlight %} 

En el ejemplo presentado solo utilizamos el método **toArray()**