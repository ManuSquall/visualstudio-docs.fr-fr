---
title: 'Étape 1 : Créer un projet Windows Forms App'
ms.date: 08/30/2019
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2d5e34d825d2a4d296a8a394105b412195b4e3fb
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579914"
---
# <a name="step-1-create-a-windows-forms-app-project"></a>Étape 1 : Créer un projet Windows Forms App

Lorsque vous créez un visualiseur d’images, la première étape consiste à créer un projet Windows Forms App.

::: moniker range="vs-2017"

## <a name="open-visual-studio-2017"></a>Ouvrez Visual Studio 2017.

1. Sur la barre de menu, choisissez **File** > **New** > **Project**. La boîte de dialogue doit ressembler à la capture d’écran suivante.

     ![Nouveau projet, boîte de dialogue](../ide/media/newprojectdialogcallouts.png)<br/>***Boîte de dialogue*** *Nouveau projet*

2. Sur le côté gauche de la boîte de dialogue **New Project,** choisissez soit **Visual C** ou **Visual Basic**, puis choisissez **Windows Desktop**.

3. Dans la liste des modèles de projet, choisissez **Windows Forms App (.NET Framework)**. Nommez le nouveau formulaire *PictureViewer*, puis sélectionnez le bouton **OK**.

    >[!NOTE]
    >Si vous ne voyez pas le modèle **Application Windows Forms (.NET Framework)**, utilisez Visual Studio Installer pour installer la charge de travail **Développement .NET Desktop**.<br/><br/>![Charge de travail de développement .NET Desktop dans Visual Studio Installer](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Pour plus d’informations, consultez la page [Installer Visual Studio](../install/install-visual-studio.md).

::: moniker-end

::: moniker range="vs-2019"

## <a name="open-visual-studio-2019"></a>Ouvrir Visual Studio 2019

1. Sur la fenêtre de départ, choisissez **Créer un nouveau projet**.

   ![Afficher la fenêtre « Créer un projet »](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Dans la fenêtre **Créer un projet**, entrez ou tapez *Windows Forms* dans la zone de recherche. Ensuite, choisissez **Desktop** parmi la liste **de type Projet.**

   Après avoir appliqué le filtre **de type Projet,** choisissez le modèle **Windows Forms App (.NET Framework)** pour C ou Visual Basic, puis choisissez **Next**.

   ![Choisissez le modèle de base visuel ou Cmd pour l’application formulaires Windows (.NET Framework)](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Si vous ne voyez pas le modèle **Windows Forms App (.NET Framework),** vous pouvez l’installer à partir de la **fenêtre Créer un nouveau projet.** Dans le **Vous ne trouvez pas ce que vous cherchez ?**, choisissez le lien **Installer plus d’outils et de fonctionnalités**.
   >
   > ![Le lien « Installer plus d’outils et de fonctionnalités » du message « Vous ne trouvez pas ce que vous cherchez ? » dans la fenêtre « Créer un projet »](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Ensuite, dans Visual Studio Installer, choisissez la charge de travail **Développement .NET Desktop**.
   >
   > ![Charge de travail .NET Core dans Visual Studio Installer](../ide/media/install-dot-net-desktop-env.png)
   >
   > Après cela, choisissez le bouton **Modifier** dans Visual Studio Installer. Vous pouvez être invité à enregistrer votre travail ; le cas échéant, faites-le. Ensuite, choisissez **Continuer** pour installer la charge de travail.

1. Dans la fenêtre **Configurer votre nouveau projet**, tapez ou entrez *PictureViewer* dans la zone **Nom du projet**. Ensuite, choisissez **Créer**.

::: moniker-end

Visual Studio crée une solution pour votre application. Une solution agit comme un conteneur pour tous les projets et fichiers nécessaires à votre application. Ces termes seront expliqués plus en détail dans les prochaines étapes de ce didacticiel.

## <a name="about-the-windows-forms-app-project"></a>À propos du projet Windows Forms App

1. L’environnement de développement contient trois fenêtres : une fenêtre principale, l’**Explorateur de solutions** et la fenêtre **Propriétés**.

     Si l’une de ces fenêtres est manquante, vous pouvez restaurer la disposition de la fenêtre par défaut. Sur la barre de menu, choisissez **Window** > **Reset Window Layout**.

     Vous pouvez également afficher les fenêtres à l'aide des commandes de menu. Sur la barre de menu, choisissez **View** > **Properties Window** ou Solution **Explorer**.

     Si d’autres fenêtres sont ouvertes, fermez-les en choisissant le bouton **Fermer** (x) dans l’angle supérieur droit.

    ::: moniker range="vs-2017"

    * **Fenêtre principale** Dans cette fenêtre, vous effectuez la majeure partie de votre travail, notamment l’utilisation des formulaires et la modification du code. La fenêtre montre un formulaire dans l’**éditeur de formulaires**. En haut de la fenêtre, les onglets **Page de démarrage** et **Form1.cs [Design]** s’affichent. (En Visual Basic, le nom d'un onglet se termine par *.vb* au lieu de *.cs*.)

    ::: moniker-end

    ::: moniker range=">=vs-2019"

    * **Fenêtre principale** Dans cette fenêtre, vous effectuez la majeure partie de votre travail, notamment l’utilisation des formulaires et la modification du code. La fenêtre montre un formulaire dans l’**éditeur de formulaires**.

    ::: moniker-end

    * **Fenêtre Explorateur de solutions** Dans cette fenêtre, vous pouvez afficher tous les éléments de votre solution et y accéder.

    Si vous sélectionnez un fichier, le contenu de la fenêtre **Propriétés** est modifié. Si vous ouvrez un fichier de code (qui se termine en *.cs* dans C et *.vb* dans Visual Basic), le fichier de code ou un concepteur pour le fichier de code apparaît. Un concepteur est une surface visuelle à laquelle vous pouvez ajouter des contrôles tels que des boutons et des listes. Pour les formulaires Visual Studio, le concepteur est appelé **Concepteur Windows Forms**.

    * **Fenêtre Propriétés** Elle vous permet de modifier les propriétés des éléments que vous choisissez dans les autres fenêtres. Par exemple, si vous sélectionnez Form1, vous pouvez modifier son titre en définissant la propriété **Text**, et vous pouvez modifier la couleur d’arrière-plan en définissant la propriété **Backcolor**.

      > [!NOTE]
      > La première ligne de l’**Explorateur de solutions** affiche **Solution « PictureViewer » (1 projet)**, ce qui signifie que Visual Studio a créé une solution pour vous. Une solution peut contenir plusieurs projets, mais, pour le moment, vous utiliserez des solutions contenant un seul projet.

1. Sur la barre de menu, choisissez **File** > **Save All**.

     Comme alternative, choisissez le bouton **Enregistrer tous** sur la barre d’outils, que l’image suivante montre.

     ![Enregistrer tout, bouton de barre d’outils](../ide/media/express_iconsaveall.png)<br/>
     ***Enregistrer tous les*** *boutons de barre d’outils*

     Visual Studio renseigne automatiquement le nom du dossier et le nom du projet, puis crée le projet dans votre dossier de projets.

## <a name="next-steps"></a>Étapes suivantes

* Pour passer à l’étape suivante tutoriel, voir **[Étape 2: Exécuter votre application](../ide/step-2-run-your-program.md)**.

* Pour revenir à la rubrique de présentation, consultez [Tutoriel 1 : créer une visionneuse d’images](../ide/tutorial-1-create-a-picture-viewer.md).

## <a name="see-also"></a>Voir aussi

* [Tutorial 2: Créer un quiz de mathématiques chronométré](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Créer un jeu correspondant](tutorial-3-create-a-matching-game.md)
