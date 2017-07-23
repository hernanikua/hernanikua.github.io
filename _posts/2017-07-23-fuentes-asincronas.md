---
published: false
layout: post
categories: web
title: Cargar las fuentes de manera asíncrona con WebFont Loader
---


{% highlight ts %}
	
   WebFontConfig = {
      google: {
	  	families: [ 'Nunito:300,400,700,900' ]
	  }
   };

   (function(d) {
      var wf = d.createElement('script'), s = d.scripts[0];
      wf.src = 'https://ajax.googleapis.com/ajax/libs/webfont/1.6.26/webfont.js';
      wf.async = true;
      s.parentNode.insertBefore(wf, s);
   })(document);
   
{% endhighlight %}


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
