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

## Busqueda AND y OR

AND

```shell
{$and:[{property_type: {$eq: "House"}},{beds:{$gte:10}}]}
```

OR

```shell
# $lte representa "less than equal" y $gte representa "greater than equal" 
{$or:{beds:{$lte:2},{beds:{$gte:11}}}}
```


#  En un documento puede que haya campos que no existan en otros docs!!

## Mostar documentos donde [nombre_de_campo] exista

```shell
{cleaning_fee:{$exists:true}}
```

## Mostrar documentos donde [nombre_de_campo] NO exista
```shell
{cleaning_fee:{$exists:false}}
```


## Mostrar los documentos si se cumple condición

```shell
#esto es como un IF statement
{cleaning_fee:{$exists:true, $lte:50}}

#se podría hacer con un AND
{$and:[{cleaning_fee:{$exists:true}}, {cleaning_fee:{$lte:50}}]}
```

# Ejercicios

## Muestra todos los documentos que contengan el campo cleaning fee, su valor sea menor o igual que 50 y que la propiedad sea una casa. 

```shell
{$and:[{cleaning_fee:{$exists:true, $lte:50}}, {property_type:{$eq:"House"}}]}
```

## Mostrar el tipo de un campo (int, string, array...)

```shell
# buscar por nombre de tipo
{beds:{$type:["int","long"]}}

# buscar por numero de tipo --> 16 equivale a "int" y 18 a "long"
{beds:{$type:[16,18]}}

# buscar el contrario al tipo segun num
# esta consulta también mostraría los documentos en los que el campo "beds" NO exista
{beds:{$not:{$type:[16,18]}}}

```

# Como hacer consultas desde _MONGOSH

## Primero decidimos qué bbdd usamos

```shell
use [nombre_base_datos]
```

## MODELO DE BUSQUEDA
## db.[nombre_coleccion].funcion({argumentos de busqueda})

```shell
db.listingsAndReviews.find({beds:{$eq:5}})
```
