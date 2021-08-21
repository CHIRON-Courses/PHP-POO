# [Les interfaces](https://www.php.net/manual/fr/language.oop5.interfaces.php)

Une `interface` n'est pas instanciable, elle déclare des prototypes de méthodes public. En implémentant une interface, la classe devient du type de l'interface en proposant un **standard d’interaction**.

## Déclaration

```php
interface EtudiantInterface
{
    public function learn(): bool
}
```

## Utilisation

Une classe implémentant l'interface doit respecter les signatures déclarées.

```php
class Etudiant implements EtudiantInterface
{
    public function learn(): bool
    {
        return true;
    }
}
```

Il est possible d'implémenter plusieurs interfaces.

```php
interface ProgrammeurInterface
{
    public function code(): bool
}

class Etudiant extends Personne implements 
    EtudiantInterface, 
    ProgrammeurInterface
{
    public function learn(): bool
    {
        return true;
    }

    public function code(): bool
    {
        return true;
    }
}
```

----------

# [Les exceptions](https://www.php.net/manual/fr/class.exception.php)

Il est possible de créer ses propres exceptions en utilisant les notions abordées.

## Déclaration

```php
class StudentException extends Exception
{
}
```

## Utilisation

L'avantage est de pouvoir attraper une exception précise.

```php
try {
    $student = new Student();
    $student->learn();
} catch (StudentException $e) {
    echo  $e-getMessage();
}
```

----------

[Retour au sommaire](00_sommaire.md)
