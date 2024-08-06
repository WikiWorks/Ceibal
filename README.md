# Canasta
A full-featured MediaWiki stack for easy deployment of enterprise-ready MediaWiki on production environments.

This repo is for the MediaWiki application Docker image included in the Canasta stack. For complete documentation on the overall Canasta tech stack, including installation instructions, please visit https://github.com/CanastaWiki/Canasta-Documentation.

## Instrucciones de iniciar
Aquí hay un conjunto de llamadas de muestra (ejecutadas en orden) para extraer e iniciar Canasta:
```
sudo docker pull ninjaneered/ceibal
```

```
sudo docker run
-e MW_ALLOW_UNMOUNTED_VOLUME=1
-e DOMAIN=domain.com
-e wgDBtype="mysql"
-e wgDBserver=localhost
-e wgDBname=canastatest
-e wgDBuser=canastauser
-e wgDBpassword=password
-v ../extensions:/var/www/mediawiki/w/user-extensions
-v ../skins:/var/www/mediawiki/w/user-skins
-v ./images:/mediawiki/images
-v ../cert.crt:/etc/caddy/cert.crt
-v ../private.key:/etc/caddy/private.key
-v ./config:/mediawiki/config
ceibal
```

Y aquí hay una explicación de todas las opciones enumeradas.

Primero, las variables de entorno, configuradas con el indicador "-e":
- `MW_ALLOW_UNMOUNTED_VOLUME` - si se configura en 1, ignora los problemas con los volúmenes desmontados, en lugar de cancelar la instalación (necesario, por ahora)
- `DOMAIN` - configura el dominio de la URL de esta wiki
- `wgDBtype`, `wgDBserver`, `wgDBname`, `wgDBuser`, `wgDBpassword` - estas son variables estándar de MediaWiki, que juntas se utilizan para conectarse a la base de datos que contiene los datos de la wiki

Luego, los volúmenes (directorios persistentes) definidos de la imagen de Docker, configurados con el indicador "-v":
- `extensions` - el directorio utilizado para almacenar todas las extensiones personalizadas (no de Canasta) que se han instalado
- `skin` - el directorio utilizado para almacenar todas las "skins" (apariencias) personalizadas (no de Canasta) que se han instalado
- `images` - el directorio images/ estándar de MediaWiki, utilizado para almacenar imágenes y otros archivos cargados
- `cert.crt` - el archivo que contiene el certificado para el cifrado SSL
- `private.key` -  el archivo que contiene la clave privada para el cifrado SSL
- `config` - el directorio que contiene los archivos de configuración para esta imagen de Canasta

Finalmente, el nombre de la imagen de Docker que se va a instalar:
- `ceibal`
