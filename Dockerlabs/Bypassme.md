<h1>Máquina BypassMe</h1>

<h2>1. Corremos la máquina en Docker</h2>

<img width="522" height="410" alt="image" src="https://github.com/user-attachments/assets/9e193642-051b-4694-8786-eba950c6ae9c" />

<h2>2. Se verifica la conexion con la maquina</h2>
<img width="477" height="163" alt="image" src="https://github.com/user-attachments/assets/8b6c49d2-435b-4f62-ae6d-5d7af2271da8" />
<h2>3. Se hace un escaneo con nmap</h2>
<h3>Con nmap se identifica que entre los 1000 puertos mas comunes se encontro que hay 2 puertos abiertos los cuales son el 22 servicio ssh y el 80 servicio http y ademas los posibles sistemas operativos asociados al host</h3>
<img width="988" height="332" alt="image" src="https://github.com/user-attachments/assets/83708653-7242-4a5c-aa07-d523e9e9a4ad" />
<h2>4. Se accede a la ip de la maquina</h2>
<h3>Se puede observar que hay un login</h3>
<img width="1173" height="712" alt="image" src="https://github.com/user-attachments/assets/e065422e-8dcd-4a35-bea3-bcacce39e12c" />
<h2>5. Se intenta acceder mediante de SQLInjection</h2>
<h3>username: admin' or '1'='1
password: admin' or '1'='1</h3>
<h3>Ahora en el cuadro de mando se indica que los logs están públicos</h3>
<img width="1176" height="590" alt="image" src="https://github.com/user-attachments/assets/a134fb26-8f0b-4f99-ad31-ccb0ae8fc0c3" />
<h2>6. Utilizamos la herramienta DIRB</h2>
<h3>Con esta herramienta podemos identificar o encontrar rutas no publicas en un sitio web</h3>
<img width="459" height="410" alt="image" src="https://github.com/user-attachments/assets/75f09f3e-0880-4113-8062-e855b97074ce" />
<h3>Como podemos ver exite la ruta /logs con 403 acceso restringido</h3>
<h2>7. Intentamos entrar a la direccion</h2>
<img width="724" height="331" alt="image" src="https://github.com/user-attachments/assets/3a7b9ce4-5488-42d4-b15b-790160054d07" />
<h3>Utilizamos el formato page para poder ingresar</h3>
<img width="1903" height="268" alt="image" src="https://github.com/user-attachments/assets/0e4caaeb-7deb-46da-94c7-7313e91cd74b" />
<h3>En este log.txt encontramos al usuario albert y se identifica que el 12:04:24 albert se autentico exitosamente con 'NGxiM3J0MTIz' </h3>
