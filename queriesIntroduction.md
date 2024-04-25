# INTRODUCCIÓN A QUERIES EN MONGODB COMPASS

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

## 
```shell
```

## 
```shell
```

## 
```shell
```

## 
```shell
```

## 
```shell
```

## 
```shell
```
