---
title: Didacticiel en savoir plus sur Django dans Visual Studio, étape 2, affichages et modèle de page
titleSuffix: ''
description: Une procédure pas à pas des principes de base de Django dans le contexte de projets Visual Studio, en particulier les étapes de création d’une application et l’utilisation des affichages et modèles.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18, SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: 196b15dff25681a23c05118a02f19109e09e3959
ms.sourcegitcommit: 5fe2462ffc33c7ece9cf3a179fb598354c916e1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2021
ms.locfileid: "110320470"
---
# <a name="step-2-create-a-django-app-with-views-and-page-templates"></a>Étape 2 : Créer une application Django avec des vues et des modèles de pages

**Étape précédente : [créer une solution et un projet Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)**

Le projet Visual Studio vous offre jusqu’à présent uniquement les composants au niveau du site d’un *projet* Django, qui peut exécuter une ou plusieurs *applications* Django. L’étape suivante consiste à créer votre première application avec une seule page.

Dans cette étape, vous apprenez comment :

> [!div class="checklist"]
> - créer une application Django avec une seule page (étape 2-1)
> - exécuter l’application à partir du projet Django (étape 2-2)
> - afficher un affichage à l’aide de HTML (étape 2-3)
> - afficher un affichage à l’aide d’un modèle de page Django (étape 2-4)

## <a name="step-2-1-create-an-app-with-a-default-structure"></a>Étape 2-1 : créer une application avec une structure par défaut

Une application Django est un package Python distinct qui contient un ensemble de fichiers associés dans un but spécifique. Un projet Django peut contenir plusieurs applications, par conséquent, un hôte Web peut servir plusieurs points d’entrée distincts à partir d’un nom de domaine unique. Par exemple, un projet Django pour un domaine comme contoso.com peut contenir une application pour `www.contoso.com`, une deuxième application pour support.contoso.com et une troisième application pour docs.contoso.com. Dans ce cas, le projet Django gère le routage d’URL et les paramètres au niveau du site (dans ses fichiers *urls.py* et *settings.py*), tandis que chaque application possède son propre style et comportement distinct via son routage interne, ses affichages, modèles, fichiers statiques et son interface d’administration.

Une application Django commence généralement par un ensemble standard de fichiers. Visual Studio fournit des modèles d’élément pour initialiser une application Django dans un projet Django, ainsi qu’une commande de menu intégrée qui remplit la même fonction :

- Modèles : dans **Explorateur de solutions**, cliquez avec le bouton de droite sur le projet, puis sélectionnez **Ajouter** > **Nouvel élément**. Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez le modèle **Application Django 1.9**, spécifiez le nom de l’application dans le champ **Nom**, puis sélectionnez **OK**.

- Commande intégrée : dans **Explorateur de solutions**, cliquez avec le bouton de droite sur le projet et sélectionnez **Ajouter** > **l’application Django**. Cette commande vous demande un nom et crée une application Django 1.9.

    ![Commande de menu pour l’ajout d’une application Django](media/django/step02-add-django-app-command.png)

À l’aide de l’une ou l’autre de ces méthodes, créez une application avec le nom « HelloDjangoApp ». Le résultat est un dossier dans votre projet portant ce nom qui contient des éléments comme décrit dans la table suivante.

![Fichiers de l’application Django dans Explorateur de solutions](media/django/step02-django-app-in-solution-explorer.png)

