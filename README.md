<![endif]-->

# TTY interactiva: ¿Como hacer una terminal interactiva?

Durante una prueba de penetración, tener una TTY interactiva es       crucial porque mejora significativamente la capacidad del pentester      para interactuar con el sistema objetivo. Una TTY interactiva ofrece     un entorno completo de línea de comandos, permitiendo ejecutar una       amplia gama de comandos y scripts, utilizar herramientas interactivas    como editores de texto, y manipular el sistema de manera más       eficiente y efectiva. Esto es especialmente importante cuando se       explotan vulnerabilidades o se realiza un análisis en profundidad del    sistema, ya que una TTY interactiva proporciona una experiencia       similar a la de una sesión local, permitiendo al pentester realizar      acciones complejas, diagnosticar problemas y explorar el sistema de forma mucho más efectiva que con una shell limitada o no interactiva.

Esta capacidad de interactuar de manera efectiva con el sistema objetivo a través de una TTY interactiva se alinea estrechamente con el modelo del [Cyber Kill Chain](https://www.lockheedmartin.com/en-us/capabilities/cyber/cyber-kill-chain.html), desarrollado por Lockheed Martin, para describir las etapas de un ataque cibernético. En este modelo, la ejecución de un RCE (Remote Command Execution) y la obtención de una TTY interactiva son fundamentales en la etapa de “Explotación”, donde se realiza la intrusión activa en el sistema. Además, su uso puede extenderse hasta las etapas de “Instalación” y “Comando y Control”, facilitando el establecimiento de una presencia más sólida dentro del sistema y permitiendo una gestión más eficaz del control sobre el mismo. Por lo tanto, comprender y aplicar efectivamente la TTY interactiva es esencial para navegar con éxito a través de estas etapas críticas del Cyber Kill Chain en el contexto de las pruebas de penetración.


## Ejecución:
Para obtener una TTY interactiva en una máquina objetivo, puedes seguir los siguientes pasos. Ten en cuenta que este proceso debería tomar entre 5 a 10 segundos, aunque el tiempo exacto dependerá de la máquina objetivo. Aquí está el script y una explicación detallada de cada comando:

    script /dev/null -c bash
    ctrl + z
    stty raw -echo;fg
    reset
    xterm
    export TERM=xterm
    export SHELL=bash
    stty rows 24 columns 126

## Explicación:

 - **script /dev/null -c bash**: Este comando inicia una nueva sesión de bash sin guardar la salida. **script** se usa a menudo para hacer que
   las sesiones interactivas actúen como si estuvieran conectadas a un
   TTY real, lo cual es útil cuando se accede a un sistema de manera
   remota y la sesión actual no está vinculada a un TTY.
 - **ctrl + z**: Suspende la sesión de bash actual, devolviéndote a la sesión de shell original.
 - **stty raw -echo; fg**: Cambia el modo del terminal actual a raw y desactiva el eco, lo que significa que el terminal no procesará las
   entradas de manera especial (como interpretar caracteres de control).
   Luego, **fg** trae el proceso bash suspendido de nuevo al primer
   plano, pero ahora en el entorno modificado.
 - **reset**: Este comando reinicializa el estado de la terminal. Es útil después de cambiar el modo del terminal a raw, ya que puede
   limpiar cualquier estado inconsistente.
 - **xterm**: Ejecutar el emulador de terminal **xterm**.
 - **export TERM=xterm** y **export SHELL=bash**: Estos comandos configuran las variables de entorno para definir el tipo de terminal
   y la shell que se está utilizando, asegurando que los programas que
   se ejecutan en la sesión interactúen correctamente con el terminal.
 - **stty rows 24 columns 126**: Ajusta el tamaño de la ventana del terminal para que tenga 24 filas y 126 columnas, lo cual es necesario
   para asegurar que la salida de los comandos se muestre correctamente.

# Apoyo 
Si te gustaría contribuir con 1 dólar, estaría muy agradecido. Puedes hacerlo aquí:

https://www.paypal.com/paypalme/JoseFloresFuentes
