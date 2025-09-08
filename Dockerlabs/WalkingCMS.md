<h1>Máquina WalkingCMS</h1>

<h2>1. Corremos la máquina en Docker</h2>
<img width="567" height="222" alt="image" src="https://github.com/user-attachments/assets/82fbde96-3f23-4a5f-95fc-bf96b1481be3" />
<h2>2. Se verifica la conexion con la maquina</h2>
<img width="478" height="144" alt="image" src="https://github.com/user-attachments/assets/13734a24-6f5c-4fff-94c1-626287e54630" />
<h2>3. Se realiza un escaneo con nmap</h2>
<h3>Logramos identificar que el puerto 80 http esta abierto</h3>
<img width="995" height="315" alt="image" src="https://github.com/user-attachments/assets/c4ef47dd-8d18-4daf-af5b-c9a7240ab4cf" />
<h2>4. Accedemos al sitio web</h2>
<h3>Al parecer se trata de un default page de APACHE</h3>
<img width="1527" height="888" alt="image" src="https://github.com/user-attachments/assets/8389df70-db2d-44fd-a45b-c8ca4c7a23bb" />

<h2>6. Utilizamos la herramienta DIRB</h2>
<h3>Con esta herramienta podemos identificar o encontrar rutas no publicas en un sitio web
Encontramos http://172.17.0.2/wordpress/index.php (CODE:301|SIZE:0)  </h3>
<img width="576" height="784" alt="image" src="https://github.com/user-attachments/assets/8092a337-dd42-410e-af74-58a5c83dc93a" />
<h3>No se encontraron archivos sensibles pero si http://172.17.0.2/wordpress/</h3>
<img width="1807" height="824" alt="image" src="https://github.com/user-attachments/assets/f718ddf6-de43-4da1-949a-cff1b43e7a85" />
<h2>7. Utilizamos el wfuzz para buscar wp-config.php</h2>
<h3>Los archivos como wp-config.php contienen credenciales de la base de datos y rutas críticas, pero al ingresar no se muetra nada ya porque realmente no posee nada o no es accesible HTTP</h3>
<img width="1680" height="437" alt="image" src="https://github.com/user-attachments/assets/1b108374-bda1-4bd0-9879-5dac4fa06a62" />
<img width="1319" height="689" alt="image" src="https://github.com/user-attachments/assets/d7908a97-1ad9-4514-b854-ef06ed2ffc2f" />
<h3>Utilizando otra herramienta de busqueda de directorios en el se encontro varios con autenticacion wordpress </h3>
<img width="1146" height="534" alt="image" src="https://github.com/user-attachments/assets/fe56802c-4448-4364-bc9a-b0aa20ea8fe1" />
<h2>8.Procedemos a realizar un SQLInjection mediante la herramienta wpscan</h2>
<img width="585" height="632" alt="image" src="https://github.com/user-attachments/assets/47a0394d-2b5d-4271-b747-2d3caf5fdbf7" />
<h3>Se encontro vulnerabilidades con el XML-RPC.php y  un Usurio registrado como mario mediante wpscan --url http://172.17.0.2/wordpress/ --enumerate u, vp </h3>
<img width="785" height="167" alt="image" src="https://github.com/user-attachments/assets/5a25c113-1585-4b54-beb7-ae016c7f8866" />
<img width="717" height="168" alt="image" src="https://github.com/user-attachments/assets/67d19560-720d-4e20-8516-c37f81a43799" />
<h3>WPScan intentará cada contraseña de la lista para el usuario mario con wpscan --url http://172.17.0.2/wordpress/ --passwords /usr/share/wordlists/rockyou.txt --usernames mario </h3>
<img width="833" height="332" alt="image" src="https://github.com/user-attachments/assets/9b01a492-e7c3-40aa-bd44-0541befa8f07" />
<h2>9.Ingresamos credenciales de mario</h2>
<img width="1914" height="778" alt="image" src="https://github.com/user-attachments/assets/163ab3b0-e69d-4479-9847-5ccccc5e562e" />
<h2>10. Ejecucion remota</h2>
<h3>Se realiza ingresando al Theme Code Editor y modificando en este caso el index.php, este código es una puerta de acceso completa al sistema</h3>
<img width="1891" height="758" alt="image" src="https://github.com/user-attachments/assets/c3a16928-36a7-4fcb-9ac1-72a6b5b28b14" />
<h3>Hacemos UpdateFile</h3>
<img width="111" height="67" alt="image" src="https://github.com/user-attachments/assets/fd7917e7-5fc3-42e1-acc4-941cc1a01c1a" />
<h3>Se ejecutó un comando sencillo para verificar la vulnerabilidad http://172.17.0.2/wordpress/wp-content/themes/twentytwentytwo/index.php?cmd=whoami
 al ejecutarse debera salir whoami y www-data al usuario con el que corre el servicio web.</h3>
<img width="1900" height="620" alt="image" src="https://github.com/user-attachments/assets/e8d6dea6-2ac4-41ad-80eb-53b0d78be8ac" />
<h3>Se ha conseguido una ejecucion remota con el cmd, ahora se procede al reverse shell poniendo en escucha el puerto 443</h3>
<img width="267" height="50" alt="image" src="https://github.com/user-attachments/assets/a4d2170b-88ec-4731-bb0a-55212c501a1a" />
<img width="964" height="38" alt="image" src="https://github.com/user-attachments/assets/5ada3306-2aca-451f-a48c-a704189f8cb8" />
<img width="647" height="128" alt="image" src="https://github.com/user-attachments/assets/3e6077f7-ed00-4fe0-bbbb-0408179b23b2" />
<h3>Buscamos todos los archivos SUID del sistema</h3>
<img width="693" height="186" alt="image" src="https://github.com/user-attachments/assets/82e68443-b80c-4cd7-912c-22b08b11c251" />
<h3>/usr/bin/env se encuentra en la lista el cual nos permitirá escalar privilegios </h3>
<img width="584" height="72" alt="image" src="https://github.com/user-attachments/assets/135e739e-5be7-4376-89b8-0eb0b564ec0b" />














