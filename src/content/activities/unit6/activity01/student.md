+ ¿Qué ocurrió en la terminal cuando ejecutaste npm install? ¿Cuál crees que es su propósito?
  + creo que intala todo el programa des servidor dentot de la carpeta de archivos de programa
```
added 121 packages, and audited 122 packages in 2s

16 packages are looking for funding
  run `npm fund` for details

5 vulnerabilities (3 low, 2 high)

To address all issues, run:
  npm audit fix

Run `npm audit` for details.
npm notice
npm notice New major version of npm available! 10.2.0 -> 11.3.0
npm notice Changelog: https://github.com/npm/cli/releases/tag/v11.3.0
npm notice Run npm install -g npm@11.3.0 to update!
npm notice
  ```

+ ¿Qué mensaje específico apareció en la terminal después de ejecutar npm start? ¿Qué indica este mensaje?
  + que ha arrancado el servidor
```
> nodejs-test-1@1.0.0 start
> node server.js
```
+ Describe lo que ves inicialmente en page1 y page2 en tu navegador.
  + inicialmente en el uno aparecian las dos ezferas condectadas y creoqen el 2 solo una pero desincronizada y a medida que movia una pagina se actualizaba la posicion de la otra
+ ¿Qué mensajes aparecieron en la terminal del servidor cuando abriste page1 y page2?
```
A user connected
A user connected
  ```


+ Describe qué sucede en ambas páginas del navegador cuando mueves una de las ventanas. ¿Cambia algo visualmente? ¿Qué mensajes aparecen (si los hay) en la consola del navegador (usualmente accesible con F12 -> Pestaña Consola) y en la terminal del servidor?
  + se actualiza la posicion de la otra, y se ve su conexion
  + ela page 1 `jLzaE4uyMSf7eHiMAAAL` y en la dos `GSYEcny0t8kbd4FcAAAJ` y  a medida que se mueve la otra actualiza esto `{x: 91, y: 114, width: 400, height: 944}`
  
