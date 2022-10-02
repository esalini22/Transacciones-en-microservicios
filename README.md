# Transacciones en microservicios
## Indice 🔎

## Introducción 🚪

## Conceptos previos 👨‍🎓
### 👉 Web Services

Un web service es un sistema de software diseñado para admitir la interacción interoperable de varias máquinas entre si a través de una red que puede ser descripta, publicada, localizada e invocada desde cualquier plataforma y en cualquier lenguaje de programación. El funcionamiento detrás de las funcionalidades que entregan los servicios web es algo desconocido para la máquina que los ocupa, es por esto que quien quiera recibir los datos solo necesita usar el servicio y punto. 

![Dibujo del funcionamiento de un web service](https://media.geeksforgeeks.org/wp-content/uploads/20210627134636/m1.png)

El proceso que sigue un web service para funcionar es muy sencillo y se trata únicamente de un servicio de interacción y comunicación entre distintas aplicaciones a través de Internet.

#### Funcionamiento

Los webs services tienen una interfaz descrita en un formato procesable por él computador. Los sistemas interactúan entre si utilizando mensajes SOAP, normalmente transmitidos mediante HTTP con una serialización XML junto con otros estándares relacionados con la web.

El proceso de funcionamiento se puede describir de la siguiente manera:

1. El proveedor de servicios envía un archivo WSDL con la definición del servicio web al corredor de servicios. Con este archivo, el corredor de servicios es capaz de saber qué funciones será posible ejecutar en el servidor a través del web service. 

2. Después, el solicitante del servicio se comunica con el corredor de servicios para averiguar quién es el proveedor. De esta forma, el solicitante puede comunicarse con el proveedor de servicios para enviar una solicitud SOAP en forma de mensaje HTTP al servidor. 

3.  Una vez que esto sucede, el web service interpreta el contenido de la solicitud y el proveedor de servicios valida la petición del solicitante. Posteriormente, el web service envía los datos de respuesta necesarios en formato XML , usando nuevamente el protocolo SOAP y HTTP. 

4.  Finalmente, el fichero XML, enviado por el proveedor de servicios, es validado una vez más por el solicitante de los servicios, utilizando un fichero XSD para interpretarlo. La información resultante se envía al software y estará lista para ser procesada. 


#### Ejemplos de web services

Algunos ejemplos que podemos encontrar son: 

- Microsoft .NET 

- WebLogic 

- WebSphere 

- Java Web Services Development Pack (JWSDP) 





### 👉 Transacciones
Corresponden a una serie de acciones que deben ejecutarse exitosamente en una base de datos. Si una  de las operaciones falla, todos los pasos deben retroceder a su estado anterior para que la aplicación quede en su estado estable antiguo. Las transacciones poseen las siguientes propiedades:
- Atomicidad: La transacción ocurre completamente o no ocurre.
- Consistencia: La base de datos debe ser consistente (es decir, el cambio solo ocurre si el nuevo estado es válido) antes y después de la transacción
- Aislamiento: Ocurren múltiples transacciones independientemente sin interferencia
- Durabilidad: Los cambios de una transacción exitosa ocurren incluso si el sistema falla.
Dentro de una transacción, un evento es un cambio de estado que le ocurre a una entidad, y un comando encapsula toda la información necesaria para ejecutar una acción o gatillar un evento futuro.

### 👉 Microservicios






### 👉 Arquitectura monolítica vs de microservicios

#### Arquitectura monolítica

Una arquitectura monolítica corresponde a una arquitectura donde todos los procesos están estrechamente asociados y se ejecutan como un solo servicio.

| Ventajas ✅| Desventajas ❌|
| -----------|---------------|
|Son más fáciles de desarrollar y desplegar, pues los componentes están centralizados|Agregar o mejorar las características se vuelve más complejo a medida que crece la base del código|
|Más fáciles de testear, ya que hay solo un repositorio de código|Aumentan el riesgo de la disponibilidad de la aplicación porque muchos procesos dependientes y estrechamente vinculados aumentan el impacto del error de un proceso|
|No se requieren, o se requieren menos habilidades especializadas|Difícil de escalar, ya que para escalar una aplicación monolítica, esto debe hacerse todo a la vez añadiendo recursos de cómputo adicionales, lo cual es caro|

#### Arquitectura de microservicios

Una arquitectura de microservicios corresponde a una arquitectura donde la aplicación se crea con componentes independientes que ejecutan cada proceso de la aplicación como un servicio, los que se comunican a través de una interfaz bien definida mediante APIs ligeras.
Los microservicios son autónomos, es decir, cada servicio componente en una arquitectura de microservicios se puede desarrollar, implementar, operar y escalar sin afectar el funcionamiento de otros servicios, sin tener que compartir código o implementaciones con otros servicios; y especializados, es decir, cada servicios está diseñado para un conjunto de capacidades y se enfoca en resolver un problema específico, y si el servicio se vuelve más complejo, se puede dividir en servicios más pequeños.


| Ventajas ✅| Desventajas ❌|
| -----------|---------------|
|Debido a que se ejecutan de forma independiente, cada servicio se puede actualizar, implementar y escalar para satisfacer la demanda de funciones de la aplicación|La complejidad es más alta, debido a la manera en que los microservicios están conectados entre sí|
|Los equipos pueden fácilmente añadir funcionalidades y nuevas tecnologías a una arquitectura de microservicios a medida que se necesite|Requiere habilidades y conocimientos especializados, los que no todos los desarrolladores poseen|
||La seguridad y el testeo están distribuidos, ya que cada módulo tiene sus propias vulnerabilidades y bugs, lo cual toma más tiempo de debuggear|

### 👉 Mecanismos de seguridad
#### Patrón Saga
Es un patrón de manejo de fallos que ayuda a establecer la consistencia en aplicaciones distribuidas, y coordina transacciones entre múltiples microservicios para mantener la consistencia de datos. Una saga es una secuencia de transacciones que actualizan cada servicio y publican un mensaje o evento para gatillar el siguiente paso de a transacción. Si un paso falla, la saga ejecuta transacciones compensadoras que contrarrestan las transacciones anteriores.

Un microservicio publica un evento por cada transacción, y la siguiente transacción está basada inicialmente en el resultado del evento. Puede tomar dos diferentes caminos, dependiendo del éxito o fracaso de la transacción.

![alt text](https://learn.microsoft.com/en-us/azure/architecture/reference-architectures/saga/images/saga-overview.png)

El patrón saga es útil si:
- La aplicación requiere mantener consistencia de datos  a través de múltiples microservicios sin acoplamiento estrecho
- Hay transacciones longevas y no se quieren bloquear otros microservicios si un microservicio corre por un largo tiempo
- Se necesita retroceder si una operación falla en la secuencia.

El patrón saga es difícil de debuggear e implementar y su complejidad aumenta con el número de microservicios.

#### Protocolo Two-phase commit
Es un protocolo de commit atómico y un algoritmo distribuido que coordina todos los procesos que participan en una transacción atómica distribuida para hacer commit o abortar (retroceder) la transacción. Corresponde a un set de acciones usadas para asegurarse de que un programa hace todos los cambios o no.

### 👉 APIs


## Referencias 📖
