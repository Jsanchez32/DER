![](https://raw.githubusercontent.com/CampusLands/DER/main/DER.jpg)

**1. Listar todas las ventas que se realizaron en el mes de julio de 2023**

```sql
SELECT * FROM venta  WHERE fecha > '2023-06-30' AND fecha <'2023-08-01';
```

**2. Seleccionar todos los empleados con sus respectivos cargos y municipios**

```sql
SELECT empleado.nombre, cargos.descripcion, municipio.nombre FROM empleado INNER JOIN cargos ON empleado.idCargoFk = cargos.id INNER JOIN municipio ON empleado.idMunicipioFk = municipio.id;
```

**3. Obtener la lista de todas las ventas con la información de los clientes y la forma de pago**

```sql 
SELECT venta.id, venta.fecha, venta.idEmpleadoFk,cliente.nombre,cliente.idCliente,cliente.fechaRegistro,cliente.idMunicipioFk,forma_pago.descripcion FROM venta 
INNER JOIN cliente ON venta.idClienteFk = cliente.id
INNER JOIN forma_pago ON venta.idFormaPagoFk = forma_pago.id;
```

**4. Mostrar los detalles de todas las órdenes junto con los nombres de los empleados y clientes asociados**

```sql
SELECT orden.fecha, empleado.nombre, cliente.nombre, orden.idEstadoFk FROM orden
    INNER JOIN cliente
    ON orden.idClienteFk = cliente.id
    INNER JOIN empleado
    ON orden.idEmpleadoFk = empleado.id;
```

**5. Listar los productos disponibles en el inventario junto con su talla y color**

```sql
SELECT inventario.*,talla.descripcion as talla,color.descripcion as color FROM inventario
INNER JOIN inventario_talla
ON inventario.id = inventario_talla.idInvFk
INNER JOIN talla
ON inventario_talla.idInvFk = talla.id

INNER JOIN prenda
ON inventario.idPrendaFk = prenda.id
INNER JOIN detalle_orden
ON prenda.id = detalle_orden.id
INNER JOIN color
ON detalle_orden.idColorFk = color.id;
```

**6. Mostrar todos los proveedores junto con la lista de insumos que suminis**

```sql
SELECT proveedor.id,proveedor.nitProveedor,proveedor.nombre,proveedor.idTipoPersona,proveedor.idMunicipioFk,insumo.nombre FROM proveedor
LEFT JOIN insumo_proveedor
ON proveedor.id = insumo_proveedor.idProveedorFk
LEFT JOIN insumo
ON insumo_proveedor.idInsumoFK = insumo.id
```

**7. Encontrar la cantidad de ventas realizadas por cada empleado**

```sql
    SELECT e.nombre AS empleado, COUNT(v.id) AS cantidad_ventas
    FROM empleado e
    LEFT JOIN venta v ON e.id = v.IdEmpleadoFk
    GROUP BY e.id;	
```

**8. Mostrar la lista de órdenes en proceso junto con los nombres de los clientes y empleados asociados**

```sql
SELECT o.id,o.fecha,c.nombre as nombre_cliente, e.nombre as nombre_empleado, es.descripcion as estado FROM orden o 
JOIN cliente c ON  o.idClienteFk = c.id
JOIN empleado e ON  o.idEmpleadoFk = e.id
JOIN estado es ON  o.idEstadoFk = es.id
WHERE es.descripcion ="En proceso";
```

**9. Obtener el nombre de la empresa y su respectivo representante legal junto con el nombre del municipio al que pertenecen**

```sql
SELECT e.razon_social AS nombre_empresa,e.representante_legal,m.nombre AS municipio FROM empresa e
JOIN municipio m ON e.idMunicipioFk = m.id;
```

**10. Mostrar la lista de prendas y su respectivo stock disponible**

```sql
SELECT p.nombre,p.codigo, ip.cantidad FROM prenda p
JOIN insumo_prendas ip ON p.id = ip.idPrendaFk;
```

**11. Encontrar el nombre de los clientes que realizaron compras en una fecha específica junto con la cantidad de artículos comprados**

```sql
SELECT c.nombre, do.cantidad_producir AS cantidad_articulos,o.fecha FROM cliente c
LEFT JOIN orden o ON c.id = o.idClienteFk
LEFT JOIN detalle_orden do ON o.id = do.idOrdenFk
WHERE o.fecha = "2023-08-10"
```

**12. Mostrar la lista de empleados y la duración de su empleo en años**

```sql
SELECT nombre AS NombreEmpleado, DATEDIFF(CURRENT_DATE, fecha_ingreso)/365 AS DuracionEmpleoAnos FROM empleado;
```

**13. Obtener el nombre de las prendas junto con el valor total de ventas en dólares para cada una**

```sql
SELECT p.nombre AS prenda, SUM(p.valorUnitUsd*do.cantidad_producir) AS total  FROM prenda p
LEFT JOIN detalle_orden do ON p.id = do.idPrendaFk
GROUP BY p.id
```

**14. Obtener el nombre de las prendas junto con la cantidad mínima y máxima de insumos necesarios para su fabricación**

```sql
SELECT p.nombre ,i.stock_min, i.stock_max FROM prenda p
LEFT JOIN insumo_prendas ip ON p.id = ip.idPrendaFk
LEFT JOIN insumo i ON ip.idInsumoFk = i.id 
```

**15. Obtener la lista de empleados y su información de contacto, incluyendo el nombre, el cargo y el municipio**

```sql
# Consulta realizada ....
```

**16. Mostrar la lista de ventas realizadas en un rango de fechas específico junto con el nombre del cliente y la forma de pago**

```sql
# Consulta realizada ....
```

**17. Obtener el nombre de las prendas y su valor unitario en dólares junto con el estado de disponibilidad**

```sql
# Consulta realizada ....
```

**18. Mostrar la lista de clientes y la cantidad de compras que han realizado**

```sql
# Consulta realizada ....
```

**19. Obtener la lista de órdenes junto con el estado actual y la fecha en que se crearon**

```sql
# Consulta realizada ....
```

**20. Obtener el nombre y la descripción de los cargos con un sueldo base superior a 2.000.000 **

```sql
# Consulta realizada ....
```

**21. Mostrar la lista de clientes con sus respectivos municipios y países **

```sql
# Consulta realizada ....
```

**22 Obtener el nombre y la descripción de los tipos de protección y el número de prendas asociadas a cada tipo **

```sql
# Consulta realizada ....
```

**23 Mostrar la lista de empleados con sus cargos y fechas de ingreso ordenados por la fecha de ingreso de manera descendente **

```sql
# Consulta realizada ....
```

**24 Mostrar el nombre y la descripción de todos los cargos junto con la cantidad de empleados en cada cargo **

```sql
# Consulta realizada ....
```

**25 Obtener el nombre y la descripción de los estados junto con la cantidad de prendas asociadas a cada estado **

```sql
# Consulta realizada ....
```

**26 Obtener el nombre y la descripción de los tipos de persona junto con la cantidad de clientes asociados a cada tipo **

```sql
# Consulta realizada ....
```

**27 Mostrar el nombre y la descripción de los tipos de protección junto con la cantidad de prendas asociadas a cada tipo **

```sql
# Consulta realizada ....
```

**28 Obtener el nombre y la descripción de los estados junto con la cantidad de órdenes asociadas a cada estado **

```sql
# Consulta realizada ....
```

**29 Obtener el nombre y la descripción de los tipos de pago junto con la cantidad de ventas asociadas a cada tipo **

```sql
# Consulta realizada ....
```

**30 Mostrar el nombre y la descripción de los tipos de insumos junto con la cantidad de prendas que los utilizan**

```sql
# Consulta realizada ....
```

**31 Obtener el nombre de los clientes y la cantidad total gastada por cada uno en ventas**

```sql
# Consulta realizada ....
```

**32 Mostrar el nombre y la descripción de las prendas junto con el valor total de ventas en pesos colombianos para cada una**

```sql
# Consulta realizada ....
```

**33 Mostrar el nombre y la descripción de los estados junto con la cantidad de prendas asociadas a cada estado en orden ascendente de la cantidad de prendas**

```sql
# Consulta realizada ....
```