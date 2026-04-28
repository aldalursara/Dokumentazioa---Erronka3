---
Almacenamiento y Gestión de Cuotas
---
Para simular el almacenamiento de una empresa, se ha configurado un disco dedicado montado en /mnt/datos_empresa y se han establecido políticas de restricción de espacio (cuotas) para los usuarios.
Configuración de Cuotas

Se han aplicado cuotas de disco para limitar el espacio máximo que pueden consumir usuarios específicos (ej. usuario Alex). Esto evita que un solo empleado sature el servidor.

Para comprobar el estado global de las cuotas como administrador, utilizamos el comando:

sudo repquota -as

<img width="753" height="493" alt="Captura de pantalla 2026-04-28 083322" src="https://github.com/user-attachments/assets/be719969-823f-42a2-bd66-fa3afd7bac66" />
