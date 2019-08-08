# fb-sleep-stats: Uso de Facebook para rastrear el sueño de tus contactos

Una pequeña herramienta para mostrar las posibles implicaciones de privacidad que tienen las redes sociales modernas. Al rastrear el estado en línea / fuera de línea de las personas en Facebook, es posible obtener una imagen precisa de su patrón de sueño.

Lea la publicación del blog: https://medium.com/@sqrendk/how-you-can-use-facebook-to-track-your-friends-sleeping-habits-505ace7fffb6

![Facebook Sleep Screenshot](https://cloud.githubusercontent.com/assets/209966/13382859/b7b31aa4-de7e-11e5-8fca-35d68fe2f02f.png)


## Instalación

**Prerequisitos**
 - Git ([how to install](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git))
 - Node.js ([how to install](https://docs.npmjs.com/getting-started/installing-node))

**Clonar repositorio**
```
git clone https://github.com/sqren/fb-sleep-stats.git
```

**Configuración**

Abra la carpeta del código fuente:
```
cd fb-sleep-stats
```

Copie el archivo de configuración predeterminado:
```
cp config/default.json config/development.json
```

Actualice los siguientes valores en `config/development.json`
 - "c_user": [su identificación de usuario numérica de Facebook] (http://findmyfbid.com/)
 - "xs": [valor xs de la cookie de Facebook] (https://gist.github.com/sqren/0e4563f258c9e85e4ae1)
 - "appId": [Id. de la aplicación de Facebook] (https://gist.github.com/sqren/1ac0f5d316fcbd46d8c1)

* ¡Asegúrate de que no haya pestañas o espacios finales en el archivo de configuración! *

** Instalar dependencias **
```
npm install
```

** Construir dependencias del navegador **
```
npm run webpack
```

## Comenzando

Debe tener dos procesos ejecutándose simultáneamente: el raspador y el servidor web. Por lo tanto, debe ejecutar los siguientes dos comandos en ventanas / pestañas separadas.

** Comienza a raspar **

* Esto se ejecutará continuamente, sondeando Facebook cada 10 minutos. Manténgalo en funcionamiento durante el tiempo que desee seguir el sueño. *
```
npm run scrape
```

** Iniciar servidor **
```
npm start
```

Vea el resultado en el navegador: [http: // localhost: 3000] (http: // localhost: 3000)

#Solución de problemas

** Recibo un error al ejecutar "npm run webpack" **

Intente reinstalar los módulos de nodo:
```
rm -rf node_modules
npm install
npm run webpack
```

** No se muestran usuarios **
 - Si tiene un bloqueador de anuncios, debe deshabilitarlo para el sitio.
 - Necesita ejecutar `npm run scrape` y mantenerlo en funcionamiento. Cuando lo detenga, dejará de rastrear.

** Los cambios en development.json no se recogen **
 - Tienes que ejecutar `npm run webpack`

** ¿Cómo actualizo a la última versión? **

Después de extraer la última versión, debe reconstruir las dependencias:
```
git pull
rm -rf node_modules
npm install
npm run webpack
```

** ReferenceError: la promesa no está definida **

Actualice Node.js a la última versión estable de la rama en la que se encuentra (v5.7.1, v4.3.2 o v0.12.11). Después de eso reconstruir dependencias:
```
rm -rf node_modules
npm install
npm run webpack
```

** No se puede analizar el archivo de configuración **

Su archivo de configuración contiene un formato json no válido. Encuentre los errores utilizando una herramienta como [http://jsonlint.com/font>(http://jsonlint.com/)

** ¿Dónde se almacenan los datos? **

Puede encontrar los datos en formato JSON aquí: `src/server/services/db.json`.

**Otros asuntos**

Si encuentra un error o tiene un problema, vaya a [Problemas] (https://github.com/sqren/fb-sleep-stats/issues?utf8=%E2%9C%93&q=is%3Aissue+) y use la funcionalidad de búsqueda, en caso de que alguien más ya haya hecho la pregunta. Si no puede encontrar nada útil, puede crear un [nuevo número] (https://github.com/sqren/fb-sleep-stats/issues/new)


# Descargo de responsabilidad
Facebook me contactó y me informó que está en contra de sus términos acceder a su sitio web por medios automáticos. Además, no puedo instar a nadie a que lo haga. Por lo tanto: le insto a que use este proyecto solo con fines educativos y no lo use para acceder a Facebook.
