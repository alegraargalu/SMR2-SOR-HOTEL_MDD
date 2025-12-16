# Instalación de Active Directory
## Activar e instalar Hiper-V
Durante todo este repositorio cada vez que escriba: guión, comilla o paréntesis. Seguidos o precedidos de una coma y haya mencionado que voy a proporcionar un comando me estaré refiriendo a los signos.

```mermaid
flowchart TD
A[Entra en la configuración de Windows y escribe en la barra de búsqueda Panel de Control]-->B[Clica en Programas.]
B-->C[Luego en Activar o desactivar las características de Windows.]
C-->D[Buscas Hiper-V, lo seleccionas, clicas Aceptar y lo instalas.]
D-->E[Cuando acabe le das a reiniciar y lo búscas en la lupa de la barra de tareas.]
E-->F[Entra en la configuración de Hiper-V]
F-->G[Selecciona dónde quieres que se guarden las máquinas virtuales y en qué disco duro, le das a aceptar]
G-->H[Abres el PowerShell]
H-->I[Escribes los siguientes comandos New,guión,VMSwitch guión,SwitchName comilla,NATSwitch,comilla ,guión,SwitchType Internal]
I-->J[New,guión,NetIPAddres guión,IPAddress 10.10.10.1 guión,PrefixLength 24 guión,InterfaceAlias ,comilla,vEthernet,paréntesis,NATSwitch,paréntesis,comilla]
J-->K[New,guión,NetNat guión,Name comillaNATNetwork,comilla guión,InternalIPInterfaceAddressPrefix comilla,10.10.10.0/24,comilla]
K-->L[Después de ejecutar estos comandos puedes cerar el PowerShell]
```

## Creación de la Máquina virtual e instalación de Active Directory
## Creación de la máquina

```mermaid
flowchart TD
A[Donde pone PC123, los números los he puesto de forma aleatoria, haz clic derecho y selecciona nuevo y máuqina virtual]-->B[La en la primera página dale a siguiente]
B-->C[En el nombre de la máquina pon TAILWIND-DC1 y dale a siguiente]
C-->D[Elige la Generación 2 y siguiente]
D-->E[En la memoria RAM elige 4096MB, activar el uso dinámico de la memoria para esta máuina y siguiente]
E-->F[En la configuración de red el tipo de conexión elige NATSwitch y siguiente]
F-->G[En la página del disco duro déjalo por defecto y siguiente]
G-->H[En las opciones de instalación elgie la instalación según un archivo de imagen, elige la imagen ISO de Windows Server 2022, dale a siguiente y acabar/instalar]
```

## Iniciación e instalación de Active Directory

### Configuración de red

```mermaid
flowchart TD
A-->B[Dale clic derecho en la máquina virtual y ve a puntos de acceso]
B-->C[Si la opción de usar los puntos de acceso de forma automática está desactivada dale a aceptar y si no lo está desactívala, aplica los cambio y acepta]
C-->D[En tu máquina virtual dale a conectar]
D-->E[En la pantalla que te salga dale a Start]
E-->F[Cuando aparezca la pantalla en negro y el texto que te dice que apretes cualquier tecla clica la pantalla de la virtualización y pulsa el espacio]
F --> G[Si aparece algo antes del cuadrado azul que pone Install now déjalo por defecto y sigue]
G --> H[Dale a Install now]
H --> I[Todo por defecto hasta que te pida el sistema operativo a instalar, seleciona la experiencia de escritorio, suele ser la segunda opción, y dale a Next]
I --> J[Dale todo por defecto hasta que te pida que le digas que tipoo de instalación quieres, selecciona la personalizada]
J --> K[Cuando te pida que le digas dónde quieres instalar el sistema operativo selecciona la primera opción y dale a siguiente]
K --> L[Sigue todo por defecto hasta la contraseña, que tiene que tener una mayúscula, minúscula y un carácter especial cómo un punto, la que yo he puesto es Pa55w.rdPa55w.rd]
L --> M[Acaba la instalación]
M --> N[Cuando ya estés en el escritorio entra en la configuración de red]
N --> O[Entra en cambiar las opciones del adaptador]
O --> P[Clic derecho en el adaptador]
P --> Q[Propiedades]
Q --> R[Cambiar la configuración TCP/IPv4 y aceptar]
R --> S[Direccióno IP 10.10.10.10, máscara de red 255.255.255.0 y puerta de enlace 10.10.10.1]
S --> T[Servidor DNS 1.1.1.1 y 8.8.8.8]
T --> U[Cierra y cuando te pregunte si quieres que tu dispositivo sea descubrible dile que sí]
```

