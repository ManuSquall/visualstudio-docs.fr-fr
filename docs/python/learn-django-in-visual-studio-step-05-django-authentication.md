---
title: Tutoriel - Découvrez Django dans Visual Studio, étape 5
description: Une procédure pas à pas des principes de base de Django dans le contexte de projets Visual Studio, en particulier les fonctionnalités d’authentification comme fournies par les modèles de projet Web Django.
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
ms.openlocfilehash: e2c5f9461eafa83551ba15c36d8ef212922a52ff
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="tutorial-step-5-authenticate-users-in-django"></a>Étape 5 du tutoriel : authentifier les utilisateurs dans Django

**Étape précédente : [utiliser le modèle de projet Web Django complet](learn-django-in-visual-studio-step-04-full-django-project-template.md)**

Étant donné que l’authentification est un besoin courant pour les applications Web, le modèle « Projet Web de Django » contient un flux de l’authentification de base. (Le modèle « Sondages sur le projet Web Django » discuté à l’étape 6 de ce tutoriel inclut également le même flux.) Lorsque vous utilisez un des modèles de projet Django, Visual Studio inclut tous les modules nécessaires pour l’authentification dans le `settings.py` du projet Django.

Dans cette étape vous apprenez :

> [!div class="checklist"]
> - à utiliser le flux d’authentification fourni dans les modèles Visual Studio (étape 5-1)

## <a name="step-5-1-use-the-authentication-flow"></a>Étape 5-1 : utiliser le flux d’authentification

Les étapes suivantes exécutent le flux d’authentification et décrivent les parties du projet qui sont impliquées :

1. Si vous n’avez pas déjà suivi les instructions du fichier `readme.html` dans la racine du projet pour créer un compte de superutilisateur (administrateur), faites-le maintenant.

1. Exécuter l’application à partir de Visual Studio en utilisant **Déboguer** > **Démarrer le débogage** (F5). Lorsque l’application s’affiche dans le navigateur, observez que **Connecter** s’affiche dans le coin supérieur droit de la barre de navigation.

    ![Contrôle de connexion dans la page d’application du projet Web Django](media/django/step05-login-control.png)

1. Ouvrez `templates/app/layout.html` et remarquez que l’élément `<div class="navbar ...>` contient la balise `{% include app/loginpartial.html %}`. La balise `{% include %}` indique au système de création de modèles de Django d’extraire le contenu du fichier inclus à ce stade dans le modèle contenant.

1. Ouvrez `templates/app/loginpartial.html` et observez l’utilisation de la balise conditionnelle `{% if user.is_authenticated %}` avec une balise `{% else %}` pour afficher les différents éléments d’interface utilisateur en fonction de l’authentification de l’utilisateur ou non :

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

1. Étant donné qu’aucun utilisateur n’est authentifié lors du premier démarrage de l’application, ce code de modèle affiche uniquement le lien « Se connecter » vers la « connexion » du chemin relatif. Comme spécifié dans `urls.py` tel qu’indiqué dans la section précédente, cet itinéraire est mappé à l’affichage `django.contrib.auth.views.login` donné dans les données suivantes :

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

    Ici, `template_name` identifie le modèle pour la page de connexion, dans ce cas `templates/app/login.html`. La propriété `extra_context` est ajoutée aux données de contexte par défaut fournies au modèle. Enfin, `authentication_form` spécifie une classe de formulaire à utiliser avec la connexion dans le modèle qui apparaît comme l’objet `form`. La valeur par défaut est `AuthenticationForm` (à partir de `django.contrib.auth.views`) ; à la place, le modèle de projet Visual Studio utilise le formulaire défini dans le fichier `forms.py` de l’application :

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

1. Lorsque vous accédez à la page de connexion, l’application affiche alors le modèle `login.html`. Les variables `{{ form.username }}` et `{{ form.password }}` affichent les formulaires `CharField` à partir de `BootstrapAuthenticationForm`. Il existe également une section intégrée pour afficher les erreurs de validation et un élément prêts à l’emploi pour les connexions sociales si vous choisissez d’ajouter ces services.

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

