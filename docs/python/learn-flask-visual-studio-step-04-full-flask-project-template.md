---
title: Tutoriel d’apprentissage de Flask dans Visual Studio - étape 4, modèles de projet web
titleSuffix: ''
description: Une procédure pas à pas montrant les principes de base de Flask dans le contexte de projets Visual Studio, en particulier les fonctionnalités fournies par les modèles Projet web Flask et Projet web Flask/Jade.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: ef9154a34ddd08e7e0a4b9434f7f748b2603aef4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882867"
---
# <a name="step-4-use-the-full-flask-web-project-template"></a>Étape 4 : Utiliser le modèle Projet web Flask complet

**Étape précédente : [servir les fichiers statiques, ajouter des pages et utiliser l’héritage du modèle](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)**

Maintenant que vous avez exploré les concepts de base de Flask en créant une application sur le modèle « Projet d’application Flask vide » dans Visual Studio, vous pouvez facilement comprendre l’application complète qui est produite par le modèle « Projet web Flask ».

Dans cette étape vous pouvez désormais :

> [!div class="checklist"]
> - créer une application web Flask complète en utilisant le modèle « Projet web Flask » et examiner la structure du projet (étape 4-1)
> - comprendre les affichages et les modèles de page créés par le modèle de projet, qui se composent de trois pages héritées d’un modèle de page de base et qui utilisent des bibliothèques JavaScript statiques telles que jQuery et Bootstrap (étape 4-2)
> - comprendre le routage d’URL fourni par le modèle (étape 4-3)

Cet article s’applique également au modèle « Projet web Flask/Jade », qui produit une application identique à celle du « Projet web Flask » en utilisant le moteur de création de modèles Jade au lieu de Jinja. Vous pouvez trouver des détails supplémentaires à la fin de cet article.

## <a name="step-4-1-create-a-project-from-the-template"></a>Étape 4-1 : créer un projet à partir du modèle

1. Dans Visual Studio, accédez à **Explorateur de solutions**, cliquez avec le bouton droit sur la solution **LearningFlask** créée précédemment dans ce didacticiel, puis sélectionnez **Ajouter**  >  **un nouveau projet**. (Sinon, si vous souhaitez utiliser une nouvelle solution, sélectionnez **fichier**  >  **Nouveau**  >  **Projet** à la place.)

1. Dans la boîte de dialogue Nouveau projet, recherchez et sélectionnez le modèle de **projet Web fiole** , appelez le projet « FlaskWeb », puis sélectionnez **OK**.

1. Comme le modèle inclut à nouveau un fichier *requirements.txt*, Visual Studio vous demande où installer ces dépendances. Choisissez l’option, **Installer dans un environnement virtuel** et dans la boîte de dialogue **Ajouter un environnement virtuel**, sélectionnez **Créer** pour accepter les valeurs par défaut.

1. Une fois que Visual Studio a terminé la configuration de l’environnement virtuel, affectez la valeur par défaut au projet **FlaskWeb** pour la solution Visual Studio en cliquant avec le bouton droit sur ce projet dans **Explorateur de solutions** et en sélectionnant **définir comme projet de démarrage**. Le projet de start-up, affiché en gras est ce qui est exécuté lorsque vous démarrez le débogueur.

    ![L’Explorateur de solutions affichant le projet FlaskWeb comme projet de démarrage](media/flask/step04-second-project-in-solution-set-as-startup-project.png)

1. Sélectionnez **Déboguer**  >  **Démarrer le débogage** (**F5**) ou utilisez le bouton **serveur Web** dans la barre d’outils pour exécuter le serveur :

    ![Exécuter le bouton de la barre d’outils du serveur Web dans Visual Studio](media/flask/run-web-server-toolbar-button.png)

1. L’application créée par le modèle dispose de trois pages, Accueil, À propos et Contact, entre lesquelles vous naviguez à l’aide de la barre de navigation. Prenez une minute ou deux pour examiner les différentes parties de l’application. Pour vous authentifier auprès de l’application via la commande **Se connecter**, utilisez les informations d’identification de superutilisateur créées précédemment.

    ![Vue complète du navigateur de l’application Projet web Flask](media/flask/step04-full-app-desktop-view.png)

1. L’application créée par le modèle « Projet web Flask » utilise Bootstrap pour une disposition réactive qui prend en charge les facteurs de formes des mobiles. Pour afficher cette réactivité, redimensionnez le navigateur à un affichage plus étroit afin que le contenu soit affiché verticalement et que la barre de navigation se transforme en icône de menu :

    ![Vue pour mobile (étroite) de l’application Projet web Flask](media/flask/step04-full-app-mobile-view.png)