### Instalación de Active Directory

```mermaid
flowchart TD
A[Entra en el Administrador del Servidor] --> B[Ves al Servidor  Local]
B --> C[Clica el nombre del equipo]
C --> D[En la ventana que te aparece pulsa cambiar]
D --> E[Pónle de nombre al equipo TAILWIND-DC1, que es el nombre que le hemos puesto a la máquina virtual y a aceptar]
E --> F[Cierra la ventana y te dará la opción de reiniciar, dale a Restart Now, si no te sale la opción de restart now reinicia tú el sistema operativo]
F --> G[Cuando hayas vuelto a entrar en la cuenta de administrador y el Server Manager/Administrador del Servidor, clica la opción Administrar/Manage y Add Roles and Features/Agregar roles y características]
G --> H[Al principio dale a siguiente, en tipo de instalación selecciona la instalación basada en roles o características]
H --> I[En el destinatario elige la opción Seleccionar uno de los servidores del grupo]
I --> J[Selecciona TAILWIND-DC1 y siguiente]
J --> K[Elige el Servicio de Dominio de Active Directory/Active Directory Domain Services y agregar roles]
K --> L[siguiente Hasta el final e Install]
L --> M[Cuanto se instale dale a la bandera]
M --> N[Clica el texto en azul que dice Promover este servidor a un controlador de dominio]
N --> O[Selecciona añadir nuevo bosque y llámalo tailwindtraders.internal y siguiente]
O --> P[Deja todos las configuraciones por defecto hasta que tengas que elegir la contraseña, tienes que seguir las mismas directrices que he dicho antes, y también es recomendable que utilices la misma contraseña que te he dicho yo, Pa55w.rdPa55w.rd]
P --> Q[DNS por defecto]
Q --> R[Opciones adicionales por defecto]
R --> S[Rutas por defecto]
S --> T[Review Options y prerrequisitos por defecto]
T --> U[Instalar y reiniciar]
U --> V[Cuando vuelvas a entrar pon de nombre de usuario tailwindtraders\administrador y la contraseña]
```

## Creación de la segunda máquina virtual, Windows Server miembro del dominio

```mermaid
flowchart TD
A[Donde pone PC123, los números los he puesto de forma aleatoria, haz clic derecho y selecciona nuevo y máuqina virtual]-->B[La en la primera página dale a siguiente]
B-->C[En el nombre de la máquina pon TAILWIND-MBR1 y dale a siguiente]
C-->D[Elige la Generación 2 y siguiente]
D-->E[En la memoria RAM elige 4096MB, activar el uso dinámico de la memoria para esta máuina y siguiente]
E-->F[En la configuración de red el tipo de conexión elige NATSwitch y siguiente]
F-->G[En la página del disco duro déjalo por defecto y siguiente]
G-->H[En las opciones de instalación elgie la instalación según un archivo de imagen, elige la imagen ISO de Windows Server 2022, dale a siguiente y acabar/instalar]
H --> I[Clic derecho a la máquin TAILWIND-MBR1]
I --> J[En la opción puntos de acceso si la opción de usar de forma automática los puntos de acceso está desactivada acepta y sal, y si no está descativado desactívalo y aplica los cambios]
J --> K[Inicia la máquina igual que antes, conectar, Start, Install now]
K --> L[Todo por defecto hasta el tipo de sistema operativo que quieres instalar, la experiencia de escritorio]
L --> M[Sigue todo por defecto hasta que te pregunte el tipo de instalación quieres, la personalizada, luego, dónde quieres instalar el sistema, en el primer disco que aparece y siguiente]
M --> N[Cuando tengas que seleccionar la contraseña pon la de antes, Pa55w.rdPa55w.rd y acabar]
N --> O[Entra en las opciones de red y cambiar las opciones de adaptador, TCP/IPv4, propiedades]
O --> P[IP 10.10.10.20, máscara 255.255.255.0 y puerta de enlace 10.10.10.1]
P --> Q[DNS 10.10.10.10 y 8.8.8.8]
Q --> R[Cierra y cuando te pregunte si quieres permitir que tu dispositivo sea descubierto di que si]
R --> S[Entra en el Administrador del Servidor, Servidor Local y cambia el nombre del equiupo a TAILWIND-MBR1, acepta y reinicia]
S --> T[Entra en la consola del Administrador del Servidor]
T --> U[Ves a la sección del Servidor Local]
U --> V[Clica cambiar en las propiedades del sistema]
V --> W[Cambia el nombre de domninio a TAILWINDTRADERS y aceptar]
```

