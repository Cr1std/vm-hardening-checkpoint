## Configuración de Red (Red Interna)

<img width="805" height="513" alt="Red cfg" src="https://github.com/user-attachments/assets/0408caf1-5b76-4ec2-b610-acfe97f5e36f" />

Elegí el modo Red Interna porque permite que la máquina virtual funcione en un entorno completamente aislado, sin conexión a mi red doméstica ni a internet. Esto simula un laboratorio controlado donde cualquier prueba o configuración riesgosa no puede afectar a mi equipo real (Host) ni a otros dispositivos de mi red. No usé el modo Bridged porque expondría la VM directamente en mi red física con una IP visible para todos los demás dispositivos, lo cual sería un riesgo innecesario para una práctica educativa.

## Usuario sin privilegios

<img width="496" height="224" alt="Practicante" src="https://github.com/user-attachments/assets/73b3eac1-7b47-4e97-acc6-d2867a47dcf8" />


Creé un usuario llamado practicante sin permisos de administrador (sudo adduser practicante, sin agregarlo al grupo sudo). Este usuario no puede instalar programas, modificar archivos del sistema ni ejecutar comandos con privilegios elevados. Trabajar con una cuenta de permisos limitados para las tareas cotidianas reduce el daño posible si esa cuenta llegara a ser comprometida, ya que un atacante no podría escalar directamente a control total del sistema.

## Sistema actualizado

<img width="675" height="234" alt="Sistema actualizado" src="https://github.com/user-attachments/assets/68f745ed-f804-4ee9-a14c-549811ea1c1a" />

Ejecuté sudo apt update && sudo apt upgrade -y para traer el sistema al día con los últimos parches de seguridad disponibles en los repositorios de Kali. Mantener el sistema actualizado es una de las medidas más básicas y efectivas de seguridad, ya que corrige vulnerabilidades conocidas antes de que puedan ser explotadas. Para poder descargar las actualizaciones cambié temporalmente el adaptador de red a NAT (ya que en Red Interna la VM no tiene salida a internet), y una vez terminado el proceso volví la configuración a Red Interna para mantener el aislamiento original.

## Snapshot

<img width="1919" height="905" alt="Snapshot" src="https://github.com/user-attachments/assets/e67d840d-585e-44cf-84bc-c52d6661bddd" />

Creé una instantánea llamada "Hardening inicial" una vez aplicadas todas las medidas anteriores (usuario limitado y sistema actualizado). Esta snapshot funciona como un punto de restauración: si en el futuro alguna prueba o configuración dentro del laboratorio compromete el sistema, puedo volver a este estado seguro y verificado en cuestión de segundos, sin tener que reinstalar todo desde cero.
