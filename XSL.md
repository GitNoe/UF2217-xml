# Ejercicios Prácticos de la Unidad UF2217 (XSL)

En este ejercicio se han implementado los archivos de formato XSL que se referencian en los archivos XML para que estos tengan una estructura y organización determinadas, es decir, que se establecen como hojas de estilos para dar a XML un layout concreto, el que el desarrollador decida.

## Ejercicio: Archivos XSL unidos a XML.

El objetivo es, en un archivo XML de varios miles de líneas, implementar varios estilos distintos mediante XSL. Para ello se ha descargado el archivo "SAPsimple_es.xml" y se han hecho 5 copias ordenadas por número. A su vez se han creado 5 archivos XSL, también ordenados por número, para que cada uno se corresponda con un XML.

En cada XSL se ha hecho una distribución distinta de los datos del archivo XML, de la siguiente manera:

**Versión 01:**

```
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="text"/>
  <xsl:template match="/">
    <xsl:for-each select="raíz/registro">
      <xsl:value-of select="identificador"/>,<xsl:value-of select="título"/>,<xsl:value-of select="fecha/año"/><xsl:text>&#xA;</xsl:text>
    </xsl:for-each>
  </xsl:template>
</xsl:stylesheet>
```

En el archivo *XML* correspondiente, la *segunda línea* es la referencia a la hoja de estilo:

```
<?xml-stylesheet type="text/xsl" href="01.xsl"?>
```



**Versión 02:**

````
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="text"/>
  <xsl:template match="/">
    <xsl:for-each select="raíz/registro">
      [<xsl:value-of select="identificador"/>]
      <xsl:value-of select="texto"/>
    </xsl:for-each>
  </xsl:template>
</xsl:stylesheet>
````

*Línea en el XML:*

````
<?xml-stylesheet type="text/xsl" href="02.xsl"?>
````



**Versión 03:**

````
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="text"/>
  <xsl:template match="/">
    <xsl:for-each select="raíz/registro">
      <xsl:text>&#xA;</xsl:text>
      <xsl:value-of select="título"/>
      <xsl:text>&#32;</xsl:text>
      <xsl:value-of select="fecha/@cuándo"/>
    </xsl:for-each>
  </xsl:template>
</xsl:stylesheet>
````

*Línea en el XML:*

````
<?xml-stylesheet type="text/xsl" href="03.xsl"?>
````



**Versión 04:**

````
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="text" />
  <xsl:template match="/">
    <xsl:for-each select="raíz/registro">
      <xsl:sort select="fecha/@cuándo" order="ascending" data-type="text"/>
      <xsl:for-each select="texto/p">
        <xsl:text>&#xA;</xsl:text><xsl:value-of select="."/>
      </xsl:for-each>
      <xsl:text>&#xA;</xsl:text>
    </xsl:for-each>
  </xsl:template>
</xsl:stylesheet>
````

*Línea en el XML:*

````
<?xml-stylesheet type="text/xsl" href="04.xsl"?>
````



**Versión 05:**

````
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="text"/>
  <xsl:template match="/">
    <xsl:for-each select="raíz/registro">
      <xsl:sort select="fecha/@cuándo" order="descending" data-type="text"/>
      <xsl:if test="fecha/año = '1789'">
        <xsl:value-of select="identificador"/>, <xsl:value-of select="título"/>, <xsl:value-of select="fecha/@cuándo"/><xsl:text>&#xA;</xsl:text>
      </xsl:if>
    </xsl:for-each>
  </xsl:template>
</xsl:stylesheet>
````

*Línea en el XML:*

````
<?xml-stylesheet type="text/xsl" href="05.xsl"?>
````



Cada uno de estos archivos XSL implica que, cuando abrimos el XML en el navegador, los datos se han distribuido de diferente manera (líneas, párrafos, contenido, etc.).



## Repositorio de Github:

Los archivos se ha subido [aquí](https://github.com/GitNoe/UF2217-xml) para su acceso y visualización.

![github](xsl.png)



Noelia Figueiras Fernández | 39488208-Z