## Instalación de Active Directory en la segunda máquina

```mermaid
flowchart TD
A --> B[Cuando hayas entrado ves al Server Manager/Administrador del Servidor, clica la opción Administrar/Manage y Add Roles and Features/Agregar roles y características]
B --> C[Al principio dale a siguiente, en tipo de instalación selecciona la instalación basada en roles o características]
C --> D[En el destinatario elige la opción Seleccionar uno de los servidores del grupo]
D --> E[Selecciona TAILWIND-DC1 y siguiente]
E --> F[Elige el Servicio de Dominio de Active Directory/Active Directory Domain Services y agregar roles]
F --> G[siguiente Hasta el final e Install]
G --> H[Cuanto se instale dale a la bandera]
H --> I[Clica el texto en azul que dice Promover este servidor a un controlador de dominio]
I --> J[Selecciona añadir un controlador de dominio a un dominio existente y escribe tailwindtraders.internal]
J --> K[Cuando hayas introducido el dominio clica en la casilla de al lado que pone seleccionar y pon en el nombre de usuario TAILWINDTRADERS\Administrador y en la contraseña la que hayas establecido, en mi caso Pa55w.rdPa55w.rd]
K --> L[En la seiguiente pestaña, las opciones de controlador de dominio, déjalas por defecto y en el modo de restauración de servicios de directorio DSRM, escribe la misma contraseña que antes]
L --> M[DNS por defecto]
M --> N[Opciones adicionales por defecto]
N --> O[Rutas por defecto]
O --> P[Review Options y prerrequisitos por defecto]
P --> Q[Cuando se reinicie inicia sesión como tailwindtraders\Administrador con la contraseña que has estado utilizando todo el rato]
```

## Transferir el RID Master a la segunda máquina

```mermaid
flowchart TD
A[Entra en el Administrador del Servidor] --> B[En herramientas entra en Usuarios y equipos de Active Directory]
B --> C[Haz clic derecho en Usuarios y equipos de Active Directory]
C --> D[Todas las tareas y Maestros de operaciones]
D --> E[En la pestaña RID pulsa cambiar, di que Sí y luego acepta]
```

## Creación de un sitio y configuración de una subred

```mermaid
flowchart TD
A[Entra con la cuenta TAILWINDTRADERS\Administrador] --> B[En Herramientas entra en Servicios y sitios de Active Directory]
B --> C[Haz clic derecho en sitios]
C --> D[Nuevo sitio]
D --> E[En la casilla nombre pon Sydney]
E --> F[En el nombre de enlace elige DEFAULTIPSITELINK y aceptar]
F --> G[Expande la carpeta sitios]
G --> H[Haz clic derecho en subredes]
H --> I[Nueva subred]
I --> J[En el prefijo escribe 172.16.1.0/24]
J --> K[Elige Sydney en el nombre de sitio y acepta]
```