1. Vous pouvez laisser l’application s’exécuter pour les sections qui suivent.

    Si vous souhaitez arrêter l’application et [valider des modifications dans le contrôle de code source](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control), ouvrez tout d’abord la page **Modifications** dans **Team Explorer**, cliquez avec le bouton droit sur le dossier de l’environnement virtuel (probablement **env**), puis sélectionnez **Ignorer ces éléments locaux**.

### <a name="examine-what-the-template-creates"></a>Examinez ce qui crée le modèle

Le modèle « Projet web Flask » crée la structure ci-dessous. Le contenu est très similaire à ce que vous avez créé dans les étapes précédentes. La différence est que le modèle « Projet web Flask » contient une structure plus importante dans le dossier *static*, car il inclut jQuery et Bootstrap pour une conception réactive. Le modèle ajoute également une page Contact. Globalement, si vous avez suivi les étapes précédentes de ce tutoriel, tout ce qui se trouve dans le modèle doit vous être familier.

- Fichiers dans la racine du projet :
  - *runserver.py*, un script pour exécuter l’application dans un serveur de développement.
  - *requirements.txt*, qui contient une dépendance sur Flask 0.x.
- Le dossier *FlaskWeb* contient tous les fichiers de l’application :
  - init.py marque le code de l’application en tant que module Python, crée l’objet de la fiole et importe les vues de l’application. *\_ \_ \_ \_*
  - *views.py* contient le code pour afficher les pages.
  - Le dossier *static* contient des sous-dossiers nommés *content* (fichiers CSS), *fonts* (fichiers de polices) et *scripts* (fichiers JavaScript).
  - Le dossier *templates* contient un modèle de base *layout.html* avec *about.html*, *contact.html* et *index.html* pour des pages spécifiques qui étendent chacune *layout.html*.

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>Question : est-il possible de partager un environnement virtuel entre des projets Visual Studio ?

Réponse : oui, mais pour ce faire, gardez à l’esprit que différents projets sont susceptibles d’utiliser différents packages au fil du temps et par conséquent, un environnement virtuel partagé doit contenir tous les packages pour tous les projets qui l’utilisent.

Néanmoins, pour utiliser un environnement virtuel existant, procédez comme suit :

1. Lorsque vous êtes invité à installer des dépendances dans Visual Studio, sélectionnez l’option **Je vais les installer moi-même**.
1. Dans **Explorateur de solutions**, cliquez avec le bouton de droite sur le nœud **Environnements Python** et sélectionnez **Ajouter un environnement virtuel existant**.
1. Accédez au dossier contenant l’environnement virtuel et sélectionnez-le, puis sélectionnez **OK**.

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>Étape 4-2 : comprendre les affichages et les modèles de page créés par le modèle de projet

Comme vous pouvez le constater lors de l’exécution du projet, l’application contient trois vues : Accueil, À propos et Contact. Le code de ces affichages se trouve dans le dossier *FlaskWeb/views.py*. Chaque fonction d’une vue appelle simplement `flask.render_template` avec le chemin vers un modèle et une liste variable d’arguments pour les valeurs à donner au modèle. Par exemple, la page About est gérée par la fonction `about` (dont le décorateur fournit le routage d’URL) :

```python
@app.route('/about')
def about():
    """Renders the about page."""
    return render_template(
        'about.html',
        title='About',
        year=datetime.now().year,
        message='Your application description page.'
    )
```

Les fonctions `home` et `contact` sont pratiquement identiques, avec des décorateurs similaires et des arguments légèrement différents.

Les modèles se trouvent dans le dossier *templates* de l’application. Le modèle de base, *layout.html*, est le plus complet. Il fait référence à tous les fichiers statiques nécessaires (JavaScript et CSS), définit un bloc nommé « contenu » que d’autres pages remplacent et fournit un autre bloc nommé « scripts ». Les extraits annotés suivants de *layout.html* affichent ces zones spécifiques :

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />

    <!-- Define a viewport for Bootstrap's responsive rendering -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ title }} - My Flask Application</title>

    <link rel="stylesheet" type="text/css" href="/static/content/bootstrap.min.css" />
    <link rel="stylesheet" type="text/css" href="/static/content/site.css" />
    <script src="/static/scripts/modernizr-2.6.2.js"></script>
</head>

