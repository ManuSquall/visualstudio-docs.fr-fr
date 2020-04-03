---
title: Cloner un dépôt
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: d146d801a1519d3282b4e2c5dd72fd23b0df7206
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638642"
---
# <a name="clone-a-repository-of-python-code-in-visual-studio"></a>Cloner un dépôt de code Python dans Visual Studio

Une fois que vous avez [installé Visual Studio Tools pour IA](installation.md), vous pouvez facilement cloner un dépôt de code Python et créer un projet à partir de celui-ci.

1. Pour vous connecter aux référentiels GitHub, exécutez l’installateur Visual Studio, **sélectionnez Modifier**et sélectionnez **l’onglet Composants individuels.** Faites défiler vers le bas vers la section **des outils de code,** sélectionnez **l’extension GitHub pour Visual Studio**, et sélectionnez **Modifier**.

    ![Sélection de l’extension GitHub dans le programme d’installation de Visual Studio](media/create-project-repo/installation-github-extension.png)

2. Lancez Visual Studio.

3. Sélectionnez **View > Team Explorer** pour ouvrir la fenêtre Team **Explorer** dans laquelle vous pouvez vous connecter à GitHub ou Azure DevOps, ou cloner un référentiel.

    ![Fenêtre Team Explorer montrant Azure DevOps Services, GitHub et le clonage d’un dépôt](media/create-project-repo/team-explorer-devops.png)

4. Dans le champ URL, sous **Dépôts Git locaux**, entrez `https://github.com/Microsoft/samples-for-ai`, entrez un dossier pour les fichiers clonés, puis sélectionnez **Cloner**.

    > [!Tip]
    > Le dossier que vous spécifiez dans Team Explorer est le dossier spécifique pour recevoir les fichiers clonés. Contrairement à la commande `git clone`, la création d’un clone dans Team Explorer ne crée pas automatiquement un sous-dossier avec le nom du dépôt.

5. Quand le clonage est terminé, double-cliquez sur le dossier du dépôt dans le bas de Team Explorer pour accéder au tableau de bord du dépôt. Sous **Solutions**, sélectionnez **Nouveau**.

    ![Fenêtre Team Explorer, création d’un projet à partir d’un clone](media/create-project-repo/team-explorer-new-project.png)

6. Dans le dialogue **new Project** qui apparaît, sélectionnez " From Existing**Python Code**", spécifier un nom pour le projet, définir **l’emplacement** au même dossier que le dépôt, et sélectionnez **OK**. Dans l’Assistant qui apparaît, sélectionnez **Terminer**.

7. Sélectionnez **Affichage > Explorateur de solutions** dans le menu.

8. Dans Solution Explorer, `TensorFlow Examples> MNIST` étendre le nœud, clic `convolutional.py`droit et sélectionnez Set comme startup **File**. Cette étape indique à Visual Studio quel fichier utiliser quand vous exécutez le projet.

9. Appuyez sur **Ctrl**+**F5** ou sélectionnez **Debug > Start Without Debugging** pour exécuter le programme. Si vous voyez une erreur, vérifiez le paramètre du répertoire de travail défini à l’étape précédente.

10. Lorsque le programme s’exécute correctement, vous le voyez commencer à télécharger votre jeu de données d’apprentissage et de test, puis effectuer l’apprentissage du modèle et générer votre taux d’erreur. Vous voulez que le taux d’erreur diminue au fil du temps

    ![Première sortie du programme Python MNIST](media/create-project-repo/tensorflow-mnist-running.png)

   > [!NOTE]
   > Si vous utilisez Anaconda et obtenez une erreur relative à l’absence de numpy, vous devrez peut-être [modifier votre environnement Python pour utiliser Anaconda](../python/selecting-a-python-environment-for-a-project.md).

11. Vous pouvez visualiser la progression avec TensorBoard. Cliquez avec le bouton droit sur votre projet et cliquez sur **Exécuter TensorBoard**, puis sélectionnez le répertoire de vos journaux TensorBoard de sortie.

   ![exécuter tensorboard](media/create-project-repo/run-tensorboard.png)

12. Notez la baisse du taux d’erreurs au fil du temps, ce qui signifie que la qualité s’améliore.

   ![exécuter tensorboard](media/create-project-repo/tensorboard.png)
