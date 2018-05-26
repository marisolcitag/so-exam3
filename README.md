**1.**
# Examen Final 
**Nombre:** Marisol Giraldo Cobo

**Código:** A00246380

**Correo:** marisol.giraldo@correo.icesi.edu.co

**Curso:** Sistemas Operativos

**Tema:**  Comandos de Linux, python3, APIs, Pruebas unitarias.

**Profesor:** Daniel Barragán

**2.**
# DESCRIPCIÓN:
Con la realización de este Readme, se pretende demostrar que se conocen y saben emplear comandos de Linux para tareas específicas. Se sabe realizar programas en python3 que obtengan información del sistema operativo. Se diseña e implementan APIs REST para la integración con microservicios y se sabe implementar pruebas unitarias con mecanismos de integración continua. Para este examen se utilizará la máquina virtual ejecutando a través de VM VirtualBox con el Sistema Operativo CENTOS 7, y los scripts se realizarán en el Lenguaje de Programación Python .

**3.**
# IMPLEMENTACIÓN SERVICIO WEB FLASK
Para la implementación del SERVICIO WEB FLASK se realizan los siguientes pasos:                                                         
1. Crear un ambiente virtual con el nombre de flaskdev.                                                                                  
$ mkvirtualenv flaskdev                                                                                                                  
$ workon flaskdev

2. Instalar la libreria Flask y psutil                                                                                                    
$ pip install Flask                                                                                                                      
$ pip install psutil

3. Se crean los achivos de nombre requirements.txt y requirements_dev.txt.
   NOTA: El código fuente se obtuvo del repositorio del curso en la URL GITHUB: https://github.com/ICESI-Training/so-microservice.git

4. Se crea una carpeta con el nombre op_stats donde se encontrará:
- El archivo __init__.py que se encarga de inicializar paquetes de Python. 

- El archivo app.py que contiene el programa con los métodos necesarios para conocer el consumo de la CPU, la Memoria RAM Disponible y     el Espacio Disponible en Disco.

