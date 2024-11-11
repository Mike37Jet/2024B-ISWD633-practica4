# COMPLETAR  
Antes de realizar esta práctica sobre Docker, mis conocimientos se limitaban a una comprensión general de la virtualización de contenedores, pero no había trabajado de forma tan detallada en la gestión de los recursos del sistema a nivel de contenedores, ni en cómo Docker puede ser usado para optimizar el uso de CPU, memoria y otros recursos.

**Despues de la práctica aprendí:**

**Optimización del uso de recursos:** Aprendí a establecer límites para la memoria y CPU en los contenedores. Esto es fundamental en entornos de producción para garantizar que los contenedores no sobreutilicen los recursos del sistema y afecten negativamente a otras aplicaciones. Comprendí la importancia de opciones como --memory y --cpus para ajustar estos límites.

**Memoria y Swap:** La práctica me permitió entender cómo Docker maneja la memoria física y swap. Esto fue importante, ya que me permitió calcular de forma precisa la cantidad de swap disponible y aplicar estrategias para evitar la sobrecarga de memoria. 

**Políticas de reinicio y healthchecks:** Me familiaricé con las políticas de reinicio de Docker, como no, on-failure, always, lo cual es clave para garantizar que los contenedores se gestionen de manera adecuada ante fallos o reinicios del sistema. También adquirí experiencia configurando healthchecks, que son esenciales para garantizar que los servicios dentro de los contenedores estén funcionando correctamente y que Docker pueda tomar decisiones sobre reinicios automáticos si un contenedor no es saludable.

**Caché y capas en Docker:** Aprendí cómo Docker utiliza un mecanismo de caché para reducir los tiempos de construcción de imágenes, lo cual optimiza el proceso de desarrollo. Entender cómo Docker reutiliza capas fue interesante para mejorar la eficiencia en la creación de nuevas versiones de imágenes.

**Gestión de imágenes huérfanas:** Comprendí la importancia de limpiar imágenes huérfanas, que son aquellas que no están en uso por ningún contenedor, para mantener un entorno limpio y optimizado en términos de almacenamiento.

**Construcción de imágenes desde Dockerfile:** Experimenté con la creación de imágenes Docker personalizadas utilizando Dockerfiles, y comprendí cómo diferentes instrucciones como FROM, COPY, RUN, y CMD juegan un papel crucial en la construcción de un contenedor funcional.

SOLUCIÓN DE PROBLEMA:
Debido a la discontinuidad de la distribucion de fedora:7 utilice una distribucion similar que es almalinux:8 para que no me de error al actulizar.

Docekerfile
```
FROM almalinux:8
RUN yum -y update
RUN yum -y install httpd
COPY ./web /var/www/html
EXPOSE 80
CMD ["apachectl", "-D", "FOREGROUND"]
```


