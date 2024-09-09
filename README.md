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
-e wgDBtype="mysql"
-e wgDBserver=localhost
-e wgDBname=canastatest
-e wgDBuser=canastauser
-e wgDBpassword=password
-v ./mediawiki:/mediawiki
ceibal
```

Y aquí hay una explicación de todas las opciones enumeradas.

Primero, las variables de entorno, configuradas con el indicador "-e":
- `wgDBtype`, `wgDBserver`, `wgDBname`, `wgDBuser`, `wgDBpassword` - estas son variables estándar de MediaWiki, que juntas se utilizan para conectarse a la base de datos que contiene los datos de la wiki

Luego, los volúmenes (directorios persistentes) definidos de la imagen de Docker, configurados con el indicador "-v":
- `mediawiki` - el directorio estándar de MediaWiki, utilizado para almacenar LocalSettings.php, imágenes, configuraciones y otros archivos cargados
- `cert.crt` - el archivo que contiene el certificado para el cifrado SSL
- `private.key` -  el archivo que contiene la clave privada para el cifrado SSL

Finalmente, el nombre de la imagen de Docker que se va a instalar:
- `ceibal`
