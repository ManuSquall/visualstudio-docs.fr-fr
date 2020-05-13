---
title: Tutoriel d’apprentissage de Django à l’étape 4 de Visual Studio, modèle de projet web
titleSuffix: ''
description: Une procédure pas à pas des principes de base de Django dans le contexte de projets Visual Studio, en particulier les fonctionnalités fournies par le modèle de projet Web Django.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c778d830b20797962306700a5af938eb3a3bb142
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "62961680"
---
# <a name="step-4-use-the-full-django-web-project-template"></a>Étape 4 : Utiliser le modèle de projet web Django complet

**Étape précédente : [servir les fichiers statiques, ajouter des pages et utiliser l’héritage du modèle](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)**

Maintenant que vous avez exploré les principes de base de Django en créant une application sur le modèle « Projet web Django vide » dans Visual Studio, vous pouvez facilement comprendre l’application complète qui est produite par le modèle « Projet web Django ».

Dans cette étape vous pouvez désormais :

> [!div class="checklist"]
> - créer une application Web Django complète à l’aide du modèle « Projet Web Django » et examiner la structure de projet (étape 4-1)
> - comprendre les affichages et les modèles de page créés par le modèle de projet, qui se composent de trois pages héritées d’un modèle de page de base et qui utilisent des bibliothèques JavaScript statiques telles que jQuery et Bootstrap (étape 4-2)
> - comprendre le routage d’URL fourni par le modèle (étape 4-3)

Le modèle fournit également l’authentification de base, traitée à l’étape 5.

## <a name="step-4-1-create-a-project-from-the-template"></a>Étape 4-1 : créer un projet à partir du modèle

1. Dans Visual Studio, accédez à **Explorateur de solutions**, cliquez avec le bouton droit sur la solution **LearningDjango** créée précédemment dans ce tutoriel, puis sélectionnez **Ajouter** > **Nouveau projet**. (Alternativement, si vous voulez utiliser une nouvelle solution, sélectionnez **Fichier** > **Nouveau** > **Projet** à la place.)

1. Dans la boîte de dialogue Nouveau projet, recherchez et sélectionnez le modèle **Projet Web Django**, appelez le projet « DjangoWeb » et sélectionnez **OK**.

1. Comme le modèle inclut à nouveau un fichier *requirements.txt*, Visual Studio vous demande où installer ces dépendances. Choisissez l’option, **Installer dans un environnement virtuel** et dans la boîte de dialogue **Ajouter un environnement virtuel**, sélectionnez **Créer** pour accepter les valeurs par défaut.

1. Une fois que Visual Studio a terminé la configuration de l’environnement virtuel, suivez les instructions du fichier *readme.html* qui s’affiche pour créer un superutilisateur Django (c’est-à-dire un administrateur). Il suffit de cliquer sur le projet Visual Studio et de sélectionner la commande **Python** > **Django Créer Superuser,** puis suivez les invites. Veillez à enregistrer votre nom d’utilisateur et mot de passe lorsque vous l’utilisez en exerçant les fonctionnalités d’authentification de l’application.

1. Définissez le projet **DjangoWeb** selon la valeur par défaut pour la solution Visual Studio en cliquant avec le bouton droit sur ce projet dans **Explorateur de solutions** et en sélectionnant **Définir en tant que projet de start-up**. Le projet de start-up, affiché en gras est ce qui est exécuté lorsque vous démarrez le débogueur.

    ![Explorateur de solutions affichant le projet DjangoWeb en tant que projet de start-up](media/django/step04-second-project-in-solution-set-as-startup-project.png)

1. Sélectionnez **Debug** > **Start Debugging** (**F5**) ou utilisez le bouton **Serveur Web** sur la barre d’outils pour faire fonctionner le serveur :

    ![Exécuter le bouton de la barre d’outils du serveur Web dans Visual Studio](media/django/run-web-server-toolbar-button.png)

1. L’application créée par le modèle dispose de trois pages, Accueil, À propos et Contact, entre lesquelles vous naviguez à l’aide de la barre de navigation. Prenez une minute ou deux pour examiner les différentes parties de l’application. Pour vous authentifier auprès de l’application via la commande **Se connecter**, utilisez les informations d’identification de superutilisateur créées précédemment.

    ![Affichage complet du navigateur de l’application du Projet Web Django](media/django/step04-full-app-desktop-view.png)