::: moniker range="vs-2017"
| Élément | Description |
| --- | --- |
| **\_\_init \_ \_ . py** | Le fichier qui identifie l’application en tant que package. |
| **migrations** | Un dossier dans lequel Django stocke les scripts qui mettent à jour la base de données pour s’aligner avec les modifications apportées aux modèles. Les outils de migration de Django s’appliquent alors aux modifications nécessaires apportées à toute version précédente de la base de données afin qu’elle corresponde aux modèles actuels. À l’aide des migrations, restez concentré sur vos modèles et laissez Django gérer le schéma de la base de données sous-jacente. Les migrations sont décrites à l’étape 6. pour le moment, le dossier contient simplement un fichier *\_ \_ init \_ \_ . py* (indiquant que le dossier définit son propre package Python). |
| **templates** | Dossier pour les modèles de page Django contenant un seul fichier *index.html* dans un dossier correspondant au nom de l’application. (Dans Visual Studio 2017 15,7 et versions antérieures, le fichier est contenu directement sous *modèles* et étape 2-4 vous demande de créer le sous-dossier.) Les modèles sont des blocs de code HTML dans lesquels des vues peuvent ajouter des informations pour afficher dynamiquement une page. Les « variables » du modèle de page, comme `{{ content }}` dans *index.html*, sont des espaces réservés pour des valeurs dynamiques, comme expliqué plus loin dans cet article (étape 2). Les applications Django créent généralement un espace de noms pour les modèles en les plaçant dans un sous-dossier qui correspond au nom de l’application. |
| **admin.py** | Le fichier Python dans lequel vous étendez l’interface d’administration de l’application (reportez-vous à l’étape 6), utilisée pour initialiser une base de données et modifier ses données. Au départ, ce fichier contient uniquement l’instruction, `from django.contrib import admin`. Par défaut, Django inclut une interface administrative standard à partir des entrées dans le fichier *settings.py* du projet Django, que vous pouvez activer en décommentant les entrées existantes dans *urls.py*. |
| **apps.py** | Un fichier Python qui définit une classe de configuration de l’application (voir ci-après, après cette table). |
| **models.py** | Les modèles sont des objets de données, identifiés par des fonctions, grâce auxquels les affichages interagissent avec la base de données sous-jacente de l’application (consultez l’étape 6). Django fournit le calque de connexion de base de données afin que les applications n’aient pas à se préoccuper de ces détails. Le fichier *models.py* est l’emplacement par défaut dans lequel créer vos modèles et contient initialement uniquement l’instruction, `from django.db import models`. |
| **tests.py** | Un fichier Python qui contient la structure de base des tests unitaires. |
| **views.py** | Les affichages sont en général ce que vous appelez pages Web, qui prennent une requête HTTP et retournent une réponse HTTP. Les affichages affichent généralement en langage HTML que les navigateurs Web savent comment afficher, mais un affichage ne doit pas nécessairement être visible (par exemple, un formulaire intermédiaire). Un affichage est défini par une fonction Python dont la responsabilité est d’afficher le langage HTML à envoyer au navigateur. Le fichier *views.py* est l’emplacement par défaut dans lequel créer des affichages et contient initialement uniquement l’instruction, `from django.shortcuts import render`. |
::: moniker-end

