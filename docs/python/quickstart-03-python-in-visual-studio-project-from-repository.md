---
title: 'Démarrage rapide : Cloner un dépôt de code Python'
description: Ce guide de démarrage rapide vous permet de créer un projet Python dans Visual Studio par clonage du référentiel koans de Python à l’aide de Visual Studio Team Explorer.
ms.date: 12/06/2018
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 446c2622c01e1b127347a668e199e3e6e6e0b1c5
ms.sourcegitcommit: 0e22ead8234b2c4467bcd0dc047b4ac5fb39b977
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59367002"
---
# <a name="quickstart-clone-a-repository-of-python-code-in-visual-studio"></a>Démarrage rapide : Cloner un dépôt de code Python dans Visual Studio

Une fois que vous avez [installé la prise en charge de Python dans Visual Studio](installing-python-support-in-visual-studio.md), vous pouvez ajouter l’extension GitHub pour Visual Studio. L’extension vous permet de cloner facilement un dépôt de code Python et de vous en servir pour créer un projet dans l’IDE. Vous pouvez également cloner des dépôts sur la ligne de commande et les utiliser dans Visual Studio.

## <a name="install-the-github-extension-for-visual-studio"></a>Installer l’extension GitHub pour Visual Studio

[!INCLUDE[install-github-extension](includes/install-github-extension.md)]

## <a name="work-with-github-in-visual-studio"></a>Utiliser GitHub dans Visual Studio

1. Lancez Visual Studio.

1. Sélectionnez **Affichage** > **Team Explorer** pour ouvrir la fenêtre **Team Explorer**, où vous pouvez vous connecter à GitHub ou à Azure Repos, ou bien cloner un dépôt. (Si la page **Connecter** ne s’affiche pas ci-dessous, sélectionnez l’icône de connexion sur la barre d’outils supérieure pour ouvrir cette page.)

    ![Fenêtre Team Explorer montrant Azure Repos, GitHub et le clonage d’un dépôt](media/team-explorer.png)

1. Sous **Dépôts Git locaux**, sélectionnez la commande **Cloner**, puis entrez `https://github.com/gregmalcolm/python_koans` dans le champ de l’URL, entrez un dossier pour les fichiers clonés et sélectionnez le bouton **Cloner**.

    > [!Tip]
    > Le dossier que vous spécifiez dans **Team Explorer** est le dossier qui recevra les fichiers clonés. Contrairement à la commande `git clone`, la création d’un clone dans **Team Explorer** ne crée pas automatiquement un sous-dossier avec le nom du dépôt.

1. Lorsque le clonage est terminé, le nom du référentiel s’affiche dans la liste **référentiels Git locaux**. Double-cliquez sur ce nom pour accéder au tableau de bord du référentiel dans **Team Explorer**.

1. Sous **Solutions**, sélectionnez **Nouveau**.

    ![Fenêtre Team Explorer, création d’un projet à partir d’un clone](media/team-explorer-new-project.png)

1. Dans la boîte de dialogue **Nouveau projet** qui s’affiche, accédez au langage **Python** (ou cherchez « Python »), sélectionnez **À partir de code Python existant**, spécifiez un nom pour le projet, affectez à **Emplacement** le même dossier que celui du dépôt, puis sélectionnez **OK**. Dans l’Assistant qui apparaît, sélectionnez **Terminer**.

1. Dans le menu, sélectionnez **Affichage** > **Explorateur de solutions**.

1. Dans l’**Explorateur de solutions**, développez le nœud **python3**, cliquez avec le bouton droit sur **contemplate_koans.py**, puis sélectionnez **Définir comme fichier de démarrage**. Cette étape indique à Visual Studio quel fichier utiliser quand vous exécutez le projet.

1. Dans le menu, sélectionnez **Projet** > **Propriétés Koans**, sélectionnez l’onglet **Général**, puis affectez la valeur « python3 » à **Répertoire de travail**. Cette étape est nécessaire, car par défaut, Visual Studio définit en tant que répertoire de travail la racine du projet et non l’emplacement du fichier de démarrage (*python3\contemplate_koans.py*, que vous pouvez également voir dans les propriétés du projet). Le code du programme recherche un fichier *koans.txt* dans le dossier de travail. Ainsi, si vous ne changez pas cette valeur, une erreur d’exécution s’affiche.

    ![Définition du répertoire de travail pour un projet Python](media/projects-set-working-directory.png)

1. Appuyez sur **Ctrl**+**F5**, ou sélectionnez **Déboguer** > **Exécuter sans débogage**, pour exécuter le programme. Si vous voyez s’afficher un message **FileNotFoundError** pour *koans.txt*, vérifiez le paramètre du répertoire de travail, comme indiqué à l’étape précédente.

1. Quand le programme s’exécute correctement, une erreur d’assertion s’affiche à la ligne 17 de *python3/koans/about_asserts.py*. Ceci est intentionnel : le programme est conçu pour vous apprendre Python en vous demandant de corriger toutes les erreurs intentionnelles. (Vous pouvez trouver plus d’informations sur [Ruby Koans](https://rubykoans.com/), qui a inspiré Python Koans.)

    ![Première sortie du programme koans Python](media/koans-output.png)

1. Ouvrez *python3/koans/about_asserts.py* en y accédant dans l’**Explorateur de solutions**, puis en double-cliquant sur le fichier. Notez que par défaut, les numéros de ligne n’apparaissent pas dans l’éditeur. Pour changer cela, sélectionnez **Outils** > **Options**, **Afficher tous les paramètres** au bas de la boîte de dialogue, puis accédez à **Éditeur de texte** > **Python** > **Général**, et sélectionnez **Numéros de ligne** :

    ![Activation des numéros de ligne pour les fichiers Python](media/options-general-line-numbers.png)

1. Corrigez l’erreur en changeant l’argument `False` sur la ligne 17 en `True`. La ligne doit se présenter comme suit :

    ```python
    self.assertTrue(True) # This should be True
    ```

1. Réexécutez le programme. Si Visual Studio vous avertit qu’il y a des erreurs, répondez **Oui** pour continuer l’exécution du code. Vous verrez alors que la première vérification réussit et que le programme s’arrête sur le koan suivant. Continuez à corriger les erreurs et le programme comme vous le souhaitez.

> [!Important]
> Dans ce démarrage rapide, vous avez créé un clone direct du référentiel *python_koans* sur GitHub. Un dépôt de ce type est protégé par son auteur des modifications directes : par conséquent, la tentative de validation des modifications dans le dépôt échoue. Dans la pratique, les développeurs dupliquent (fork) ce type de dépôt dans leur propre compte GitHub, y apportent leurs modifications, puis créent des demandes de tirage (pull) pour envoyer ces modifications dans le dépôt d’origine. Lorsque vous avez votre propre duplication, utilisez son URL au lieu de l’URL du référentiel d’origine préalablement utilisé.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Tutoriel : Utiliser Python dans Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Voir aussi

- [Identifier manuellement un interpréteur Python existant](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Installer la prise en charge de Python dans Visual Studio 2015 et les versions antérieures](installing-python-support-in-visual-studio.md)
- [Emplacements d’installation](installing-python-support-in-visual-studio.md#install-locations)
