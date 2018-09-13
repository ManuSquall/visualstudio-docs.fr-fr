---
title: Tutoriel – Découvrir Flask dans Visual Studio, étape 2
description: Une procédure pas à pas montrant les concepts de base de Flask dans le contexte de projets Visual Studio, en particulier les étapes de création d’une application, et l’utilisation de vues et de modèles.
ms.date: 09/04/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 61a7b36892e5cec36a4641c154227df8621c6602
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43776153"
---
# <a name="step-2-create-a-flask-app-with-views-and-page-templates"></a>Étape 2 : Créer une application Flask avec des vues et des modèles de pages

**Étape précédente : [créer une solution et un projet Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)**

Après l’étape 1 de ce tutoriel, vous disposez d’une application Flask avec une seule page et de tout le code dans un même fichier. Pour permettre les développements futurs, il est préférable à refactoriser le code et de créer une structure pour les modèles de page. En particulier, vous voulez séparer le code pour les vues de l’application du code lié à d’autres aspects, comme code du démarrage.

Dans cette étape, vous apprenez comment :

> [!div class="checklist"]
> - Refactoriser le code de l’application pour séparer le code des vues du code du démarrage (étape 2-1)
> - Afficher une vue en utilisant un modèle de page (étape 2-2)

## <a name="step-2-1-refactor-the-project-to-support-further-development"></a>Étape 2-1 : refactoriser le projet pour prendre en charge les développements futurs

Dans le code créé par le modèle « Projet web Flask vide », vous avez un seul fichier *app.py* qui contient le code du démarrage ainsi qu’une seule vue. Pour permettre les développements futurs d’une application avec plusieurs vues et modèles, il est préférable de séparer ces aspects.

1. Dans votre dossier de projet, créez un dossier d’application nommé `HelloFlask` (cliquez avec le bouton droit sur le projet dans **l’Explorateur de solutions** et sélectionnez **Ajouter** > **Nouveau dossier**.)

1. Dans le dossier *HelloFlask*, créez un fichier nommé *\_\_init\_\_.py* avec le contenu suivant, qui crée l’instance de `Flask` et charge les vues de l’application (créées à l’étape suivante) :

    ```python
    from flask import Flask
    app = Flask(__name__)

    import HelloFlask.views
    ```

1. Dans le dossier *HelloFlask*, créez un fichier nommé *views.py* avec le contenu suivant. Le nom *views.py* est important, car vous avez utilisé `import HelloFlask.views` dans *\_\_init\_\_.py* ; vous obtiendrez une erreur au moment de l’exécution si les noms ne correspondent pas.

    ```python
    from flask import Flask
    from HelloFlask import app

    @app.route('/')
    @app.route('/home')
    def home():
        return "Hello Flask!"
    ```

    En plus de renommer la fonction et de router vers `home`, ce code contient le code de rendu des pages *d’app.py* et importe l’objet `app` qui est déclaré dans *\_\_init\_\_.py*.

1. Créez un sous-dossier dans *HelloFlask* nommé *templates*, qui va rester vide pour l’instant.

1. Dans le dossier racine du projet, renommez *app.py* en *runserver.py*, et faites en sorte que son contenu corresponde au code suivant :

    ```python
    import os
    from HelloFlask import app    # Imports the code from HelloFlask/__init__.py

    if __name__ == '__main__':
        HOST = os.environ.get('SERVER_HOST', 'localhost')

        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555

        app.run(HOST, PORT)
    ```
1. La structure de votre projet doit ressembler à ceci :

    ![Structure du projet après refactorisation du code](media/flask/step02-project-structure.png)

1. Sélectionnez **Déboguer** > **Démarrer le débogage** (**F5**) ou utilisez le bouton **Serveur web** dans la barre d’outils (le navigateur affiché peut varier) pour démarrer l’application et ouvrir un navigateur. Essayez les deux routes d’URL / et /home.

1. Vous pouvez également définir des points d’arrêt dans différentes parties du code et redémarrer l’application pour suivre la séquence de démarrage. Par exemple, définissez un point d’arrêt sur les premières lignes de *runserver.py* et *HelloFlask\__init__.py*, puis sur la ligne `return "Hello Flask!"` dans *views.py*. Ensuite, redémarrez l’application (**Déboguer** > **Redémarrer**, **Ctrl**+**F5** ou le bouton de la barre d’outils montré ci-dessous) et exécutez pas à pas (**F10**) le code, ou exécutez à partir de chaque point d’arrêt en utilisant **F5**.

    ![Bouton Redémarrer de la barre d’outils de débogage dans Visual Studio](media/debugging-restart-toolbar-button.png)

