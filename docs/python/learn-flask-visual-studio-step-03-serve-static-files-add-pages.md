---
title: Tutoriel d’apprentissage de Flask dans Visual Studio - étape 3, pages et fichiers statiques
titleSuffix: ''
description: Une procédure pas à pas montrant les concepts de base de Flask dans le contexte de projets Visual Studio, expliquant en particulier comment prendre en charge des fichiers statiques, ajouter des pages à l’application et utiliser l’héritage de modèle
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: d474236aca50a74b96689001a56e7d0701caae30
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942384"
---
# <a name="step-3-serve-static-files-add-pages-and-use-template-inheritance-with-flask-app"></a>Étape 3 : traiter les fichiers statiques, ajouter des pages et utiliser l’héritage de modèle avec l’application de la fiole

**Étape précédente : [Créer une application Flask avec des vues et des modèles de page](learn-flask-visual-studio-step-02-create-app.md)**

Dans les étapes précédentes de ce tutoriel, vous avez découvert comment créer une application Flask minimale avec une seule page HTML autonome. Les applications web modernes sont cependant composées en général de nombreuses pages et utilisent des ressources partagées, comme des fichiers CSS et JavaScript, pour offrir un comportement et un style cohérents.

Dans cette étape, vous apprenez comment :

> [!div class="checklist"]
> - Utiliser des modèles d’élément Visual Studio pour ajouter rapidement de nouveaux fichiers de types différents avec un code réutilisable pratique (étape 3-1)
> - Produire des fichiers statiques à partir du code (étape 3-2, facultative)
> - ajoutez des pages supplémentaires à l’application (étape 3-3)
> - utiliser l’héritage de modèle pour créer un en-tête et une barre de navigation utilisés sur plusieurs pages (étape 3-4)

## <a name="step-3-1-become-familiar-with-item-templates"></a>Étape 3-1 : se familiariser avec les modèles d’élément

Quand vous développez une application Flask, vous ajoutez généralement beaucoup plus de fichiers Python, HTML, CSS et JavaScript. Pour chaque type de fichier (ainsi que d’autres fichiers tels que *web.config* dont vous pouvez avoir besoin pour le déploiement), Visual Studio fournit des [modèles d’élément](python-item-templates.md) pratiques pour bien commencer.

Pour afficher les modèles disponibles, accédez à **Explorateur de solutions**, cliquez avec le bouton de droite sur le dossier dans lequel vous souhaitez créer l’élément, sélectionnez **Ajouter** > **Nouvel élément** :

![Boîte de dialogue Ajouter nouvel élément dans Visual Studio](media/flask/step03-add-new-item-dialog.png)

Pour utiliser un modèle, sélectionnez le modèle souhaité, spécifiez un nom pour le fichier et sélectionnez **OK**. L’ajout d’un élément de cette manière permet d’ajouter automatiquement le fichier à votre projet Visual Studio et marque les modifications du contrôle de code source.

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>Question : comment Visual Studio sait quel modèle d’élément proposer ?

Réponse : le fichier projet Visual Studio (*.pyproj*) contient un identificateur de type de projet qui le marque comme projet Python. Visual Studio utilise cet identificateur de type pour afficher uniquement les modèles d’élément qui conviennent pour le type de projet. De cette manière, Visual Studio peut fournir un ensemble riche de modèles d’élément pour plusieurs types de projet sans vous demander de les trier à chaque fois.

## <a name="step-3-2-serve-static-files-from-your-app"></a>Étape 3-2 : prendre en charge les fichiers statiques à partir de votre application

Dans une application Web générée avec Python (à l’aide de n’importe quelle infrastructure), vos fichiers Python s’exécutent toujours sur le serveur de l’hôte Web et ne sont jamais transmis à l’ordinateur d’un utilisateur. D’autres fichiers, cependant, tels que CSS et JavaScript, sont utilisés exclusivement par le navigateur, afin que le serveur hôte les remette simplement tel-quel à chaque fois qu’ils sont demandés. Ces fichiers sont appelés des fichiers « statiques » et Flask peut les produire automatiquement sans que vous ayez besoin d’écrire du code. Dans les fichiers HTML, vous pouvez par exemple référencer des fichiers statiques en utilisant seulement un chemin relatif dans le projet. La première section de cette étape ajoute un fichier CSS à votre modèle de page existant.

