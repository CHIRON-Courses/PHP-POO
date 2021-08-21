# Constante

Il est possible de définir des constantes par classes qui restent identique et non modifiables. La visibilité par défaut des constantes de classe est public. Les constantes de classes peuvent être redéfinis par une classe enfant.

## Déclaration

```php
class Personne
{
    const CONST_VALUE = "Une valeur constante";
}
```

Notez que les constantes de classe sont allouées une fois par classe, et non pour chaque instance de classe.

Il est aussi possible pour les interfaces d'avoir des constantes.

## [L'opérateur de résolution de portée (::)](https://www.php.net/manual/fr/language.oop5.paamayim-nekudotayim.php)

L'opérateur de résolution de portée (aussi appelé Paamayim Nekudotayim) ou, en termes plus simples, le symbole "double deux-points" (::), fournit un moyen d'accéder aux membres static ou constant, ainsi qu'aux propriétés ou méthodes surchargées d'une classe.

> Paamayim Nekudotayim pourrait au premier abord sembler être un choix étrange pour nommer un double deux-points. Cependant, au moment de l'écriture du Zend Engine 0.5 (qui faisait fonctionner PHP 3), c'est le nom qui a été choisi par l'équipe Zend. En fait, cela signifie un double deux-points... en hébreu !

## Utilisation

```php
class Personne
{
    public const CONST_VALUE = "Une valeur constante";
    
    function showConstant() {
        echo  self::CONST_VALUE;
    }
}

$obj = new Personne();
echo $obj::CONST_VALUE; // Une valeur constante
$obj->showConstant(); // Une valeur constante
echo Personne::CONST_VALUE; // Une valeur constante
```

À partir de PHP 7.1.0, les modificateurs de visibilité sont autorisés sur les constantes de classe.

## La constante spéciale ::class

La constante spéciale `::class` permet une résolution de nom de classe pleinement qualifié au moment de la compilation, cela est utile pour les classes dans un espace de nom.

```php
namespace App;

class Personne
{
}
```

```php
echo Personne::class; // App\Personne
```

----------

[Retour au sommaire](00_sommaire.md)
