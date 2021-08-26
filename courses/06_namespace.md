# Les espaces de nommage

Les `espaces de noms` permettent d'**éviter les collisions de nom** entre deux classes ayant le même identifiant. Ils permettent également d'utiliser des **normes de chargement de classes**.

## Déclaration

```php
namespace App\Controller;

class EtudiantController
{
}
```

## Utilisation


```php
use App\Controller\EtudiantController;

$obj = new EtudiantController();
```

Chaque classe devrait être sous espace de nom respectant la norme `psr-4`.

----------

# L'autoload

PHP possède la fonction `spl_autoload_register` permettant d'invoquer une fonction utilisateur quand une classe est non trouvée. **Un autoloader va renseigner une fonction permettant de charger une classe** en utilisant son identifiant complet pour trouver son fichier. L'outil phare pour charger les classes est `composer`.

[Composer](https://getcomposer.org/Composer-Setup.exe)

## Exécuter

```
composer
```

Si composer n'est pas reconnu il faut l'ajouter aux variables d'environnement

## Initialiser un projet

```
composer init
```

Le fichier `composer.json` généré décrit le projet.

## Configurer

Dans le fichier composer.json nous allons ajouter une section pour **déclarer notre norme de chargement**.
```json
"autoload": {
    "psr-4": {
        "App\\": "src/",
        "Test\\": "tests/"
    }
}
```

## Générer l'autoloader

```
composer dump-autoload
```

L'autoloader a été généré dans le dossier _vendor_.

## Inclure l'autoloader

Il nous faut inclure l'autoloader dans le point d'entée de notre programme.

```php
include "./../vendor/autoload.php";
```

Quand une classe est instanciée, si elle n'est pas déjà présente dans notre programme, l'autoloader inclura son fichier après que sa fonction de rappel soit invoquée automatiquement.

----------

[Retour au sommaire](00_sommaire.md)
