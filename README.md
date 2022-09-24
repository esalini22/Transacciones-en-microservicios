# Transacciones en microservicios
## Indice 🔎

## Introducción 💁‍

## Conceptos previos 👶
### 👉 Web Services


### 👉 Transacciones
Corresponden a una serie de acciones que deben ejecutarse exitosamente en una base de datos. Si una  de las operaciones falla, todos los pasos deben retroceder a su estado anterior para que la aplicación quede en su estado estable antiguo. Las transacciones poseen las siguientes propiedades:
- Atomicidad: La transacción ocurre completamente o no ocurre.
- Consistencia: La base de datos debe ser consistente (es decir, el cambio solo ocurre si el nuevo estado es válido) antes y después de la transacción
- Aislamiento: Ocurren múltiples transacciones independientemente sin interferencia
- Durabilidad: Los cambios de una transacción exitosa ocurren incluso si el sistema falla.

### 👉 Microservicios

### 👉 Arquitectura monolítica vs de microservicios
Una arquitectura monolítica corresponde a una arquitectura donde todos los procesos están estrechamente asociados y se ejecutan como un solo servicio.

| Ventajas ✅| Desventajas ❌|
| -----------|---------------|
|Son más fáciles de desarrollar y desplegar, pues los componentes están centralizados|Agregar o mejorar las características se vuelve más complejo a medida que crece la base del código|
|Más fáciles de testear, ya que hay solo un repositorio de código|Aumentan el riesgo de la disponibilidad de la aplicación porque muchos procesos dependientes y estrechamente vinculados aumentan el impacto del error de un proceso|
|No se requieren, o se requieren menos habilidades especializadas|Difícil de escalar, ya que para escalar una aplicación monolítica, esto debe hacerse todo a la vez añadiendo recursos de cómputo adicionales, lo cual es caro|

Una arquitectura de microservicios corresponde a una arquitectura donde la aplicación se crea con componentes independientes que ejecutan cada proceso de la aplicación como un servicio, los que se comunican a través de una interfaz bien definida mediante APIs ligeras.
Los microservicios son autónomos, es decir, cada servicio componente en una arquitectura de microservicios se puede desarrollar, implementar, operar y escalar sin afectar el funcionamiento de otros servicios, sin tener que compartir código o implementaciones con otros servicios; y especializados, es decir, cada servicios está diseñado para un conjunto de capacidades y se enfoca en resolver un problema específico, y si el servicio se vuelve más complejo, se puede dividir en servicios más pequeños.


| Ventajas ✅| Desventajas ❌|
| -----------|---------------|
|Debido a que se ejecutan de forma independiente, cada servicio se puede actualizar, implementar y escalar para satisfacer la demanda de funciones de la aplicación|La complejidad es más alta, debido a la manera en que los microservicios están conectados entre sí|
|Los equipos pueden fácilmente añadir funcionalidades y nuevas tecnologías a una arquitectura de microservicios a medida que se necesite|Requiere habilidades y conocimientos especializados, los que no todos los desarrolladores poseen|
||La seguridad y el testeo están distribuidos, ya que cada módulo tiene sus propias vulnerabilidades y bugs, lo cual toma más tiempo de debuggear|


### 👉 APIs


## Referencias 📖
