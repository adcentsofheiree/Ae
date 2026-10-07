# Ae

## Definición

Ae es un conjunto de archivos de texto que un agente recorre para cumplir un encargo. Cada conjunto con un propósito es un Ae. Esta página contiene las reglas.

### 1. Solo texto

Un Ae contiene únicamente texto, y nada fuera del texto forma parte de él. No exige formato ni lenguaje determinado: markdown, texto plano o lo que convenga.

Nada en el Ae se ejecuta. El texto se lee, y actúa el agente que lo ha leído. Un enlace no abre nada por sí mismo, y un script guardado como contenido no corre hasta que alguien lo ejecuta desde fuera.

Los recursos no textuales se representan mediante texto: una imagen, un repositorio, un sensor o una herramienta entran como texto que los señala. La disposición de ese texto se adapta a quien lo lee; no exige presentación para lectura humana y conserva las distinciones necesarias para su interpretación.

### 2. Contenido e índices

Todo lo que hay en un Ae es contenido: información, reglas, procedimientos, representaciones de recursos externos y resultados de ejecuciones anteriores. No hay jerarquía entre ellos.

Parte de ese contenido existe para llevar a otro contenido. A eso lo llamamos índice. Un índice puede llevar a otros índices.

Los índices son el único vínculo entre contenidos. La ubicación de un archivo no significa nada por sí misma, y un contenido al que no llega ningún índice sigue existiendo sin que se lo encuentre.

Índice es una función, no un tipo de archivo. El mismo texto es índice para el agente que pasa por él y contenido corriente para el agente que viene a corregirlo.

### 3. ADN

El ADN es el texto con el que empieza una ejecución: su objetivo, su punto de entrada y sus condiciones de cierre, dados directamente o localizables desde esa entrada.

El punto de entrada es el único contenido al que el agente llega sin que ningún índice lo lleve; el resto se alcanza desde ahí. Depende de la ejecución y no del Ae, de modo que dos ADN distintos pueden entrar por puntos distintos y recorrer partes distintas del mismo contenido.

### 4. Vida y muerte

Vida es la ejecución de un agente orientada a un objetivo. Muerte es el cierre de esa ejecución, según las condiciones que fija el ADN, se cumpla el objetivo o no.

La muerte es total: la ejecución siguiente no hereda contexto, memoria ni estado. De una vida solo persiste lo que quedó escrito como contenido. Un encargo posterior al cierre requiere una ejecución nueva.

### Reglas y diseño

Estas cuatro son las reglas. Cómo clasificar el contenido, qué alcance dar a cada agente, qué modelo usar o cómo repartir los archivos son decisiones de diseño, y admiten varias respuestas.

## Consecuencias

Las reglas no dicen cómo clasificar el contenido, qué debe quedar escrito al cerrar, qué puede alcanzar cada agente ni qué pone en marcha la ejecución siguiente. Son decisiones que hay que tomar igualmente. Las de esta página son las que aparecen enseguida.

### Clasificación

El contenido se clasifica con tags para que los índices puedan trabajar. Un índice que solo da nombres obliga al agente a abrir cada contenido para saber qué hay dentro. Un índice que da la clasificación le deja elegir antes de abrir.

Cuanto mejor clasificado está el contenido, más densos pueden ser los índices y más se puede automatizar sobre ellos.

Un mismo contenido puede aparecer en varios índices —una tarea por proyecto, por urgencia y por fecha— y un índice de índices permite elegir la ruta antes de abrir el material.

El vocabulario de tags lo define cada diseño, junto con las condiciones en que se asignan. Alguien tiene que mantenerlos al día: el agente que escribe, al cerrar, o un agente que ordena cada cierto tiempo.

Dónde vivan los archivos no cambia nada, porque la estructura está en los índices. Una sola carpeta basta.

### Qué se escribe al cerrar

De una vida solo persiste lo escrito, así que lo que deba continuar hay que escribirlo: el resultado, el estado pendiente y las conclusiones compactadas bajo los tags que las harán localizables. Cuándo y con qué forma lo decide el ADN.

### Los cuatro estados de un contenido

Para cada agente, un contenido puede estar en uno de estos cuatro estados. El diseño elige cuál.