<body>
    <!-- Navbar omitted -->

    <div class="container body-content">
        <!-- "content" block that pages are expected to override -->
        {% block content %}{% endblock %}
        <hr />
        <footer>
            <p>&copy; {{ year }} - My Flask Application</p>
        </footer>
    </div>

    <!-- Additional scripts; use the "scripts" block to add page-specific scripts.  -->
    <script src="/static/scripts/jquery-1.10.2.js"></script>
    <script src="/static/scripts/bootstrap.js"></script>
    <script src="/static/scripts/respond.js"></script>
    {% block scripts %}{% endblock %}

</body>
</html>
```

Les modèles de page individuelle *about.html*, *contact.html* et *index.html* étendent chacun le modèle de base *layout.html*. *about.html* est le plus simple et affiche les balises `{% extends %}` et `{% block content %}` :

```html
{% extends "app/layout.html" %}

{% block content %}

<h2>{{ title }}.</h2>
<h3>{{ message }}</h3>

<p>Use this area to provide additional information.</p>

{% endblock %}
```

*index.html* et *contact.html* utilisent la même structure et fournissent le contenu le plus long dans le bloc « content ».

## <a name="the-flaskjade-web-project-template"></a>Le modèle Projet web Flask/Jade

Comme mentionné au début de cet article, Visual Studio fournit un modèle de « Projet web Flask/Jade », qui crée une application visuellement identique à ce qui est produit par le « Projet web Flask ». La principale différence est qu’il utilise le moteur de création de modèles Jade, qui est une extension de Jinja implémentant les mêmes concepts avec un langage plus concis. Plus précisément, Jade utilise par exemple des mots clés au lieu de balises entre des délimiteurs {% %}, et vous permet de référencer des styles CSS et des éléments HTML en utilisant des mots clés.

Pour activer Jade, le modèle de projet inclut d’abord le package pyjade dans *requirements.txt*.

Le fichier *\_ \_ init \_ \_ . py* de l’application contient une ligne à

```python
app.jinja_env.add_extension('pyjade.ext.jinja.PyJadeExtension')
```

Dans le dossier *templates*, vous voyez des fichiers *.jade* au lieu de modèles *.html*, et les vues dans *views.py* référencent ces fichiers dans leurs appels à `flask.render_template`. Sinon, le code des vues est le même.

Si vous ouvrez un des fichiers *.jade*, vous pouvez voir l’expression plus concise d’un modèle. Par exemple, voici le contenu de *templates/layout.jade* tel qu’il est créé par le modèle « Projet web Flask/Jade » :

```jade
doctype html
html
  head
    meta(charset='utf-8')
    meta(name='viewport', content='width=device-width, initial-scale=1.0')
    title #{title} - My Flask/Jade Application
    link(rel='stylesheet', type='text/css', href='/static/content/bootstrap.min.css')
    link(rel='stylesheet', type='text/css', href='/static/content/site.css')
    script(src='/static/scripts/modernizr-2.6.2.js')
  body
    .navbar.navbar-inverse.navbar-fixed-top
      .container
        .navbar-header
          button.navbar-toggle(type='button', data-toggle='collapse', data-target='.navbar-collapse')
            span.icon-bar
            span.icon-bar
            span.icon-bar
          a.navbar-brand(href='/') Application name
        .navbar-collapse.collapse
          ul.nav.navbar-nav
            li
              a(href='/') Home
            li
              a(href='/about') About
            li
              a(href='/contact') Contact
    .container.body-content
      block content
      hr
      footer
        p &copy; #{year} - My Flask/Jade Application

    script(src='/static/scripts/jquery-1.10.2.js')
    script(src='/static/scripts/bootstrap.js')
    script(src='/static/scripts/respond.js')

    block scripts
```

Et voici le contenu de *templates/about.jade*, qui montre l’utilisation de `#{ <name>}` pour les espaces réservés :

```jade
extends layout

block content
  h2 #{title}.
  h3 #{message}
  p Use this area to provide additional information.
```

N’hésitez pas à faire des essais avec les syntaxes de Jinja et de Jade pour déterminer celle qui fonctionne le mieux pour vous.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Le modèle Projet web Flask de sondage](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md)

## <a name="go-deeper"></a>Approfondir la question

- [Écriture de votre première application Flask, partie 4 - Formulaires et vues génériques](https://docs.djangoproject.com/en/2.0/intro/tutorial04/) (docs.djangoproject.com)
- [Jade sur GitHub (documentation)](https://github.com/liuliqiang/pyjade) (github.com)
- Code source du tutoriel sur GitHub : [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
