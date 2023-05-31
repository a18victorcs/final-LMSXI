```
<xsl:stylesheet version="2.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="html" encoding="utf-8" indent="yes"/>
  <xsl:template match="/">
    <html>
      <head>
        <title>Datos por edificio</title>
      </head>
      <body>
        <h1>Resultados</h1>
        <table border='1'>
          <xsl:for-each select="inventario/producto">
            <tr>
              <td>
                <xsl:value-of select="nombre"/>
              </td>
              <td>
                <xsl:if test="peso[@unidad='kg']">
                  <xsl:value-of select="peso"/>
                </xsl:if>
                <xsl:if test="peso[@unidad='g']">
                  <xsl:value-of select="peso * 0.001"/> 
                </xsl:if>
              </td>
              <td>
                <xsl:value-of select="lugar/@edificio"/>
                <xsl:value-of select="lugar/aula"/>
              </td>
            </tr>
          </xsl:for-each>
        </table>
      </body>
    </html>
  </xsl:template>
</xsl:stylesheet>
```

```
<xsl:stylesheet version="2.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="html" encoding="utf-8" indent="yes"/>
  
  <xsl:template match="/">
    <html>
      <head>
        <title>Calificaciones Junio</title>
        <style type="text/css">
          .azul1{background-color:#369;}
          .azul2{background-color:#69C;}
          .azul3{background-color:#e0ffff;}
          td{text-align: center;}
          h1{color:#f00; font-weight:bold; text-align:center;}
        </style>
      </head>
      <body>
        <div>
          <h1>Calificaciones de la convocatoria de Junio</h1>
          <table border="3" align="center">
            <tr class="azul1">
              <th colspan="3">Datos</th>
              <th colspan="3">Notas</th>
            </tr>
            <tr class="azul2">
              <th>Nombres</th>
              <th>Apellidos</th>
              <th>Tareas</th>
              <th>Cuestionarios</th>
              <th>Examen</th>
              <th>Final</th>
            </tr>
            
            <xsl:for-each select="//alumno[@convocatoria='Junio']">
              <tr class="azul3">
                <td><xsl:value-of select="nombre"/></td>
                <td><xsl:value-of select="apellidos"/></td>
                <td><xsl:value-of select="tareas"/></td>
                <td><xsl:value-of select="cuestionarios"/></td>
                <td><xsl:value-of select="examen"/></td>
                <td>
                    <xsl:if test="final&gt;=9">
                      <span style="color:blue;">Sobresaliente</span>
                    </xsl:if>
                    <xsl:if test="final&gt;=7 and final&lt;9">
                      <span style="color:#5F9EA0;">Notable</span>
                    </xsl:if>
                    <xsl:if test="final&gt;=6 and final&lt;7">
                      <span style="color:black;">Bien</span>
                    </xsl:if>
                    <xsl:if test="final&gt;=5 and final&lt;6">
                      <span style="color:orange;">Suficiente</span>
                    </xsl:if>
                    <xsl:if test="final&lt;5">
                      <span style="color:red;">Suspenso</span>
                    </xsl:if>
                </td>
              </tr>
            </xsl:for-each>
            
          </table>
        </div>
      </body>
    </html>
  </xsl:template>
</xsl:stylesheet>
```