1. Arrêtez l’application quand vous avez terminé.

### <a name="commit-to-source-control"></a>Valider pour le contrôle de code source

Étant donné que vous avez apporté des modifications à votre code et que vous les avez testées avec succès, il est temps à présent d’examiner et de valider vos modifications dans le contrôle de code source. Les étapes ultérieures de ce tutoriel vous rappellent les moments opportuns pour revalider le contrôle de code source et revenir à cette section.

1. Sélectionnez le bouton des modifications en bas de Visual Studio (dans le cercle ci-dessous), qui accède à **Team Explorer**.

    ![Le contrôle de code source modifie le bouton sur la barre d’état de Visual Studio](media/flask/step02-source-control-changes-button.png)

1. Dans **Team Explorer**, entrez un message de validation comme « Refactoriser le code » et sélectionnez **Valider tout**. Quand la validation est terminée, vous voyez un message **\<Hachage> de validation créé localement. Synchronisez pour partager vos modifications avec le serveur.** Si vous souhaitez envoyer les modifications vers votre référentiel distant, sélectionnez **Synchronisation**, puis sélectionnez **Envoyer** sous **Validations sortantes**. Vous pouvez également accumuler plusieurs validations locales avant d’envoyer à distance.

    ![Envoyer des validations à distance dans Team Explorer](media/flask/step02-source-control-push-to-remote.png)

### <a name="question-how-frequently-should-one-commit-to-source-control"></a>Question : à quelle fréquence faut-il valider auprès du contrôle de code source ?

Réponse : la validation des modifications auprès du contrôle de code source crée un enregistrement dans le journal des modifications et un point auquel vous pouvez rétablir le dépôt si nécessaire. Vous pouvez aussi examiner les modifications spécifiques de chaque validation. Les validations dans Git ne coûtant rien, il est préférable de faire des validations fréquentes que d’accumuler un grand nombre de modifications dans une même validation. Vous n’avez clairement pas besoin de valider chaque petite modification apportée à des fichiers individuels. En général, vous faites une validation lors de l’ajout d’une fonctionnalité, lors d’un changement de la structure comme celui que vous avez effectué dans cette étape, ou quand vous avez procédé à une refactorisation du code. Vérifiez également avec les autres membres de votre équipe quelle granularité des validations convient le mieux à tous.

La fréquence à laquelle vous validez et celle à laquelle vous envoyez (push) les validations dans un dépôt distant sont deux problèmes différents. Vous pouvez accumuler plusieurs validations dans votre dépôt local avant de les envoyer (push) dans le dépôt distant. Là encore, la fréquence à laquelle vous validez dépend de la façon dont votre équipe veut gérer le dépôt.

## <a name="step-2-2-use-a-template-to-render-a-page"></a>Étape 2-2 : Utiliser un modèle pour restituer une page

La fonction `home` que vous avez jusqu’à présent dans *views.py* ne génère rien de plus qu’une réponse HTTP de texte brut pour la page. Cependant, la plupart des pages web réelles répondent avec des pages HTML riches qui intègrent souvent des données dynamiques. En effet, la raison principale pour définir une vue en utilisant une fonction est de générer du contenu dynamiquement.

Étant donné que la valeur de retour de la vue est simplement une chaîne, vous pouvez construire n’importe quel code HTML dans une chaîne en utilisant du contenu dynamique. Cependant, comme il est recommandé de séparer le balisage des données, il est préférable de placer le balisage dans un modèle et de conserver les données dans le code.

1. Pour commencer, modifiez *views.py* et ajoutez-y le code suivant, qui utilise du code HTML inline pour la page avec du contenu dynamique :

    ```python
    from datetime import datetime
    from flask import render_template
    from HelloFlask import app

    @app.route('/')
    @app.route('/home')
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        html_content = "<html><head><title>Hello Flask</title></head><body>"
        html_content += "<strong>Hello Flask!</strong> on " + formatted_now
        html_content += "</body></html>"

        return html_content
    ```

1. Exécutez l’application et actualisez la page plusieurs fois pour constater que la date/heure est mise à jour. Arrêtez l’application quand vous avez terminé.

1. Pour convertir le rendu de la page et lui faire utiliser un modèle, créez un fichier nommé *index.html* dans le dossier *templates* avec le contenu suivant, où `{{ content }}` est un espace réservé ou un jeton de remplacement (également appelé une *variable de modèle*) pour lequel vous fournissez une valeur dans le code :

    ```html
    <html>
        <head><title>Hello Flask</title></head>

        <body>
            {{ content }}
        </body>
    </html>
    ```

