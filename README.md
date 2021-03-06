# NCF DGII Reports

   <pre>
        ###############################
        ## AVISO!
        ###############################
    </pre>    
   ```              
        print("Haz un pull request o integrate al equipo de desarrollo, no hasgas tu propia isla a parte.  
            La colaboración en conjunto es más beneficiosa!")

   ```   

Este módulo para ODOO 12 implementa los reportes de los números de comprobantes fiscales (NCF) para el cumplimento de la norma 06-18 de la Dirección de Impuestos Internos (DGII) en la República Dominicana, así como un resumén para la declaración del ITBIS (IT1) y del anexo A del IT-1 (ITA) *(próximamente la guía completa de ambos reportes)*. Actualmente está en desarrollo y puede que necesita validaciones y calculos extras para ser implementado en negocios de personas físicas que usan su cédula como RNC, empresas de construcción y empresas de telecomunicaciones.

Estamos coordinando para que este módulo sea integrado en https://github.com/odoo-dominicana/l10n-dominicana y que sea mantenido por la comunidad de ODOO Dominicana.  Mientras tanto todo aquel que desee colaborar, puede hacer un Pull Request aquí o si será un desarrollador activo, puede contactarnos para que sea miembro del equipo.

## CONFIGURAR IMPUESTOS
Se debe configurar correctamente los impuestos, para ello ir al listado de impuestos y en la opción de **Tipo de Impuesto de Compra** *(Cuando el Ámbito del Impuesto es Compra)* seleccionar la opción adecuada para cada caso.

## CONFIGURAR CORRECTAMENTE LOS TIPOS DE PRODUCTOS
En cada producto, se debe configurar correctamente el **Tipo de Producto** para poder filtrar el **Monto Facturado en Servicios** y el **Monto Facturado en Bienes**.  Actualmente si un producto es del tipo "Servicio" pues se suma al Monto Facturado en Servicios y si es otra cosa como puede ser Consumible o Almacenable, entonces lo sumamos al Monto Facturado en Bienes.  OJO que si venden productos digitales (como libros, fotos, etc..) en teoría serían servicios al no ser algo mateiral pero esto tampoco lo estamos filtrado en la actualidad y en dado caso de ponerlo caerían como Bienes.

## CONFIGURAR LA(S) CUENTA(S) QUE ES(SON) USADA(S) PARA EL ITBIS RETENIDO EN VENTAS (REPORTE 607) SEGÚN LA NORMA 02-05
En el catálogo de cuentas hemos colocado un nuevo campo opcional para escoger, este se llama: **Tipo de Impuesto en Venta** y por lo general las empresas que tiene RNC solo deberán escoger allí la primera opción **ITBIS Retenido Persona Jurídica (N 02-05)**, y cuando la cuenta sea *ITBIS Retenido Persona Jurídica (N 02-05)* que por defecto en el catálogo de cuentas dominicano en ODOO 12 es la *no. 21030201* y tiene el ID *100*.

Con esta acción podemos obtener las columnas *7 - FECHA DE RETENCIÓN* y *10 - ITBIS RETENIDO POR TERCEROS* del reporte 607.

NOTA: Lo anterior también se puede lograr vía el nuevo campo: **Tipo Cuenta Fiscal** ***(account_fiscal_type)*** que también está en el catálogo de cuenta. Para ello se debe escojer la opción: **Pagos Computables por otras Retenciones (N02-05)**


## REGISTRAR CORRECTAMENTE LAS FACTURAS DE PROVEEDORES QUE NOS DAN UN SERVICIO Y AL CUAL LE HACEMOS RETENCIÓN DE 30% ITBIS (REPORTE 606) SEGÚN LA NORMA 02-05
Al registrar los impuestos de este tipo de factura, se debe seleccionar el **18% de ITBIS compra - Servicios** y además como le vamos a hacer retención de 30% ITBIS según la norma 02-05, debemos seleccionar también como impuesto **Retención 30% ITBIS Servicios a Jurídicas (N02-05)** y que por defecto ese impuesto viene atado a la cuenta contable **21030201 ITBIS Retenido a Persona Jurídica (N02-05)**, además recordar que ese impuesto se debe configurar como **ITBIS Retenido**

Con esta acción podemos obtener la columna *12 - ITBIS RETENIDO* del reporte 606.

*Nota: del mismo modo, otro impuesto a escoger podría ser el Retención ISR 10% a Personas Físicas en los casos que aplique* 

