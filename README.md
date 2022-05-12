# Ejercicios Prácticos de la Unidad UF2217 (XML)

En primer lugar, se ha utilizado esta [página](https://www.mclibre.org/consultar/xml/) para acceder a recursos sobre XML, incluyendo la guía de instalación del [XML Copy Editor](https://www.mclibre.org/consultar/xml/otros/xmlcopyeditor.html), herramienta que se utilizará durante estos ejercicios para manipular y editar el código en XML y que se ha instalado en el equipo con ese objetivo.

Este editor permite:

* Crear nuevos archivos xml.
* Configurar dichos archivos y su comportamiento.
* Comprobar que un documento está bien formado (F2).
* Comprobar que un documento es válido (F5).
* Enlazar hojas de estilo CSS (algo que no permite, por ejemplo, markdown).
* Evaluar expresiones XPath.
* Aplicar transformaciones XSLT.

## Ejercicio: Documentos bien formados.

El objetivo es observar una serie de documentos xml y encontrar los errores, corregirlos y comprobar con el editor si está todo correcto. A continuación se muestran los archivos proporcionados y sus correcciones:

1. *Deportistas:*

   **Antes:**

   ```
   <?xml version="1.0" encoding="UTF-8"?>
   <deportistas>
     <deportista>
       <deporte Atletismo />
       <nombre>Jesse Owens</nombre>
     <deportista>
       <deporte Natación />
       <nombre>Mark Spitz</nombre>
     </deportista>
   </deportistas>
   ```

   Aquí observamos que la primera etiqueta deportista no está bien cerrada y que en las dos etiquetas deporte hay elementos sueltos.

   **Después:**

  ```
   <?xml version="1.0" encoding="UTF-8"?>
   <deportistas>
     <deportista>
       <deporte> Atletismo </deporte>
       <nombre>Jesse Owens</nombre>
     </deportista>
     <deportista>
       <deporte> Natación </deporte>
       <nombre>Mark Spitz</nombre>
     </deportista>
   </deportistas>
  ```

2. *Películas:*

   **Antes:**

   ```
   <?xml version="1.0" encoding="UTF-8"?>
   <pelicula>
     <titulo>Con faldas y a lo loco</titulo>
     <director>Billy Wilder</director>
   </pelicula>
   <pelicula>
     <director>Leo McCarey</director>
     <titulo>Sopa de ganso</titulo>
   </pelicula>
   <autor />barto</autor>
   ```

   Aquí faltaría por un lado el elemento raíz del documento, y por otro estaría mal escrita la etiqueta autor.

   **Después:**

  ```
   <?xml version="1.0" encoding="UTF-8"?>
   <peliculas>
     <pelicula>
       <titulo>Con faldas y a lo loco</titulo>
       <director>Billy Wilder</director>
     </pelicula>
     <pelicula>
       <director>Leo McCarey</director>
       <titulo>Sopa de ganso</titulo>
     </pelicula>
     <autor>Barto</autor>
   </peliculas>
  ```

3. *Texto:*

   **Antes:**

   ```
   <?xml version="1.0" encoding="UTF-8"?>
   <texto>
     <Titulo>XML explicado a los niños</titulo>
     <párrafo>El <abreviatura>XML</abreviatura>define cómo crear
     lenguajes de marcas.</párrafo>
     <párrafo>Las marcas se añaden a un documento de texto
     para añadir información.</párrafo>
     <http://>www.example.org</http://>
   </texto>
   ```

   Por una parte la etiqueta de título no coincide en apertura y cierre, y por otra hay caracteres no permitidos en la de http. También se pueden eliminar las tildes de las etiquetas que las tienen.

   **Después:**

  ```
   <?xml version="1.0" encoding="UTF-8"?>
   <texto>
     <titulo>XML explicado a los niños</titulo>
     <parrafo>El <abreviatura>XML</abreviatura>define cómo crear
     lenguajes de marcas.</parrafo>
     <parrafo>Las marcas se añaden a un documento de texto
     para añadir información.</parrafo>
     <http>www.example.org</http>
   </texto>
   ```

4. *Información geográfica:*

   **Antes:**

   ```
   <?xml version="1.0" encoding="UTF-8"?>
   <geografia mundial>
     <pais>
       <pais>España</pais>
       <continente>Europa</continente>
       <capital></capital nombre="Madrid">
     </pais>
   </geografia mundial>
   ```

   La primera etiqueta debería ser una sola cadena de caracteres, sin espacios, y la de capital debe tener su valor entre ellas, no al final.

   **Después:**

  ```
   <?xml version="1.0" encoding="UTF-8"?>
   <geografia-mundial>
     <pais>
       <pais>España</pais>
       <continente>Europa</continente>
       <capital>Madrid</capital>
     </pais>
   </geografia-mundial>
   ```

5. *Programas:*

   **Antes:**

   ```
   <?xml version="1.0" encoding="UTF-8"?>
   <programas>
     <programa nombre="Firefox" licencia="GPL" licencia="MPL" />
     <programa nombre="LibreOffice" licencia="LGPL" />
     <programa nombre="Inkscape" licencia=GPL />
   </programas>
   ```

   En primer lugar el primer programa tiene un atributo repetido, y al tercero le faltan las comillas del valor.

   **Después:**

  ```
   <?xml version="1.0" encoding="UTF-8"?>
   <programas>
     <programa nombre="Firefox" licencia="GPL MPL" />
     <programa nombre="LibreOffice" licencia="LGPL" />
     <programa nombre="Inkscape" licencia="GPL" />
   </programas>
   ```

6. *Mundiales de fútbol:*

   **Antes:**

   ```
   <?xml version="1.0" encoding="UTF-8"?>
   <mundiales-de-futbol>
     <mundial>
       <pais="España" />
       <1982 />
     </mundial>
   </mundiales-de-futbol>
   ```

   En este caso los errores se encentran en las etiquetas, ya que algunas están incompletas o directamente no aparecen.

   **Después:**

  ```
   <?xml version="1.0" encoding="UTF-8"?>
   <mundiales-de-futbol>
     <mundial>
       <pais>España</pais>
       <año>1982</año>
     </mundial>
   </mundiales-de-futbol>
  ```

7. *Medios de transporte:*

   **Antes:**

   ```
   <?xml version="1.0" encoding="UTF-8"?>
   <mediosDeTransporte>
     <bicicleta velocidad="v<100km/h" />
     <patinete velocidad maxima="50 km/h"
   </mediosDeTransporte>
   ```

   Dentro de mediosDeTransporte, la etiqueta superior tiene un caracter que solo se usa como inicio de etiqueta, y la inferior está mal cerrada y su atributo no debe tener espacios en blanco.

   **Después:**

  ```
   <?xml version="1.0" encoding="UTF-8"?>
   <mediosDeTransporte>
     <bicicleta velocidad="v&lt;100km/h" />
     <patinete velocidad-maxima="50 km/h" />
   </mediosDeTransporte>
  ```

​		En xml, menor que (<) se escribe como "& lt ;" (junto), si se quisiera un mayor que (>) sería "& gt ;".

Noelia Figueiras Fernández
