---
title: Démarrage rapide - Créer un projet Python à l’aide d’un modèle
description: Ce guide de démarrage rapide aide à créer un projet Visual Studio pour Python à l’aide du modèle prédéfini pour une application Flask de base.
ms.date: 03/22/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: quickstart
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: a033d8b2709a6eaf871758d1bd46a3ad34f7a08f
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
---
# <a name="quickstart-create-a-python-project-from-a-template-in-visual-studio"></a>Démarrage rapide : Créer un projet Python à partir d’un modèle dans Visual Studio

Une fois que vous avez [installé la prise en charge de Python dans Visual Studio 2017](installing-python-support-in-visual-studio.md), il est facile de créer un projet Python avec une large gamme de modèles. Dans ce guide de démarrage rapide, vous allez créer une application Flask simple à l’aide d’un modèle. Le projet ainsi produit sera similaire au projet créé manuellement avec le [Guide de démarrage rapide : Créer une application web avec Flask](../ide/quickstart-python.md).

1. Lancez Visual Studio 2017.

1. Dans la barre de menus supérieure, choisissez **Fichier > Nouveau > Projet...**  ; dans la boîte de dialogue **Nouveau projet**, recherchez « flask vide », sélectionnez le modèle « Projet Web Flask vide » dans la liste du milieu, donnez un nom au projet et sélectionnez **OK** :

    ![Créer un projet avec le modèle Projet Web Flask vide](media/quickstart-python-06-blank-flask-template.png)

1. Visual Studio affiche une boîte de dialogue indiquant « Des packages externes sont nécessaires pour ce projet ». En effet, le modèle comprend un fichier `requirements.txt` qui spécifie une dépendance vis-à-vis de Flask. Visual Studio peut installer les packages automatiquement, et offre la possibilité de les installer dans un *environnement virtuel*. Sachant qu’il est recommandé d’utiliser un environnement virtuel plutôt qu’un environnement global, sélectionnez **Installer dans un environnement virtuel** pour continuer.

    ![Installer Flask dans un environnement virtuel](media/quickstart-python-07-install-into-virtual-environment.png)

1. Visual Studio affiche la boîte de dialogue **Ajouter un environnement virtuel**. Acceptez la valeur par défaut et sélectionnez **Créer**, puis donnez votre consentement à toutes les demandes d’élévation.

    > [!Tip]
    > Au début d’un projet, il est vivement recommandé de créer un environnement virtuel immédiatement ; la plupart des modèles Visual Studio invitent à le faire. Les environnements virtuels préservent les exigences précises du projet au fil du temps et des ajouts et suppressions de bibliothèques. Il est alors facile de générer un fichier `requirements.txt`, qui permet de réinstaller ces dépendances sur d’autres ordinateurs de développement (comme avec le contrôle de code source) et se révèle utile pour déployer le projet sur un serveur de production. Pour plus d’informations sur les environnements virtuels et leurs avantages, consultez la section [Utiliser des environnements virtuels](../python/selecting-a-python-environment-for-a-project.md#using-virtual-environments) et la page [Gérer les packages requis avec requirements.txt](../python/managing-required-packages-with-requirements-txt.md).

1. Une fois que Visual Studio a créé cet environnement, parcourez **l’Explorateur de solutions** pour voir s’il existe un fichier `app.py` avec `requirements.txt`. Ouvrez `app.py` : le modèle a fourni un code similaire dans le [ Guide de démarrage rapide : Créer une application web avec Flask](../ide/quickstart-python.md), avec deux sections supplémentaires.

    Au début se trouve la ligne `wsgi_app = app.wsgi_app`, qui peut être utile pour déployer une application sur un hôte web.

    Ensuite vient le code de démarrage permettant de définir l’hôte et le port par le biais de variables d’environnement plutôt qu’en les codant en dur. Il est donc facile de contrôler la configuration sur les ordinateurs de développement et de production sans modifier le code :

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

1. Sélectionnez **Déboguer > Démarrer sans débogage** pour exécuter l’application et ouvrir un navigateur sur `localhost:5555`.

**Question : Quels sont les autres modèles Python offerts par Visual Studio ?**

**Réponse** : Lorsque la charge de travail Python est installée, Visual Studio offre de nombreux modèles de projet, notamment pour les [infrastructures web Flask, Bottle et Django](../python/python-web-application-project-templates.md), Azure Cloud Services et différents scénarios de Machine Learning. Il existe même un modèle pour créer un projet à partir d’une structure de dossiers existante contenant une application Python. Vous pouvez y accéder par la boîte de dialogue **Fichier > Nouveau > Projet...**  en sélectionnant le nœud de langage **Python** et ses nœuds enfants.

Visual Studio propose également un ensemble de *modèles d’élément* ou de fichier pour créer rapidement une classe Python, un package Python, un test unitaire Python, des fichiers `web.config`, etc. Lorsqu’un projet Python est ouvert, vous pouvez accéder aux modèles d’élément par le biais de la commande de menu **Projet > Ajouter un élément**. Consultez [Référence de modèles d’élément](python-item-templates.md).

Les modèles peuvent faire gagner beaucoup de temps au démarrage d’un projet ou lors de la création d’un fichier. Ils permettent également de se renseigner sur les différents types d’applications et les différentes structures de code. Prenez quelques minutes pour créer des projets et des éléments à partir des modèles pour vous familiariser avec leur contenu.

**Question : Peut-on également utiliser des modèles Cookiecutter ?**

**Réponse** : Oui ! En fait, Visual Studio assure une intégration directe avec Cookiecutter. Pour plus d’informations, consultez le [Guide de démarrage rapide : Créer un projet à partir d’un modèle Cookiecutter](../python/quickstart-04-python-in-visual-studio-project-from-cookiecutter.md).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Didacticiel : Utilisation de Python dans Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Voir aussi

- [Identifier manuellement un interpréteur Python existant](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).
- [Installer la prise en charge de Python dans Visual Studio 2015 et antérieur](installing-python-support-in-visual-studio.md).
- [Emplacements d’installation](installing-python-support-in-visual-studio.md#install-locations).
