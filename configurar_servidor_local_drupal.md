# Cómo configurar un servidor local en Drupal

- Instalar XAMPP
- Iniciar control XAMPP y activar los servicios de Apache y MySQL.
- Configurar desde el control de XAMPP el my.ini => MySQL/config/my.ini y ampliar todos los límites:
  - key_buffer = 16M
  - max_allowed_packet = 4096M
  - sort_buffer_size = 10M
  - net_buffer_length = 10M
  - read_buffer_size = 10M
  - read_rnd_buffer_size = 10M
  - myisam_sort_buffer_size = 8M
  - innodb_log_file_size = 500M
  - innodb_log_buffer_size = 800M
  - innodb_flush_log_at_trx_commit = 1
  - innodb_lock_wait_timeout = 5000
- Configurar desde el control el php.ini => apache/config/php.ini
  - upload_max_filesize=200M (por defecto el valor está en 2: Poner un valor mayor al tamaño del archivo que se desea importar).
- En Xampp/phpMyAdmin/libraries/config.default.php poner $cfg['ExecTimeLimit'] = 0;
- Importar base de datos: 
  - Crear base de datos en phpMyAdmin: nombre y codificación (cuidado con la codificación que puede producir muchos errores).
  - Importar base de datos: 
    - Archivo a importar: 
      - Se selecciona el archivo.
      - Se marca la codificación.
    - Importación parcial: desmarcar checkbox.
    - Otras opciones: desmarcar checkbox.
    - Opciones específicas del formato: desmarcar checkbox.
 - Copiar la carpeta de drupal en la carpeta htdocs:
 - Nombre-carpeta/sites/default/settings.php
   - base-url: 'http://localhost' (nunca con el valor vacío, porque aparece el error: Undefined Offset 1 in bootstrap.inc y no muestra el contenido de las páginas de contenido).
   - $databases = array (
        'default' => 
        array (
          'default' => 
          array (
            'database' => 'nombre-database',
            'username' => 'root',
            'password' => '',
            'host' => 'localhost',
            'port' => '',
            'driver' => 'mysql',
            'prefix' => '',
          ),
        ),
      );  
      
- Windows/System32/drivers/etc/hosts: 127.0.0.1  nombre-del-sitio
- xampp/apache/conf/extra/httpd-vhosts.conf:
     <VirtualHost *:80>
          ServerAdmin webmaster@dummy-host2.example.com
          DocumentRoot "C:/xampp/htdocs/nombre-carpeta-en-htdocs"
          ServerName nombre-del-sitio
          ErrorLog "logs/dummy-host2.example.com-error.log"
          CustomLog "logs/dummy-host2.example.com-access.log" common
      </VirtualHost>

**Comprobar el nombre-del-sitio en la url del navegador (debería estar ya funcionando).**

## Instalar la plantilla bizreview para Drupal 8.

- Instalar todo el contenido de la plantilla en la carpeta de la web dentro de htdocs en el xampp.
- Sustituir la plantilla por la verisón 1.1 y volver a importar la base de datos. Sustotuir todos los archivos del core de la última versión de drupal compatible con esa base de datos (drupal 8.7.4): carpetas core, profiles y vendor y todos los archivos que están en el raíz de la carpeta.
- Seguir el instalador de drupal.

**Comprobar el nombre-del-sitio en la url del navegador (debería estar ya funcionando).**

## Actualizar módulos en drupal

Descargar actualizaciones e instalarlas.

## Configurar el idioma

Extend/Multilingual install los módulos Configuration translation, content translation, Language, Interface Tranlation

Install new modules: language icons (para poner las banderas en el menú de idiomas)
Enable newly added modules.


