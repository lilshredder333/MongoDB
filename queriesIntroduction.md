# INTRODUCCIÓN A QUERIES EN MONGODB COMPASS

## OJO MONGODB IS CASE SENSITIVE

## Cuando queremos hacer una consulta sobre un campo numérico 

Por ejemplo mostrar solo los documentos en los que su campo beds sea igual a 5
```shell
{beds: {$eq: 5}}
```

## Cuando queremos hacer una consulta sobre un campo tipo string

Los campos tipo string se buscan con comillas doble

```shell
{property_type: {$eq: "House"}}
```
Se podría obviar la funcion $eq pero no deberíamos acostumbrarnos, ya que 
en otras consultas más complejas debe seguirse el ejemplo de arriba :)

```shell
#Nos daría el mismo resultado
{property_type: "House"} 
```

## Consulta con operadores lógicos

Queremos encontrar los documentos en los que el número de camas sea mayor que 10
```shell
# $gt es una funcion que representa mayor que
{beds: {$gt: 10}}
```

Queremos encontrar los documentos en los que el número de camas sea menor que 10
```shell
# $gt es una funcion que representa menor que
{beds: {$gte: 10}}
```

## Consulta para encontrar campos no rellenos (NO SON NULL)
```shell
{access: {$eq: ""}}
```

## Ampliamos el rango de busqueda

Busca todos los documentos donde "property_type" sea "Apartment" o "House" \
Busqueda con colección de valores :) 
```shell
{property_type: {$in:["House", "Apartment"]}}
```

## Rangos de busqueda con negación

```shell
# $nin representa not in
{property_type: {$nin:["House", "Apartment"]}}
```

## Mostrar el último resultado
```shell
# $ne muestra el último resultado coincidente
{property_type: {$ne: "Bed and Breakfast}}
```

## Busqueda con varios operadores lógicos

AND

```shell
{$and:[{property_type: {$eq: "House"}},{beds:{$gte:10}}]}
```

OR

```shell
# $lte representa "less than equal" y $gte representa "greater than equal" 
{$or:{beds:{$lte:2},{beds:{$gte:10}}}}
```
