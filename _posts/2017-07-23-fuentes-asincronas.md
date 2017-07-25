---
published: false
layout: post
categories: web
title: Cargar las fuentes de manera asíncrona con WebFont Loader
---
**WebFont Loader** es una librería de javascript que ofrece un mayor control de la carga de las fuentes en una web. Permite gestionar la carga de varios proveedores de fuentes. Ha sido desarrollado conjuntamente por **Google** y **Typekit**. 

Podemos utilizar WebFont Loader de manera asíncrona, evitando así bloquear la carga de la página mientras se descargan las fuentes. En el siguiente ejemplo cargamos la  familia de fuentes **Ubuntu** desde el servicio de [Google Fonts](https://fonts.google.com/):

{% highlight ts %}
	
   WebFontConfig = {
      google: {
	  	families: [ 'Ubuntu:300,400,500,700','Lemonada:300,400,600' ]
	  }
   };

   (function(d) {
      var wf = d.createElement('script'), s = d.scripts[0];
      wf.src = 'https://ajax.googleapis.com/ajax/libs/webfont/1.6.26/webfont.js';
      wf.async = true;
      s.parentNode.insertBefore(wf, s);
   })(document);
   
{% endhighlight %}

También podemos cargar de manera asíncrona desde [Typekit](https://typekit.com/), cambiando la variable WebFontConfig:

{% highlight ts %}

WebFontConfig = {
		 typekit: {
			 id: 'ycv4fpr'
			}
	 };

{% endhighlight %}

El identificador lo obtendremos en la pantalla que nos presenta el script por defecto de Typekit:

![Obtener el identificador de las fuentes]({{site.baseurl}}/images/fuentes.png)

Hay fuentes de otros proveedores que podemos cargar del mismo modo, como las de [Fonts Alive](https://www.fonts.com/):

{% highlight ts %}
WebFontConfig ={
  ascender: {
    key: 'myAscenderKey',
    families: [ 'AscenderSans:bold,bolditalic,italic,regular' ]
  }
};
{% endhighlight %}

También podemos cargar nuestras propias fuentes:

{% highlight ts %}
WebFontConfig = {
  custom: {
    families: ['Mi fuente', 'Mi otra fuente:n4,i4,n7'],
    urls: ['/fuentes.css']
  }
};
{% endhighlight %}

En el ejemplo anterior el archivo **fuentes.css** sería del siguiente modo:

{% highlight ts %}
@font-face {
  font-family: 'Mi Fuente';
  src: ...;
}
@font-face {
  font-family: 'Mi otra fuente';
  font-style: normal;
  font-weight: normal; /* o 400 */
  src: ...;
}
@font-face {
  font-family: 'Mi otra fuente';
  font-style: italic;
  font-weight: normal; /* o 400 */
  src: ...;
}
@font-face {
  font-family: 'Mi otra fuente';
  font-style: normal;
  font-weight: bold; /* o 700 */
  src: ...;
}
{% endhighlight %}

## CSS Callbacks

WebFont Loader aplica nombres de clase al elemento HTML durante la operación de carga:

    .wf-loading — Cuando todas las fuentes han sido pedidas.
    .wf-active — Cuando están disponibles todas las fuentes.
    .wf-inactive — Cuando ninguna fuente ha podido ser descargada.
    
Tambíen se añaden clases a cada fuente:

    .wf-<familyname>-<fvd>-loading — Una fuente única ha sido pedida.
    .wf-<familyname>-<fvd>-active — Una fuente única está disponible.
    .wf--<familyname>-<fvd>-inactive — Una única fuente no ha podido ser descargada.

Esto nos permite cambiar las fuentes una vez se han descargado:


{% highlight ts %}
/* Fuentes del sistema por defecto */
body {
	font-family: arial, sans-serif;
}

/* Fuentes descargadas */
.wf-active body {
	font-family: 'Ubuntu';
}
{% endhighlight %}

## JavaScript Callbacks

## Timeouts

