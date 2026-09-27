# reporte tecnico de configuracion de laboratorio

## alcance

se preparo una maquina virtual con windows 11 en virtualbox para realizar practicas de ciberseguridad. se configuro la red en modo nat, se separaron las cuentas de administracion y trabajo, y se creo una instantanea inicial para poder recuperar el entorno.

## 1. virtualbox y configuracion de red

![adaptador de red de virtualbox en modo nat](red-nat.png)

el adaptador de la maquina virtual esta habilitado en modo nat. este modo permite que el sistema invitado salga a internet a traves del host y evita que la vm quede expuesta directamente como otro equipo de la red local. se eligio para descargar actualizaciones sin usar el modo puente. nat reduce la exposicion de la vm, pero no garantiza aislamiento total del host: durante las practicas tambien se deben evitar carpetas compartidas innecesarias y ejecutar muestras peligrosas.

## 2. cuentas de windows 11

![lista de usuarios y grupos de windows 11](usuarios.png)

se crearon dos cuentas con funciones diferentes. `juankz2` pertenece al grupo `users` y se usa para las tareas habituales del laboratorio con privilegios limitados. la otra cuenta pertenece a `users; administrators` y queda reservada para cambios de configuracion que requieren elevacion. esta separacion aplica el principio de minimo privilegio: si una tarea o programa se ejecuta desde la cuenta estandar, no recibe permisos de administrador por defecto.

### estado de windows update

![windows update indica que el sistema esta al dia](windows-update.png)

la captura de windows update indica que el sistema esta al dia al momento de la comprobacion. mantener el sistema actualizado ayuda a corregir vulnerabilidades conocidas y reduce la superficie de ataque. las actualizaciones futuras deben seguir revisandose de manera periodica.

## 3. instantanea inicial

![administrador de instantaneas de virtualbox](snapshot.png)

se creo una instantanea llamada `hardening inicial` despues de preparar la vm. sirve como punto de recuperacion: si una practica modifica o rompe el sistema, se puede restaurar este estado de referencia. una instantanea no reemplaza una copia de seguridad independiente.

la captura del entregable solicita una instantanea llamada `hardening inicial`. el nombre de la captura coincide con ese requisito. la vm estaba apagada cuando se creo la instantanea, lo que deja un estado inicial consistente para restaurar.

## evidencias disponibles

| control | archivo | estado |
| --- | --- | --- |
| red nat | `red-nat.png` | documentado |
| usuario estandar y administrador | `usuarios.png` | documentado |
| windows update | `windows-update.png` | documentado |
| snapshot inicial | `snapshot.png` | documentado |

## conclusion

la vm cuenta con red nat, cuentas separadas por nivel de privilegio, windows update al dia y un punto inicial de recuperacion con el nombre solicitado en el entregable.