1. Modifiez la fonction `home` pour qu’elle utilise `render_template` pour charger le modèle et fournissez une valeur pour « content », ce que vous faites en utilisant un argument nommé correspondant au nom de l’espace réservé. Flask recherche automatiquement des modèles dans le dossier *templates* ; le chemin du modèle est donc relatif à ce dossier :

    ```python
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        return render_template(
            "index.html",
            content = "<strong>Hello, Flask!</strong> on " + formatted_now)
    ```

1. Exécutez l’application pour voir les résultats et observer que le code HTML inclus dans la valeur `content` ne s’affiche pas *en tant que* code HTML, car le moteur de création de modèles (Jinja) place automatiquement en échappement le contenu HTML. L’échappement automatique empêche les vulnérabilités accidentelles aux attaques par injection : les développeurs recueillent souvent les données entrées dans une page et les utilisent comme valeurs dans une autre page via un espace réservé du modèle. L’échappement sert également de rappel pour indiquer qu’il est à nouveau préférable de conserver le code HTML en dehors du code.

    En conséquence, modifiez *templates\index.html* de façon à ce qu’il contienne des espaces réservés distincts pour chaque élément de données dans le balisage :

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

    Ensuite, mettez à jour la fonction `home` de façon à ce qu’elle fournisse des valeurs pour tous les espaces réservés :

    ```python
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        return render_template(
            "index.html",
            title = "Hello Flask",
            message = "Hello, Flask!",
            content = " on " + formatted_now)
    ```

1. Réexécutez l’application pour vérifier que le résultat s’affiche correctement.

    ![Exécution de l’application à l’aide du modèle](media/flask/step02-result.png)

1. Validez vos modifications auprès du contrôle de code source et si vous le souhaitez, mettez à jour votre dépôt distant, comme décrit dans [l’étape 2-1](#commit-to-source-control).

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Question : les modèles de page doivent-ils être dans un fichier distinct ?

Réponse : bien que les modèles soient généralement conservés dans des fichiers HTML distincts, vous pouvez également utiliser un modèle inclus. L’utilisation d’un fichier distinct est recommandée, toutefois, pour maintenir une séparation nette entre la balise et le code.

### <a name="question-must-templates-use-the-html-file-extension"></a>Question : les modèles doivent-ils utiliser l’extension de fichier .html ?

Réponse : l’extension *.html* pour les fichiers de modèle de page est entièrement facultative, car vous identifiez toujours le chemin relatif exact du fichier dans le premier argument de la fonction `render_template`. Toutefois, Visual Studio (et d’autres éditeurs) en général vous offrent des fonctionnalités comme la complétion de code et la coloration syntaxique avec des fichiers *.html*, ce qui compense le fait que les modèles de page ne soient pas strictement HTML.

En fait, quand vous travaillez avec un projet Flask, Visual Studio détecte automatiquement lorsque le fichier HTML que vous êtes en train de modifier est réellement un modèle Flask et fournit certaines fonctionnalités de saisie semi-automatique. Par exemple, quand vous commencez à saisir un commentaire sur le modèle de page Flask, `{#`, Visual Studio vous donne automatiquement les caractères de fermeture `#}`. Les commandes **Commenter la sélection** et **Supprimer les marques de commentaire de la sélection** (sur le menu **Modifier** > **Avancé** et la barre d’outils) utilisent également les commentaires des modèles au lieu des commentaires HTML.

### <a name="question-when-i-run-the-project-i-see-an-error-that-the-template-cannot-be-found-whats-wrong"></a>Question : lorsque j’exécute le projet, je vois une erreur indiquant qu’il est impossible de trouver le modèle. Quel est le problème ?

Réponse : si vous rencontrez des erreurs indiquant que le modèle est introuvable, vérifiez que vous avez ajouté l’application au script *settings.py* du projet Flask dans la liste `INSTALLED_APPS`. Sans cette entrée, Flask ne saura pas qu’il doit rechercher dans le dossier *templates* de l’application.

### <a name="question-can-templates-be-organized-into-further-subfolders"></a>Question : les modèles peuvent-ils être organisés selon d’autres sous-dossiers ?

Réponse : oui, vous pouvez utiliser des sous-dossiers, puis référencer le chemin relatif sous *templates* dans les appels à `render_template`. Procéder ainsi est un excellent moyen pour créer efficacement des espaces de noms pour vos modèles.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Prendre en charge les fichiers statiques, ajouter des pages et utiliser l’héritage du modèle](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)

## <a name="go-deeper"></a>Approfondir la question

- [Flask - Démarrage rapide : Rendu des modèles](http://flask.pocoo.org/docs/1.0/quickstart/#rendering-templates) (flask.pocoo.org)
- Code source du tutoriel sur GitHub : [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