## Creación de unidades organizativas

```mermaid
flowchart TD
A[Entra a la otra máquina virtual, TAILWIND-DC1, y al Administrador del Servidor] --> B[En Herrmientas entra en la opción Usuarios y equipos de Active Directory]
B --> C[Clic derecho en tailwindtraders.internal]
C --> D[Nuevo]
D --> E[Unidad Organizativa]
E --> F[En nombre escribe Sydney y acepta]
F --> G[Vuelve a hacerlo pero en el nombre en lugar de Sydney escribe Melbourne y Brisbane]
```

## Creación de usuarios

```mermaid
flowchart TD
A[Entra en Administrador del Servidor] --> B[Entra en Usuarios y equipos de Active Directory, está en Herramientas]
B --> C[Clic derecho en Sydney]
C --> D[Nuevo]
D --> E[Escribe SydneyContractor en la casilla de nombre completo y nombre de inicio de sesión de usuario]
E --> F[Siguiente]
F --> G[En la contraseña escribe Pa55w.rdPa55w.rd y siguiente]
G --> H[Finalizar]
H --> I[Clica Sydney]
I --> J[Haz doble clic en SydneyContractor]
J --> K[En la pestaña Cuenta ves al tiempo de caducación]
K --> L[En Fin de... pon de fecha 1 de enero de 2030]
L --> M[Aceptar]
M --> N[Haz clic derecho en SydneyContractor]
N --> O[Copiar]
O --> P[Escribe MelbourneContractor en la casilla de nombre completo y inicio de sesión de usuario]
P --> Q[Siguiente]
Q --> R[En contraseña escribe Pa55w.rdPa55w.rd]
R --> S[Siguiente y Finalizar]
S --> T[Haz clic derecho en SydneyContractor y copiar]
T --> U[En el apartado de nombre completo y nombre de inicio de sesión de usuario BrisbaneContractor]
U --> V[Siguiente]
V --> W[En la contraseñea escribe Pa55w.rdPa55w.rd]
W --> X[Siguiente y Finalizar]
X --> Y[Mueve el MelbourneContractor a Melbourne y acepta la advertencia]
Y --> Z[Mueve el BrisbaneContractor a Brisbane y acepta la advertencia]
```

## Creación de grupo de administradores de Sydney

```mermaid
flowchart TD
A[Entra en el Administrador del Servidor] --> B[En la pestaña Herramientas entra en Usuarios y equipos de Active Directory]
B --> C[Clic derecho en tailwindtraders.internal]
C --> D[Nuevo]
D --> E[Grupo]
E --> F[En el nombre escribe Administradores de Sydney]
F --> G[Selecciona Universal]
G --> H[Acepta]
H --> I[En Sydney haz doble clic en SydneyContractor]
I --> J[En la ventana Miembro de... pulsa agregar]
J --> K[Escribe Administradores de Sydney]
K --> L[Comprobar nombres]
L --> M[Acepta todo]
```

## Creación de un usuario como un usuario protegido

```mermaid
flowchart TD
A[Entra en el Administrador del Servidor] --> B[En la ventana Herramientas entra en Usuarios y Equipos de Active Directory]
B --> C[Ves a Sydney]
C --> D[Doble clic en SydneyContractor]
D --> E[En la venta Miembro de... clica agregar]
E --> F[Escribe Usuarios protegidos]
F --> G[Comprueba el nombre]
G --> H[Acepta todo]
```

## Delegar permisos de seguridad

```mermaid
flowchart TD
A[Entra en el Administrador del Servidor] --> B[Desplega la ventana de Herramientas y abre Usuarios y Equipos de Active Directory]
B --> C[Haz clic derecho en Sydney]
C --> D[Delegar control]
D --> E[En la primera página déjala por defecto y sigue]
E --> F[Pulsa agregar y escribe Administradores de Sydney]
F --> G[Comprobar nombres]
G --> H[Aceptar y siguiente]
H --> I[En las tareas a delegar elige Restaurar contraseñas de usuarios y forzar el cambio de contraseñas en le siguiente inicio de sesión]
I --> J[Siguiente y Finalizar]
```

