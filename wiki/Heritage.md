# [L'héritage](https://www.php.net/manual/fr/language.oop5.inheritance.php)

Une classe peut hériter d'une autre avec le mot clef `extends`. Elle peut **accéder à l'ensemble des propriétés et méthodes qui ne sont pas private**.

L'héritage permet de `factoriser` des fonctionnalités dans la classe parente et pouvoir les utiliser dans plusieurs classes enfants. Il n'est possible d'étendre que d'une seule classe parente.

## Déclaration

```php
class Personne
{
}

class Etudiant extends Personne
{
}
```

----------

## Propriété et méthode

Si le parent possède des propriétés ou des méthodes, ils peuvent être invoqué depuis une classe enfant. On dit que la classe enfant hérite des propriétés et des méthodes de la classe parente.

```php
class Personne
{
    public string $message = "Hello";

    public function sayHello(): void
    {
		echo "Hello";
    }
}

class Etudiant extends Personne
{
}

$obj = new Etudiant();
$obj->message; // Hello
$obj->sayHello(); // Hello
```

Une classe enfant peut surcharger une méthode de la classe parent pour redéfinir sa fonctionnalité. Pour cela, elle doit la redéclarer avec le même nom que dans la classe parente.

```php
class Personne
{
    public string $message = "Hello";

    public function sayHello(): void
    {
		echo $this->message;
    }
}

class Etudiant extends Personne
{
    public string $target = "World";
    
    public function sayHello(): void
    {
        echo this->message . " " . $this->target;
    }
}

$obj = new Etudiant();
$obj->sayHello(); // Hello World
```

--------

## Constructeur

Si l'enfant possède un constructeur il sera invoqué. Si le parent possède un constructeur et que l'enfant ne l'a pas déclaré il sera invoqué.

En présence des deux constructeurs, il faut invoquer le constructeur `parent` depuis l'enfant afin qu'il puisse initialiser l'objet correctement.

```php
class Personne
{
    public string $message;

    public function __construct(string $message)
    {
        $this->message = $message;
    }
}

class Etudiant extends Personne
{
    public string $target;

    public function __construct(string $message, string $target)
    {
        parent::__construct($message);
        $this->target = $target;
    }
}

$obj = new Etudiant("Hello", "World");
echo $obj->message; // Hello
echo $obj->target; // World
```

----------

[Retour au sommaire](_Sidebar.md)
