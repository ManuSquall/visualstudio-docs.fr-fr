---
title: Tutoriel d’apprentissage de Django dans Visual Studio, étape 5, authentification
titleSuffix: ''
description: Une procédure pas à pas des principes de base de Django dans le contexte de projets Visual Studio, en particulier les fonctionnalités d’authentification comme fournies par les modèles de projet Web Django.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 3f589aed953a852cb57570988d914f77b2fa10b2
ms.sourcegitcommit: f1dff6c4532c43b0444aa12ea57e90bb7dba6fba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104806015"
---
# <a name="step-5-authenticate-users-in-django"></a>Étape 5 : Authentifier les utilisateurs dans Django

**Étape précédente : [utiliser le modèle de projet Web Django complet](learn-django-in-visual-studio-step-04-full-django-project-template.md)**

::: moniker range="vs-2017"
Étant donné que l’authentification est un besoin courant pour les applications Web, le modèle « Projet Web de Django » contient un flux de l’authentification de base. (Le modèle de « projet Web Django d’interrogation » abordé à l’étape 6 de ce didacticiel comprend également le même fluide.) Lorsque vous utilisez l’un des modèles de projet Django, Visual Studio comprend tous les modules nécessaires pour l’authentification dans le *Settings.py* du projet Django.
::: moniker-end

::: moniker range=">=vs-2019"
Étant donné que l’authentification est un besoin courant pour les applications Web, le modèle « Projet Web de Django » contient un flux de l’authentification de base. Quand vous utilisez un des modèles de projet Django, Visual Studio inclut tous les modules nécessaires pour l’authentification dans le script *settings.py* du projet Django.
::: moniker-end

Dans cette étape vous apprenez :

> [!div class="checklist"]
> - à utiliser le flux d’authentification fourni dans les modèles Visual Studio (étape 5-1)

## <a name="step-5-1-use-the-authentication-flow"></a>Étape 5-1 : utiliser le flux d’authentification

Les étapes suivantes exécutent le flux d’authentification et décrivent les parties du projet qui sont impliquées :

1. Si vous n’avez pas déjà suivi les instructions du fichier *readme.html* dans la racine du projet pour créer un compte de superutilisateur (administrateur), faites-le maintenant.

1. Exécutez l’application à partir de Visual Studio à **l’aide du débogage**  >  **Démarrer le débogage** (**F5**). Lorsque l’application s’affiche dans le navigateur, observez que **Connecter** s’affiche dans le coin supérieur droit de la barre de navigation.

    ![Contrôle de connexion dans la page d’application du projet Web Django](media/django/step05-login-control.png)

1. Ouvrez *templates/app/layout.html* et remarquez que l’élément `<div class="navbar ...>` contient la balise `{% include app/loginpartial.html %}`. La balise `{% include %}` indique au système de création de modèles de Django d’extraire le contenu du fichier inclus à ce stade dans le modèle contenant.

1. Ouvrez *templates/app/loginpartial.html* et observez l’utilisation de la balise conditionnelle `{% if user.is_authenticated %}` avec une balise `{% else %}` pour afficher les différents éléments d’interface utilisateur en fonction de l’authentification de l’utilisateur ou non :

    ```html
    {% if user.is_authenticated %}
    <form id="logoutForm" action="/logout" method="post" class="navbar-right">
        {% csrf_token %}
        <ul class="nav navbar-nav navbar-right">
            <li><span class="navbar-brand">Hello {{ user.username }}!</span></li>
            <li><a href="javascript:document.getElementById('logoutForm').submit()">Log off</a></li>
        </ul>
    </form>

    {% else %}

    <ul class="nav navbar-nav navbar-right">
        <li><a href="{% url 'login' %}">Log in</a></li>
    </ul>

    {% endif %}
    ```