Quand vous avez besoin de produire un fichier statique à partir du code, comme via une implémentation d’un point de terminaison d’API, Flask fournit une méthode pratique qui vous permet de référencer des fichiers en utilisant des chemins relatifs au sein d’un dossier nommé *static* (à la racine du projet). La deuxième section de cette étape montre comment utiliser cette méthode avec un fichier de données statique simple.

Dans les deux cas, vous pouvez organiser les fichiers comme vous le souhaitez sous *static*.

### <a name="use-a-static-file-in-a-template"></a>Utiliser un fichier statique dans un modèle

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le dossier **HelloFlask** dans le projet Visual Studio, sélectionnez **Ajouter** > **Nouveau dossier** et nommez le dossier `static`.

1. Cliquez avec le bouton droit sur le dossier **static** et sélectionnez **Ajouter** > **Nouvel élément**. Dans la boîte de dialogue qui s’affiche, sélectionnez le modèle de **feuille de style** , nommez le fichier `site.css` , puis sélectionnez **OK**. Le fichier **site.css** apparaît dans le projet et est ouvert dans l’éditeur. Votre structure de dossiers doit apparaître semblable à l’image suivante :

    ![Structure de fichier statique comme indiqué dans l’Explorateur de solutions](media/flask/step03-static-file-structure.png)

1. Remplacez le contenu de *site.css* par le code suivant et enregistrez le fichier :

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. Remplacez le contenu du fichier *templates/index.html* de l’application par le code suivant, qui remplace l’élément `<strong>` utilisé à l’étape 2 par un `<span>` qui fait référence à la classe de style `message`. Une telle utilisation d’une classe de style vous offre davantage de flexibilité dans l’ajout des styles à l’élément.

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            <link rel="stylesheet" type="text/css" href="/static/site.css" />
        </head>
        <body>
            <span class="message">{{ message }}</span>{{ content }}
        </body>
    </html>
    ```

1. Exécutez le projet et observez le résultat. Arrêtez l’application quand c’est terminé et si vous le souhaitez, validez vos modifications auprès du contrôle de code source (comme expliqué dans [l’étape 2](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control)).

### <a name="serve-a-static-file-from-code"></a>Produire un fichier statique à partir du code

Flask fournit une fonction appelée `serve_static_file`, que vous pouvez appeler à partir du code pour référencer n’importe quel fichier au sein du dossier *static* du projet. Le processus suivant crée un point de terminaison d’API simple qui retourne un fichier de données statiques.

1. Si ce n’est déjà fait, créez un dossier *static* : dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le dossier **HelloFlask** dans le projet Visual Studio, sélectionnez **Ajouter** > **Nouveau dossier** et nommez le dossier `static`.

1. Dans le dossier *static*, créez un fichier de données JSON statique nommé *data.json*, avec le contenu suivant (qui est un exemple de données sans signification) :

    ```json
    {
        "01": {
            "note" : "Data is very simple because we're demonstrating only the mechanism."
        }
    }
    ```

1. Dans *views.py*, ajoutez une fonction avec la route /api/data qui retourne le fichier de données statique en utilisant la méthode `send_static_file` :

    ```python
    @app.route('/api/data')
    def get_data():
      return app.send_static_file('data.json')
    ```

1. Exécutez l’application et accédez au point de terminaison /api/data pour constater que le fichier statique est retourné. Arrêtez l’application quand vous avez terminé.

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>Question : Existe-t-il des conventions pour organiser des fichiers statiques ?

Réponse : vous pouvez ajouter d’autres fichiers CSS, JavaScript et HTML dans votre dossier *static* comme vous le souhaitez. Une façon classique d’organiser des fichiers statiques consiste à créer des sous-dossiers nommés *fonts*, *scripts* et *content* (pour les feuilles de style et autres fichiers).

### <a name="question-how-do-i-handle-url-variables-and-query-parameters-in-an-api"></a>Question : Comment gérer les variables d’URL et les paramètres de requête dans une API ?

Réponse : Reportez-vous à la réponse donnée à l’étape 1-4 pour [Question : Comment Flask fonctionne-t-il avec les routes d’URL et les paramètres de requête des variables ?](learn-flask-visual-studio-step-01-project-solution.md#qa-url-variables)

## <a name="step-3-3-add-a-page-to-the-app"></a>Étape 3-3 : ajouter une page à l’application

L’ajout d’une autre page à l’application signifie les éléments suivants :

- Ajouter une fonction de Python qui définit l’affichage.
- Ajouter un modèle pour la balise de la page.
- Ajouter le routage nécessaire au fichier *urls.py* du projet Flask.

Les étapes suivantes ajoutent une page « About » au projet « HelloFlask » et des liens vers cette page depuis la page d’accueil :

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le dossier **templates**, sélectionnez **Ajouter** > **Nouvel élément**, sélectionnez le modèle d’élément **Page HTML**, nommez le fichier `about.html`, puis sélectionnez **OK**.

    > [!Tip]
    > Si la commande **Nouvel élément** n’apparaît pas dans le menu **Ajouter**, vérifiez que vous avez arrêté l’application pour que Visual Studio quitte le mode Débogage.

1. Remplacez le contenu de *about.html* par le balisage suivant (vous remplacez le lien explicite vers la page d’accueil par une barre de navigation simple à l’étape 3-4) :

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            <link rel="stylesheet" type="text/css" href="/static/site.css" />
        </head>
        <body>
            <div><a href="home">Home</a></div>
            {{ content }}
        </body>
    </html>
    ```

