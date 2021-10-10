# [Abstract](https://www.php.net/manual/fr/language.oop5.abstract.php)

PHP peut avoir des classes et méthodes abstraites. Les **classes définies comme abstraites ne peuvent pas être instanciées**, et **toute classe contenant au moins une méthode abstraite doit elle-aussi être abstraite**. Les méthodes définies comme abstraites déclarent simplement la signature de la méthode, elles ne peuvent définir son implémentation.

## Déclaration d'une classe abstraite

```php
abstract class Personne
{
}
```

## Utilisation d'une classe abstraite

```php
abstract class Personne
{
    public function parler(): void
    {
        echo "Blah blah blah...";
    }
}

class Stagiaire extends Personne
{
}

$obj = new Stagiaire();
$obj->parler(); // Blah blah blah...
```

## Déclaration d'une méthode abstraite

```php
abstract class Employe
{
    abstract public function calculerSalaire(): void;
}
```

## Utilisation d'une méthode abstraite

```php
abstract class Employe
{
    protected string $numSS;
    
    abstract public function calculerSalaire(): void;
}

class Commercial extends Employe
{
    private int $vente;
    private int $pourcentage;

    public function calculerSalaire(): void
    {
        echo $this->vente * $this->pourcentage;
    }
}
```

Lors de l'héritage d'une classe abstraite, toutes les méthodes marquées comme abstraites dans la déclaration de la classe parente doivent être définies par la classe enfant et suivre les règles habituelles d'héritage et de compatibilité de signature.

----------

[Retour au sommaire](_Sidebar.md)