1. Étant donné qu’aucun utilisateur n’est authentifié lors du premier démarrage de l’application, ce code de modèle affiche uniquement le lien « Se connecter » vers la « connexion » du chemin relatif. Comme spécifié dans *urls.py* (comme indiqué dans la section précédente), cette route est mappée à la vue `django.contrib.auth.views.login`. Cette vue reçoit les données suivantes :

    ```python
    {
        'template_name': 'app/login.html',
        'authentication_form': app.forms.BootstrapAuthenticationForm,
        'extra_context':
        {
            'title': 'Log in',
            'year': datetime.now().year,
        }
    }
    ```

    Ici, `template_name` identifie le modèle pour la page de connexion, dans ce cas *templates/app/login.html*. La propriété `extra_context` est ajoutée aux données de contexte par défaut fournies au modèle. Enfin, `authentication_form` spécifie une classe de formulaire à utiliser avec la connexion ; dans le modèle, elle apparaît en tant qu’objet `form`. La valeur par défaut est `AuthenticationForm` (à partir de `django.contrib.auth.views`) ; à la place, le modèle de projet Visual Studio utilise le formulaire défini dans le fichier *forms.py* de l’application :

    ```python
    from django import forms
    from django.contrib.auth.forms import AuthenticationForm
    from django.utils.translation import ugettext_lazy as _

    class BootstrapAuthenticationForm(AuthenticationForm):
        """Authentication form which uses boostrap CSS."""
        username = forms.CharField(max_length=254,
                                   widget=forms.TextInput({
                                       'class': 'form-control',
                                       'placeholder': 'User name'}))
        password = forms.CharField(label=_("Password"),
                                   widget=forms.PasswordInput({
                                       'class': 'form-control',
                                       'placeholder':'Password'}))
    ```

    Comme vous pouvez le voir, cette classe de formulaire dérive de `AuthenticationForm` et remplace en particulier les champs nom d’utilisateur et mot de passe pour ajouter du texte d’espace réservé. Le modèle Visual Studio inclut ce code explicit sur l’hypothèse que vous souhaiterez probablement personnaliser le formulaire, tels que l’ajout d’une validation de force du mot de passe.

1. Quand vous accédez à la page de connexion, l’application affiche alors le modèle *login.html*. Les variables `{{ form.username }}` et `{{ form.password }}` affichent les formulaires `CharField` à partir de `BootstrapAuthenticationForm`. Il existe également une section intégrée pour afficher les erreurs de validation et un élément prêts à l’emploi pour les connexions sociales si vous choisissez d’ajouter ces services.

    ```html
    {% extends "app/layout.html" %}

    {% block content %}

    <h2>{{ title }}</h2>
    <div class="row">
        <div class="col-md-8">
            <section id="loginForm">
                <form action="." method="post" class="form-horizontal">
                    {% csrf_token %}
                    <h4>Use a local account to log in.</h4>
                    <hr />
                    <div class="form-group">
                        <label for="id_username" class="col-md-2 control-label">User name</label>
                        <div class="col-md-10">
                            {{ form.username }}
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="id_password" class="col-md-2 control-label">Password</label>
                        <div class="col-md-10">
                            {{ form.password }}
                        </div>
                    </div>
                    <div class="form-group">
                        <div class="col-md-offset-2 col-md-10">
                            <input type="hidden" name="next" value="/" />
                            <input type="submit" value="Log in" class="btn btn-default" />
                        </div>
                    </div>
                    {% if form.errors %}
                    <p class="validation-summary-errors">Please enter a correct user name and password.</p>
                    {% endif %}
                </form>
            </section>
        </div>
        <div class="col-md-4">
            <section id="socialLoginForm"></section>
        </div>
    </div>

    {% endblock %}
    ```

1. Quand vous envoyez le formulaire, Django tente d’authentifier vos informations d’identification (par exemple, les informations d’identification du superutilisateur). Si l’authentification échoue, vous restez sur la page actuelle, mais `form.errors` a la valeur true. Si l’authentification réussit, Django navigue vers l’URL relative dans le champ « suivant », `<input type="hidden" name="next" value="/" />`, qui est dans ce cas la page d’accueil (`/`).

1. Désormais, quand la page d’accueil est réaffichée, la propriété `user.is_authenticated` est définie sur true quand le modèle *loginpartial.html* est affiché. Ainsi, vous consultez un message **Bonjour (nom d’utilisateur)** et **Se déconnecter**. Vous pouvez utiliser `user.is_authenticated` dans d’autres parties de l’application pour vérifier l’authentification.

    ![Message d’accueil et contrôle de fermeture de session dans la page d’application du projet Web Django](media/django/step05-logoff-control.png)