1. Ouvrez le fichier *views.py* de l’application et ajoutez une fonction nommée `about` qui utilise le modèle :

    ```python
    @app.route('/about')
    def about():
        return render_template(
            "about.html",
            title = "About HelloFlask",
            content = "Example app page for Flask.")
    ```

1. Ouvrez le fichier *templates/index.html* et ajoutez la ligne suivante immédiatement dans l’élément `<body>` à lier à la page About (notez à nouveau que vous remplacez ce lien par une barre de navigation à l’étape 3-4) :

    ```html
    <div><a href="about">About</a></div>
    ```

1. Enregistrez tous les fichiers à l’aide de la commande de menu **fichier**  >  **enregistrer tout** ou appuyez simplement sur **CTRL** + **MAJ** + **S**. (Techniquement, cette étape n’est pas nécessaire puisque l’exécution du projet dans Visual Studio enregistre automatiquement les fichiers. Toutefois, c’est une commande bonne à connaître !)

1. Exécutez le projet pour observer les résultats et contrôler la navigation entre les pages. Arrêtez l’application quand c’est terminé.

### <a name="question-does-the-name-of-a-page-function-matter-to-flask"></a>Question : Est-ce que le nom d’une fonction de page compte pour Flask ?

Réponse : Non, car c’est le décorateur `@app.route` qui détermine les URL pour lesquelles Flask appelle la fonction de façon à générer une réponse. Les développeurs font généralement correspondre le nom de la fonction à la route, mais cette correspondance n’est pas obligatoire.

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>Étape 3-4 : utiliser l’héritage du modèle pour créer un en-tête et une barre de navigation

Au lieu de liens de navigation explicites sur chaque page, les applications Web modernes utilisent généralement un en-tête de marque et une barre de navigation qui fournit les liens de page, menus contextuels, et ainsi de suite, les plus importants. Pour vous assurer que l’en-tête et la barre de navigation sont les mêmes dans toutes les pages, toutefois, vous ne souhaitez pas répéter le même code dans chaque modèle de page. Au lieu de cela, vous souhaitez définir les parties communes de toutes les pages dans un seul emplacement.

Le système de création de modèles de Flask offre deux moyens de réutiliser des éléments spécifiques dans plusieurs modèles : les fichiers include et l’héritage.

