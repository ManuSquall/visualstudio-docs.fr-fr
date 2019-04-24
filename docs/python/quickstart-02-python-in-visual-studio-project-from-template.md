---
title: Démarrage rapide - Créer un projet Python à l’aide d’un modèle
description: Ce guide de démarrage rapide aide à créer un projet Visual Studio pour Python à l’aide du modèle prédéfini pour une application Flask de base.
ms.date: 12/06/2018
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 089be3e6f28a939979f6bd97097ea7558824b493
ms.sourcegitcommit: 0e22ead8234b2c4467bcd0dc047b4ac5fb39b977
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59365949"
---
# <a name="quickstart-create-a-python-project-from-a-template-in-visual-studio"></a>Démarrage rapide : Créer un projet Python à partir d’un modèle dans Visual Studio

Une fois que vous avez [installé la prise en charge de Python dans Visual Studio](installing-python-support-in-visual-studio.md), il est facile de créer un projet Python avec une large gamme de modèles. Dans ce guide de démarrage rapide, vous allez créer une application Flask simple à l’aide d’un modèle. Le projet ainsi produit sera similaire au projet créé manuellement avec le [Guide de démarrage rapide : Créer une application web avec Flask](../ide/quickstart-python.md).

1. Démarrez Visual Studio.

1. Dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet**, puis dans la boîte de dialogue **Nouveau projet**, recherchez « flask vide », sélectionnez le modèle **Projet web Flask vide** dans la liste du milieu, donnez un nom au projet, puis sélectionnez **OK** :

    ![Créer un projet avec le modèle Projet Web Flask vide](media/quickstart-python-06-blank-flask-template.png)

1. Visual Studio affiche une boîte de dialogue indiquant **Ce projet nécessite des packages externes.** Cette boîte de dialogue s’affiche, car le modèle comprend un fichier *requirements.txt* qui spécifie une dépendance par rapport à Flask. Visual Studio peut installer les packages automatiquement. Il permet de les installer dans un *environnement virtuel*. Sachant qu’il est recommandé d’utiliser un environnement virtuel plutôt qu’un environnement global, sélectionnez **Installer dans un environnement virtuel** pour continuer.

    ![Installer Flask dans un environnement virtuel](media/quickstart-python-07-install-into-virtual-environment.png)

1. Visual Studio affiche la boîte de dialogue **Ajouter un environnement virtuel**. Acceptez la valeur par défaut et sélectionnez **Créer**, puis donnez votre consentement à toutes les demandes d’élévation.

    > [!Tip]
    > Au début d’un projet, il est vivement recommandé de créer un environnement virtuel immédiatement ; la plupart des modèles Visual Studio invitent à le faire. Les environnements virtuels préservent les exigences précises du projet au fil du temps et des ajouts et suppressions de bibliothèques. Vous pouvez ensuite générer facilement un fichier *requirements.txt*, qui vous permet de réinstaller ces dépendances sur d’autres ordinateurs de développement (comme avec le contrôle de code source), et de déployer le projet sur un serveur de production. Pour plus d’informations sur les environnements virtuels et leurs avantages, consultez [Utiliser des environnements virtuels](../python/selecting-a-python-environment-for-a-project.md#use-virtual-environments) et [Gérer les packages requis avec requirements.txt](../python/managing-required-packages-with-requirements-txt.md).

1. Une fois que Visual Studio a créé cet environnement, parcourez l’**Explorateur de solutions** pour voir s’il existe un fichier *app.py* aux côtés de *requirements.txt*. Ouvrez *app.py*. Vous pouvez constater que le modèle a fourni un code similaire à celui de [Démarrage rapide : Créer une application web avec Flask](../ide/quickstart-python.md), avec quelques sections supplémentaires. L’ensemble du code ci-dessous est créé par le modèle. Vous n’avez pas besoin d’en coller certaines parties dans *app.py*.

    Le code commence par les importations nécessaires :

    ```python
    from flask import Flask
    app = Flask(__name__)
    ```

    Ensuite figure la ligne suivante, qui peut être utile lors du déploiement d’une application sur un hôte web :

    ```python
    wsgi_app = app.wsgi_app
    ```

    Vient ensuite l’élément décoratif de l’itinéraire sur une fonction simple qui définit une vue :

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

    Pour finir, le code de démarrage ci-dessous vous permet de définir l’hôte et le port par le biais de variables d’environnement plutôt qu’en les codant en dur. Il est donc facile de contrôler la configuration sur les ordinateurs de développement et de production sans modifier le code :

    ```python
    if __name__ == '__main__':
        import os
        HOST = os.environ.get('SERVER_HOST', 'localhost')
        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555
        app.run(HOST, PORT)
    ```

1. Sélectionnez **Déboguer** > **Exécuter sans débogage** pour exécuter l’application et ouvrir un navigateur sur `localhost:5555`.

**Question : J'utilise un certificat X.509 avec mon service et j'obtiens une System.Security.Cryptography.CryptographicException. Quels sont les autres modèles Python proposés par Visual Studio ?**

**Réponse** : Lorsque la charge de travail Python est installée, Visual Studio offre de nombreux modèles de projet, notamment pour les [infrastructures web Flask, Bottle et Django](../python/python-web-application-project-templates.md), Azure Cloud Services et différents scénarios d’apprentissage automatique. Il existe même un modèle pour créer un projet à partir d’une structure de dossiers existante contenant une application Python. Vous pouvez y accéder par la boîte de dialogue **Fichier** > **Nouveau** > **Projet** en sélectionnant le nœud de langage **Python** et ses nœuds enfants.

Visual Studio propose également divers *modèles d’éléments* ou de fichiers pour créer rapidement une classe Python, un package Python, un test unitaire Python, des fichiers *web.config*, etc. Quand un projet Python est ouvert, vous pouvez accéder aux modèles d’éléments via la commande de menu **Projet** > **Ajouter un nouvel élément**. Consultez [Référence de modèles d’élément](python-item-templates.md).

Les modèles peuvent faire gagner beaucoup de temps au démarrage d’un projet ou lors de la création d’un fichier. Ils permettent également de se renseigner sur les différents types d’applications et les différentes structures de code. Prenez quelques minutes pour créer des projets et des éléments à partir des modèles pour vous familiariser avec leur contenu.

**Question : J'utilise un certificat X.509 avec mon service et j'obtiens une System.Security.Cryptography.CryptographicException. Peut-on également utiliser des modèles Cookiecutter ?**

**Réponse** : Oui. En fait, Visual Studio fournit une intégration directe avec Cookiecutter, que vous pouvez découvrir via [Démarrage rapide : Créer un projet à partir d’un modèle Cookiecutter](../python/quickstart-04-python-in-visual-studio-project-from-cookiecutter.md).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Tutoriel : Utiliser Python dans Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Voir aussi

- [Identifier manuellement un interpréteur Python existant](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Installer la prise en charge de Python dans Visual Studio 2015 et les versions antérieures](installing-python-support-in-visual-studio.md)
- [Emplacements d’installation](installing-python-support-in-visual-studio.md#install-locations)