1. L’application créée par le modèle « Projet Web Django » utilise Bootstrap pour une disposition réactive qui prend en charge les facteurs de forme mobiles. Pour afficher cette réactivité, redimensionnez le navigateur à un affichage plus étroit afin que le contenu soit affiché verticalement et que la barre de navigation se transforme en icône de menu :

    ![Affichage mobile (étroit) de l’application du Projet Web Django](media/django/step04-full-app-mobile-view.png)

1. Vous pouvez laisser l’application s’exécuter pour les sections qui suivent.

    Si vous souhaitez arrêter l’application et [valider des modifications dans le contrôle de code source](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control), ouvrez tout d’abord la page **Modifications** dans **Team Explorer**, cliquez avec le bouton droit sur le dossier de l’environnement virtuel (probablement **env**), puis sélectionnez **Ignorer ces éléments locaux**.

### <a name="examine-what-the-template-creates"></a>Examinez ce qui crée le modèle

Au niveau le plus large, le modèle « Projet Web de Django » crée la structure suivante :

- Fichiers dans la racine du projet :
  - *manage.py*, l’utilitaire d’administration Django.
  - *db.sqlite3*, une base de données SQLite par défaut.
  - *requirements.txt*, qui contient une dépendance sur Django 1.x.
  - *readme.html*, un fichier qui s’affiche dans Visual Studio après avoir créé le projet. Comme indiqué dans la section précédente, suivez les instructions suivantes pour créer un compte de superutilisateur (administrateur) pour l’application.
- Le dossier *app* contient tous les fichiers d’application, y compris les affichages, modèles, tests, formulaires et fichiers statiques (voir l’étape 4-2). En règle générale, vous renommez ce dossier pour utiliser un nom d’application plus significatif.
- Le dossier *DjangoWeb* (projet Django) contient les fichiers typiques du projet Django : * \_ \_\_\_init .py*, *settings.py*, *urls.py*, et *wsgi.py*. À l’aide du modèle de projet, *settings.py* est déjà configuré pour l’application et le fichier de base de données, et *urls.py* est déjà configuré avec des routes pour toutes les pages d’application, y compris le formulaire de connexion.

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>Question : est-il possible de partager un environnement virtuel entre des projets Visual Studio ?

Réponse : oui, mais pour ce faire, gardez à l’esprit que différents projets sont susceptibles d’utiliser différents packages au fil du temps et par conséquent, un environnement virtuel partagé doit contenir tous les packages pour tous les projets qui l’utilisent.

Néanmoins, pour utiliser un environnement virtuel existant, procédez comme suit :

1. Lorsque vous êtes invité à installer des dépendances dans Visual Studio, sélectionnez l’option **Je vais les installer moi-même**.
1. Dans **Explorateur de solutions**, cliquez avec le bouton de droite sur le nœud **Environnements Python** et sélectionnez **Ajouter un environnement virtuel existant**.
1. Accédez au dossier contenant l’environnement virtuel et sélectionnez-le, puis sélectionnez **OK**.

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>Étape 4-2 : comprendre les affichages et les modèles de page créés par le modèle de projet

Comme vous pouvez le constater lors de l’exécution du projet, l’application contient trois vues : Accueil, À propos et Contact. Le code de ces affichages se trouve dans le dossier *app/views*. Chaque fonction de l’affichage appelle simplement `django.shortcuts.render` avec le chemin d’accès d’un modèle et un objet de dictionnaire simple. Par exemple, la page À propos est gérée par la fonction `about` :

```python
def about(request):
    """Renders the about page."""
    assert isinstance(request, HttpRequest)
    return render(
        request,
        'app/about.html',
        {
            'title':'About',
            'message':'Your application description page.',
            'year':datetime.now().year,
        }
    )
```

Les modèles sont situés dans le dossier *templates/app* de l’application (et vous souhaitez généralement renommer *app* par le nom de votre application réelle). Le modèle de base, *layout.html*, est le plus complet. Il fait référence à tous les fichiers statiques nécessaires (JavaScript et CSS), définit un bloc nommé « contenu » que d’autres pages remplacent et fournit un autre bloc nommé « scripts ». Les extraits annotés suivants de *layout.html* affichent ces zones spécifiques :

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />

    <!-- Define a viewport for Bootstrap's responsive rendering -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ title }} - My Django Application</title>

    {% load staticfiles %}
    <link rel="stylesheet" type="text/css" href="{% static 'app/content/bootstrap.min.css' %}" />
    <link rel="stylesheet" type="text/css" href="{% static 'app/content/site.css' %}" />
    <script src="{% static 'app/scripts/modernizr-2.6.2.js' %}"></script>
