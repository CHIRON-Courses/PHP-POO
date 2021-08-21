
# [Le constructeur](https://www.php.net/manual/fr/language.oop5.decon.php)

## Déclaration

```php
class Personne
{
    public string $message;

    public function __construct()
    {
        $this->message = "Hello";
    }
}
```

Le constructeur est invoqué lors de la construction de l'objet, il est intéressant pour toute `initialisation` de propriété déclarée.

```php
$pers = new Personne();
echo $pers->message;
```

----------

## Argument d'un constructeur

```php
class Personne
{
    public string $message;

    public function __construct(string $message)
    {
        $this->message = $message;
    }
}
```

Il est encore plus intéressant de pouvoir initialiser les propriétés d'un objet dynamiquement en les passant en argument lors de son instanciation.

```php
$pers = new Personne("Hello");
echo $pers->message;
```

----------

## [Promotion du Constructeur](https://www.php.net/manual/fr/language.oop5.decon.php#language.oop5.decon.constructor.promotion)

À partir de PHP 8.0.0, les paramètres du constructeur peuvent être promu pour correspondre à une propriété de l'objet. Il est très commun pour les paramètres d'un constructeur d'être assigné à une propriété sans effectuer d'opérations dessus. La promotion du constructeur fournie un raccourci pour ce cas d'utilisation.

```php
class Personne
{
    public function __construct(protected string $message)
    {
    }
}
```

```php
$pers = new Personne("Hello");
echo $pers->message;
```

----------

# [Le destructeur](https://www.php.net/manual/fr/language.oop5.decon.php#language.oop5.decon.destructor)

PHP possède un concept de destructeur similaire à celui d'autres langages orientés objet, comme le `C++`. La méthode destructeur est appelée dès qu'il n'y a plus de référence sur un objet donné, ou dans n'importe quel ordre pendant la séquence d'arrêt.

```php
class Personne
{
    public function __destruct(): void
    {
        echo "Destruction de l'objet de la classe " . __CLASS__;
    }
}
```

Le destructeur sera appelé même si l'exécution du script est stoppée en utilisant la fonction [exit()](https://www.php.net/manual/fr/function.exit.php).

```php
$obj = new Personne();
exit(); // Destruction de l'objet de la classe Personne
```

----------

[Retour au sommaire](00_sommaire.md)
