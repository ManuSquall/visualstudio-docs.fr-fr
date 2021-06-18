---
title: 'Étape 1 : Créer un projet d’application Windows Forms'
description: Découvrez comment créer un projet d’application Windows Forms pour votre visionneuse d’images.
ms.custom: SEO-VS-2020
ms.date: 08/30/2019
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fccce125b66101b05544cba22b3724a8a40dc0f3
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307737"
---
# <a name="step-1-create-a-windows-forms-app-project"></a>Étape 1 : Créer un projet d’application Windows Forms

Lorsque vous créez une visionneuse d’images, la première étape consiste à créer un projet d’application Windows Forms.

::: moniker range="vs-2017"

## <a name="open-visual-studio-2017"></a>Ouvrez Visual Studio 2017.

1. Dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet**. La boîte de dialogue doit ressembler à la capture d’écran suivante.

     ![Nouveau projet, boîte de dialogue](../ide/media/newprojectdialogcallouts.png)<br/>***Nouveau projet** _ _dialog Box *

2. Sur le côté gauche de la boîte de dialogue **nouveau projet** , choisissez **Visual C#** ou **Visual Basic**, puis choisissez **Bureau Windows**.

3. Dans la liste modèles de projet, choisissez **Windows Forms application (.NET Framework)**. Nommez le nouveau formulaire *PictureViewer*, puis sélectionnez le bouton **OK**.

    >[!NOTE]
    >Si vous ne voyez pas le modèle **Application Windows Forms (.NET Framework)**, utilisez Visual Studio Installer pour installer la charge de travail **Développement .NET Desktop**.<br/><br/>![Charge de travail de développement .NET Desktop dans Visual Studio Installer](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Pour plus d’informations, consultez la page [Installer Visual Studio](../install/install-visual-studio.md).

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="open-visual-studio"></a>Ouvrez Visual Studio.

1. Dans la fenêtre Démarrer, choisissez **créer un nouveau projet**.

   ![Afficher la fenêtre « Créer un projet »](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Dans la fenêtre **Créer un projet**, entrez ou tapez *Windows Forms* dans la zone de recherche. Ensuite, choisissez **Bureau** dans la liste **type de projet** .

   Après avoir appliqué le filtre de **type de projet** , choisissez le modèle d' **application Windows Forms (.NET Framework)** pour C# ou Visual Basic, puis choisissez **suivant**.

   ![Choisir le modèle C# ou Visual Basic pour l’application Windows Forms (.NET Framework)](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Si vous ne voyez pas le modèle d' **application Windows Forms (.NET Framework)** , vous pouvez l’installer à partir de la fenêtre **créer un nouveau projet** . Dans le **Vous ne trouvez pas ce que vous cherchez ?**, choisissez le lien **Installer plus d’outils et de fonctionnalités**.
   >
   > ![Le lien « Installer plus d’outils et de fonctionnalités » du message « Vous ne trouvez pas ce que vous cherchez ? » dans la fenêtre « Créer un projet »](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Ensuite, dans Visual Studio Installer, choisissez la charge de travail **Développement .NET Desktop**.
   >
   > ![Charge de travail .NET Core dans Visual Studio Installer](../ide/media/install-dot-net-desktop-env.png)
   >
   > Après cela, choisissez le bouton **Modifier** dans Visual Studio Installer. Vous pouvez être invité à enregistrer votre travail ; le cas échéant, faites-le. Ensuite, choisissez **Continuer** pour installer la charge de travail.

1. Dans la fenêtre **Configurer votre nouveau projet**, tapez ou entrez *PictureViewer* dans la zone **Nom du projet**. Ensuite, choisissez **créer**.

::: moniker-end

Visual Studio crée une solution pour votre application. Une solution agit comme un conteneur pour tous les projets et fichiers requis par votre application. Ces termes seront expliqués plus en détail dans les prochaines étapes de ce didacticiel.

## <a name="about-the-windows-forms-app-project"></a>À propos du projet d’application Windows Forms

1. L’environnement de développement contient trois fenêtres : une fenêtre principale, l’**Explorateur de solutions** et la fenêtre **Propriétés**.

     Si l’une de ces fenêtres est manquante, vous pouvez restaurer la disposition de fenêtre par défaut. Dans la barre de menus, choisissez **fenêtre**  >  **Réinitialiser la disposition de fenêtre**.

     Vous pouvez également afficher les fenêtres à l'aide des commandes de menu. Dans la barre de menus, choisissez **Afficher** la  >  **fenêtre Propriétés** ou **Explorateur de solutions**.

     Si d’autres fenêtres sont ouvertes, fermez-les en choisissant le bouton **Fermer** (x) dans l’angle supérieur droit.

    ::: moniker range="vs-2017"

    * **Fenêtre principale** Dans cette fenêtre, vous effectuez la majeure partie de votre travail, notamment l’utilisation des formulaires et la modification du code. La fenêtre montre un formulaire dans l’**éditeur de formulaires**. En haut de la fenêtre, les onglets **Page de démarrage** et **Form1.cs [Design]** s’affichent. (En Visual Basic, le nom d'un onglet se termine par *.vb* au lieu de *.cs*.)

    ::: moniker-end

    ::: moniker range=">=vs-2019"

    * **Fenêtre principale** Dans cette fenêtre, vous effectuez la majeure partie de votre travail, notamment l’utilisation des formulaires et la modification du code. La fenêtre montre un formulaire dans l’**éditeur de formulaires**.

    ::: moniker-end

    * **Fenêtre Explorateur de solutions** Dans cette fenêtre, vous pouvez afficher tous les éléments de votre solution et y accéder.

    Si vous sélectionnez un fichier, le contenu de la fenêtre **Propriétés** est modifié. Si vous ouvrez un fichier de code (qui se termine par *. cs* en C# et *. vb* dans Visual Basic), le fichier de code ou un concepteur pour le fichier de code s’affiche. Un concepteur est une surface visuelle à laquelle vous pouvez ajouter des contrôles tels que des boutons et des listes. Pour les formulaires Visual Studio, le concepteur est appelé **Concepteur Windows Forms**.

    * **Fenêtre Propriétés** Elle vous permet de modifier les propriétés des éléments que vous choisissez dans les autres fenêtres. Par exemple, si vous sélectionnez Form1, vous pouvez modifier son titre en définissant la propriété **Text**, et vous pouvez modifier la couleur d’arrière-plan en définissant la propriété **Backcolor**.

      > [!NOTE]
      > La première ligne de l’**Explorateur de solutions** affiche **Solution « PictureViewer » (1 projet)**, ce qui signifie que Visual Studio a créé une solution pour vous. Une solution peut contenir plusieurs projets, mais, pour le moment, vous utiliserez des solutions contenant un seul projet.

1. Dans la barre de menus, choisissez **fichier**  >  **enregistrer tout**.

     Vous pouvez également cliquer sur le bouton **enregistrer tout** de la barre d’outils, comme le montre l’image suivante.

     ![Enregistrer tout, bouton de barre d’outils](../ide/media/express_iconsaveall.png)<br/>
     *Bouton **enregistrer tout** _ _toolbar *

     Visual Studio renseigne automatiquement le nom du dossier et le nom du projet, puis crée le projet dans votre dossier de projets.

## <a name="next-steps"></a>Étapes suivantes

* Pour passer à l’étape suivante du didacticiel, consultez **[étape 2 : exécuter votre application](../ide/step-2-run-your-program.md)**.

* Pour revenir à la rubrique de présentation, consultez [Tutoriel 1 : créer une visionneuse d’images](../ide/tutorial-1-create-a-picture-viewer.md).

## <a name="see-also"></a>Voir aussi

* [Didacticiel 2 : créer un questionnaire mathématique chronométré](tutorial-2-create-a-timed-math-quiz.md)
* [Didacticiel 3 : créer un jeu de combinaisons](tutorial-3-create-a-matching-game.md)