## Configuración de atributos para un usuario

```mermaid
flowchart TD
A[Entra en el Administardor del Servidor] --> B[Enra en Usuarios y Equipos de Active Directory]
B --> C[Selecciona Sydney]
C --> D[Haz clic derecho en SydneyContractor]
D --> E[Propiedades]
E --> F[En la ventana de Direcciones selecciona en la casilla de ciudad Sydney]
F --> G[Siguiente]
G --> H[Haz clic derecho en tailwindtrader.internal]
H --> I[Buscar]
I --> J[En la ventana Avanzado pulsa la casilla de arriba a la izquierda]
J --> K[Selecciona usuario y luego ciudad]
K --> L[En la condicion selecciona Es paréntesis,exacto,paréntesis]
L --> M[Elige o escribe Sydney y encontrar ahora]
M --> N[Clica Sí]
N --> O[Comprueba que el SydneyContractor aparece en la lista de resultados encontrados]
O --> P[Ciérralo]
```

## Desactivar el Usuario Contratista de Melbourne

```mermaid
flowchart TD
A[Entrar en el Administrador del Servidor] --> B[En la ventana Herramientas entra en Usuarios y Equipos de Active Directory]
B --> C[Dale a Melbourne]
C --> D[Clic derecho en MelbourneContrator]
D --> E[Desactivar cuenta]
E --> F[Aceptar]
```

## Restablecer contraseña del Usuario Contratista de Brisbane

```mermaid
flowchart TD
A[Entra en el Administrador del Servidor] --> B[En la ventana Herramientas entra en Usuarios y Equipos de Active Directory]
B --> C[Entra en Brisbane]
C --> D[Clic derecho en BrisbaneContractor]
D --> E[Restablecer contraseña]
E --> F[En la caja de texto para restablecer la contraseña escribe Pa66w.rdPa66w.rd]
F --> G[Acepta todo]
```

## Configuración de Directiva de Contraseña de Dominio

```mermaid
flowchart TD
A[Entra en el Administrador del Servidor] --> B[En la ventana Herramientas entra en el Administrador de Directivas de Grupo]
B --> C[Expande el Bosque tailwindtraders.internal]
C --> D[Expande la carpeta Dominios]
D --> E[Expande el Dominio tailwindtraders.internal]
E --> F[Clic derecho en las Directivas de Dominio por Defecto]
F --> G[Editar]
G --> H[Expande Equipo/Computer]
H --> I[Expande Configuración]
I --> J[Expande Directivas]
J --> K[Expande Configuración de Windows]
K --> L[Expande Configuración de Seguridad]
L --> M[Expande Directivas de Cuenta]
M --> N[Expande Directivas de contraseñas]
N --> O[Dale doble clic a la longitud mínima de la contraseña]
O --> P[Cambia la longitud mínima a 14]
P --> Q[Acepta y ciérralo todo]
```

## Configuración de Directivas de Contraseñas

```mermaid
flowchart TD
A[Entra en el Administrador del Servidor] --> B[En la vetana Herramientas entra en el Centro Administrativo de Active Directory]
B --> C[Clica en tailwindtraders paréntesis,local,paréntesis]
C --> D[Busca la opción Sistema en el panel que hay al lado en la mitad superior del panel donde está la opción que hemos seleccionado anteriormente]
D --> E[Expande esa opción]
E --> F[Busca Configuración de contraseña, clic derecho, nuevo]
F --> G[Configuración de contraseña]
G --> H[En la casilla a rellenar pon Domain Admin Password Policy]
H --> I[La casilla Precedente ponla en 1]
I --> J[La longitud mínima de la contraseña ponla en 16]
J --> K[Acepta]
K --> L[Abre la nueva Directiva de Contraseña de Administradores de Dominio]
L --> M[En la sección de Aplicación directa, en la casilla de texto, escribe Domain Admins si tu versión de Windows server está en inglés y Admins. del dominio si está en español]
M --> N[Comprobar nombres]
N --> O[Acepta todo]
```

