# pushNotificacions
Proyecto básico de ionic con notificaciones


1.- Crear el proyecto:

`$ ionic start pushNotificacions sidemenu`

`$ cd pushNotificacions/`

`$ ionic add ionic-platform-web-client`

2.- Agregar las plataformas ios y android:

`$ ionic add platform ios`

`$ ionic add platform android`

De manera opcional actualizar cordova:

`$ cordova platform update ios@4.0.0`

3.- Crear un proyecto dentro de https://console.developers.google.com

4.- Ejecutar el comando:

`$ ionic plugin add phonegap-plugin-push --variable SENDER_ID="GCM_PROJECT_NUMBER"`

en donde *GCM_PROJECT_NUMBER* es el numero de proyecto creado.

5.- Ingresar o crear una cuenta en Ionic.io dashboard: https://apps.ionic.io/login?next=/apps

6.- Con los datos de la cuenta ejecutar el comando:

`$ ionic io init`

ingresar el correo electronico y password solicitados.

7.- Ahora configurar las notificaicones en modo desarrollo:

`$ ionic config set dev_push true`

8.- Abrir el **app.js** y agregar:

``` 
	  var push = new Ionic.Push({
	      "debug": true
	    });

	  push.register(function(token) {
	      console.log("My Device token:",token.token);
	      push.saveToken(token);  // persist the token in the Ionic Platform
	    });
```

9.- Crear un **security profile** y crear un  **API key** dentro de  **Ionic.io dashboard** 
![profile](https://devdactic.com/wp-content/uploads/2016/04/ionic-security-profile.png)
![api key](https://devdactic.com/wp-content/uploads/2016/04/ionic-api-token.png)

En este momento esta todo listo para poder usar las notificaciones en modo Dev.

10.- Iniciar el proyecto:

`$ ionic serve`

11.- Se puede utilizar [POSTMAN](https://chrome.google.com/webstore/detail/postman/fhbjgbiflinjbdggehcddcbncdddomop) para conectar con el servidor y mandar la notificación:

```
curl -X POST -H "Authorization: Bearer API_TOKEN" -H "Content-Type: application/json" -d '{
    "tokens": ["DEV_DEVICE_TOKEN"],
    "profile": "PROFILE_NAME",
    "notification": {
        "message": "This is my demo push!"
    }
}' "https://api.ionic.io/push/notifications"
```
![postman](https://devdactic.com/wp-content/uploads/2016/04/postman-push-body-1024x813.png)

***

# Configuración para Android

12.- En el proyecto creado dentro de Google developer Console hay que habilitar el servicio **GCM**

13.- Obtener el API key
[Los pasos se encuentran aqui](http://docs.ionic.io/docs/android-push-profiles)

14.- Conectar con Ionic.io:

Ir al Ionic.io dashboard y navegar hasta **Settings -> Certificates.** . Editar el perfil creado y en la pestaña de Android ingresar el API key generado en **Google Cloud Messaging.**

```
ionic platform add android
ionic plugin rm phonegap-plugin-push
ionic plugin add phonegap-plugin-push --variable SENDER_ID="GCM_PROJECT_NUMBER"
ionic config set gcm_key <your-gcm-project-number>
```

# Enviar notificaciones reales:

15.- `ionic config set dev_push false`

16.- `ionic buil android`

## Referencias:
http://docs.ionic.io/docs/push-sending-push

https://devdactic.com/ionic-push-notifications-guide/

https://cordova.apache.org/announcements/2015/12/08/cordova-ios-4.0.0.html

https://thinkster.io/ionic-push-notifications-tutorial

https://www.airpair.com/javascript/posts/push-it-real-good-with-ionic

https://www.airpair.com/ionic-framework/posts/push-notifications-using-ionic-framework

https://onesignal.com/
