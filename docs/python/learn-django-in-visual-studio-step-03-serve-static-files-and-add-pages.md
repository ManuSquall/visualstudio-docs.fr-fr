---
title: Tutoriel - Découvrez Django dans Visual Studio, étape 3
description: Une procédure pas à pas des principes de base de Django dans le contexte de projets Visual Studio, expliquant en particulier comment prendre en charge des fichiers statiques, ajouter des pages à l’application et utiliser l’héritage du modèle
ms.date: 04/25/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: b267c4963eede53f433bd929eb7944ad53e9a8ba
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="tutorial-step-3-serve-static-files-add-pages-and-use-template-inheritance"></a>Étape 3 du tutoriel : prendre en charge les fichiers statiques, ajouter des pages et utiliser l’héritage du modèle

**Étape précédente : [créer une application Django avec des affichages et modèles de page](learn-django-in-visual-studio-step-02-create-an-app.md)**

Dans les étapes précédentes de ce tutoriel, vous avez appris comment créer une application Django minimale avec une seule page HTML autonome. Toutefois, les applications Web modernes sont généralement composées de plusieurs pages et utilisent des ressources partagées, tels que CSS et JavaScript et un fichier pour fournir un comportement et un style cohérents.

Dans cette étape, vous apprenez comment :

> [!div class="checklist"]
> - utiliser des modèles d’élément Visual Studio pour créer rapidement de nouveaux fichiers de types différents avec un code réutilisable pratique (étape 3-1)
> - configurer le projet Django pour prendre en charge des fichiers statiques (étape 3-2)
> - ajoutez des pages supplémentaires à l’application (étape 3-3)
> - utiliser l’héritage de modèle pour créer un en-tête et une barre de navigation utilisés sur plusieurs pages (étape 3-4)

## <a name="step-3-1-become-familiar-with-item-templates"></a>Étape 3-1 : se familiariser avec les modèles d’élément

Lorsque vous développez une application Django, vous ajoutez généralement beaucoup plus de fichiers Python, HTML, CSS et JavaScript. Pour chaque type de fichier (ainsi que d’autres fichiers tel que `web.config` dont vous avez besoin pour le déploiement), Visual Studio fournit des [modèles d’élément](python-item-templates.md) pratiques pour aider la prise en main.

Pour afficher les modèles disponibles, accédez à **Explorateur de solutions**, cliquez avec le bouton de droite sur le dossier dans lequel vous souhaitez créer l’élément, sélectionnez **Ajouter** > **Nouvel élément** :

![Boîte de dialogue Ajouter nouvel élément dans Visual Studio](media/django/step03-add-new-item-dialog.png)

Pour utiliser un modèle, sélectionnez le modèle souhaité, spécifiez un nom pour le fichier et sélectionnez **OK**. L’ajout d’un élément de cette manière permet d’ajouter automatiquement le fichier à votre projet Visual Studio et marque les modifications du contrôle de code source.

Visual Studio ajoute également des options fréquemment utilisées directement au menu **Ajouter**. Par exemple, dans un projet Python, vous pouvez voir les commandes **Page HTML** ou **Feuille de style** en bas du menu **Ajouter**, qui vous invitent à entrer un nom et créent le fichier.

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>Question : comment Visual Studio sait quel modèle d'élément proposer ?

Réponse : le fichier projet Visual Studio (`.pyproj`) contient un identificateur de type de projet qui le marque comme projet Python. Visual Studio utilise cet identificateur de type pour afficher uniquement les modèles d’élément qui conviennent pour le type de projet. De cette manière, Visual Studio peut fournir un ensemble riche de modèles d’élément pour plusieurs types de projet sans vous demander de les trier à chaque fois.

## <a name="step-3-2-serve-static-files-from-your-app"></a>Étape 3-2 : prendre en charge les fichiers statiques à partir de votre application

Dans une application Web générée avec Python (à l’aide de n’importe quelle infrastructure), vos fichiers Python s’exécutent toujours sur le serveur de l’hôte Web et ne sont jamais transmis à l’ordinateur d’un utilisateur. D’autres fichiers, cependant, tels que CSS et JavaScript, sont utilisés exclusivement par le navigateur, afin que le serveur hôte les remette simplement tel-quel à chaque fois qu’ils sont demandés. Ces fichiers sont appelés fichiers « statiques » et Django peut les remettre automatiquement sans que vous ayez besoin d’écrire du code.

