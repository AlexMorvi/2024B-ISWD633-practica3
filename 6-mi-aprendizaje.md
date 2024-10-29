# COMPLETAR  
Durante esta práctica, consolidé mis conocimientos sobre Docker, profundizando en la gestión de volúmenes, redes y configuraciones. Aprendí a trabajar con volúmenes anónimos y nombrados, persistiendo datos y configuraciones de aplicaciones como Drupal y WordPress conectadas a bases de datos en contenedores separados. Además, comprendí cómo los volúmenes de tipo host permiten el acceso directo a archivos del sistema del host, aunque requieren permisos específicos para funcionar. En el proceso, enfrenté y resolví problemas relacionados con la conexión entre contenedores, permisos de escritura y conflictos de puertos, aplicando ajustes en redes y permisos.
 
Para Drupal tuve que crear directorios y darles permisos adecuados, se usó:
docker exec -it server-drupal bash

mkdir -p /var/www/html/sites/default/files/translations

chown -R www-data:www-data /var/www/html/sites/default/files/translations

exit

docker restart server-drupal