</head>
<body>
    <!-- Navbar omitted -->

    <div class="container body-content">

<!-- "content" block that pages are expected to override -->
{% block content %}{% endblock %}
        <hr/>
        <footer>
            <p>&copy; {{ year }} - My Django Application</p>
        </footer>
    </div>

<!-- Additional scripts; use the "scripts" block to add page-specific scripts.  -->
    <script src="{% static 'app/scripts/jquery-1.10.2.js' %}"></script>
    <script src="{% static 'app/scripts/bootstrap.js' %}"></script>
    <script src="{% static 'app/scripts/respond.js' %}"></script>
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

Dans le dossier *templates/app* se trouve également une quatrième page *login.html*, avec *loginpartial.html* qui est importée dans *layout.html* à l’aide de `{% include %}`. Ces fichiers de modèle sont décrits à l’étape 5 sur l’authentification.

### <a name="question-can--block--and--endblock--be-indented-in-the-django-page-template"></a>Question : {% block %} et {% endblock %} peuvent-ils être mis en retrait dans le modèle de page Django ?

Réponse : oui, les modèles de page Django fonctionnent bien si vous mettez en retrait des balises de bloc, par exemple pour les aligner dans leurs éléments parents appropriés. Ils ne sont pas mis en retrait dans les modèles de page générés par le modèle de projet Visual Studio afin que vous puissiez voir clairement où ils sont placés.

## <a name="step-4-3-understand-the-url-routing-created-by-the-template"></a>Étape 4-3 : comprendre le routage d’URL créé par le modèle

Le fichier *urls.py* du projet Django, tel que créé par le modèle « Projet Web Django », contient le code suivant :

```python
from datetime import datetime
from django.conf.urls import url
import django.contrib.auth.views

import app.forms
import app.views

urlpatterns = [
    url(r'^$', app.views.home, name='home'),
    url(r'^contact$', app.views.contact, name='contact'),
    url(r'^about$', app.views.about, name='about'),
    url(r'^login/$',
        django.contrib.auth.views.login,
        {
            'template_name': 'app/login.html',
            'authentication_form': app.forms.BootstrapAuthenticationForm,
            'extra_context':
            {
                'title': 'Log in',
                'year': datetime.now().year,
            }
        },
        name='login'),
    url(r'^logout$',
        django.contrib.auth.views.logout,
        {
            'next_page': '/',
        },
        name='logout'),
]
```

Les trois premiers modèles de l’URL mappent directement aux affichages `home`, `contact` et `about` dans le fichier *views.py* de l’application. Les modèles `^login/$` et `^logout$`, d’autre part, utilisent des affichages Django intégrés au lieu des affichages définis par l’application. Les appels à la méthode `url` incluent également des données supplémentaires pour personnaliser l’affichage. L’étape 5 explore ces appels.

### <a name="question-in-the-project-i-created-why-does-the-about-url-pattern-uses-about-instead-of-about-as-shown-here"></a>Question : Dans le projet que j’ai créé, pourquoi le modèle d’URL « À propos » utilise-t-il '^about' plutôt que '^about$' comme indiqué ici ?

Réponse : l’absence du symbole de fin « $ » dans l’expression régulière est une simple omission dans de nombreuses versions du modèle de projet. Le modèle d’URL fonctionne parfaitement pour une page nommée « à propos », mais sans le symbole de fin « $ » le modèle d’URL correspond également aux URL comme « about=django », « about09876 », « aboutoflaughter », etc. Le symbole de fin « $ » est affiché ici pour créer un modèle d’URL qui correspond *uniquement* à « à propos ».

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Authentifier les utilisateurs dans Django](learn-django-in-visual-studio-step-05-django-authentication.md)

## <a name="go-deeper"></a>Approfondir la question

- [Déployer l’application web sur Azure App Service.](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Écrire votre première application Django, partie 4 - formulaires et affichages génériques](https://docs.djangoproject.com/en/2.0/intro/tutorial04/) (docs.djangoproject.com)
- Code source du tutoriel sur GitHub : [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