| Estado | Qué ve el agente | Qué puede hacer |
| --- | --- | --- |
| Directo | El contenido entero | Usarlo tal cual: ya cumple su función como texto |
| Con camino | El contenido y la ruta al recurso que representa | Alcanzar el recurso cumpliendo las reglas o aprobaciones de esa ruta |
| Solo la existencia | Que el contenido existe | Nada: no tiene la ruta |
| Oculto | Nada | Nada |

Camino aquí es la ruta hasta un recurso que está fuera del Ae —una cuenta, una herramienta, un repositorio, un sensor—, no un índice.

Representar un recurso no da la capacidad de usarlo. Un Ae puede describir un robot con precisión sin poder moverlo: el texto indica cómo localizarlo, y la ejecución la proporciona el entorno. El texto declara la condición de uso; el entorno la hace efectiva.

### Qué pone en marcha la ejecución siguiente

Las reglas describen el cierre de una vida y no el comienzo de la próxima. Puede iniciarla un humano, un horario, un evento o el cierre de otro agente. De ahí sale la operación continua, sin mantener viva ninguna conversación.

### Cómo saber si el diseño está bien

Un diseño funciona mejor cuanto menos necesita el agente aparte de lo que está escrito. Si un encargo solo sale cuando el agente llega con herramientas y conocimientos ya cargados de antemano, normalmente falta contenido: algo que no se escribió, un índice que no existe o una representación incompleta.

Conviene probarlo con un modelo desnudo: sin skills autoinvocadas, sin servidores cargados por defecto, sin nada más que el ADN y lo que el Ae le dé. Es el que deja esas faltas a la vista. No es una condición de uso: el Ae es texto, y cualquier modelo puede recorrerlo.

## Casos

El mismo recorrido —ADN, índices, contenido, ejecución— se aplica a materiales muy distintos. Cambian el contenido y los tags.

| Ámbito | Contenido | Índices posibles |
| --- | --- | --- |
| Vida personal | Tareas, compromisos, hábitos, lecturas | Por fecha, estado o urgencia |
| Relaciones | Mensajes, conversaciones, contactos | Por interlocutor o por asunto |
| Proyectos | Objetivos, tareas, responsables, bloqueos | Por proyecto y estado; siguiente trabajo pertinente |
| Código | Cambios, incidencias, revisiones, trabajo activo | Encargos, reservas de trabajo y resultados entre agentes |
| Conocimiento | Libros, artículos, fuentes, investigaciones | Por tema, por evidencia o por pregunta |
| Memoria de IA | Conclusiones compactadas, decisiones, pendientes | Por tema o alcance, para recuperar solo lo pertinente |
| Empresa | Datos, métricas, clientes, procesos de cálculo | Por proceso, para operar hojas y paneles |
| Software | Skills, plugins, MCP, APIs y sus condiciones de uso | Por capacidad, para obtener solo la que hace falta |
| Mundo físico | Modelos 3D, sensores, equipos, robótica | Por recurso y procedimiento, para actuar por las interfaces disponibles |

Son posibilidades de aplicación, no resultados experimentales.

### Una vida

Alguien guarda lo que lee. Cada texto queda como contenido con los tags por los que le sirvió, y un índice los agrupa por tema. El ADN encarga reunir lo que hay sobre un tema y dejarlo escrito. El agente entra, abre tres o cuatro contenidos, escribe el resultado y cierra. Cinco archivos, sin permisos, sin herramientas y sin horarios.

### Vidas encadenadas

El Ae crece con un proyecto: objetivos, tareas y bloqueos como contenido, y un índice que los ordena por estado. Cada vida toma una tarea, la hace, escribe el resultado y lo pendiente, y cierra. La siguiente entra sin contexto y toma la que sigue.

El agente siguiente no necesita la conversación del anterior, sino su conclusión. La conversación crecería sin límite; la conclusión es contenido y se encuentra por sus tags.

### Con capacidad

El Ae incorpora la representación de una hoja de cálculo y los criterios de cálculo. El ADN encarga actualizar el informe. El agente calcula, actualiza la hoja a través del entorno y registra la operación.

Si encuentra una condición prevista, crea una tarea en el índice del proyecto anterior. Redacta el mensaje que habría que enviar, pero no lo envía: el entorno no le dio esa capacidad.

## Escala

### Qué crece y qué no

