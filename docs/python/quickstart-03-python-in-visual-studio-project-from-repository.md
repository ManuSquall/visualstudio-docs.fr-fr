---
title: "Démarrage rapide : Clonage d’un dépôt de code Python dans Visual Studio | Microsoft Docs"
description: "Commencez rapidement à utiliser Python en clonant le dépôt koans Python à l’aide de Visual Studio Team Explorer."
ms.custom: 
ms.date: 09/25/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: quickstart
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: ca32058d9207221c1752e522bbba82d0033626f2
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="quickstart-clone-a-repository-of-python-code-in-visual-studio"></a>Démarrage rapide : Clonage d’un dépôt de code Python dans Visual Studio

Une fois que vous avez [installé la prise en charge de Python dans Visual Studio 2017](installing-python-support-in-visual-studio.md), vous pouvez facilement cloner un dépôt de code Python et créer un projet à partir de celui-ci.

[!INCLUDE[install-github-extension](includes/install-github-extension.md)]

2. Lancez Visual Studio.

3. Sélectionnez **Affichage > Team Explorer...** pour ouvrir la fenêtre **Team Explorer**, dans laquelle vous pouvez vous connecter à GitHub ou à Visual Studio Team Services, ou cloner un dépôt.

    ![Fenêtre Team Explorer montrant Visual Studio Team Services, GitHub et le clonage d’un dépôt](media/team-explorer.png)

4. Dans le champ URL, sous **Dépôts Git locaux**, entrez `https://github.com/gregmalcolm/python_koans`, entrez un dossier pour les fichiers clonés, puis sélectionnez **Cloner**.

    > [!Tip]
    > Le dossier que vous spécifiez dans Team Explorer est le dossier spécifique pour recevoir les fichiers clonés. Contrairement à la commande `git clone`, la création d’un clone dans Team Explorer ne crée pas automatiquement un sous-dossier avec le nom du dépôt.

5. Quand le clonage est terminé, double-cliquez sur le dossier du dépôt dans le bas de Team Explorer pour accéder au tableau de bord du dépôt. Sous **Solutions**, sélectionnez **Nouveau...**.

    ![Fenêtre Team Explorer, création d’un projet à partir d’un clone](media/team-explorer-new-project.png)

6. Dans la boîte de dialogue **Nouveau projet** qui s’affiche, sélectionnez « À partir de code Python existant », spécifiez un nom pour le projet, définissez **Emplacement** sur le même dossier que le dépôt, puis sélectionnez **OK**. Dans l’Assistant qui apparaît, sélectionnez **Terminer**.

7. Sélectionnez **Affichage > Explorateur de solutions** dans le menu.

8. Dans l’Explorateur de solutions, développez le nœud `python3`, cliquez avec le bouton droit sur `contemplate_koans.py`, puis sélectionnez **Définir comme fichier de démarrage**. Cette étape indique à Visual Studio quel fichier utiliser quand vous exécutez le projet.

9. Sélectionnez **Projet > Propriétés** dans le menu, sélectionnez l’onglet **Général** et définissez **Répertoire de travail** sur « python3 ». Ceci est nécessaire car par défaut, Visual Studio définit le répertoire de travail sur la racine du projet et non pas sur l’emplacement du fichier de démarrage (`python3\contemplate_koans.py`, que vous pouvez voir également dans les propriétés du projet). Le code du programme recherche un fichier `koans.txt` dans le dossier de travail. Par conséquent, si vous ne changez pas cette valeur, vous recevrez une erreur à l’exécution.

    ![Définition du répertoire de travail pour un projet Python](media/projects-set-working-directory.png)

10. Appuyez sur Ctrl+F5 ou sélectionnez **Déboguer > Démarrer sans débogage** pour exécuter le programme. Si vous voyez une `FileNotFoundError` pour `koans.txt`, revérifiez la valeur du répertoire de travail de l’étape précédente.

11. Quand le programme s’exécute avec succès, une erreur d’assertion s’affiche sur la ligne 17 de `python3/koans/about_asserts.py`. Ceci est intentionnel : le programme est conçu pour vous apprendre Python en vous demandant de corriger toutes les erreurs intentionnelles. (Vous pouvez trouver plus d’informations sur [Ruby Koans](http://rubykoans.com/), qui a inspiré Python Koans.)

    ![Première sortie du programme koans Python](media/koans-output.png)

12. Ouvrez `python3/koans/about_asserts.py` en y accédant dans l’Explorateur de solutions, puis en double-cliquant sur le fichier. Notez que par défaut, les numéros de ligne n’apparaissent pas dans l’éditeur. Pour changer cela, sélectionnez **Outils > Options**, sélectionnez **Afficher tous les paramètres** dans le bas de la boîte de dialogue, puis accédez à **Éditeur de texte > Python > Général** et sélectionnez **Numéros de ligne** :

    ![Activation des numéros de ligne pour les fichiers Python](media/options-general-line-numbers.png)

13. Corrigez l’erreur en changeant l’argument `False` sur la ligne 17 en `True`. La ligne doit se présenter comme suit :

    ```python
    self.assertTrue(True) # This should be True
    ```

14. Réexécutez le programme pour vérifier que la première vérification réussit, et le programme s’arrête sur le koan suivant. Continuez la correction des erreurs et réexécutez le programme comme vous le souhaitez.

> [!Important]
> Dans ce démarrage rapide, vous avez créé un clone direct du dépôt *python_koans* sur GitHub. Un dépôt de ce type est protégé par son auteur des modifications directes : par conséquent, la tentative de validation des modifications dans le dépôt échoue. Dans la pratique, les développeurs dupliquent (fork) ce type de dépôt dans leur propre compte GitHub, y apportent leurs modifications, puis créent des demandes de tirage (pull) pour envoyer ces modifications dans le dépôt d’origine. Ces étapes sont décrites dans [Didacticiel, Étape 6 : Utilisation de Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Didacticiel : Utilisation de Python dans Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Voir aussi

- [Création d’un environnement pour un interpréteur Python existant](managing-python-environments-in-visual-studio.md#creating-an-environment-for-an-existing-interpreter).
- [Installer la prise en charge de Python dans Visual Studio 2015 et antérieur](installing-python-support-in-visual-studio.md).
- [Emplacements d’installation](installing-python-support-in-visual-studio.md#install-locations).
