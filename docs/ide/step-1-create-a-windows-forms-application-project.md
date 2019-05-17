---
title: 'Étape 1 : Créer un projet Application Windows Forms'
ms.date: 03/23/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7f529d737816406b3a4f6aa9921a8dc6b902d2fb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979856"
---
# <a name="step-1-create-a-windows-forms-application-project"></a>Étape 1 : Créer un projet Application Windows Forms

Lorsque vous créez une visionneuse d’images, la première étape consiste à créer un projet d’application Windows Forms.

 > [!TIP]
 > ![lien vers la vidéo](../data-tools/media/playvideo.gif)Pour obtenir une version vidéo de cette rubrique, consultez [Turoriel 1 : Créer une visionneuse d’images en Visual Basic – vidéo 1](http://go.microsoft.com/fwlink/?LinkId=205209) ou [Tutoriel 1 : Créer une visionneuse d'images en C# - Vidéo 1](http://go.microsoft.com/fwlink/?LinkId=205199). Ces vidéos utilisent une version antérieure de Visual Studio et présentent donc de légères différences quant à certaines commandes de menu et autres éléments d’interface utilisateur. Toutefois, les concepts et les procédures fonctionnent de façon similaire dans la version actuelle de Visual Studio.

::: moniker range="vs-2017"

## <a name="open-visual-studio-2017"></a>Ouvrez Visual Studio 2017.

1. Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet**. La boîte de dialogue doit se présenter comme suit.

     ![Nouveau projet, boîte de dialogue](../ide/media/newprojectdialogcallouts.png)<br/>
*Boîte de dialogue **Nouveau projet***

2. Choisissez **Visual C#** ou **Visual Basic** dans la partie gauche de la boîte de dialogue **Nouveau projet**.

3. Dans la liste des modèles, choisissez **Application Windows Forms (.NET Framework)**. Nommez le nouveau formulaire **PictureViewer**, puis sélectionnez le bouton **OK**.

    >[!NOTE]
    >Si vous ne voyez pas le modèle **Application Windows Forms (.NET Framework)**, utilisez Visual Studio Installer pour installer la charge de travail **Développement .NET Desktop**.<br/><br/>![Charge de travail de développement .NET Desktop dans Visual Studio Installer](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Pour plus d’informations, consultez la page [Installer Visual Studio](../install/install-visual-studio.md).

::: moniker-end

::: moniker range="vs-2019"

## <a name="open-visual-studio-2019"></a>Ouvrir Visual Studio 2019

1. Dans la fenêtre de démarrage, choisissez **Créer un projet**.

   ![Afficher la fenêtre « Créer un projet »](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Dans la fenêtre **Créer un projet**, entrez ou tapez *Windows Forms* dans la zone de recherche. Ensuite, choisissez **Visual Basic** dans la liste des langages, puis choisissez **Windows** dans la liste des plateformes. 

   Après avoir appliqué les filtres de langage et de plateforme, choisissez le modèle **Application Windows Forms (.NET Framework)**, puis choisissez **Suivant**.

   ![Choisir le modèle Visual Basic pour l’application Windows Forms (.NET Framework)](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Si vous ne voyez pas le modèle **Windows Forms (.NET Framework)**, vous pouvez l’installer à partir de la fenêtre **Créer un projet**. Dans le **Vous ne trouvez pas ce que vous cherchez ?**, choisissez le lien **Installer plus d’outils et de fonctionnalités**.
   >
   > ![Le lien « Installer plus d’outils et de fonctionnalités » du message « Vous ne trouvez pas ce que vous cherchez ? » dans la fenêtre « Créer un projet »](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Ensuite, dans Visual Studio Installer, choisissez la charge de travail **Développement .NET Desktop**.
   > 
   > ![Charge de travail .NET Core dans Visual Studio Installer](../ide/media/install-dot-net-desktop-env.png)
   >
   > Après cela, choisissez le bouton **Modifier** dans Visual Studio Installer. Vous pouvez être invité à enregistrer votre travail ; le cas échéant, faites-le. Ensuite, choisissez **Continuer** pour installer la charge de travail. 

1. Dans la fenêtre **Configurer votre nouveau projet**, tapez ou entrez *PictureViewer* dans la zone **Nom du projet**. Choisissez ensuite **Créer**.

::: moniker-end

Visual Studio crée une solution pour votre programme. Une solution joue le rôle de conteneur pour tous les projets et fichiers requis par votre programme. Ces termes seront expliqués plus en détail dans les prochaines étapes de ce didacticiel.

## <a name="about-the-windows-forms-application-project"></a>À propos du projet Application Windows Forms

1. L’environnement de développement contient trois fenêtres : une fenêtre principale, l’**Explorateur de solutions** et la fenêtre **Propriétés**.

     Si l’une de ces fenêtres est manquante, restaurez la disposition de fenêtre par défaut en sélectionnant dans la barre de menus **Fenêtre** > **Rétablir la disposition de fenêtre**. Vous pouvez également afficher les fenêtres à l'aide des commandes de menu. Dans la barre de menus, choisissez **Affichage** > **Fenêtre Propriétés** ou **Explorateur de solutions**. Si d’autres fenêtres sont ouvertes, fermez-les en choisissant le bouton **Fermer** (x) dans l’angle supérieur droit.

    ::: moniker range="vs-2017"

    - **Fenêtre principale** Dans cette fenêtre, vous effectuez la majeure partie de votre travail, notamment l’utilisation des formulaires et la modification du code. La fenêtre montre un formulaire dans l’**éditeur de formulaires**. En haut de la fenêtre, les onglets **Page de démarrage** et **Form1.cs [Design]** s’affichent. (En Visual Basic, le nom d'un onglet se termine par *.vb* au lieu de *.cs*.)

    ::: moniker-end

    ::: moniker range=">=vs-2019"

    - **Fenêtre principale** Dans cette fenêtre, vous effectuez la majeure partie de votre travail, notamment l’utilisation des formulaires et la modification du code. La fenêtre montre un formulaire dans l’**éditeur de formulaires**.

    ::: moniker-end

    - **Fenêtre Explorateur de solutions** Dans cette fenêtre, vous pouvez afficher tous les éléments de votre solution et y accéder. Si vous sélectionnez un fichier, le contenu de la fenêtre **Propriétés** est modifié. Si vous ouvrez un fichier de code (qui se termine par *.cs* en Visual C# et par *.vb* en Visual Basic), le fichier de code ou un concepteur pour le fichier de code s'affiche. Un concepteur est une surface visuelle à laquelle vous pouvez ajouter des contrôles tels que des boutons et des listes. Pour les formulaires Visual Studio, le concepteur est appelé **Concepteur Windows Forms**.

    - **Fenêtre Propriétés** Elle vous permet de modifier les propriétés des éléments que vous choisissez dans les autres fenêtres. Par exemple, si vous sélectionnez Form1, vous pouvez modifier son titre en définissant la propriété **Text**, et vous pouvez modifier la couleur d’arrière-plan en définissant la propriété **Backcolor**.

    > [!NOTE]
    > La première ligne de l’**Explorateur de solutions** affiche **Solution « PictureViewer » (1 projet)**, ce qui signifie que Visual Studio a créé une solution pour vous. Une solution peut contenir plusieurs projets, mais, pour le moment, vous utiliserez des solutions contenant un seul projet.

1. Dans la barre de menus, sélectionnez **Fichier** > **Enregistrer tout**.

     Vous pouvez aussi sélectionner le bouton **Enregistrer tout**, présenté dans l’illustration suivante, dans la barre d’outils.

     ![Enregistrer tout, bouton de barre d’outils](../ide/media/express_iconsaveall.png)<br/>
     *Bouton de barre d’outils **Enregistrer tout***

     Visual Studio renseigne automatiquement le nom du dossier et le nom du projet, puis crée le projet dans votre dossier de projets.

## <a name="to-continue-or-review"></a>Pour continuer ou examiner

- Pour passer à l’étape suivante du tutoriel, consultez [Étape 2 : Exécuter votre programme](../ide/step-2-run-your-program.md).

- Pour revenir à la rubrique de vue d’ensemble, consultez [Tutoriel 1 : Créer une visionneuse d’images](../ide/tutorial-1-create-a-picture-viewer.md).

## <a name="see-also"></a>Voir aussi

- [Création d’un Windows Form](/dotnet/framework/winforms/creating-a-new-windows-form/)