- *Les fichiers inclus* représentent d’autres modèles de pages que vous insérez à un endroit spécifique dans le modèle de référence à l’aide de la syntaxe `{% include <template_path> %}`. Vous pouvez également utiliser une variable si vous souhaitez modifier le chemin d’accès dynamiquement dans le code. Les fichiers inclus sont généralement utilisés dans le corps d’une page pour s’extraire dans le modèle partagé dans un emplacement spécifique de la page.

- *L’héritage* utilise le `{% extends <template_path> %}` au début d’un modèle de page pour spécifier un modèle de base partagé sur lequel le modèle de référence s’appuie ensuite. L’héritage est couramment utilisé pour définir une disposition partagée, la barre de navigation et les autres structures pour les pages d’une application, de sorte que les modèles de référence doivent uniquement ajouter ou modifier des zones spécifiques du modèle de base appelé *blocs*.

Dans les deux cas, `<template_path>` est relatif au dossier *templates* de l’application (`../` ou `./` sont également autorisés).

Un modèle de base délimite les *blocs* à l’aide `{% block <block_name> %}` de `{% endblock %}` balises et. Si un modèle de référence utilise ensuite des étiquettes portant le même nom de bloc, le contenu de son bloc remplace celui du modèle de base.

Les étapes suivantes démontrent l’héritage :

1. Dans le dossier *templates* de l’application, créez un fichier HTML (en utilisant le menu contextuel **Ajouter** > **Nouvel élément** ou **Ajouter** > **Page HTML**) nommé *layout.html* et remplacez son contenu par le balisage ci-dessous. Vous pouvez voir que ce modèle contient un bloc nommé « contenu » qui représente tout ce que les pages de référence doivent remplacer :

    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8" />
        <title>{{ title }}</title>
        <link rel="stylesheet" type="text/css" href="/static/site.css" />
    </head>

    <body>
        <div class="navbar">
            <a href="/" class="navbar-brand">Hello Flask</a>
            <a href="{{ url_for('home') }}" class="navbar-item">Home</a>
            <a href="{{ url_for('about') }}" class="navbar-item">About</a>
        </div>

        <div class="body-content">
            {% block content %}
            {% endblock %}
            <hr/>
            <footer>
                <p>&copy; 2018</p>
            </footer>
        </div>
    </body>
    </html>
    ```

1. Ajouter les styles suivants au fichier *static/site.css* de l’application (cette procédure pas à pas ne tente pas d’illustrer une conception réactive ici ; ces styles permettent simplement de générer un résultat intéressant) :

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

1. Modifiez *templates/index.html* pour faire référence au modèle de base et remplacer le bloc de contenu. Vous pouvez voir cela en utilisant l’héritage, ce modèle devient simple :

    ```html
    {% extends "layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. Modifiez *templates/about.html* pour faire également référence au modèle de base et remplacer le bloc de contenu :

    ```html
    {% extends "layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. Exécutez le serveur et observez le résultat. Fermez le serveur une fois terminé.

    ![Application en cours d’exécution affichant la barre de navigation](media/flask/step03-nav-bar.png)

1. Comme vous avez apporté des modifications importantes à l’application, vous pouvez à nouveau [valider vos modifications auprès du contrôle de code source](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Utiliser le modèle de projet web Flask complet](learn-flask-visual-studio-step-04-full-flask-project-template.md)

## <a name="go-deeper"></a>Approfondir la question

- [Déployer l’application web sur Azure App Service.](publishing-python-web-applications-to-azure-from-visual-studio.md)
- Pour plus d’informations sur les fonctionnalités des modèles Jinja, comme les flux de contrôle, consultez la [documentation du concepteur de modèle Jinja](http://jinja.palletsprojects.com/en/2.10.x/templates/) (jinja.pocoo.org)
- Pour plus d’informations sur l’utilisation de `url_for`, consultez [url_for](https://flask.palletsprojects.com/en/1.0.x/api/#flask.url_for) dans la documentation de l’objet d’application Flask (flask.pocoo.org)
- Code source du tutoriel sur GitHub : [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
