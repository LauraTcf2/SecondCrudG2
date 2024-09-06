# SecondCrudG2

## Installation

Installation de Symfony `LTS` (Long Term Support) en mode webapp (avec la plupart des dépendances pour un site web)

    symfony new SecondCrudG2 --version=lts --webapp

On rentre dans le répertoire

    cd SecondCrudG2

On crée un repository sur `github` et on le lie au projet

    git remote add origin git@github.com:WebDevCF2m2023/secondCrudG2.git
    git branch -M main
    git push -u origin main

On crée le README.md sur github, on effectue un commit sur github, puis on le charge en local avec `git pull`

## Mise a jour de la dernière version de composer

        composer self-update

### Mise a jours des bibliothèques

        composer update

### Démarrage du serveur

        symfony serve -d
        fermeture
        symfony serve:stop

### Création d'un 'controller' 

        php bin/console make:controller Mycontroller
        created: src/Controller/MyController.php
        created: templates/my/index.html.twig

### Voir les chemins de notre projet

        php bin/console debug:route

Pour le détail d'une route particulière

        php bin/console debug:route app-my

### Mise de 'Mycontroller' comme racine du projet

Dans le fichier 'Mycontroller'

<?php

namespace App\Controller;

use Symfony\Bundle\FrameworkBundle\Controller\AbstractController;
use Symfony\Component\HttpFoundation\Response;
use Symfony\Component\Routing\Attribute\Route;

class MyController extends AbstractController
{
    #[Route('/my', name: 'app_my')]
    public function index(): Response
    {
        return $this->render('my/index.html.twig', [
            'controller_name' => 'MyController',
        ]);
    }
}

#[Route('/', name: 'homepage)]
public function index(): Response
{
     resturn $this->render('home/index.html.twig', [

     ])
}





# SecondCrudG2

## Installation

Installation de Symfony `LTS` (Long Term Support) en mode webapp (avec la plupart des dépendances pour un site web)

    symfony new SecondCrudG2 --version=lts --webapp

On rentre dans le répertoire

    cd SecondCrudG2

On crée un repository sur `github` et on le lie au projet

    git remote add origin git@github.com:WebDevCF2m2023/secondCrudG2.git
    git branch -M main
    git push -u origin main

On crée le README.md sur github, on effectue un commit sur github, puis on le charge en local avec `git pull`

### Mise à jour de la dernière version de composer

    composer self-update

### Mise à jour des bibliothèques

    composer update

### Démarrage du serveur

    symfony serve -d

fermeture

    symfony server:stop

### Création d'un `controller`

    php bin/console make:controller MyController
        created: src/Controller/MyController.php
        created: templates/my/index.html.twig

### Voir les chemins de notre projet

    php bin/console debug:route

Pour le détail d'une route particulière

    php bin/console debug:route app_my

### Mise de `MyController` comme racine du projet

Dans le fichier `src/Controller/MyController.php`

```php
    #[Route('/my', name: 'app_my')]
    public function index(): Response
    return $this->render('my/index.html.twig', [
            'controller_name' => 'MyController',
        ]);
    
    ### en
    
    #[Route('/', name: 'homepage')]
    public function index(): Response
    return $this->render('my/index.html.twig', [
            'titre' => 'homepage',
        ]);
```twig
{% extends 'base.html.twig' %}

{% block title %}{{ titre }}{% endblock %}

{% block body %}
    <div class="container">
        <h1>{{ titre }}</h1>
    </div>
{% endblock %}

```

### Changement de `templates/my/index.html.twig`


### Création d'un environnement sécurisé

Copie de `.env` vers `.env.local (cp.env .env .loacl)
il faut changer la clé dans '.env.local`



```.env
# choix prod -> production, test -> test, dev -> devloppement
APP_ENV=dev
APP_SECRET=uneclefsecrete

#changement des ligne ci-dessous
# DATABASE_URL="mysql://app:!ChangeMe!@127.0.0.1:3306/app?serverVersion=8.0.32&charset=utf8mb4"
# DATABASE_URL="mysql://app:!ChangeMe!@127.0.0.1:3306/app?serverVersion=10.11.2-MariaDB&charset=utf8mb4"
DATABASE_URL="postgresql://app:!ChangeMe!@127.0.0.1:5432/app?serverVersion=16&charset=utf8"

#par

DATABASE_URL="mysql://root:@127.0.0.1:3306/secondcrudg2?serverVersion=8.0.32&charset=utf8mb4"
# DATABASE_URL="mysql://app:!ChangeMe!@127.0.0.1:3306/app?serverVersion=10.11.2-MariaDB&charset=utf8mb4"
# DATABASE_URL="postgresql://app:!ChangeMe!@127.0.0.1:5432/app?serverVersion=16&charset=utf8"

```

### On va créer la DB via `Doctrine`

Symfony va chercher le chemin depuis `.env.local`

$ php bin/console doctrine:database:create


Racourci `php bin/console d:d:c` (doctrine:database:create)