::: moniker range=">=vs-2019"
| Élément | Description |
| --- | --- |
| **\_\_init \_ \_ . py** | Le fichier qui identifie l’application en tant que package. |
| **migrations** | Un dossier dans lequel Django stocke les scripts qui mettent à jour la base de données pour s’aligner avec les modifications apportées aux modèles. Les outils de migration de Django s’appliquent alors aux modifications nécessaires apportées à toute version précédente de la base de données afin qu’elle corresponde aux modèles actuels. À l’aide des migrations, restez concentré sur vos modèles et laissez Django gérer le schéma de la base de données sous-jacente. Les migrations sont décrites dans la [documentation Django](https://docs.djangoproject.com/en/3.2/topics/migrations/). pour le moment, le dossier contient simplement un fichier *\_ \_ init \_ \_ . py* (indiquant que le dossier définit son propre package Python). |
| **templates** | Dossier pour les modèles de page Django contenant un seul fichier *index.html* dans un dossier correspondant au nom de l’application. (Dans Visual Studio 2017 15,7 et versions antérieures, le fichier est contenu directement sous *modèles* et étape 2-4 vous demande de créer le sous-dossier.) Les modèles sont des blocs de code HTML dans lesquels des vues peuvent ajouter des informations pour afficher dynamiquement une page. Les « variables » du modèle de page, comme `{{ content }}` dans *index.html*, sont des espaces réservés pour des valeurs dynamiques, comme expliqué plus loin dans cet article (étape 2). Les applications Django créent généralement un espace de noms pour les modèles en les plaçant dans un sous-dossier qui correspond au nom de l’application. |
| **admin.py** | Fichier python dans lequel vous étendez l’interface d’administration de l’application, qui est utilisée pour amorcer et modifier des données dans une base de données. Au départ, ce fichier contient uniquement l’instruction, `from django.contrib import admin`. Par défaut, Django inclut une interface administrative standard à partir des entrées dans le fichier *settings.py* du projet Django, que vous pouvez activer en décommentant les entrées existantes dans *urls.py*. |
| **apps.py** | Un fichier Python qui définit une classe de configuration de l’application (voir ci-après, après cette table). |
| **models.py** | Les modèles sont des objets de données, identifiés par des fonctions, via lesquels les vues interagissent avec la base de données sous-jacente de l’application. Django fournit le calque de connexion de base de données afin que les applications n’aient pas à se préoccuper de ces détails. Le fichier *models.py* est l’emplacement par défaut dans lequel créer vos modèles et contient initialement uniquement l’instruction, `from django.db import models`. |
| **tests.py** | Un fichier Python qui contient la structure de base des tests unitaires. |
| **views.py** | Les affichages sont en général ce que vous appelez pages Web, qui prennent une requête HTTP et retournent une réponse HTTP. Les affichages affichent généralement en langage HTML que les navigateurs Web savent comment afficher, mais un affichage ne doit pas nécessairement être visible (par exemple, un formulaire intermédiaire). Un affichage est défini par une fonction Python dont la responsabilité est d’afficher le langage HTML à envoyer au navigateur. Le fichier *views.py* est l’emplacement par défaut dans lequel créer des affichages et contient initialement uniquement l’instruction, `from django.shortcuts import render`. |
::: moniker-end

Le contenu de *apps.py* se présente comme suit quand vous utilisez le nom « HelloDjangoApp » :

```python
from django.apps import AppConfig

class HelloDjangoAppConfig(AppConfig):
    name = 'HelloDjango'
```

### <a name="question-is-creating-a-django-app-in-visual-studio-any-different-from-creating-an-app-on-the-command-line"></a>Question : la création d’une application Django dans Visual Studio diffère-t-elle de la création d’une application sur la ligne de commande ?

Réponse : l’exécution de la commande **Ajouter**  >  une **application Django** ou l’utilisation de l’option **Ajouter**  >  un **nouvel élément** avec un modèle d’application Django produit les mêmes fichiers que la commande Django `manage.py startapp <app_name>` . L’avantage de la création de l’application dans Visual Studio est que le dossier de l’application et tous ses fichiers sont automatiquement intégrés dans le projet. Vous pouvez utiliser la même commande de Visual Studio pour créer toutes les applications que vous désirez dans votre projet.

## <a name="step-2-2-run-the-app-from-the-django-project"></a>Étape 2-2 : exécuter l’application à partir du projet Django

À ce stade, si vous réexécutez le projet dans Visual Studio (à l’aide du bouton **de barre d’outils ou du**  >  **débogage démarrer le débogage**), vous voyez toujours la page par défaut. Aucun contenu de l’application ne s’affiche, car vous devez définir une page spécifique à l’application et ajouter l’application au projet Django :

1. Dans le dossier *HelloDjangoApp*, modifiez *views.py* pour faire correspondre le code ci-dessous, qui définit un affichage nommé « index » :

    ```python
    from django.shortcuts import render
    from django.http import HttpResponse

    def index(request):
        return HttpResponse("Hello, Django!")
    ```

1. Dans le dossier *BasicProject* (créé à l’étape 1), modifiez *urls.py* pour qu’il corresponde au moins au code suivant (vous pouvez conserver les commentaires intéressants si vous le souhaitez) :

    ```python
    from django.conf.urls import include, url
    import HelloDjangoApp.views

    # Django processes URL patterns in the order they appear in the array
    urlpatterns = [
        url(r'^$', HelloDjangoApp.views.index, name='index'),
        url(r'^home$', HelloDjangoApp.views.index, name='home'),
    ]
    ```

    Chaque modèle d’URL décrit les affichages pour lesquels Django achemine les URL relatives au site spécifiques (autrement dit, la partie qui suit `https://www.domain.com/`). La première entrée dans `urlPatterns` qui commence par l’expression régulière `^$` est le routage pour la racine du site, « / ». La deuxième entrée, `^home$` achemine en particulier « /home ». Vous pouvez avoir plusieurs routages pour le même affichage.

1. Réexécutez le projet pour voir le message **Hello, Django !** tel que défini par l'utilisateur. Arrêtez le serveur lorsque vous avez terminé.

### <a name="commit-to-source-control"></a>Valider pour le contrôle de code source

Étant donné que vous avez apporté des modifications à votre code et que vous les avez testées avec succès, il est temps à présent d’examiner et de valider vos modifications dans le contrôle de code source. Les étapes ultérieures de ce tutoriel vous rappellent les moments opportuns pour revalider le contrôle de code source et revenir à cette section.

1. Sélectionnez le bouton des modifications en bas de Visual Studio (dans le cercle ci-dessous), qui accède à **Team Explorer**.

    ![Le contrôle de code source modifie le bouton sur la barre d’état de Visual Studio](media/django/step02-source-control-changes-button.png)

1. Dans **Team Explorer**, entrez un message de validation comme « Créer une application Django initiale » et sélectionnez **Valider tout**. Une fois la validation terminée, vous voyez s’afficher une validation de message **\<hash> créée localement. Synchronisez pour partager vos modifications avec le serveur.** Si vous souhaitez envoyer les modifications vers votre référentiel distant, sélectionnez **Synchronisation**, puis sélectionnez **Envoyer** sous **Validations sortantes**. Vous pouvez également accumuler plusieurs validations locales avant d’envoyer à distance.

    ![Envoyer des validations à distance dans Team Explorer](media/django/step02-source-control-push-to-remote.png)

### <a name="question-what-is-the-r-prefix-before-the-routing-strings-for"></a>Question : Que représente le préfixe « r » avant les chaînes de routage ?

Réponse : le préfixe « r » sur une chaîne dans Python signifie « brut, » et avertit Python de ne pas échapper des caractères dans la chaîne. Étant donné que les expressions régulières utilisent plusieurs caractères spéciaux, l’utilisation du préfixe « r » permet une lecture de ces chaînes beaucoup plus facile que si elles contenaient un certain nombre de caractères d’échappement « \\ ».

### <a name="question-what-do-the--and--characters-mean-in-the-url-routing-entries"></a>Question : Que signifient les caractères ^ et $ dans les entrées de routage d’URL ?

Réponse : dans les expressions régulières qui définissent des modèles d’URL, ^ signifie « début de ligne » et $ signifie « fin de ligne, » où une nouvelle fois les URL sont relatives par rapport à la racine du site (la partie qui suit `https://www.domain.com/`). L’expression régulière `^$` signifie effectivement « vide » et par conséquent correspond à l’URL complète `https://www.domain.com/` (rien n’est ajouté à la racine du site). Le modèle `^home$` correspond exactement à `https://www.domain.com/home/`. (Django n’utilise pas le symbole de fin / dans les critères spéciaux.)

Si vous n’utilisez pas un symbole $ de fin dans une expression régulière, comme avec `^home`, le modèle d’URL correspond alors à *toute* URL qui commence par « home », tels que « home », « homework », « homestead » et « home192837 ».

Pour faire des essais avec différentes expressions régulières, essayez les outils en ligne tels que [regex101.com](https://regex101.com) sur [pythex.org](https://www.pythex.org).

## <a name="step-2-3-render-a-view-using-html"></a>Étape 2-3 : afficher un affichage à l’aide de HTML

La fonction `index` que vous avez jusqu’à présent dans *views.py* ne génère rien de plus qu’une réponse HTTP de texte brut pour la page. Les pages Web les plus réelles, bien entendu, répondent avec des pages HTML riches qui intègrent souvent des données dynamiques. En effet, la principale raison pour laquelle vous définissez une vue à l’aide d’une fonction est de vous permettre de générer ce contenu de manière dynamique.

Étant donné que l’argument pour `HttpResponse` est simplement une chaîne, vous pouvez générer tout le langage HTML que vous désirez dans une chaîne. À titre d’exemple, remplacez la fonction `index` par le code suivant (en conservant les instructions `from` existantes), ce qui génère une réponse HTML à l’aide de contenu dynamique mis à jour chaque fois que vous actualisez la page :

```python
from datetime import datetime

def index(request):
    now = datetime.now()

    html_content = "<html><head><title>Hello, Django</title></head><body>"
    html_content += "<strong>Hello Django!</strong> on " + now.strftime("%A, %d %B, %Y at %X")
    html_content += "</body></html>"

    return HttpResponse(html_content)
```

Exécutez le projet à nouveau pour afficher le message tel que «**Bonjour, Django !** le lundi 16 avril 2018 à 16:28:10 ». Actualisez la page pour mettre à jour l’heure et confirmer que le contenu est généré à chaque requête. Arrêtez le serveur lorsque vous avez terminé.

> [!Tip]
> Un raccourci pour arrêter et redémarrer le projet consiste à utiliser la commande de menu redémarrer le **débogage**  >   (**CTRL** + **MAJ** + **F5**) ou le bouton **redémarrer** dans la barre d’outils de débogage :
>
> ![Bouton Redémarrer de la barre d’outils de débogage dans Visual Studio](media/debugging-restart-toolbar-button.png)

## <a name="step-2-4-render-a-view-using-a-page-template"></a>Étape 2-4 : afficher un affichage à l’aide d’un modèle de page

La génération HTML dans le code fonctionne bien pour les très petites pages, mais à mesure que les pages deviennent plus sophistiquées, vous souhaiterez généralement conserver les parties HTML statiques de votre page (ainsi que les références à des fichiers CSS et JavaScript) en tant que « modèles de page », dans lesquels vous insérez ensuite un contenu dynamique, généré par le code. Dans la section précédente, seules la date et l’heure à partir de l’appel `now.strftime` sont dynamiques, ce qui signifie que tout autre contenu peut être placé dans un modèle de page.

Un modèle de page Django est un bloc de langage HTML qui peut contenir plusieurs jetons de remplacement appelés « variables » délimités par `{{` et `}}`, comme dans `{{ content }}`. Le module de création de modèles de Django remplace alors les variables par un contenu dynamique que vous fournissez dans le code.

Les étapes suivantes illustrent l’utilisation de modèles de page :

1. Sous le dossier *BasicProject* qui contient le projet Django, ouvrez le fichier *settings.py* et ajoutez le nom de l’application, « HelloDjangoApp », à la liste `INSTALLED_APPS`. L’ajout de l’application à la liste indique au projet Django qu’il existe un dossier du même nom qui contient une application :

    ```python
    INSTALLED_APPS = [
        'HelloDjangoApp',
        # Other entries...
    ]
    ```

1. Également dans *settings.py*, assurez-vous que l’objet `TEMPLATES` contient la ligne suivante (incluse par défaut), qui indique à Django de rechercher des modèles dans un dossier *templates* de l’application installée :

    ```json
    'APP_DIRS': True,
    ```

1. Dans le dossier *HelloDjangoApp*, ouvrez le fichier de modèle de page *templates/HelloDjangoApp/index.html* (ou *templates/index.html* dans VS 2017 version 15.7 et les versions antérieures) pour voir qu’il contient une variable, `{{ content }}` :

    ```html
    <html>
    <head><title></title></head>

    <body>

    {{ content }}

    </body>
    </html>
    ```

1. Dans le dossier *HelloDjangoApp*, ouvrez *views.py* et remplacez la fonction `index` par le code suivant qui utilise la fonction auxiliaire `django.shortcuts.render`. L’assistance `render` offre une interface simplifiée pour utiliser des modèles de page. Veillez à conserver toutes les instructions `from` existantes.

    ```python
    from django.shortcuts import render   # Added for this step

    def index(request):
        now = datetime.now()

        return render(
            request,
            "HelloDjangoApp/index.html",  # Relative path from the 'templates' folder to the template file
            # "index.html", # Use this code for VS 2017 15.7 and earlier
            {
                'content': "<strong>Hello Django!</strong> on " + now.strftime("%A, %d %B, %Y at %X")
            }
        )
    ```

    Le premier argument pour `render`, comme vous pouvez le voir, est l’objet de requête, suivi par le chemin d’accès relatif au fichier de modèle dans le dossier *templates* de l’application. Un fichier de modèle est nommé pour la prise en charge de l’affichage, le cas échéant. Le troisième argument de `render` est alors un dictionnaire de variables auquel le modèle fait référence. Vous pouvez inclure des objets dans le dictionnaire, auquel cas une variable dans le modèle peut faire référence à `{{ object.property }}`.

1. Exécutez le projet et observez le résultat. Vous devez voir un message similaire à celui de l’étape 2-2, ce qui indique que le modèle fonctionne.

    Notez, toutefois, que le langage HTML que vous avez utilisé dans la propriété `content` s’affiche uniquement en tant que texte brut, car la fonction `render` échappe automatiquement ce langage HTML. L’échappement automatique empêche les vulnérabilités accidentelles aux attaques par injection : les développeurs recueillent souvent les données entrées dans une page et les utilisent comme valeurs dans une autre page via un espace réservé du modèle. L’échappement sert également de rappel pour indiquer qu’il est à nouveau préférable de conserver le code HTML dans le modèle de page et en dehors du code. Heureusement, il est très simple de créer des variables supplémentaires quand elles sont nécessaires. Par exemple, remplacez *index.html* par *templates* pour correspondre au code suivant, ce qui permet d’ajouter un titre de page et de conserver toute la mise en forme dans le modèle de page :

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
        </head>
        <body>
            <strong>{{ message }}</strong>{{ content }}
        </body>
    </html>
    ```

    Écrivez ensuite la fonction d’affichage `index` comme suit, pour fournir des valeurs pour toutes les variables dans le modèle de page :

    ```python
    def index(request):
        now = datetime.now()

        return render(
            request,
            "HelloDjangoApp/index.html",  # Relative path from the 'templates' folder to the template file
            # "index.html", # Use this code for VS 2017 15.7 and earlier
            {
                'title' : "Hello Django",
                'message' : "Hello Django!",
                'content' : " on " + now.strftime("%A, %d %B, %Y at %X")
            }
        )
    ```

1. Arrêtez le serveur et redémarrez le projet. Notez alors que la page s’affiche maintenant correctement :

    ![Exécution de l’application à l’aide du modèle](media/django/step02-result.png)

1. <a name="template-namespacing"></a>Visual Studio 2017 version 15.7 et versions antérieures : pour finir, déplacez vos modèles dans un sous-dossier portant le même nom que votre application, ce qui permet de créer un espace de noms et d’éviter les conflits potentiels avec d’autres applications que vous pouvez éventuellement ajouter au projet. (Les modèles dans VS 2017 15.8 + le font automatiquement pour vous.) Autrement dit, créez un sous-dossier dans les *modèles* nommés *HelloDjangoApp*, déplacez *index.html* dans ce sous-dossier, puis modifiez la `index` fonction d’affichage pour faire référence au nouveau chemin d’accès du modèle, *HelloDjangoApp/index.html*. Puis exécutez le projet, vérifiez que la page s’affiche correctement et arrêtez le serveur.

1. Validez vos modifications du contrôle de code source et mettez à jour votre référentiel distant, si vous le souhaitez, comme indiqué sous [l’étape 2-2](#commit-to-source-control).

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Question : Les modèles de page doivent-ils être dans un fichier distinct ?

Réponse : bien que les modèles soient généralement conservés dans des fichiers HTML distincts, vous pouvez également utiliser un modèle inclus. L’utilisation d’un fichier distinct est recommandée, toutefois, pour maintenir une séparation nette entre la balise et le code.

### <a name="question-must-templates-use-the-html-file-extension"></a>Question : Les modèles doivent-ils utiliser l’extension de fichier .html ?

Réponse : L’extension *.html* pour les fichiers de modèle de page est entièrement facultative, car vous identifiez toujours le chemin d’accès relatif exact au fichier dans le deuxième argument de la fonction `render`. Toutefois, Visual Studio (et d’autres éditeurs) en général vous offrent des fonctionnalités comme la complétion de code et la coloration syntaxique avec des fichiers *.html*, ce qui compense le fait que les modèles de page ne soient pas strictement HTML.

En fait, lorsque vous travaillez avec un projet Django, Visual Studio détecte automatiquement lorsque le fichier HTML que vous êtes en train de modifier est réellement un modèle Django et fournit certaines fonctionnalités de saisie semi-automatique. Par exemple, lorsque vous commencez à saisir un commentaire sur le modèle de page Django, `{#`, Visual Studio vous donne automatiquement les caractères de fermeture `#}`. Les commandes **Commenter la sélection** et **Supprimer les marques de commentaire de la sélection** (sur le menu **Modifier** > **Avancé** et la barre d’outils) utilisent également les commentaires des modèles au lieu des commentaires HTML.

### <a name="question-when-i-run-the-project-i-see-an-error-that-the-template-cannot-be-found-whats-wrong"></a>Question : lorsque j’exécute le projet, je vois une erreur indiquant qu’il est impossible de trouver le modèle. Quel est le problème ?

Réponse : Si vous rencontrez des erreurs indiquant que le modèle est introuvable, vérifiez que vous avez ajouté l’application au script *settings.py* du projet Django dans la liste `INSTALLED_APPS`. Sans cette entrée, Django ne saura pas qu’il doit rechercher dans le dossier *templates* de l’application.

### <a name="question-why-is-template-namespacing-important"></a>Question : pourquoi les espaces de noms du modèle sont-ils importants ?

Réponse : lorsque Django recherche un modèle référencé dans la fonction `render`, il utilise le premier fichier qu’il trouve correspondant au chemin d’accès relatif. Si vous avez plusieurs applications Django dans le même projet qui utilisent les mêmes structures de dossiers pour les modèles, il est probable qu’une seule application utilisera involontairement un modèle à partir d’une autre application. Pour éviter de telles erreurs, créez toujours un sous-dossier sous un dossier *templates* d’une application qui correspond au nom de l’application afin d’éviter toute duplication.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Prendre en charge les fichiers statiques, ajouter des pages et utiliser l’héritage du modèle](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)

## <a name="go-deeper"></a>Approfondir la question

- [Écrire votre première application Django, partie 1 - affichages](https://docs.djangoproject.com/en/2.0/intro/tutorial01/#write-your-first-view) (docs.djangoproject.com)
- Pour davantage de fonctionnalités avec les modèles Django, tels que fichiers inclus et héritage, consultez [Le langage de gabarit Django](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (docs.djangoproject.com)
- [Formation d’expression régulière sur inLearning](https://www.linkedin.com/learning/topics/regular-expressions) (LinkedIn)
- Code source du tutoriel sur GitHub : [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
