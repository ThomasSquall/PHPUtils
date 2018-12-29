# String Utils for php

## List of available functions

1) [array_to_object](#array_to_object)
2) [json_to_object](#json_to_object)
3) [parse_args](#parse_args)

#### Other contained Repositories

1) [String utils](https://github.com/ThomasSquall/PHPStringUtils)

### array_to_object

#### Description

Returns an object out of an array.
Note that only fields corresponding to the array keys will be returned.

#### Definition

array_to_object($array, $object)

Where:
1) $array is the array to convert
2) $object is the object or class to be returned
3) $add_not_existing_properties is used to choose whether to add properties not defined in the class to the object

#### Usage

``` php
class Person
{
    public $name;
    public $age;
}

$array = [
    "name" => "MyName",
    "surname" => "MySurname",
    "age" => 27
];

print_r(array_to_object($array, "Person"));
echo PHP_EOL;
print_r(array_to_object($array, "Person", true));
```

This will print:

``` sh
Person Object ( [name] => MyName [age] => 27 ) 
Person Object ( [name] => MyName [age] => 27 [surname] => MySurname )
```

### json_to_object

#### Description

Returns an object out of a json string.
Note that only fields corresponding to the json keys will be returned  unless you pass $add_not_existing_properties to true.

#### Definition

json_to_object($json, $object, $add_not_existing_properties = false)

Where:
1) json is the json to convert
2) $object is the object or class to be returned
3) $add_not_existing_properties is used to choose whether to add properties not defined in the class to the object

#### Usage

``` php
class Person
{
    public $name;
    public $age;
}

$json = '{
    "name": "MyName",
    "surname": "MySurname",
    "age": 27
}';

print_r(array_to_object($json, "Person"));
echo PHP_EOL;
print_r(array_to_object($json, "Person", true));
```

This will print:

``` sh
Person Object ( [name] => MyName [age] => 27 ) 
Person Object ( [name] => MyName [age] => 27 [surname] => MySurname )
```

### parse_args

#### Description

Build a new array out of the $options one with defaults values taken from $defaults when nothing is found.

#### Definition

parse_args($options, $defaults)

Where:
1) $options is the array to be parsed and used to build the new array
2) $defaults is the array containing default values to use when no correspondence is found

#### Usage

``` php
$defaults = [
    "name" => "MyName",
    "surname" => "MySurname",
    "age" => 27
];

$person = [
    "name" => "MyRealName",
    "surname" => "MyRealSurname"
];

print_r(parse_args($person, $defaults));
```

This will print:

``` sh
Array ( [name] => MyRealName [surname] => MyRealSurname [age] => 27 )
```

## More utilities coming