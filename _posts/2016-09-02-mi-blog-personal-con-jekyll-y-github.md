---
layout: post
title: 'Mi blog personal con con Jekyll y Github'
date: 2016-09-02 11:23:42
categories: desarrollo web
tags: jekyll github ruby
featured_image: 'v1472827673/jekyll-github_hedkb6.png'
lead_text: 'He aquí como he creado mi blog estático con Jekyll y Github, más mi dominio personal.'
seo: 'jekyll, github, ruby, desarrollo, web'
---
![Bootstrap 3 Jekyll](https://scotch.io/wp-content/uploads/2015/10/bootstrap-plus-jekyll.png)

Podemos comenzar con una simple pregunta:

## ¿Qué es Jekyll?

[Jekyll](http://jekyllrb.com/) es un generador estático diseñado para blogs, así de simple. En términos de los laicos, es sólo una herramienta para que puedas tener las mejores características de un CMS en toda regla, sin tener que preocuparse por la gestión de una base de datos. Esto significa que en un hosting es extremadamente fácil y escalable ya que todo lo que estamos haciendo es la gestión de un montón de archivos.
Yo no le recomendaría [Jekyll](http://jekyllrb.com/) a cualquiera, [Jekyll](http://jekyllrb.com/) requiere que se trabaje desde una consola y requiere configuraciones que no son sencillas para cualquier usuario final.

Dicho eso, posiblemente la mayor ventaja que tiene un generador estático sobre un framework dinámico esta en que requiere menos recursos para su ejecución y permite inclusive ser puesto a funcionar directamente en CDNs u opciones gratuitas o económicas de hosting, lo cual es una gran ventaja en rendimiento y costo operativo de un sitio.

Además de esto, [Jekyll](http://jekyllrb.com/) esta desarrollado en [Ruby](https://www.ruby-lang.org/es/) y puede ser fácilmente extendido a través de plugins.

Personalmente la razón de migrar mi sitio a [Jekyll](http://jekyllrb.com/) corresponde a 3 razones: 

* Rendimiento de mi sitio: quiero que mi sitio sea lo más rápido posible y no hay nada que sobrepase a archivos estáticos.
* Experimentación: Quería experimentar algo nuevo, algo diferente a Wordprees, Drupal, Joomla, con tecnologías que quiero aprender. 
* Bajo mantenimiento: Una vez configurado [Jekyll](http://jekyllrb.com/) el mantenimiento el literalmente mínimo y puedo enfocarme en escribir más seguido.

## ¿Cómo lo hice?

En diciembre del año pasado, cuando estaba trabajando en la [Universidad Simón Bolívar](http://usb.ve/) Del Litoral, Las maquinas que están ahí tienen como sistema operativo [Ubuntu](http://www.ubuntu.com/), y ahí comenzó mi intriga por saber que era y como funcionaba [Jekyll](http://jekyllrb.com/), duré un par de semanas investigando sobre el tema, bueno lo cierto es que entendí como funcionaba, pero lo dejé por un tiempo.

Hace unos mese atrás volví a recobrar el interés por [Jekyll](http://jekyllrb.com/), pero esta vez no perdí el interés.

Lo primero que hice fue clonar el repositorio de [@scotch-io](https://github.com/scotch-io/) `https://github.com/scotch-io/scotch-io.github.io`

{% highlight shell %}
git clone https://github.com/scotch-io/scotch-io.github.io thevacs.github.io
cd thevacs.github.io
{% endhighlight %}

Cloné el repositorio de [@scotch-io](https://github.com/scotch-io/) a mi carpeta `thevacs.github.io`

Primero necesitaba instalar [Ruby](http://jekyllrb.com/) 
{% highlight shell %}
apt install ruby
{% endhighlight %}

... Unos minutos después instalé [Jekyll](http://jekyllrb.com/)
{% highlight shell %}
gem install jekyll
{% endhighlight %}

Lo inicié con el comando `jekyll serve`
{% highlight console %}
Configuration file: /home/vacs/scotch-io.github.io/_config.yml
            Source: .
       Destination: ./_site
 Incremental build: disabled. Enable with --incremental
      Generating... 
                    done in 0.781 seconds.
 Auto-regeneration: enabled for '.'
Configuration file: /home/vacs/scotch-io.github.io/_config.yml
    Server address: http://127.0.0.1:4000/
  Server running... press ctrl-c to stop.
{% endhighlight %}

Hice muchas modificaciones en `_config.yml` y agregue mis url y esas cosas.
Seguí desarrollando en el diseño y algunas otras cosas más.

## ¿Y Github?

Después agregue un archivo `CNAME` a mi carpeta `thevacs.github.io` con el nombre de mi dominio [jr.co.ve](https://jr.co.ve/)

{% highlight shell %}
echo jr.co.ve > CNAME
{% endhighlight %}

Y lo subí a [Github](https://github.com/)

{% highlight shell %}
git init
git add *
git commit -m "Página Personal"
git remote add origin git@github.com:thevacs/thevacs.github.io.git
git push -u origin master
{% endhighlight %}

El dominio `jr.co.ve` ya estaba apuntando a [Github](https://github.com/) así que fue rápido.

> He agregado los famosos emoji
{% highlight yml %}
gems:
  - jemoji
{% endhighlight %}

:bowtie:  :smile: