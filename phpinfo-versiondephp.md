Sí, crear un archivo PHP que llame a phpinfo() puede ser mejor que verificar la página de información de PHP en http://localhost/info.php por las siguientes razones:

Mayor control sobre la salida: Al crear su propio archivo PHP, puede controlar exactamente qué información se muestra en la página de información de PHP. Por ejemplo, puede elegir mostrar solo cierta información, como la versión de PHP o las extensiones cargadas.
Mayor flexibilidad: Puede crear su propio archivo PHP en cualquier ubicación de su servidor web, lo que le brinda más flexibilidad para organizar y estructurar su código.
Mayor seguridad: Si crea su propio archivo PHP, puede protegerlo con una contraseña o restringir el acceso a ciertos usuarios o grupos. Esto puede ser útil si desea evitar que usuarios no autorizados accedan a información confidencial sobre su servidor web.
Para crear un archivo PHP que llame a phpinfo(), siga estos pasos:

Cree un nuevo archivo PHP en su servidor web. Puede llamarlo como quiera, pero es común usar el nombre phpinfo.php.
Abra el archivo PHP en un editor de texto y agregue el siguiente código:

```
<?php
phpinfo();
?>
```
Guarde el archivo PHP.
Abra un navegador web y vaya a la siguiente URL: http://localhost/phpinfo.php.
Ahora debería ver una página que muestra información sobre la configuración de PHP.

Tenga en cuenta que si desea proteger el archivo phpinfo.php con una contraseña, puede hacerlo agregando el siguiente código al principio del archivo:

```
<?php
if (!isset($_SERVER['PHP_AUTH_USER']) || $_SERVER['PHP_AUTH_USER'] != 'username' || $_SERVER['PHP_AUTH_PW'] != 'password') {
    header('WWW-Authenticate: Basic realm="My Realm"');
    header('HTTP/1.0 401 Unauthorized');
    echo 'Access denied';
    exit;
}
?>
```
Reemplace username y password con el nombre de usuario y la contraseña que desea utilizar.

También puede restringir el acceso al archivo phpinfo.php a ciertas direcciones IP o rangos de direcciones IP agregando el siguiente código al principio del archivo:

```
<?php
$allowed_ips = array('127.0.0.1', '192.168.1.0/24');
if (!in_array($_SERVER['REMOTE_ADDR'], $allowed_ips)) {
    header('HTTP/1.0 403 Forbidden');
    echo 'Access denied';
    exit;
}

?>
```
Reemplace 127.0.0.1 y 192.168.1.0/24 con las direcciones IP o rangos de direcciones IP a los que desea permitir el acceso.