1. Pour vérifier si l’utilisateur authentifié est autorisé à accéder aux ressources spécifiques, vous devez récupérer les autorisations spécifiques à l’utilisateur à partir de votre base de données. Pour plus d’informations, consultez [Utilisation du système d’authentification Django](https://docs.djangoproject.com/en/2.0/topics/auth/default/#permissions-and-authorization) (documents Django).

1. Le superutilisateur ou l’administrateur, en particulier, est autorisé à accéder aux interfaces d’administrateur intégrées Django à l’aide des URL relatives « /admin/ » et « /admin/doc/ ». Pour activer ces interfaces, effectuez ce qui suit :

    1. Installez le package Python docutils dans votre environnement. Pour y parvenir, ajoutez « docutils » à votre fichier *requirements.txt*, puis dans l’**Explorateur de solutions**, développez le projet, développez le nœud **Environnements Python**, puis cliquez avec le bouton droit sur l’environnement utilisé et sélectionnez **Installer à partir de requirements.txt**.

    1. Ouvrez le fichier *urls.py* du projet Django, puis supprimez les commentaires par défaut des entrées suivantes :

        ```python
        from django.conf.urls import include
        from django.contrib import admin
        admin.autodiscover()

        # ...
        urlpatterns = [
            # ...
            url(r'^admin/doc/', include('django.contrib.admindocs.urls')),
            url(r'^admin/', include(admin.site.urls)),
        ]
        ```

    1. Dans le fichier *settings.py* du projet Django, accédez à la collection `INSTALLED_APPS` et ajoutez `'django.contrib.admindocs'`.

    1. Quand vous redémarrez l’application, vous pouvez accéder à « /admin/ » et « /admin/doc/ », et effectuer des tâches telles que la création de comptes d’utilisateurs supplémentaires.

        ![Interface de l’administrateur Django](media/django/step05-administrator-interface.png)

1. La dernière partie du flux d’authentification est la fermeture de session. Comme vous pouvez le voir dans *loginpartial.html*, le lien **Fermeture de session** place simplement une requête POST à l’URL relative « /login », qui est gérée par l’affichage intégré `django.contrib.auth.views.logout`. Cet affichage n’affiche aucune interface utilisateur et simplement accède à la page d’accueil (comme indiqué dans *urls.py* pour le modèle « ^logout$ »). Si vous souhaitez afficher une page de fermeture de session, tout d’abord modifiez le modèle d’URL comme suit pour ajouter une propriété « template_name » et supprimez la propriété « next_page » :

    ```python
    url(r'^logout$',
        django.contrib.auth.views.logout,
        {
            'template_name': 'app/loggedoff.html',
            # 'next_page': '/',
        },
        name='logout')
    ```

    Créez ensuite *templates/app/loggedoff.html* avec le contenu suivant (minimal) :

    ```html
    {% extends "app/layout.html" %}
    {% block content %}
    <h3>You have been logged off</h3>
    {% endblock %}
    ```

    Vous obtenez le résultat suivant :

    ![Page ajoutée déconnectée](media/django/step05-logged-off-page.png)

1. Lorsque vous avez tout terminé, arrêtez le serveur et validez à nouveau les modifications apportées au contrôle de code source.

### <a name="question-what-is-the-purpose-of-the--csrf_token--tag-that-appears-in-the-form-elements"></a>Question : quelle est la fonction de la balise {% csrf_token%} qui apparaît dans les \<form\> éléments ?

Réponse : la balise `{% csrf_token %}` inclut la [protection (csrf) contre la falsification de requêtes intersites](https://docs.djangoproject.com/en/2.0/ref/csrf/) intégrée dans Django (documents Django). En général, vous ajoutez cette balise à tout élément qui implique des méthodes de requête POST, PUT ou DELETE, comme un formulaire. La fonction de rendu de modèle (`render`) insère ensuite la protection nécessaire.

## <a name="next-steps"></a>Étapes suivantes

::: moniker range="vs-2017"
- [Utiliser le modèle de projet web Django Sondage](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md)
::: moniker-end

::: moniker range=">=vs-2019"
> [!Note]
> Si vous validez votre solution Visual Studio lors du contrôle de code source pendant ce tutoriel, c’est le bon moment pour effectuer une autre validation. Votre solution doit correspondre au code source du tutoriel sur GitHub : [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django).

Vous avez maintenant exploré l’intégralité des modèles « projet Web Django vide » et « projet Web Django » dans Visual Studio. Vous avez appris tous les principes fondamentaux de Django, tels que l’utilisation des affichages et des modèles et vous avez exploré le routage, l’authentification et l’utilisation des modèles de base de données. Vous devez maintenant être en mesure de créer vous-même une application web avec les affichages et les modèles dont vous avez besoin.

L’exécution d’une application web sur votre ordinateur de développement n’est qu’une étape de la mise de l’application à la disposition de vos clients. Les étapes suivantes peuvent inclure les tâches suivantes :

- Déployer l’application web sur un serveur de production, tels qu’Azure App Service. Voir [Publier sur Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

- Personnaliser la page d’erreur 404 en créant un modèle nommé *templates/404.html*. Lorsqu’il est disponible, Django utilise ce modèle au lieu de son message d’erreur par défaut. Pour plus d’informations, consultez [Affichage des erreurs](https://docs.djangoproject.com/en/2.0/ref/views/#error-views) dans la documentation Django.

- Écrire des tests unitaires dans *tests.py* ; les modèles de projet Visual Studio fournissent des points de départ, et vous trouverez plus d’informations sous [Écrire votre première application Django, partie 5 – tests](https://docs.djangoproject.com/en/2.0/intro/tutorial05/) et sous [Tests dans Django](https://docs.djangoproject.com/en/2.0/topics/testing/) dans la documentation Django.

- Transformer l’application de SQLite en magasin de données au niveau de la production comme PostgreSQL, MySQL et SQL Server (qui peuvent tous être hébergés sur Azure). Comme décrit dans [Quand utiliser SQLite](https://www.sqlite.org/whentouse.html) (sqlite.org), SQLite fonctionne bien sur les sites au trafic faible à moyen, avec moins de 100 000 accès par jour, mais n’est pas recommandé pour les volumes plus élevés. Il est également limité à un seul ordinateur et ne peut par conséquent pas être utilisé dans un scénario multiserveur tel que l’équilibrage de charge et la géoréplication. Pour plus d’informations sur la prise en charge de Django pour d’autres bases de données, consultez [Configuration de la base de données](https://docs.djangoproject.com/en/2.0/intro/tutorial02/#database-setup). Vous pouvez également utiliser le [kit de développement logiciel (SDK) Azure pour Python](/azure/python/) pour travailler avec les services de stockage Azure, comme les tables et les objets blob.

- Configurez un pipeline d’intégration continue ou de déploiement continu sur un service comme Azure DevOps. En plus de l’utilisation du contrôle de code source (via Azure Repos, GitHub ou ailleurs), vous pouvez configurer un projet Azure DevOps pour exécuter automatiquement vos tests unitaires, dans le cadre des prérequis à la mise en production. Vous pouvez également configurer le pipeline pour effectuer le déploiement sur un serveur de préproduction pour des tests supplémentaires, avant le déploiement en production. Par ailleurs, Azure DevOps s’intègre aux solutions de supervision comme App Insights, et termine le cycle avec des outils de planification agile. Pour plus d’informations, consultez [Créer un pipeline CI/CD pour Python avec le projet Azure DevOps](/azure/devops-project/azure-devops-project-python?view=vsts&preserve-view=true), ainsi que la [documentation générale sur Azure DevOps ](/azure/devops/?view=vsts&preserve-view=true).
::: moniker-end
## <a name="go-deeper"></a>Approfondir la question

- [Authentification des utilisateurs dans Django](https://docs.djangoproject.com/en/2.0/topics/auth/) (docs.djangoproject.com)
- Code source du tutoriel sur GitHub : [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