## Activar la papelera de reciclaje de Active Directory

```mermaid
flowchart TD
A[Entra en el Administardor del Sistema] --> B[En la ventana Herramientas entra en el Centro de Administración de Active Directory]
B --> C[Clica tailwindtraders paréntesis,local,paréntesis]
C --> D[En la parte de la derecha Activar Papelera de reciclaje]
D --> E[Acepta las dos advertencias]
```
## Restinción de la Autenticación NTLM

```mermaid
flowchart TD
A[Entra en el Administardor del Sistema] --> B[En la ventana Herramientas entra en el Administrador de Directivas de Grupo]
B --> C[Expande el Bosque tailwindtraders.internal]
C --> D[Expande la carpeta Dominios]
D --> E[Expande el Dominio tailwindtraders.internal]
E --> F[Clic derecho en las Directivas de Dominio por Defecto]
F --> G[Editar]
G --> H[Expande Equipo/Computer]
H --> I[Expande Configuración]
I --> J[Expande Directivas]
J --> K[Expande Configuración de Windows]
K --> L[Expande Configuración de Seguridad]
L --> M[Expande Directivas Locales]
M --> N[Expande Opciones de Seguridad]
N --> O[Selecciona y haz doble clic Seguridad de la Red]
O --> P[Restringir NTLM]
P --> Q[Autenticación de NTLM en este dominio]
Q --> R[Pulsa la casilla Define esta configuración de Directiva]
R --> S[Selecciona Denegar todo]
S --> T[Acepta y di que Sí en la casilla de confirmación]
```

## Gestión de cuentas de Usuario en Sydney

```mermaid
flowchart TD
A[Entra en el Administardor del Servidor] --> B[En la ventana Herramientas entra en Administrador de directivas de grupo]
B --> C[Expande tailwindtradders.internal]
C --> D[Clic derecho en Sydney]
D --> E[Crear un GPO en este dominio o vincularlo aquí]
E --> F[Ponle de nombre al nuevo GPO SydneyOUPolicy]
F --> G[Aceptar]
G --> H[Clic derecho en SydneyOUPolicy]
H --> I[Editar]
I --> J[Pulsa Configuración de Equipo]
J --> K[Expande Políticas]
K --> L[Expande Configuración de Windows]
L --> M[Expande Configuración de Seguridad]
M --> N[Expande Configuración de Directiva de auditoría avanzada]
N --> O[Expande Directivas de auditoría]
O --> P[Pulsa Administración de cuentas]
P --> Q[Haz doble clic en Auditoría de gestión de cuentas de usuario]
Q --> R[Haz clic en la casilla de verificación Gestión de Cuentas de Usuario]
R --> S[Clic en la casilla Configurar los siguientes eventos de auditoría]
S --> T[Selecciona  los valores de Éxito y Fracaso]
T --> U[Aceptar]
```

## Denegación del inicio de sesión como servicio

```mermaid
flowchart TD
A[Entra en el Administardor del Servidor] --> B[En la ventana Herramientas entra en Administrador de directivas de grupo]
B --> C[Expande tailwindtraders.internal]
C --> D[Pulsa en Sydney]
D --> E[Clic derecho en SydneyOUPolicy]
E --> F[Editar]
F --> G[G]
G --> H[Expande Configuración de Equipo]
H --> I[Directivas]
I --> J[Configuración de Windows]
J --> K[Configuración de Seguridad]
K --> L[Directivas Locales]
L --> M[Asignaciónd de derechos de usuario]
M --> N[Haz doble clic en Denegar inicio de sesión como servicio]
N --> O[Selecciona la configuración Definir esta política]
O --> P[Agregar Usuario o grupo]
P --> Q[Explorar]
Q --> R[Avanzado]
R --> S[Buscar ahora]
S --> T[En el grupo selecciona Adminstradores de Sydney]
T --> U[Aceptar todo]
```
