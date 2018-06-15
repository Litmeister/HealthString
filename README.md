# life
#ficha medica


Paso 1: Instalar las herramientas CLI
Hay algunas herramientas de CLI útiles para desarrolladores de Composer. El más importante es composer-cli, que contiene todas las operaciones esenciales, entonces lo instalaremos primero. A continuación, también recogeremos generator-hyperledger-composer, composer-rest-servery Yeomanmás el generator-hyperledger-composer. Esos 3 últimos no son partes centrales del entorno de desarrollo, pero serán útiles si sigue los tutoriales o desarrolla aplicaciones que interactúan con su red empresarial, así que las instalaremos ahora.

Tenga en cuenta que no debe usar suni sudopara los siguientes comandos npm.

Herramientas CLI esenciales:

Copiar
npm install -g composer-cli
Utilidad para ejecutar un servidor REST en su máquina para exponer sus redes comerciales como API RESTful:

Copiar
npm install -g composer-rest-server
Utilidad útil para generar activos de aplicaciones:

Copiar
npm install -g generator-hyperledger-composer
Yeoman es una herramienta para generar aplicaciones, que utiliza generator-hyperledger-composer:

Copiar
npm install -g yo
Paso 2: instala el patio de recreo
Si ya has probado Composer en línea, habrás visto la aplicación del navegador "Playground". También puede ejecutarlo localmente en su máquina de desarrollo, proporcionándole una interfaz de usuario para ver y demostrar sus redes comerciales.

Aplicación de navegador para la edición y prueba simples Redes comerciales:

Copiar
npm install -g composer-playground
Paso 3: configura tu IDE
Si bien la aplicación de navegador se puede utilizar para trabajar en su código de red comercial, la mayoría de los usuarios preferirán trabajar en un IDE. Nuestro favorito es VSCode, porque una extensión Composer está disponible.

Instale VSCode desde esta URL: https://code.visualstudio.com/download

Abra VSCode, vaya a Extensions, luego busque e instale la Hyperledger Composerextensión desde Marketplace.

Paso 4: instala la tela Hyperledger
Este paso le proporciona un tiempo de ejecución de Hyperledger Fabric local para implementar sus redes comerciales.

En un directorio de su elección (asumiremos ~/fabric-dev-servers), obtenga el .tar.gzarchivo que contiene las herramientas para instalar Hyperledger Fabric:

Copiar
mkdir ~/fabric-dev-servers && cd ~/fabric-dev-servers

curl -O https://raw.githubusercontent.com/hyperledger/composer-tools/master/packages/fabric-dev-servers/fabric-dev-servers.tar.gz
tar -xvf fabric-dev-servers.tar.gz
A ziptambién está disponible si lo prefiere: simplemente reemplace el .tar.gzarchivo con fabric-dev-servers.zipel tar -xvfcomando con un unzipcomando en el fragmento anterior.

Utilice los scripts que acaba de descargar y extraer para descargar un tiempo de ejecución de Hyperledger Fabric local:

Copiar
cd ~/fabric-dev-servers
./downloadFabric.sh
Felicitaciones, ahora ha instalado todo lo necesario para el entorno de desarrollador típico. Siga leyendo para conocer algunas de las cosas más comunes que hará con este entorno para desarrollar y probar sus redes comerciales de Blockchain.

Controlando su entorno de desarrollo
Inicio y detención de Hyperledger Fabric
Usted controla su tiempo de ejecución usando un conjunto de scripts que encontrará ~/fabric-dev-serverssi siguió los valores predeterminados sugeridos.

La primera vez que inicie un nuevo tiempo de ejecución, deberá ejecutar el script de inicio y luego generar una tarjeta PeerAdmin:

Copiar
    cd ~/fabric-dev-servers
    ./startFabric.sh
    ./createPeerAdminCard.sh
Puede iniciar y detener su tiempo de ejecución con ~/fabric-dev-servers/stopFabric.sh, y comenzar de nuevo con ~/fabric-dev-servers/startFabric.sh.

Al final de tu sesión de desarrollo, ejecutas ~/fabric-dev-servers/stopFabric.shy luego ~/fabric-dev-servers/teardownFabric.sh. Tenga en cuenta que si ha ejecutado el script de desmontaje, la próxima vez que inicie el tiempo de ejecución, tendrá que crear una nueva tarjeta PeerAdmin tal como lo hizo en la primera puesta en marcha.

El tiempo de ejecución local está destinado a iniciarse, detenerse y derribarse con frecuencia, para uso de desarrollo. Si está buscando un tiempo de ejecución con un estado más persistente, querrá ejecutar uno fuera del entorno de desarrollo y desplegar redes comerciales en él. Ejemplos de esto incluyen ejecutarlo a través de Kubernetes, o en una plataforma administrada como IBM Cloud.

Inicie la aplicación web ("Playground")
Para iniciar la aplicación web, ejecuta:

Copiar
    composer-playground
Normalmente abrirá su navegador automáticamente, en la siguiente dirección: http: // localhost: 8080 / login

Debería ver la PeerAdmin@hlfv1tarjeta que creó con el createPeerAdminCardscript en su pantalla "My Business Networks" en la aplicación web: si no ve esto, es posible que no haya iniciado correctamente su runtime.

Felicidades, tienes todos los componentes en ejecución, y también sabes cómo pararlos y derribarlos cuando hayas terminado con tu sesión de desarrollo.