---
title: Instrucciones hospedadas en l�nea
permalink: index.html
layout: home
---

# Directorio de contenido

Hiperv�nculos a cada uno de los tutoriales. Los instructores pueden optar por usar el tutorial como una demostraci�n o un laboratorio de alumnos. 

## Tutoriales

{% asignar wts = site.pages | where_exp: "page", "page.url contiene '/Instrucciones/Tutoriales'" %}
| M�dulo | Tutorial |
| --- | --- | 
{% de actividad en wts %}| {{ activity.wts.module }} | [{{ activity.wts.title }}{% if activity.wts.type %} - {{ activity.wts.type }}{% endif %}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}