1. Quand vous envoyez le formulaire, Django tente d’authentifier les informations d’identification que vous fournissez (par exemple, les informations d’identification du superutilisateur). Si l’authentification échoue, vous restez sur la même page, mais `form.errors` défini sur true. Si l’authentification réussit, Django navigue vers l’URL relative dans le champ « suivant », `<input type="hidden" name="next" value="/" />`, qui est dans ce cas la page d’accueil (`/`).

1. Désormais, lorsque la page d’accueil est affichée, la propriété `user.is_authenticated` est définie sur true lorsque le modèle `loginpartial.html` est affiché. Par conséquent, vous consultez un message « Bonjour (nom d’utilisateur) » et « Se déconnecter ». Vous pouvez utiliser `user.is_authenticated` dans d’autres parties de l’application pour vérifier l’authentification.

    ![Message d’accueil et contrôle de fermeture de session dans la page d’application du projet Web Django](media/django/step05-logoff-control.png)

1. Pour vérifier si l’utilisateur authentifié est autorisé à accéder aux ressources spécifiques, vous devez récupérer les autorisations spécifiques à l’utilisateur à partir de votre base de données pour cet utilisateur. Pour plus d’informations, consultez [Utilisation du système d’authentification Django](https://docs.djangoproject.com/en/2.0/topics/auth/default/#permissions-and-authorization) (documents Django).

1. Le superutilisateur ou l’administrateur, en particulier, est autorisé à accéder aux interfaces d’administrateur intégrées Django à l’aide des URL relatives « /admin/ » et « /admin/doc/ ». Pour activer ces interfaces, ouvrez le `urls.py` du projet Django et supprimez les commentaires à partir des entrées suivantes :

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

    Lorsque vous redémarrez l’application, vous pouvez accéder à « /admin/ » et « / admin/doc / » et effectuer des tâches telles que créer des comptes d’utilisateur supplémentaires.

    ![Interface de l’administrateur Django](media/django/step05-administrator-interface.png)

1. La dernière partie du flux d’authentification est la fermeture de session. Comme vous pouvez le voir dans `loginpartial.html`, le lien **Fermeture de session** place simplement une requête POST à l’URL relative « /login », qui est gérée par l’affichage intégré `django.contrib.auth.views.logout`. Cet affichage n’affiche aucune interface utilisateur et simplement accède à la page d’accueil (comme indiqué dans `urls.py` pour le modèle « ^ logout$ »). Si vous souhaitez afficher une page de fermeture de session, tout d’abord modifiez le modèle d’URL comme suit pour ajouter une propriété « template_name » et supprimez la propriété « next_page » :

    ```python
    url(r'^logout$',
        django.contrib.auth.views.logout,
        {
            'template_name': 'app/loggedoff.html',
            # 'next_page': '/',
        },
        name='logout')
    ```

    Créez ensuite `templates/app/loggedoff.html` avec le contenu (minimal) suivant :

    ```html
    {% extends "app/layout.html" %}
    {% block content %}
    <h3>You have been logged off</h3>
    {% endblock %}
    ```

    Vous obtenez le résultat suivant :

    ![Page ajoutée déconnectée](media/django/step05-logged-off-page.png)

1. Lorsque vous avez tout terminé, arrêtez le serveur et validez à nouveau les modifications apportées au contrôle de code source.

### <a name="question-what-is-the-purpose-of-the--crsftoken--tag-that-appears-in-the-form-elements"></a>Question : quelle est l’objectif de la balise {% crsf_token %} qui s’affiche dans les éléments du \<formulaire\> ?

Réponse : la balise `{% crsf_token %}` inclut la [protection (crsf) de falsification de requêtes intersites](https://docs.djangoproject.com/en/2.0/ref/csrf/) intégrée dans Django (documents Django). En général, vous ajoutez cette balise à tout élément qui implique des méthodes de requête POST, PUT ou DELETE, comme un formulaire et la fonction d’affichage du modèle (`render`) insère la protection nécessaire.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Utiliser le modèle Sondages du projet Web Django](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md)

## <a name="going-deeper"></a>Pour aller plus loin

- [Authentification des utilisateurs dans Django](https://docs.djangoproject.com/en/2.0/topics/auth/) (docs.djangoproject.com)
- Code source du tutoriel sur GitHub : [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)