![app py](https://user-images.githubusercontent.com/35766585/40526334-79d17a68-5fab-11e8-9927-fd895f786801.png)

- El archivo stats.py que contiene la clase Stats() con los métodos: dar_porcentaje_cpu(), dar_memoria_disponible(), dar_espacio_disco()   que permite implementar los servicios encargados de realizar las consultas de información del sistema .

![stats py](https://user-images.githubusercontent.com/35766585/40526355-9fc0f53c-5fab-11e8-8528-7040a6c5b248.png)

5. Finalmente se ejecuta la aplicación mediante el comando:                                                                              
$ python app.py

6. Para obtener la información  del sistema se hace uso de la herramienta POSTMAN que permite el envío de peticiones HTTP REST sin          necesidad de desarrollar un cliente.
- Descargar Postman de la página: https://www.getpostman.com/
- Instalar Postman 
- Consultar la dirección IP de la máquina virtual $ ip a
- Ejecutar el comando $ python3 app.py para subir el servicio del servidor a través del puerto 8080.
- Ejecutar Postman y en la barra hacer la solicitud HTTP por medio del método GET colocando la instrucción de la siguiente forma => 
  DIRECCIONIP:8080/@app.route donde:
  DIRECCIONIP es la dirección IP de la conexión de la máquina virtual.
  8080 es el puerto mediante el cual se realizará la conexión con el servidor.
  @app.route la ruta de la variable que deseo obtener. Por ejemplo: '/v1/stats/cpu', '/v1/stats/memory', '/v1/stats/disk'                 
NOTA: Los pasos expuestos anteriormente se realizaron de acuerdo a las instrucciones del repositorio del curso en la URL GITHUB: https://github.com/ICESI/so-microservices-python.git

![postman_porcentaje_cpu](https://user-images.githubusercontent.com/35766585/40572037-9ee31bf0-6068-11e8-8bdf-78aaa6471328.png)

![postman_memoria_disponible](https://user-images.githubusercontent.com/35766585/40571862-1e86b55e-6066-11e8-9ebb-189936d2b63c.png)

![postman_espacio_libre_disco](https://user-images.githubusercontent.com/35766585/40571765-5bfc7d6c-6064-11e8-814b-b3fafe89e234.png)


**4.**
# IMPLEMENTACIÓN PRUEBAS UNITARIAS PARA LOS SERVICIOS EMPLEANDO FIXTURES Y MOCKS
Para la implementación de las PRUEBAS UNITARIAS de los servicios se empleará Fixtures y Mocks, realizando los siguientes pasos:

1. Instalar los componentes necesarios para realizar estas pruebas:                                                                        
$ pip install pytest                                                                                                                      
$ pip install mock                                                                                                                        
$ pip install pytest_mock

2. Se crea una carpeta ccon el nombre test donde se encontrará:
- El archivo __init__.py que se encarga de inicializar paquetes de Python.
 
- El archivo test_stats.py que contiene las pruebas unitarias para el servicio web con los métodos de prueba de cpu, espacio en disco y la memoria RAM  disponible, con la intención de verificar si en tiempo de ejecución el programa esta funcionando de manera correcta. Este archivo siempre deberá empezar por test ya que el comando de pytest lo buscará identificando esta palabra para proceder a ejecutarlo.

![test_stats py](https://user-images.githubusercontent.com/35766585/40526568-0dc51f9e-5fad-11e8-8414-0c37f7220ade.png)

3. Finalmente se ejecuta el archivo de pruebas mediante el comando:                                                                      
$ pytest -v

![pytest-v](https://user-images.githubusercontent.com/35766585/40571907-dd2fff60-6066-11e8-94cb-13754b8320c3.png)

**5.** 
# SERVICIO DE INTEGRACIÓN CONTINUA
Se implementará un servicio de integración continua que hace uso de las pruebas unitarias desarrolladas para validar los commits a un servicio en linea usando TOX.

1. Instalar tox mediante el siguiente comando:                                                                                            
$ pip install tox

2. Se crea el archivo tox.ini el cual contendra las especificaciones de: librería para pruebas, lenguaje base (Python3, en este caso) y dependencias que se van a usar.                                                                                                          
NOTA: El código fuente se obtuvo del repositorio del curso en la URL GITHUB: https://github.com/ICESI-Training/so-microservice.git

![toxini](https://user-images.githubusercontent.com/35766585/40526669-a58393ba-5fad-11e8-8450-4a2f815cdc3d.png)

3. Ejecutar el archivo mediante el comando:                                                                                              
$ tox -e pytest

![pytest](https://user-images.githubusercontent.com/35766585/40527018-ab878742-5faf-11e8-8028-f802ee92c3f5.png)


4. Ejecutar las pruebas de commits, utilizando las pruebas de travis-ci.org. Para esto:
- Se crea el archivo .travis.yml donde se guardara la configuración basica para correr las pruebas especificando el lenguaje de programación y la versión empleada entre otros parámetros.                                                                                
NOTA: El código fuente se obtuvo del repositorio del curso en la URL GITHUB: https://github.com/ICESI-Training/so-microservice.git

![travis](https://user-images.githubusercontent.com/35766585/40526843-bf472158-5fae-11e8-93a2-abf223787fb1.png)

- Para configurar Travis con nuestro repositorio, se accede a la página https://travis-ci.org/. Se realiza el respectivo inicio de sesión con el usuario y la contraseña de GITHUB. Se espera la sincronización con el repositorio y una vez se realice se generará la activación del repositorio en el que estamos trabajando so-exam3.Con lo anterior, Travis queda autorizado para realizar las validaciones cada vez que se realice un pull request o commit a este repositorio. 

![repositoriostravis1](https://user-images.githubusercontent.com/35766585/40571566-8662a1ca-6060-11e8-9361-56f180a4c81a.png)

![repositoriostravis](https://user-images.githubusercontent.com/35766585/40571567-9a87a9c0-6060-11e8-9e74-3831d11dea4f.png)

![travisvalidacion](https://user-images.githubusercontent.com/35766585/40526960-636be50c-5faf-11e8-8bad-ac526a52f14d.png)

![commits](https://user-images.githubusercontent.com/35766585/40526996-91670892-5faf-11e8-942a-006afb1b7da5.png)


**6**

URL GITHUB => https://github.com/marisolcitag/so-exam3.git


# BIBLIOGRAFIA

- REPOSITORIO GITHUB                                                                                                                      
  URL: https://github.com/ICESI                                                                                                             
  URL: https://github.com/ICESI-Training




