# [Static](https://www.php.net/manual/fr/language.oop5.static.php)

Le fait de déclarer des propriétés ou des méthodes comme statiques vous permet d'y accéder sans avoir besoin d'instancier la classe. Ceci peuvent être accédé statiquement depuis une instance d'objet.

## Déclaration

```php
class Personne
{
    public static string $staticProperty = "Propriété statique";

    public static function staticMethod()
    {
        echo "Méthode statique";
    }
}
```
Comme les méthodes statiques peuvent être appelées sans qu'une instance d'objet n'ait été créée, la pseudo-variable `$this` n'est pas disponible dans les méthodes déclarées comme statiques.

## Utilisation en dehors de la classe

Lorsque vous référencez ces éléments en dehors de la définition de la classe, utilisez le nom de la classe.

```php
class Personne
{
    public static string $staticProperty = "Propriété statique";

    public static function staticMethod()
    {
        echo "Méthode statique";
    }
}

$obj = new Personne();
echo Personne::$staticProperty; // "Propriété statique"
echo $obj::$staticProperty; // "Propriété statique"
Personne::staticMethod(); // "Méthode statique"
$obj::staticMethod(); // "Méthode statique"
```

## Utilisation dans la classe

Trois mots-clé spéciaux, `self`, `parent`, et `static` sont utilisés pour accéder aux propriétés ou aux méthodes depuis la définition de la classe. 

```php
class Personne {
    const CONST_VALUE = "Une valeur constante";
}

class Etudiant extends Personne
{
    public static $staticProperty = "Propriété statique";

    public static function staticMethod() {
        echo parent::CONST_VALUE;
        echo self::$staticProperty;
    }
}

Etudiant::staticMethod();
```

```php
class Personne {
    public static $staticProperty = "Propriété statique";

    public function staticTest() {
        echo static::$staticProperty;
        echo self::$staticProperty;
    }
}

class Etudiant extends Personne
{
    public static $staticProperty = "Propriété statique surchargé";
}

$obj = new Etudiant();
$obj->staticTest();
```

----------

[Retour au sommaire](00_sommaire.md)