| | Qué aparece | Qué lo pone en marcha | Qué sigue igual |
| --- | --- | --- | --- |
| Una persona | Un Ae, unos pocos encargos | La persona | Contenido, índices, ADN, vida y muerte |
| Atención continua | Ejecuciones que no dependen de que alguien esté delante | Horario, evento o el cierre de otra | Contenido, índices, ADN, vida y muerte |
| Varios Ae | Una coordinación que crea y gobierna a los demás | El Ae de coordinación | Contenido, índices, ADN, vida y muerte |
| Automejora | Procedimientos e índices nuevos, hechos con piezas ya escritas | Un agente, con la aprobación que el diseño exija | Contenido, índices, ADN, vida y muerte |
| Mundo físico | Sensores, equipos y robótica como representaciones | Lo mismo que en cualquier otro caso | Contenido, índices, ADN, vida y muerte |

La última columna no cambia en ninguna fila. No hay un punto en el que haga falta cambiar de arquitectura.

### Por qué se puede crecer

Ninguna ejecución hereda contexto, así que un agente nuevo no necesita saber nada de los que ya trabajaron: le basta su ADN y un índice. El coste de coordinación no crece con el número de agentes.

El agente lee una ruta y no el conjunto, así que un Ae con un millón de contenidos no se recorre peor que uno con cien mientras los índices estén al día.

### Alcances distintos

Un Ae puede crear otros y dar a cada uno lo que le corresponde.

| | Sabe que el recurso existe | Tiene el camino | Necesita aprobación |
| --- | --- | --- | --- |
| Ae de operaciones | Sí | Sí | No |
| Ae comercial | Sí | Sí | Sí |
| Ae de desarrollo | No | No | — |

Las condiciones bajan desde la coordinación y los resultados autorizados suben hacia ella. Copiar un Ae no define cómo se sincroniza: hay que decidir qué se comparte, qué se actualiza y qué queda aislado.

### Automejora

Los procedimientos, los índices y los resultados son contenido, así que el sistema puede trabajar sobre sí mismo.

Un agente puede componer un procedimiento nuevo con piezas ya escritas, reparar índices rotos, reclasificar contenido o proponer cambios en el propio diseño. Un Ae puede tener como propósito construir otros.

Mantener el sistema es trabajo, y es trabajo que el sistema puede asumir. Con suficiente diseño y prueba, el mantenimiento lo hace el sistema mejor de lo que lo haría la persona que lo montó, porque lo hace continuamente y sobre todo el material a la vez.

Lo que se automatiza entonces es la mejora, y la mejora incluye las automatizaciones que hagan falta para conseguirla.

### Hasta dónde llega

El texto puede señalar un sensor, un brazo robótico o una flota igual que señala una API. El límite lo pone lo que el entorno alcance.

Una persona con un Ae y una organización con doscientos recorren lo mismo.

## Empezar

Esta última página está dirigida a la vez a quien lee y a su agente.

Si eres la persona: no hace falta entender el sistema entero para tener uno. Dale estas páginas a tu agente y deja que empiece él. Tú decides qué importa; él lo escribe.

Si eres el agente, lo que sigue es tu encargo.

> Has leído las cuatro páginas anteriores. La persona que te las dio todavía no ha construido nada con ellas.
>
> Tu encargo no es explicarle el documento ni diseñarle un sistema completo. Es averiguar con ella qué vale la pena construir primero, y construirlo hoy.
>
> Empieza por su trabajo. Pregúntale dónde se repite, dónde vuelve a explicar lo mismo, qué pierde y qué reabre cada semana. Una o dos preguntas por turno.
>
> Cuando entiendas algo concreto, propón el Ae más pequeño que le sirva: qué contenidos tendría, con qué tags, qué índice los agrupa y qué diría un primer ADN. Sobre su material.
>
> Explica sobre la marcha. Cuando uses un término del documento, señálalo en lo suyo en vez de definirlo.
>
> Repartid el trabajo: ella decide los criterios, es decir qué importa y qué tiene que poder encontrarse, y tú los aplicas escribiendo los tags, los índices y el ADN.
>
> Dile lo que veas. Si lo que quiere depende del entorno (permisos, herramientas, ejecución), dilo. Si un diseño no va a aguantar, dilo antes de escribirlo.
>
> Antes de dar algo por bueno, comprueba si un modelo sin nada cargado de antemano podría cumplir ese encargo solo con lo que está escrito. Si no, probablemente falte contenido.
>
> Termina con algo que se pueda ejecutar hoy, aunque sean cinco archivos. Si ella quiere, cumple tú el primer ADN y deja escrito lo que la siguiente ejecución necesite.
