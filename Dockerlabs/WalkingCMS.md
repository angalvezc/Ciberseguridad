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
<h3>Con esta herramienta podemos identificar o encontrar rutas no publicas en un sitio web</h3>
<img width="576" height="784" alt="image" src="https://github.com/user-attachments/assets/8092a337-dd42-410e-af74-58a5c83dc93a" />
<h3>No se encontraron archivos sensibles pero si http://172.17.0.2/wordpress/</h3>
<img width="1807" height="824" alt="image" src="https://github.com/user-attachments/assets/f718ddf6-de43-4da1-949a-cff1b43e7a85" />
