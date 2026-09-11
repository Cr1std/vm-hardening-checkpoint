## Configuración de Red (NAT)

<img width="878" height="585" alt="NAT" src="https://github.com/user-attachments/assets/baab2f7d-488b-446e-9c3e-83816e4fb485" />

Configuré el adaptador de red de la máquina virtual en modo NAT. Con este modo, la VM tiene salida a internet, pero el tráfico pasa a través de una traducción de direcciones que gestiona VirtualBox — la VM no comparte la misma red que mi máquina real (Host) ni tiene una IP visible dentro de mi red doméstica. Esto significa que ningún dispositivo externo puede iniciar una conexión directa hacia la VM, protegiendo así a mi equipo real de cualquier prueba o configuración que se realice dentro del laboratorio.

## Usuario sin privilegios

<img width="496" height="224" alt="Practicante" src="https://github.com/user-attachments/assets/73b3eac1-7b47-4e97-acc6-d2867a47dcf8" />


Creé un usuario llamado practicante sin permisos de administrador (sudo adduser practicante, sin agregarlo al grupo sudo). Este usuario no puede instalar programas, modificar archivos del sistema ni ejecutar comandos con privilegios elevados. Trabajar con una cuenta de permisos limitados para las tareas cotidianas reduce el daño posible si esa cuenta llegara a ser comprometida, ya que un atacante no podría escalar directamente a control total del sistema.

## Sistema actualizado

<img width="675" height="234" alt="Sistema actualizado" src="https://github.com/user-attachments/assets/68f745ed-f804-4ee9-a14c-549811ea1c1a" />

Ejecuté sudo apt update && sudo apt upgrade -y para traer el sistema al día con los últimos parches de seguridad disponibles en los repositorios de Kali. Mantener el sistema actualizado es una de las medidas más básicas y efectivas de seguridad, ya que corrige vulnerabilidades conocidas antes de que puedan ser explotadas. Para poder descargar las actualizaciones cambié temporalmente el adaptador de red a NAT (ya que en Red Interna la VM no tiene salida a internet), y una vez terminado el proceso volví la configuración a Red Interna para mantener el aislamiento original.

## Snapshot

<img width="1919" height="905" alt="Snapshot" src="https://github.com/user-attachments/assets/e67d840d-585e-44cf-84bc-c52d6661bddd" />

Creé una instantánea llamada "Hardening inicial" una vez aplicadas todas las medidas anteriores (usuario limitado y sistema actualizado). Esta snapshot funciona como un punto de restauración: si en el futuro alguna prueba o configuración dentro del laboratorio compromete el sistema, puedo volver a este estado seguro y verificado en cuestión de segundos, sin tener que reinstalar todo desde cero.
