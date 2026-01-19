# Creación de Cuentas Operativas
```mermaid
flowchart TD
A[Entra en tu servidor con una cuenta de administrador]-->B[Abre el Administrador de servidor]
B-->C[En Herramientas entra en Usuarios y equipos de Active Directory]
C-->D[Click derecho en el dominio]
D-->E[Crea una nueva unidad organizativa para los trabajadores del Hotel]
```

### Click derecho en la unidad organizativa y “Nuevo” “Usuario”, de esta forma creas usuarios en las unidades organizativas.

<img width="1920" height="1080" alt="imagen" src="https://github.com/user-attachments/assets/7e31b733-568e-45d3-a0b7-e689595d48b9" />

### Indicas la opción “El usuario debe cambiar la contraseña en el siguiente inicio de sesión

<img width="1920" height="1080" alt="imagen" src="https://github.com/user-attachments/assets/eb640e80-25e2-4c91-b2a5-6b247687c519" />
<img width="1920" height="1080" alt="imagen" src="https://github.com/user-attachments/assets/f7db48ca-1152-4a68-9519-a9d407e5ae1a" />

### Entra en “Herramientas” y “Administración de directivas de grupo. Desplega las carpetas que se ven en la imagen y ahí puedes editar la longitud, caducidad... De las contraseñas.

<img width="937" height="767" alt="imagen" src="https://github.com/user-attachments/assets/f7fff297-1232-4d86-9109-0c4fe4babd17" />

### Vuelve a “Usuarios y equipos de Active Directory”, ves a la cuenta del trabajador que quieras, click derecho y “Propiedades”, en la sección cuenta puedes modificar las franjas horarias en las que la cuenta podrá ser usada.

<img width="938" height="743" alt="imagen" src="https://github.com/user-attachments/assets/3ed6e3e2-1e14-4c2e-890b-7f86bc4c8bbb" />

# Definición de Entornos de Trabajo

### Entra en la unidad organizativa de los trabajadores del hotel y crea otra unidad organizativa dentro para los encargados de la seguridad.

<img width="935" height="764" alt="imagen" src="https://github.com/user-attachments/assets/7a19d9fd-ae5e-4b50-91ad-dcb7f83f9299" />
<img width="935" height="764" alt="imagen" src="https://github.com/user-attachments/assets/39db01b8-44d6-4812-9aad-189134ed6601" />

### Dentro de la unidad organizativa crea un grupo y dentro del mismo las cuentas de las personas pertenecientes a la seguridad

<img width="935" height="768" alt="imagen" src="https://github.com/user-attachments/assets/0f893eb3-d0ba-4037-80b2-81a6a8445e6f" />
<img width="935" height="766" alt="imagen" src="https://github.com/user-attachments/assets/4f4ef129-a4f5-4596-aaab-43bed4f58c7c" />
<img width="935" height="767" alt="imagen" src="https://github.com/user-attachments/assets/29610f8f-282f-4a27-9b68-45b878290ed3" />
<img width="935" height="765" alt="imagen" src="https://github.com/user-attachments/assets/d1ff8035-eaa2-4c61-b159-aecaa33fcac7" />

### Crea en la unidad DVD y si no puedes en la C: una carpeta llamada finanzas, que es a la que accederán las cuentas anteriormente creadas, click derecho y Propiedades, entra en Uso compartido avanzado

<img width="929" height="764" alt="imagen" src="https://github.com/user-attachments/assets/3b9355ea-955a-4e3d-aa3f-190490b62012" />

### Dale a agregar, añade el grupo en el que están las cuentas que tienen que poder entrar a esta carpeta y activa la casilla de darle control total

<img width="933" height="768" alt="imagen" src="https://github.com/user-attachments/assets/3e36a385-fec6-4808-a379-7b7dca661d76" />

### Click derecho en la carpeta finanzas, propiedades y ves al apartado seguridad, le das a editar, quita a los usuarios y añade a la unidad organizativa en la que están los empleados encargados de esta carpeta

<img width="952" height="766" alt="imagen" src="https://github.com/user-attachments/assets/d398380c-0f1d-4eff-82c8-10b743897f23" />

### Si no te deja y te dice que ha heredado permisos antes de darle a editar entra en opciones avanzadas y dale a “desabilitar herencia” y a la primera opción “Convertir los permisos...”

### Ves a la Administración de directivas de grupo en las Herramientas, ves a la unidad organizativa del grupo de empleados que no tengan que poder tener acceso al panel de control y click derecho

<img width="933" height="766" alt="imagen" src="https://github.com/user-attachments/assets/f3d08e62-b5c5-4d70-9f65-4e1a0e435ebf" />
<img width="937" height="763" alt="imagen" src="https://github.com/user-attachments/assets/7de6864e-c8eb-4303-98af-1d916b6c1580" />
<img width="938" height="767" alt="imagen" src="https://github.com/user-attachments/assets/c119c5fe-5847-483b-97f9-153650cb945c" />
<img width="937" height="767" alt="imagen" src="https://github.com/user-attachments/assets/fc41b044-0b86-41ce-b6ff-76a0648ccc84" />
<img width="932" height="773" alt="imagen" src="https://github.com/user-attachments/assets/96fde8ea-0cf2-4fdd-aa9f-b28b364e01e3" />

