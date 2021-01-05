---
title: Cloner un dépôt
description: Découvrez comment utiliser Visual Studio Tools for AI pour cloner un référentiel de code Python et créer un projet à partir de celui-ci.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 303c410bf519561844d95cc13fa036534ddb2aa7
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726616"
---
# <a name="clone-a-repository-of-python-code-in-visual-studio"></a>Cloner un dépôt de code Python dans Visual Studio

Une fois que vous avez [installé Visual Studio Tools pour IA](installation.md), vous pouvez facilement cloner un dépôt de code Python et créer un projet à partir de celui-ci.

1. Pour vous connecter aux référentiels GitHub, exécutez le programme d’installation de Visual Studio, sélectionnez **modifier**, puis sélectionnez l’onglet **composants individuels** . Faites défiler jusqu’à la section **outils de code** , sélectionnez **extension GitHub pour Visual Studio**, puis sélectionnez **modifier**.

    ![Sélection de l’extension GitHub dans le programme d’installation de Visual Studio](media/create-project-repo/installation-github-extension.png)

2. Lancez Visual Studio.

3. Sélectionnez **afficher > Team Explorer** pour ouvrir la fenêtre **Team Explorer** dans laquelle vous pouvez vous connecter à GitHub ou à Azure DevOps, ou cloner un référentiel.

    ![Fenêtre Team Explorer montrant Azure DevOps Services, GitHub et le clonage d’un dépôt](media/create-project-repo/team-explorer-devops.png)

4. Dans le champ URL, sous **Dépôts Git locaux**, entrez `https://github.com/Microsoft/samples-for-ai`, entrez un dossier pour les fichiers clonés, puis sélectionnez **Cloner**.

    > [!Tip]
    > Le dossier que vous spécifiez dans Team Explorer est le dossier spécifique pour recevoir les fichiers clonés. Contrairement à la commande `git clone`, la création d’un clone dans Team Explorer ne crée pas automatiquement un sous-dossier avec le nom du dépôt.

5. Quand le clonage est terminé, double-cliquez sur le dossier du dépôt dans le bas de Team Explorer pour accéder au tableau de bord du dépôt. Sous **Solutions**, sélectionnez **Nouveau**.

    ![Fenêtre Team Explorer, création d’un projet à partir d’un clone](media/create-project-repo/team-explorer-new-project.png)

6. Dans la boîte de dialogue **nouveau projet** qui s’affiche, sélectionnez «**à partir de code python existant**», spécifiez un nom pour le projet, définissez **emplacement** sur le même dossier que le dépôt, puis sélectionnez **OK**. Dans l’Assistant qui apparaît, sélectionnez **Terminer**.

7. Sélectionnez **Affichage > Explorateur de solutions** dans le menu.

8. Dans Explorateur de solutions, développez le `TensorFlow Examples> MNIST` nœud, cliquez avec le bouton droit `convolutional.py` et sélectionnez **définir comme fichier de démarrage**. Cette étape indique à Visual Studio quel fichier utiliser quand vous exécutez le projet.

9. Appuyez sur **CTRL** + **F5** ou sélectionnez **Déboguer > exécuter sans débogage** pour exécuter le programme. Si vous voyez une erreur, vérifiez le paramètre du répertoire de travail défini à l’étape précédente.

10. Lorsque le programme s’exécute correctement, vous le voyez commencer à télécharger votre jeu de données d’apprentissage et de test, puis effectuer l’apprentissage du modèle et générer votre taux d’erreur. Vous voulez que le taux d’erreur diminue au fil du temps

    ![Première sortie du programme Python MNIST](media/create-project-repo/tensorflow-mnist-running.png)

   > [!NOTE]
   > Si vous utilisez Anaconda et obtenez une erreur relative à l’absence de numpy, vous devrez peut-être [modifier votre environnement Python pour utiliser Anaconda](../python/selecting-a-python-environment-for-a-project.md).

11. Vous pouvez visualiser la progression avec TensorBoard. Cliquez avec le bouton droit sur votre projet et cliquez sur **Exécuter TensorBoard**, puis sélectionnez le répertoire de vos journaux TensorBoard de sortie.

   ![Capture d’écran de l’Explorateur de solutions Visual Studio avec le projet MNIST sélectionné et l’option exécuter TensorBoard sélectionnée dans le menu contextuel.](media/create-project-repo/run-tensorboard.png)

12. Notez la baisse du taux d’erreurs au fil du temps, ce qui signifie que la qualité s’améliore.

   ![Capture d’écran de la fenêtre principale TensorBoard montrant quatre graphiques qui illustrent les données des journaux TensorBoard.](media/create-project-repo/tensorboard.png)