## CONFIGURAR LA(S) CUENTA(S) QUE ES(SON) USADA(S) PARA EL ISR RETENIDO EN VENTAS (REPORTE 607) SEGÚN LA NORMA 07-07
En el catálogo de cuentas hemos colocado un nuevo campo opcional para escoger, este se llama: **Tipo de Impuesto en Venta** y las empresas que son objeto de retención de ISR en sus ventas, como por ejemplo al facturarle a entidades del estado que se retiene un 5%, deben escoger la opción **Otras Retenciones (N07-07) (Ej. 5% ISR Gubernamentales en las ventas)**, para el ejemplo del 5% de retención de ISR que realizan las entidades del estado, la cuenta recibe el nombre de *Otras Retenciones (N07-07)* que por defecto en el catálogo de cuentas dominicano en ODOO 12 es la *no. 21030308* y tiene el ID *118*.

Con esta acción podemos obtener las columnas *RETENCIÓN RENTA* del reporte 607.

## NOTA SOBRE LA FECHA DE RETENCIÓN DE ITBIS Y/O ISR
Si una factura tiene multiples pagos y a la misma se le realiza retención ya sea de ITBIS o ISR; la fecha de retención que pondrá el sistema será la fecha del último pago registrado dado que lo lógico sería que las retenciones se realicen durante el último pago y además la factura no se pone en estado pagado hasta tanto no se realice el pago total.   Lo anterior aplica tanto para facturas de compras como de ventas.


### ESTADO ACTUAL  

- 606 en Alpha 2 (ver ISSUES AND PENDING STUFF) .
- 607 en Alpha 2 (ver ISSUES AND PENDING STUFF) .
- 608 en Alpha 1 (ver ISSUES AND PENDING STUFF) .
- 609 en Alpha 1 (ver ISSUES AND PENDING STUFF) .
- Guía del ITA (Anexo A del IT1) en desarrollo.
- Guía del IT1 (Declaración de ITBIS) en desarrollo.

## RECOMENDACIONES
Luego de implementar este módulo, se recomienda hacer una revisión manual de los reportes al menos durante 3 períodos en búsca de bugs y cada vez que en un determinado período tenga novedades nuevas antes no usadas como puede ser recibir una Nota de Crédito y otros.

## LICENCIA DE USO, DESCARGO DE RESPONSABILIDAD, AYUDA Y SOPORTE
 Este módulo “software” (programa) es de código fuente libre y abierto y está licenciado bajo la GNU General Public License Version 3 (https://www.gnu.org/copyleft/gpl.html). 

 Al usar el módulo, usted se compromete a darle un uso de conformidad con la leyes dominicanas. 
 
 Este módulo se suministra tal cual es. Por diversas razones no podemos garantizar de forma expresa o implícita, la confiabilidad o integridad de los reportes que emite este módulo, y que los mismos estén libre de fallos debido a códigos o rutinas de programación incorrectos.

 Para ayuda puede escribir un issue en este repositorio o vía la comunidad de ODOO Dominicana.  Si necesita soporte e implementaciones puede contactar con Manuel Gonzalez en SOFTNET TEAM SRL (https://www.softnet.do)



## PENDING STUFF

- Ver todos los #TODO en el código.
- Terminar guías ITA e IT1
- Certificaciones de funcionalidad de contables


### Créditos:  Basado en el trabajo inicial para ODOO 10 de Eneldo Serrata para Marcos Organizador de Negocios SRL. (https://marcos.do/) 

### Autores activos: Manuel Gonzalez (SOFTNET TEAM SRL - https://www.softnet.do) y Jeffry De La Rosa

## SCREEMSHOTS DE EJEMPLOS.

### DGII TAB EN LAS FACTURAS
![DGII tab en las facturas](https://res.cloudinary.com/drgtdlvxn/image/upload/v1557328463/DGII_REPORTS_ODOO_12_EXAMPLE_01.png)

### RESUMÉN DEL REPORTE FISCAL DEL DGII
![Reportes físcales DGII extracto/resumen](https://res.cloudinary.com/drgtdlvxn/image/upload/v1557328463/DGII_REPORTS_ODOO_12_EXAMPLE_02.png)

### RESUMEN DEL IT1
![Resumen del formulario de delcaración de ITBIS](https://res.cloudinary.com/drgtdlvxn/image/upload/v1557328463/DGII_REPORTS_ODOO_12_EXAMPLE_03.png)

### VISTA DEL FORMULARIO 607
![Vista del formulario 607](https://res.cloudinary.com/drgtdlvxn/image/upload/v1557328463/DGII_REPORTS_ODOO_12_EXAMPLE_04.png)

### VISTA DEL FORMULARIO 606
![Vista del formulario 606](https://res.cloudinary.com/drgtdlvxn/image/upload/v1557328463/DGII_REPORTS_ODOO_12_EXAMPLE_05.png)