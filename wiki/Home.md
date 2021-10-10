# Introduction

## Déclaration d'une classe

Une classe contient des propriétés et des méthodes.

```php
class Personne
{
}
```

----------

## Instanciation d'une classe

Un objet est une `instance` de classe.

```php
$pers = new Personne();
```

----------

## Méthode d'une classe

### Déclaration

```php
class Personne
{
    public function sayHello(): void
    {
        echo 'Hello';
    }
}
```

### Invocation ou instanciation

```php
$pers = new Personne();
$pers->sayHello();
```

----------

## Propriété d'une classe

### Déclaration

```php
class Personne
{
    public string $message = 'Hello';
}
```

### Utilisation

Le mot clef `$this` correspond à l'objet en cours de manipulation.

```php
class Personne
{
    public string $message = 'Hello';

    public function sayHello(): void
    {
        echo $this->message;
    }
}

$pers = new Personne();
echo $pers->message; // Hello
```

----------

## Valeur de retour d'une méthode

### Déclaration

```php
class Personne
{
    public function myMethod()
    {
        return [expression = null];
    }
}
```

L'instruction return renvoie la valeur de l'expression qui lui succède et met fin à l'exécution des instructions d'une méthode. L'expression de retour est optionnelle et sa valeur par défaut est null.

### Utilisation

```php
class Personne
{
    public function sayHello(): string
    {
        return "Hello";
    }
}

$pers = new Personne();
echo $pers->sayHello(); // Hello
```

----------

## [L'opérateur objet nullsafe](https://www.php.net/manual/fr/language.oop5.basic.php#language.oop5.basic.nullsafe)

À partir de PHP 8.0.0, les méthodes et propriétés peuvent aussi être accédés avec l'opérateur nullsafe `?->`. L'opérateur nullsafe fonctionne à l'identique que l'accès de propriétés ou méthodes comme si dessus, à l'exception que si l'objet qui est déréférencé est null alors null sera retourné au lieu de lancer une exception. Si le déréférencement fait par d'une chaîne, le reste de la chaîne est ignoré.

L'effet est similaire à entourer chaque accès par une vérification avec `is_null()` d'abord, mais plus compact.

```php
// À partir de PHP 8.0.0, cette ligne:
$result = $repository?->getUser(5)?->name;

// Est équivalente à bloc de code suivant :
if (is_null($repository)) {
    $result = null;
} else {
    $user = $repository->getUser(5);
    if (is_null($user)) {
        $result = null;
    } else {
        $result = $user->name;
    }
}
```


----------

[Retour au sommaire](_Sidebar.md)