Un projet Django est configuré par défaut pour prendre en charge les fichiers statiques à partir du dossier `static` de l’application, grâce à ces lignes dans le `settings.py` du projet Django :

```python
# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/1.9/howto/static-files/

STATIC_URL = '/static/'

STATIC_ROOT = posixpath.join(*(BASE_DIR.split(os.path.sep) + ['static']))
```

Vous pouvez organiser les fichiers à l’aide d’une structure de dossiers dans `static` de votre choix, puis utiliser les chemins d’accès relatifs au sein de ce dossier pour faire référence aux fichiers. Pour illustrer ce processus, les étapes suivantes permettent d’ajouter un fichier CSS à l’application puis utilisent cette feuille de style dans le modèle `index.html` :

1. Dans **Explorateur de solutions**, cliquez avec le bouton de droite sur le dossier « HelloDjangoApp » dans le projet Visual Studio, sélectionnez **Ajouter** > **Nouveau dossier** et nommez le dossier `static`.

1. Cliquez avec le bouton de droite sur le dossier `static` et sélectionnez **Ajouter** > **Nouvel élément**. Dans la boîte de dialogue qui s’affiche, sélectionnez le modèle « Feuille de style », nommez le fichier `site.css`, puis sélectionnez **OK**. Le fichier `site.css` apparaît dans le projet et est ouvert dans l’éditeur. Votre structure de dossiers doit apparaître semblable à l’image suivante :

    ![Structure de fichier statique comme indiqué dans l’Explorateur de solutions](media/django/step03-static-file-structure.png)

