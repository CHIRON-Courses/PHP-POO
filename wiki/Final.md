# [Final](https://www.php.net/manual/fr/language.oop5.final.php)

Le mot-clé `final` empêche les classes enfants de surcharger une méthode en préfixant la définition. Si la classe elle-même est définie comme finale, elle ne pourra pas être étendue.

## Déclaration d'une classe final

```php
final class Stagiaire
{
}
```

## Déclaration d'une méthode final

```php
class Formateur
{
    final public function enseigner(): void
    {
        echo "J'enseigne...";
    }
}
```

----------

[Retour au sommaire](_Sidebar.md)