### Click derecho y entra a propiedades, haz lo que ves en la captura
### Ejecutar este comando en el cmd de los ordenadores de Recepción y reiniciar gpupdate /force

# Registro de Dispositivos

A[Inicia el servidor]-->B[Entra en el Administrador del servidor]
B-->C[Herramientas]
C-->D[Administrador de directivas de grupo]
D-->E[Crear una UO llamada por ejemplo: Equipos_Hotel]
E-->F[Cambia el nombre el dispositivo fijo]
F-->G[Únelo al dominio]

# Diseño de la Estructura de Acceso

<img width="347" height="146" alt="imagen" src="https://github.com/user-attachments/assets/4cd99e38-f4e0-4e03-bac2-60f7a8ae06d1" />

# Implementación de Grupos Funcionales

<img width="954" height="767" alt="imagen" src="https://github.com/user-attachments/assets/23f74812-53d9-4ed5-a1fb-6bb1a30c9e73" />

A[Estos son los grupos]-->B[Para que solo ellos tengan acceso a determinados recursos cómo carpetas]
B-->C[Click derecho en la carpeta]
C-->D[Propiedades]
D-->E[Apartado seguridad]
E-->F[Editar]
F-->G[Quita el grupo usuarios que son los todos los trabajadores y añade el grupo que tenga que acceder a esa carpeta]
G-->H[Si no te dejase quitar a los usuarios antes de darle a editar dale a opciones avanzadas y dale a deshabilitar herencia y la primera opción]

# Asignación de Permisos

<img width="953" height="742" alt="imagen" src="https://github.com/user-attachments/assets/f2ab43b3-6f37-4f3f-a86c-62489432589a" />

<img width="954" height="741" alt="imagen" src="https://github.com/user-attachments/assets/b8f51a5e-5d24-4d9e-b397-a7ef0d31c10f" />

<img width="952" height="745" alt="imagen" src="https://github.com/user-attachments/assets/caee9aec-1129-4e3d-8685-10a6281a408e" />

<img width="953" height="742" alt="imagen" src="https://github.com/user-attachments/assets/02b95a1a-7c66-44a2-aa69-a829b71faa63" />

<img width="951" height="766" alt="imagen" src="https://github.com/user-attachments/assets/c61e73eb-fd4e-4d89-9e9e-b5c72f7f4e68" />

### En este caso yo he creado directamente los nuevos usuarios en los grupos correspondientes, pero si no fuese así y has creado las cuentas en sitios que no son sus unidades organizativas correspondientes solo tienes que darle click derecho a la cuenta que quieras mover, pinchas la opción mover y escribes el nombre de la unidad organizativa a la que quieras moverlo

# Auditoría de Seguridad Inicial

<img width="1365" height="767" alt="imagen" src="https://github.com/user-attachments/assets/670ae653-b86b-4d86-9c50-59ad88b5e74f" />

<img width="1365" height="743" alt="imagen" src="https://github.com/user-attachments/assets/d6442486-5f48-4e48-b09b-4c917eb05e6b" />

<img width="1366" height="742" alt="imagen" src="https://github.com/user-attachments/assets/e700a0af-b66b-4879-8026-4d77b1c0c61c" />

<img width="336" height="128" alt="imagen" src="https://github.com/user-attachments/assets/67026375-550d-4c9f-92f4-1c0a1ece0817" />

# Movilidad y Despliegue de Perfiles

### Crea una nueva unidad organizativa para los trabajadores móviles, también crea la carpeta o carpetas correspondientes y haz lo mismo que hemos hecho con la carpeta seguridad

<img width="1365" height="743" alt="imagen" src="https://github.com/user-attachments/assets/a5cba07c-ddf8-4c94-a138-f6086044e041" />

<img width="1364" height="764" alt="imagen" src="https://github.com/user-attachments/assets/1da51404-4caf-4c96-8a7b-e3d7e9e89d92" />

<img width="1366" height="765" alt="imagen" src="https://github.com/user-attachments/assets/5caf158b-b98e-42fb-be1d-d0f1c4bbcdf7" />

<img width="1364" height="767" alt="imagen" src="https://github.com/user-attachments/assets/57e8ee11-0f96-4629-8711-10946c712c9c" />

<img width="1365" height="767" alt="imagen" src="https://github.com/user-attachments/assets/c3261a65-d120-4ebe-be33-e0634cffd0bb" />

<img width="1363" height="767" alt="imagen" src="https://github.com/user-attachments/assets/33e95c7c-4cd2-4d3d-9b59-0cb7adb7398e" />

<img width="1364" height="766" alt="imagen" src="https://github.com/user-attachments/assets/84662a2b-e222-4576-8c78-522703789fdc" />

<img width="1361" height="767" alt="imagen" src="https://github.com/user-attachments/assets/141fed6b-e403-4a7c-8f8f-a6c65aa3a2ea" />