1. Remplacez le contenu de `site.css` par le code suivant et enregistrez le fichier :

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. Remplacez le contenu du fichier `templates/HelloDjangoApp/index.html` de l’application par le code suivant, qui remplace l’élément `<strong>` utilisé à l’étape 2 par un `<span>` qui fait référence à la classe de style `message`. Une telle utilisation d’une classe de style vous offre davantage de flexibilité dans l’ajout des styles à l’élément. (Si vous n’avez pas déplacé `index.html` dans un sous-dossier dans `templates`, reportez-vous aux [espaces de noms du modèle](learn-django-in-visual-studio-step-02-create-an-app.md#template-namespacing) à l’étape 2.)

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            {% load staticfiles %} <!-- Instruct Django to load static files -->
            <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
        </head>
        <body>
            <span class="message">{{ message }}</span>{{ content }}
        </body>
    </html>
    ```

1. Exécutez le projet et observez le résultat. Arrêtez le serveur lorsqu’il est terminé et validez vos modifications du contrôle de code source si vous le souhaitez (comme expliqué dans [l’étape 2](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)).

### <a name="question-what-is-purpose-of-the--load-staticfiles--tag"></a>Question : quel est l’objectif de la balise {% load staticfiles %} ?

Réponse : la ligne `{% load staticfiles %}` est nécessaire avant de faire référence aux fichiers statiques dans les éléments tels que `<head>` et `<body>`. Dans l’exemple présenté dans cette section, « staticfiles » fait référence à un ensemble de balises du modèle Django personnalisé. Ceci vous permet d’utiliser la syntaxe `{% static %}` pour faire référence aux fichiers statiques.  Sans `{% load staticfiles %}`, vous verrez une exception lorsque l’application s’exécute.

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>Question : existe-t-il des conventions pour organiser des fichiers statiques ?

Réponse : vous pouvez ajouter d’autres fichiers CSS, JavaScript et HTML dans votre dossier `static` comme vous le souhaitez. Une manière générale d’organiser des fichiers statiques consiste à créer des sous-dossiers nommés `fonts`, `scripts` et `content` (pour les feuilles de style et autres fichiers). Dans chaque cas, n’oubliez pas d’inclure ces dossiers dans le chemin d’accès relatif au fichier dans les références `{% static %}`.

## <a name="step-3-3-add-a-page-to-the-app"></a>Étape 3-3 : ajouter une page à l’application

L’ajout d’une autre page à l’application signifie les éléments suivants :

- Ajouter une fonction de Python qui définit l’affichage.
- Ajouter un modèle pour la balise de la page.
- Ajouter le routage nécessaires au fichier `urls.py` du projet Django.

Les étapes suivantes ajoutent une page « À propos » au projet « HelloDjangoApp » et des liens vers cette page à partir de la page d’accueil :

1. Dans **Explorateur de solutions**, cliquez avec le bouton de droite sur le dossier `templates/HelloDjangoApp`, sélectionnez **Ajouter** > **Nouvel élément**, sélectionnez le modèle d’élément « Page HTML », nommez le fichier `about.html`, puis sélectionnez **OK**.

    > [!Tip]
    > Si la commande **Nouvel élément** n’apparaît pas dans le menu **Ajouter**, vérifiez que vous avez arrêté le serveur afin que Visual Studio quitte le mode Débogage.

1. Remplacez le contenu de `about.html` par la balise suivante (vous remplacez le lien explicite vers la page d’accueil par une barre de navigation simple à l’étape 3-4) :

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            {% load staticfiles %}
            <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
        </head>
        <body>
            <div><a href="home">Home</a></div>
            {{ content }}
        </body>
    </html>
    ```

1. Ouvrez le fichier `views.py` de l’application et ajoutez une fonction nommée `about` qui utilise le modèle :

    ```python
    def about(request):
        return render(
            request,
            "HelloDjangoApp/about.html",
            {
                'title' : "About HelloDjangoApp",
                'content' : "Example app page for Django."
            }
        )
    ```

1. Ouvrez le fichier `urls.py` du projet Django et ajoutez la ligne suivante au tableau `urlPatterns` :

    ```python
    url(r'^about$', HelloDjangoApp.views.about, name='about'),
    ```

1. Ouvrez le fichier `templates/HelloDjangoApp/index.html` et ajoutez la ligne suivante sous l’élément `<body>` à lier à la page À propos (là encore, vous remplacez ce lien par une barre de navigation à l’étape 3-4) :

    ```html
    <div><a href="about">About</a></div>
    ```

1. Enregistrez tous les fichiers à l’aide de la commande de menu **Fichier** > **Enregistrer tout** ou appuyez simplement sur Ctrl + Maj + S. (Techniquement, cette étape n’est pas nécessaire puisque l’exécution du projet dans Visual Studio enregistre automatiquement les fichiers. Toutefois, c’est une commande bonne à connaître !)

1. Exécutez le projet pour observer les résultats et contrôler la navigation entre les pages. Fermez le serveur une fois terminé.

### <a name="question-i-tried-using-index-for-the-link-to-the-home-page-but-it-didnt-work-why"></a>Question : j’ai essayé d’utiliser « index » pour le lien vers la page d’accueil, mais cela n’a pas fonctionné. Pourquoi ?

Réponse : bien que la fonction d’affichage dans `views.py` soit nommée `index`, les modèles de routage d’URL dans le fichier `urls.py` du projet Django ne contient pas une expression régulière qui correspond à la chaîne « index ». Pour faire correspondre cette chaîne, vous devez ajouter une autre entrée pour le modèle `^index$`.

Comme indiqué dans la section suivante, il est préférable d’utiliser la balise `{% url '<pattern_name>' %}` dans le modèle de page pour faire référence au *nom* d’un modèle et dans ce cas Django crée l’URL appropriée pour vous. Par exemple, remplacez `<div><a href="home">Home</a></div>` dans `about.html` par `<div><a href="{% url 'index' %}">Home</a></div>`. L’utilisation « d’index » fonctionne ici, car le premier modèle d’URL dans `urls.py` est, en fait, nommé « index » (en vertu de l’argument `name='index'`). Vous pouvez également utiliser « accueil » pour désigner le second modèle.

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>Étape 3-4 : utiliser l’héritage du modèle pour créer un en-tête et une barre de navigation

Au lieu de liens de navigation explicites sur chaque page, les applications Web modernes utilisent généralement un en-tête de marque et une barre de navigation qui fournit les liens de page, menus contextuels, et ainsi de suite, les plus importants. Pour vous assurer que l’en-tête et la barre de navigation sont les mêmes dans toutes les pages, toutefois, vous ne souhaitez pas répéter le même code dans chaque modèle de page. Au lieu de cela, vous souhaitez définir les parties communes de toutes les pages dans un seul emplacement.

Le système de création de modèles de Django offre deux modes de réutilisation des éléments spécifiques dans plusieurs modèles : fichiers inclus et héritage.

- *Les fichiers inclus* représentent d’autres modèles de pages que vous insérez à un endroit spécifique dans le modèle de référence à l’aide de la syntaxe `{% include <template_path> %}`. Vous pouvez également utiliser une variable si vous souhaitez modifier le chemin d’accès dynamiquement dans le code. Les fichiers inclus sont généralement utilisés dans le corps d’une page pour s’extraire dans le modèle partagé dans un emplacement spécifique de la page.

- *L’héritage* utilise le `{% extends <template_path> %}` au début d’un modèle de page pour spécifier un modèle de base partagé sur lequel le modèle de référence s’appuie ensuite. L’héritage est couramment utilisé pour définir une disposition partagée, la barre de navigation et les autres structures pour les pages d’une application, de sorte que les modèles de référence doivent uniquement ajouter ou modifier des zones spécifiques du modèle de base appelé *blocs*.

Dans les deux cas, `<template_path>` est relatif au dossier `templates` de l’application (`../` ou `./` sont également autorisés).

Un modèle de base délimite les blocs à l’aide des balises `{% block <block_name> %}` et `{% endblock %}`. Si un modèle de référence utilise alors des balises portant le même nom de bloc, le contenu de son bloc remplace celui du modèle de base.

Les étapes suivantes démontrent l’héritage :

1. Dans le dossier `templates/HelloDjangoApp` de l’application, créez un nouveau fichier HTML (à l’aide du menu de contexte **Ajouter** > **Nouvel élément** ou **Ajouter** > **Page HTML**) appelé `layout.html` et collez le contenu ci-dessous. Vous pouvez voir que ce modèle contient un bloc nommé « contenu » qui représente tout ce que les pages de référence doivent remplacer :

    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8" />
        <title>{{ title }}</title>
        {% load staticfiles %}
        <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
    </head>

    <body>
        <div class="navbar">
           <a href="/" class="navbar-brand">Hello Django</a>
           <a href="{% url 'home' %}" class="navbar-item">Home</a>
           <a href="{% url 'about' %}" class="navbar-item">About</a>
        </div>

        <div class="body-content">
    {% block content %}{% endblock %}
            <hr/>
            <footer>
                <p>&copy; 2018</p>
            </footer>
        </div>
    </body>
    </html>
    ```

1. Ajouter les styles suivants au fichier `static/site.css` de l’application (cette procédure pas à pas ne tente pas d’illustrer une conception réactive ici ; ces styles permettent simplement de générer un résultat intéressant) :

    ```css
    .navbar {
        background-color: lightslategray;
        font-size: 1em;
        font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
        color: white;
        padding: 8px 5px 8px 5px;
    }

    .navbar a {
        text-decoration: none;
        color: inherit;
    }

    .navbar-brand {
        font-size: 1.2em;
        font-weight: 600;
    }

    .navbar-item {
        font-variant: small-caps;
        margin-left: 30px;
    }

    .body-content {
        padding: 5px;
        font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }
    ```

1. Modifiez `templates/HelloDjangoApp/index.html` pour faire référence au modèle de base et remplacez le bloc de contenu. Vous pouvez voir cela en utilisant l’héritage, ce modèle devient simple :

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. Modifiez `templates/HelloDjangoApp/about.html` pour faire référence au modèle de base et remplacez le bloc de contenu :

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. Exécutez le serveur et observez le résultat. Fermez le serveur une fois terminé.

    ![Application en cours d’exécution affichant la barre de navigation](media/django/step03-nav-bar.png)

1. Étant donné que vous avez apporté des modifications importantes à l’application, il est temps une fois de plus de [valider vos modifications au contrôle de code source](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Utiliser le modèle de projet Web Django complet](learn-django-in-visual-studio-step-04-full-django-project-template.md)

## <a name="going-deeper"></a>Pour aller plus loin

- [Écrire votre première application Django, partie 3 (affichages)](https://docs.djangoproject.com/en/2.0/intro/tutorial03/) (docs.djangoproject.com)
- Pour davantage de fonctionnalités des modèles Django, tel que le flux de contrôle, consultez [Le langage de gabarit Django](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (docs.djangoproject.com)
- Pour plus d’informations sur l’utilisation de la balise `{% url %}`, consultez [url](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/#url) au sein de [balises du modèle et filtres intégrés pour la référence aux modèles Django](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/) (docs.djangoproject.com)
- Code source du tutoriel sur GitHub : [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)