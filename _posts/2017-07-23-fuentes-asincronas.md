---
published: false
layout: post
categories: web
title: Cargar las fuentes de manera asíncrona con WebFont Loader
---
**WebFont Loader** es una librería de javascript que ofrece un mayor control de la carga de las fuentes en una web. Permite gestionar la carga de varios proveedores de fuentes. Ha sido desarrollado conjuntamente por **Google** y **Typekit**. 

Podemos utilizar WebFont Loader de manera asíncrona, evitando así bloquear la carga de la página por el javascript. En el siguiente ejemplo cargamos la  familia de fuentes **Ubuntu** desde el servicio de [Google Fonts](https://fonts.google.com/):

{% highlight ts %}
	
   WebFontConfig = {
      google: {
	  	families: [ 'Ubuntu:300,400,500,700' ]
	  }
   };

   (function(d) {
      var wf = d.createElement('script'), s = d.scripts[0];
      wf.src = 'https://ajax.googleapis.com/ajax/libs/webfont/1.6.26/webfont.js';
      wf.async = true;
      s.parentNode.insertBefore(wf, s);
   })(document);
   
{% endhighlight %}

También podemos cargar de manera asíncrona desde [Typekit](https://typekit.com/):

{% highlight ts %}

WebFontConfig = {
		 typekit: {
			 id: 'ycv4fpr'
			}
	 };

   (function(d) {
      var wf = d.createElement('script'), s = d.scripts[0];
      wf.src = 'https://ajax.googleapis.com/ajax/libs/webfont/1.6.26/webfont.js';
      wf.async = true;
      s.parentNode.insertBefore(wf, s);
   })(document);

{% endhighlight %}

El identificador lo obtendremos en la pantalla que nos presenta el script por defecto de Typekit:

![Obtener el identificador de las fuentes]({{site.baseurl}}/images/fuentes.png)
