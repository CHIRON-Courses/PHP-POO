# [Visibilité des attributs](https://www.php.net/manual/fr/language.oop5.visibility.php)

## Public

```php
class Visibilite
{
    public string $publicProperty = "Public property";

    public function publicMethod(): void
    {
        echo "Public method";
    }
}

$obj = new Visibilite();
echo $obj->publicProperty; // Public property
$obj->publicMethod(); // Public method
```

Une propriété ou une méthode `public` est accessible partout.

La bonne pratique consiste à ne pas déclarer les propriétés public pour ne pas compromettre l'intégrité des données et préserver le bon fonctionnement des méthodes. En revanche, les méthodes appelées `Getter` ou `Setter` seront public parce qu'elles permettent de récupérer ou d'assigner des valeurs à nos propriétés.

## Private

```php
class Visibilite
{
    private string $privateProperty = "Private property";   

    private function privateMethod(): void
    {
        echo "Private method";
    }
}

$obj = new Visibilite();
echo $obj->privateProperty; // Fatal Error
$obj->privateMethod(); // Fatal Error
```

Une propriété ou une méthode `private` n'est accessible qu'à la classe elle même.

## Protected

```php
class Visibilite
{
    protected string $protectedProperty = "Protected property";

    private function protectedMethod(): void
    {
        echo "Protected method";
    }
}

$obj = new Visibilite();
echo $obj->protectedProperty ; // Fatal Error
$obj->protectedMethod(); // Fatal Error
```

Une propriété ou une méthode `protected` est accessible à la classe elle même et ses enfants, **ce niveau de visibilité concerne l'héritage**.

----------

[Retour au sommaire](00_sommaire.md)
