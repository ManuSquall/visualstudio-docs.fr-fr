---
title: "Démarrage rapide : utiliser Visual Studio pour créer votre première application web Python | Microsoft Docs"
description: "Une brève introduction à l’utilisation de Python dans Visual Studio, qui génère une application web simple à l’aide de l’infrastructure Falcon."
ms.custom: 
ms.date: 01/08/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: quickstart
ms.devlang: python
author: kraigb
ms.author: kraigb
manager: ghogen
dev_langs: python
ms.workload:
- python
- data-science
ms.openlocfilehash: 756419ce7390ba727bc5847d95c86399838d972a
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2018
---
# <a name="quickstart-use-visual-studio-to-create-your-first-python-web-app"></a>Démarrage rapide : utiliser Visual Studio pour créer votre première application web Python

Dans cette présentation de 5-10 minutes de l’environnement de développement intégré (IDE) de Visual Studio, vous allez créer une application web Python simple. Si vous n’avez pas encore installé Visual Studio, installez-le gratuitement [ici](http://www.visualstudio.com).

## <a name="create-the-project"></a>Créer le projet

1. Ouvrez Visual Studio 2017.

1. Dans la barre de menus supérieure, choisissez **Fichier > Nouveau > Projet**.

1. Dans la boîte de dialogue **Nouveau projet**, dans le volet gauche, développez **Installé**, puis sélectionnez **Python**.

1. Dans le volet central, sélectionnez **Projet web**, donnez un nom au projet, par exemple « HelloPython », puis choisissez **OK**.

    ![Boîte de dialogue Nouveau projet avec le projet web Python sélectionné](media/quickstart-python-00-web-project.png)

    Si vous ne voyez pas les modèles de projets Python, quittez la boîte de dialogue **Nouveau projet** puis, dans la barre de menus supérieure, choisissez **Outils > Obtenir les outils et fonctionnalités** pour ouvrir Visual Studio Installer. Choisissez la charge de travail **Développement Python**, puis choisissez **Modifier**.

    ![Charge de travail de développement Python dans le programme d’installation de Visual Studio](../python/media/installation-python-workload.png)

1. Le nouveau projet s’ouvre dans **l’Explorateur de solutions** dans le volet droit. Le projet est vide à ce stade, car il ne contient aucun autre fichier.

    ![Explorateur de solutions affichant le projet vide](media/quickstart-python-01-empty-project.png)

**Question : Quel avantage présente la création d’un projet dans Visual Studio pour une application Python ?**

Réponse : Les applications Python sont généralement définies à l’aide de fichiers et de dossiers uniquement, mais cette structure peut s’avérer complexe à mesure que les applications deviennent plus volumineuses et impliquent éventuellement des fichiers générés automatiquement, JavaScript pour les applications web, etc. Un projet Visual Studio permet de gérer cette complexité. Le projet (un fichier `.pyproj`) identifie tous les fichiers sources et de contenu associés à votre projet, contient des informations de génération pour chaque fichier, conserve les informations pour l’intégration aux systèmes de contrôle de code source et vous permet d’organiser votre application en composants logiques.

## <a name="install-the-falcon-library"></a>Installer la bibliothèque Falcon

Les applications web dans Python utilisent presque toujours l’une des nombreuses bibliothèques Python disponibles pour gérer les détails de bas niveau tels que le routage des demandes web et la mise en forme des réponses. Dans ce but, Visual Studio fournit un large éventail de modèles pour les applications web qui utilisent des frameworks Bottle, Flask et Django.

Dans ce guide de démarrage rapide, toutefois, vous utilisez la bibliothèque, Falcon pour installer un package et créer l’application web à partir de zéro. (Visual Studio n’inclut pas les modèles propres à Falcon pour le moment.) Par souci de simplicité, les étapes suivantes installent Falcon dans l’environnement global par défaut.

1. Développez le nœud **Environnements Python** dans le projet pour voir l’environnement par défaut pour le projet.

    ![Explorateur de solutions montrant l’environnement Python](media/quickstart-python-02-default-environment.png)

1. Cliquez avec le bouton droit sur l’environnement et sélectionnez **Installer le package Python**. Cette commande ouvre la fenêtre **Environnements Python** sous l’onglet **Packages**. Entrez « falcon » dans le champ de recherche et sélectionnez **installation de pip falcon depuis PyPI**. Acceptez les invites de privilèges d’administrateur et observez la progression dans la fenêtre **Sortie** de Visual Studio. (Une invite d’élévation se produit lorsque le dossier des packages de l’environnement global se situe dans une zone protégée comme `c:\program files`.)

    ![Installation de la bibliothèque Falcon](media/quickstart-python-03-install-package.png)

1. Une fois installée, la bibliothèque apparaît dans l’environnement dans **l’Explorateur de solutions**, ce qui signifie que vous pouvez l’utiliser dans le code Python.

    ![Bibliothèque Falcon installée](media/quickstart-python-04-package-installed.png)

Pour plus d’informations sur Falcon, visitez [falconframework.org](https://falconframework.org/).

Notez qu’au lieu d’installer les bibliothèques dans l’environnement global, les développeurs créent généralement un « environnement virtuel » dans lequel installer les bibliothèques pour un projet spécifique. De nombreux modèles de projets Python dans Visual Studio incluent un fichier `requirements.txt` qui répertorie les bibliothèques dont dépend le modèle. Le fait de créer un projet à partir de l’un de ces modèles déclenche la création d’un environnement virtuel dans lequel les bibliothèques sont installées. Pour plus d’informations, consultez [Environnements Python - Environnements virtuels](../python/managing-python-environments-in-visual-studio.md#creating-virtual-environments).

## <a name="add-a-code-file"></a>Ajouter un fichier de code

Vous êtes maintenant prêt à ajouter un peu de code Python pour implémenter une application web minimale.

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter > Nouvel élément**.

1. Dans la boîte de dialogue qui s’affiche, sélectionnez **Fichier Python vide**, nommez-le `hello.py`, puis sélectionnez **Ajouter**. Visual Studio ouvre automatiquement le fichier dans une fenêtre d’éditeur. (En général, la commande **Ajouter > Nouvel élément** est un excellent moyen pour ajouter différents types de fichiers à un projet, car les modèles d’éléments fournissent souvent un code réutilisable utile.)

1. Copiez le code suivant et collez-le dans `hello.py` :

    ```python
    import falcon

    # In Falcon, define a class for each resource and define on_* methods
    # where * is any standard HTTP methods in lowercase, such as on_get.

    class HelloResource:
        # In this application, the single HelloResource responds to only GET
        # requests, so it has only an on_get method.

        def on_get(self, req, resp):
            resp.status = falcon.HTTP_200  # 200 is the default
            resp.body = "Hello, Python!"

    # Resources are represented by long-lived class instances
    hello = HelloResource()

    # Instruct Falcon to route / and /hello to HelloResource. If you add
    # other resources, use api.add_route to define the desired
    # resource locators for them.
    api = falcon.API()
    api.add_route('/', hello)
    api.add_route('/hello', hello)

    if __name__ == "__main__":
        # Use Python's built-in WSGI reference implementation to run
        # a web server for the application.
        from wsgiref.simple_server import make_server

        # Run the web server on localhost:8080
        print("Starting web app server")
        srv = make_server('localhost', 8080, api)
        srv.serve_forever()
    ```

1. Après avoir collé ce code, Visual Studio peut afficher une ligne ondulée sous `falcon` dans la première ligne et également sous `wsgiref.simple.server` à la ligne 20. Ces indications apparaissent lorsque Visual Studio génère encore la base de données IntelliSense pour ces modules.

Pour plus d’informations sur Falcon, consultez le [Guide de démarrage rapide de Falcon](https://falcon.readthedocs.io/en/stable/user/quickstart.html) (falcon.readthedocs.io).

## <a name="run-the-application"></a>Exécuter l'application

1. Cliquez avec le bouton droit sur `hello.py` dans **l’Explorateur de solutions** et sélectionnez **Définir comme fichier de démarrage**. La commande identifie le fichier de code à démarrer dans Python lors de l’exécution de l’application.

    ![Définition du fichier de démarrage d’un projet dans l’Explorateur de solutions](media/quickstart-python-05-set-as-startup-file.png)

1. Cliquez avec le bouton droit sur le projet « Hello Python » dans **l’Explorateur de solutions**, puis sélectionnez **Propriétés**. Ensuite, sélectionnez l’onglet **Déboguer** et affectez la valeur `8080` à la propriété **Numéro de port**. Cette étape permet de s’assurer que Visual Studio lance un navigateur avec `localhost:8080` au lieu d’utiliser un port aléatoire.

1. Sélectionnez **Déboguer > Démarrer sans débogage** (Ctrl+F5) pour enregistrer les modifications apportées aux fichiers et exécuter l’application.

1. Une fenêtre de commande s’affiche avec le message « Démarrage du serveur d’application web », puis une fenêtre de navigateur doit s’ouvrir sur `localhost:8080` où figure le message « Hello, Python ! » La requête GET apparaît également dans la fenêtre de commande.

    Si aucun navigateur ne s’ouvre automatiquement, démarrez celui de votre choix et accédez à `localhost:8080`.)

    Si vous voyez uniquement l’interpréteur de commandes interactif Python dans la fenêtre de commande, ou si cette fenêtre clignote brièvement à l’écran, vérifiez que vous avez défini `hello.py` comme fichier de démarrage à l’étape 1 ci-dessus.

1. Fermez la fenêtre de commande pour arrêter l’application, puis fermez la fenêtre du navigateur.

## <a name="next-steps"></a>Étapes suivantes

Félicitations, vous avez terminé ce guide de démarrage rapide. Vous en savez maintenant un peu plus sur l’IDE de Visual Studio avec Python. Pour continuer avec un didacticiel plus complet sur Python dans Visual Studio, qui explique notamment comment utiliser la fenêtre interactive, le débogage, la visualisation des données et Git, sélectionnez le bouton ci-dessous.

> [!div class="nextstepaction"]
> [Didacticiel : Bien démarrer avec Python dans Visual Studio](../python/tutorial-working-with-python-in-visual-studio-step-01-create-project.md).

- En savoir plus sur les [modèles de projets d’application web Python dans Visual Studio](../python/template-web.md)
- En savoir plus sur le [débogage Python](../python/debugging.md)
- En savoir plus sur [l’IDE Visual Studio](../ide/visual-studio-ide.md)
