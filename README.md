# pushNotificacions
Proyecto básico de ionic con notificaciones


1.- Crear el proyecto:

`$ ionic start pushNotificacions sidemenu`

`$ cd pushNotificacions/`

`$ ionic add ionic-platform-web-client`

2.- Agregar las plataformas ios y android:

`$ ionic add platform ios android`

De manera opcional actualizar cordova:

`$ cordova platform update ios@4.0.0`

2.- Crear un proyecto dentro de https://console.developers.google.com

3.- Ejecutar el comando:

`$ ionic plugin add phonegap-plugin-push --variable SENDER_ID="GCM_PROJECT_NUMBER"`

en donde *GCM_PROJECT_NUMBER* es el numero de proyecto creado.

4.- Ingresar o crear una cuenta en Ionic.io dashboard: https://apps.ionic.io/login?next=/apps

5.- Con los datos de la cuenta ejecutar el comando:

`$ ionic io init`

ingresar el correo electronico y password solicitados.

6.- Ahora configurar las notificaicones en modo desarrollo:

`$ ionic config set dev_push true`


## Referencias:

https://devdactic.com/ionic-push-notifications-guide/
https://cordova.apache.org/announcements/2015/12/08/cordova-ios-4.0.0.html
