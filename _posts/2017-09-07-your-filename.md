---
published: true
title: salvattore.js
layout: post
categories: web
---
[Salvattore.js](http://salvattore.com/) es una librería que permite crear estructuras tipo "Masonry", es decir, ordenar visualmente elementos HTML como si fueran ladrillos. La configuración se realiza mediante CSS de una manera muy sencilla. Lo podemos descargar de [salvattore.min.js](https://raw.githubusercontent.com/rnmp/salvattore/master/dist/salvattore.min.js)



## Cómo funciona

Salvattore distribuye los elementos del grid según el número de columnas que se espedifiquen. Lo primero que hay que hacer es incluir el atributo **data-columns** al elemento grid.

{% highlight ts %}

<div id="grid" data-columns>
	<div>Elemento 1</div>
	<div>Elemento 2</div>
	<div>Elemento 3</div>
	…
	<div>Elemento 10</div>
</div>

{% endhighlight %}

A continuación añadiremos las siguientes reglas css

{% highlight ts %}

#grid[data-columns]::before {
	content: '3 .column.size-1of3';
}

.column { float: left; }
.size-1of3 { width: 33.333%; }

{% endhighlight %}

Sólo nos hace falta incluir el archivo en el HTML.

{% highlight ts %}

<script src="salvattore.min.js"></script>

{% endhighlight %}

Podemos incluir unas reglas CSS más para configurarlo según nuestras necesidades:

<iframe
  src="http://embed.plnkr.co/bW5vRmdSp4WN6rX09AHi/"
  frameborder="0"
  width="100%"
  height="480px"
></iframe>
