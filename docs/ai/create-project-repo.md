---
title: Cloner un dépôt
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 73f1595e0e6c8f182f0bedcece51011390964ed2
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56842526"
---
# <a name="clone-a-repository-of-python-code-in-visual-studio"></a>Cloner un dépôt de code Python dans Visual Studio

Une fois que vous avez [installé Visual Studio Tools pour IA](installation.md), vous pouvez facilement cloner un dépôt de code Python et créer un projet à partir de celui-ci.

1. Pour vous connecter à des dépôts GitHub, exécutez le programme d’installation de Visual Studio, sélectionnez **Modifier**, puis sélectionnez l’onglet **Composants individuels**. Faites défiler jusqu’à la section **Outils de code**, sélectionnez **Extension GitHub pour Visual Studio**, puis sélectionnez **Modifier**.

    ![Sélection de l’extension GitHub dans le programme d’installation de Visual Studio](media/create-project-repo/installation-github-extension.png)

2. Lancez Visual Studio.

3. Sélectionnez **Affichage > Team Explorer** pour ouvrir la fenêtre **Team Explorer** dans laquelle vous pouvez vous connecter à GitHub ou Azure DevOps, ou bien cloner un dépôt.

    ![Fenêtre Team Explorer montrant Azure DevOps Services, GitHub et le clonage d’un dépôt](media/create-project-repo/team-explorer-devops.png)

4. Dans le champ URL, sous **Dépôts Git locaux**, entrez `https://github.com/Microsoft/samples-for-ai`, entrez un dossier pour les fichiers clonés, puis sélectionnez **Cloner**.

    > [!Tip]
    > Le dossier que vous spécifiez dans Team Explorer est le dossier spécifique pour recevoir les fichiers clonés. Contrairement à la commande `git clone`, la création d’un clone dans Team Explorer ne crée pas automatiquement un sous-dossier avec le nom du dépôt.

5. Quand le clonage est terminé, double-cliquez sur le dossier du dépôt dans le bas de Team Explorer pour accéder au tableau de bord du dépôt. Sous **Solutions**, sélectionnez **Nouveau**.

    ![Fenêtre Team Explorer, création d’un projet à partir d’un clone](media/create-project-repo/team-explorer-new-project.png)

6. Dans la boîte de dialogue **Nouveau projet** qui s’affiche, sélectionnez « **À partir de code Python existant** », spécifiez un nom pour le projet, définissez **Emplacement** sur le même dossier que le dépôt, puis sélectionnez **OK**. Dans l’Assistant qui apparaît, sélectionnez **Terminer**.

7. Sélectionnez **Affichage > Explorateur de solutions** dans le menu.

8. Dans l’Explorateur de solutions, développez le nœud `TensorFlow Examples> MNIST`, cliquez avec le bouton droit sur `convolutional.py`, puis sélectionnez **Définir comme fichier de démarrage**. Cette étape indique à Visual Studio quel fichier utiliser quand vous exécutez le projet.

9. Appuyez sur **Ctrl**+**F5** ou sélectionnez **Déboguer > Démarrer sans débogage** pour exécuter le programme. Si vous voyez une erreur, vérifiez le paramètre du répertoire de travail défini à l’étape précédente.

10. Lorsque le programme s’exécute correctement, vous le voyez commencer à télécharger votre jeu de données d’apprentissage et de test, puis effectuer l’apprentissage du modèle et générer votre taux d’erreur. Vous voulez que le taux d’erreur diminue au fil du temps

    ![Première sortie du programme Python MNIST](media/create-project-repo/tensorflow-mnist-running.png)

   > [!NOTE]
   > Si vous utilisez Anaconda et obtenez une erreur relative à l’absence de numpy, vous devrez peut-être [modifier votre environnement Python pour utiliser Anaconda](../python/selecting-a-python-environment-for-a-project.md).

11. Vous pouvez visualiser la progression avec TensorBoard. Cliquez avec le bouton droit sur votre projet et cliquez sur **Exécuter TensorBoard**, puis sélectionnez le répertoire de vos journaux TensorBoard de sortie.

   ![exécuter tensorboard](media/create-project-repo/run-tensorboard.png)

12. Notez la baisse du taux d’erreurs au fil du temps, ce qui signifie que la qualité s’améliore.

   ![exécuter tensorboard](media/create-project-repo/tensorboard.png)
