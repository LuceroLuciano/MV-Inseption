# Máquina Virtual Inseption
Creación de una Máquina Virtual dentro de otra Máquina Virtual

#### Una Red Virtual permite la conexión entre los servicios de Azure y on-premise (de manera local)
#### Una Máquina Virtual es la simulación de una computadora que permite virtualizar el sitema operativo

#### Creando dos redes virtuales
1. Crear dos redes virtuales en [portal.azure.com](https://portal.azure.com/#home)
  

2. Buscar el servicio redes virtuales
![redes virtuales](https://github.com/LuceroLuciano/MV-Inseption/blob/main/Img/1%20redes%20virtuales.JPG)
3. CREAR 
- En Datos basicos agrega lo siguiente: 
##### Detalles del proyecto
1. SUSCRIPCIÓN = Azure para estudiantes
2. GRUPO DE RECURSOS = lab-MV-inseption
##### Detalles de Instancia
4. NOMBRE = miredvirtual1
5. REGIÓN = Centro de EE.UU.
##### Direcciones IP
1. Espacio de direcciones IPv4  dejamos la que esta por default
2. Revisar y crear
![red virtual](https://github.com/LuceroLuciano/MV-Inseption/blob/main/Img/2%20crear%20red%20virtual.JPG)
3. Crear
![crear red](https://github.com/LuceroLuciano/MV-Inseption/blob/main/Img/4%20crear%20red.JPG)

**NOTA: Se deben crear dos redes virtuales, para hacerlo se debe seguir el mismo procedimiento que se llevo a cabo para realizar la primer red virtual, con el nombre redvirtual1, lo unico que debe cambiar es el nombre, por ejemplo, la segunda red virtual se puede llamar redvirtual2.**

#### Emperajamiento de las redes virtuales
1. Ir al recurso **miredvirtual1**
2. Configuración -> emparejamientos
![emparejamiento](https://github.com/LuceroLuciano/MV-Inseption/blob/main/Img/5%20emparejamiento%20de%20red.JPG)
3. Agregar emparejamiento para conectar las máquinas virtuales
-primero emparejamos de **redvirtual1** a **redvirtual2** y depues emparejamos de **redvirtual2** a **redvirtual1**
![agregar emparejamiento](https://github.com/LuceroLuciano/MV-Inseption/blob/main/Img/6%20agregar%20emparejamiento.JPG)
![agregar emparejamiento continuación](https://github.com/LuceroLuciano/MV-Inseption/blob/main/Img/7%20agregar%20emparejamiento%20continuacion%20.JPG)
4. El emparejamiento se ve de la siguiente manera: 
![emparejamiento listo](https://github.com/LuceroLuciano/MV-Inseption/blob/main/Img/8%20emparejamiento%20de%20red%20conectado.JPG)
#### Crear dos maquinas virtuales
1. Crear la primer maquina virtual 
![mv](https://github.com/LuceroLuciano/MV-Inseption/blob/main/Img/9%20maquina%20virtual.JPG)
2. Agregar los datos correspondientes 
- SUSCRIPCIÓN = Azure para estudiantes
- GRUPO DE RECURSOS = lab-MV-iseption
- NOMBRE DE LA MÁQUINA VIRTUAL = my-mv1
- REGIÓN = Centro de EE.UU.
- OPCIONES DE DISPONIBILIDAD= No se requiere redundancia de infraestructura
- IMAGEN = Windows Server 2016
- TAMAÑO = Standar_D2s_v3-2, cpu 8 GiB de memoria
- NOBRE DE USUARIO = Lucero (Puedes cambiar el nombre por cualquier otro)
- CONTRASEÑA = **********
- PUERTO DE ENTRADA = RDP 
![MV](https://github.com/LuceroLuciano/MV-Inseption/blob/main/Img/10%20datos%20de%20la%20maquina%20virtual%201.JPG)
![MV](https://github.com/LuceroLuciano/MV-Inseption/blob/main/Img/11%20maquina%20virtual1.1.JPG)
3. En el apartado de Redes agregar los siguiente para la maquina virtual1
- RED VIRTUAL = miredvirtual1
- SUBRED = subnet1(10.0.0.0/24)
- IP PUBLICA = my-mv1-ip
![red virtual 1](https://github.com/LuceroLuciano/MV-Inseption/blob/main/Img/16%20red%20de%20maquina%20virtual%201.JPG)
4. REVISAR Y CREAR
5. CREAR
6. Crear la segunda maquina virtual
![mv2](https://github.com/LuceroLuciano/MV-Inseption/blob/main/Img/12%20maquina%20virtual%202.JPG)
7. Asignar un nombre diferente a la segunda maquina virtual, por ejemplo: **my-mv2**
![mv2](https://github.com/LuceroLuciano/MV-Inseption/blob/main/Img/13%20maquina%20virtual%202.2.JPG)
8. Asignar las credenciales correspondientes para acceder a maquina virtual2
![mv2](https://github.com/LuceroLuciano/MV-Inseption/blob/main/Img/14%20maquina%20virtual%202.3.JPG)
9. En el apartado Redes de la maquina virtual2 agregar lo siguiente:
- RED VIRTUAL = MIREDVIRTUAL2
- SUBRED = subnet2(10.1.0.0/24)
- IP PUBLICA = my-mv1-ip
![mv2](https://github.com/LuceroLuciano/MV-Inseption/blob/main/Img/15%20red%20de%20maquina%20virtual%202.JPG)


#### Conectar las Maquinas Virtuales
1. Seleccionar la maquina virtual1 **my-vm1** y conectarla mediante RDP. 
![conectar MV](https://github.com/LuceroLuciano/MV-Inseption/blob/main/Img/18%20conectar%20mv.JPG)
2. Se descargara un archivo al que se accedera para ejecutar la maquina virtual. En este apartado se deben agregar las credenciales correspondientes.
**NOTA: Las credenciales son el usuario y contraseña que asigno al crear la maquina virtual1**
![credenciales](https://github.com/LuceroLuciano/MV-Inseption/blob/main/Img/19%20credenciaes%20para%20conectar%20la%20mv.JPG)
3. Despues de ingresar las credenciales correcta ya se tiene acceso a la maquna virtual1
![mv1](https://github.com/LuceroLuciano/MV-Inseption/blob/main/Img/20%20mv%20en%20ejecucion.JPG)
4. Una vez que se ejecuto la  maquina virtual1, abrir la consola de Power Shell para ejecutar el siguiente código que permitira ejecutar la maquina virtual2.
`New-NetFirewallRule -DisplayName "Allow ICMPv4" -Protocol ICMPv4`
![codigo power shell](https://github.com/LuceroLuciano/MV-Inseption/blob/main/Img/21%20comando%20para%20conectar%20las%20mv.JPG)
5.- Antes de escribir el código para ejecutar la maquina virtual2 se debe hacer `ping` de la maquina virtual1 (En la que se encuentra ahora) hacia la maquina virtual2. Se debe tener encuenta que la dirección IP de la maquina virtual2 es `10.1.0.4` por  lo tanto debe hacer ping de la siguiente manera `ping 10.1.0.4` 
![haciendo ping de mv1 a mv2](https://github.com/LuceroLuciano/MV-Inseption/blob/main/Img/25%20haciendo%20ping%20de%20mv1%20a%20mv2.JPG)
6. Despues de verficar la conexión entre la maquina virtual1 y la maquina virtual2, ejecuta e siguiente código para acceder a la mquina virtual2 desde la mauina virtual1: `mstsc /v:10.1.0.4` y escribe las credenciales correspondientes a la maquina viretual2.
![mv2](https://github.com/LuceroLuciano/MV-Inseption/blob/main/Img/22%20credednciales%20para%20acceder%20a%20mv2.2JPG.JPG)
7. Permitir el acceso 
![acceso a mv2](https://github.com/LuceroLuciano/MV-Inseption/blob/main/Img/23%20dar%20accedo%20a%20mv2.JPG)
8. Abrir Power Shell en la maquina virtual2 y hacer ping a la maquina virtual1 con la siguiente dirección 10.0.0.4
`ping 10.0.0.4`
![ping de mv2 a mv1](https://github.com/LuceroLuciano/MV-Inseption/blob/main/Img/24%20haciendo%20ping%20de%20mv2%20a%20mv1.JPG)

#### Hata aqui se han conectado dos maquinas virtuales mediante una red virtual. 
