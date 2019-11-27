---
title: 'Procédure pas à pas : Génération d’une application | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 4842955d-8959-4e4e-98b8-2358360179b3
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f2d9b958dacfb35877abc9ad1e83a349e43a7af0
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296873"
---
# <a name="walkthrough-building-an-application"></a>Procédure pas à pas : génération d'une application

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Avec cette procédure pas à pas, vous allez vous familiariser avec plusieurs options qu’il est possible de configurer lors de la génération d’applications avec Visual Studio. Dans l’exemple d’application, vous allez créer une configuration de build personnalisée, masquer certains messages d’avertissement et afficher davantage d’informations de sortie de build, entre autres tâches.

Cette rubrique contient les sections suivantes :

[Installer l’exemple d’application](../ide/walkthrough-building-an-application.md)

[Créer une configuration de build personnalisée](../ide/walkthrough-building-an-application.md#BKMK_CreateBuildConfig)

[Générer l’application](../ide/walkthrough-building-an-application.md#BKMK_building)

[Masquer les avertissements du compilateur](../ide/walkthrough-building-an-application.md#BKMK_hidewarning)

[Afficher des informations de build supplémentaires dans la fenêtre Sortie](../ide/walkthrough-building-an-application.md#BKMK_outputdetails)

[Créer une version Release](../ide/walkthrough-building-an-application.md)

#### <a name="to-install-the-sample-application"></a>Pour installer l’exemple d’application

1. Dans la barre de menus, choisissez **Outils**, puis **Extensions et mises à jour**.

2. Sélectionnez la catégorie **En ligne**, puis la catégorie **Galerie d’exemples**.

3. Spécifiez `Introduction` dans la zone de recherche pour rechercher l’exemple.

    ![Extensions et mises à jour, boîte de dialogue](../ide/media/buildwalk-extensionsdialogsampledownload.png "BuildWalk_ExtensionsDialogSampleDownload")

4. Dans la liste des résultats, choisissez **Introduction to Building WPF Applications (Visual C#)** ou **Introduction to Building WPF Applications (Visual Basic)** .

5. Cliquez sur le bouton **Télécharger**, puis cliquez sur le bouton **Fermer**.

   L’exemple Introduction to Building WPF Applications s’affiche dans la boîte de dialogue **Nouveau projet**.

#### <a name="to-create-a-solution-for-the-sample-application"></a>Pour créer une solution pour l’exemple d’application

1. Ouvrez la boîte de dialogue **Nouveau projet**.

     ![Dans la barre de menus, choisissez Fichier, Nouveau, Projet](../ide/media/exploreide-filenewproject.png "ExploreIDE-FileNewProject")

2. Dans la catégorie **Installé**, choisissez la catégorie **Exemples** pour afficher l’exemple Introduction to Building WPF Applications.

3. Nommez la solution `IntroWPFcsharp` pour Visual C#.

     ![Boîte de dialogue Nouveau projet, exemples installés](../ide/media/buildwalk-newprojectdlgintrotowpfsample.png "BuildWalk_NewProjectdlgIntrotoWPFsample")

     \- OU -

     Nommez la solution `IntroWPFvb` pour Visual Basic.

     ![Boîte de dialogue Nouveau projet, Visual Basic exemple](../ide/media/buildwalk-newprojectdlgintrotowpfsamplevb.png "BuildWalk_NewProjectdlgIntrotoWPFsampleVB")

4. Choisissez le bouton **OK**.

## <a name="BKMK_CreateBuildConfig"></a>Créer une configuration de build personnalisée

Lorsque vous créez une solution, les configurations de build Debug et Release, et leurs plateformes cibles par défaut, sont automatiquement définies pour la solution. Vous pouvez ensuite personnaliser ces configurations ou créer les vôtres. Les configurations de build spécifient le type de build. Les plateformes de build spécifient le système d’exploitation qui est ciblé par une application pour cette configuration. Pour plus d’informations, consultez [Présentation des configurations de build](../ide/understanding-build-configurations.md), [Présentation des plateformes de générations](../ide/understanding-build-platforms.md) et [Configurations de projet Debug et Release](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

Vous pouvez modifier ou créer des configurations et des paramètres de plateforme dans la boîte de dialogue **Gestionnaire de configurations**. Dans cette procédure, vous allez créer une configuration de build à des fins de test.

#### <a name="to-create-a-build-configuration"></a>Pour créer une configuration de build

1. Ouvrez la boîte de dialogue **Gestionnaire de configurations**.

    ![Menu Générer, commande Configuration Manager](../ide/media/buildwalk-configurationmanagerdialogbox.png "BuildWalk_ConfigurationManagerDialogBox")

2. Dans la liste **Configuration de la solution active**, choisissez **Nouveau**.

3. Dans la boîte de dialogue **Nouvelle configuration de solution**, attribuez à la nouvelle configuration le nom de `Test`, copiez les paramètres de la configuration Debug existante, puis cliquez sur le bouton **OK**.

    ![Boîte de dialogue nouvelle configuration de solution](../ide/media/buildwalk-newsolutionconfigdlgbox.png "BuildWalk_NewSolutionConfigDlgBox")

4. Dans la liste **Plateforme de la solution active**, choisissez **Nouveau**.

5. Dans la boîte de dialogue **Nouvelle plateforme de solution**, sélectionnez **x64** et ne copiez pas les paramètres de la plateforme x86.

    ![Boîte de dialogue nouvelle plateforme de solution](../ide/media/buildwalk-newsolutionplatform.png "BuildWalk_NewSolutionPlatform")

6. Choisissez le bouton **OK**.

   La configuration de la solution active a été remplacée par la configuration de test et la plateforme de la solution active a été définie sur x64.

   ![Configuration Manager avec la configuration de test](../ide/media/buildwalk-configmanagertestconfig.png "BuildWalk_ConfigManagerTestconfig")

   Vous pouvez rapidement vérifier ou modifier la configuration de la solution active à l’aide de la liste **Configurations de solutions** présente dans la barre d’outils **Standard**.

   ![Barre d’outils standard de l’option de configuration de solution](../ide/media/buildwalk-standardtoolbarsolutioncongfig.png "BuildWalk_StandardToolbarSolutionCongfig")

## <a name="BKMK_building"></a> Générer l’application

Ensuite, vous allez générer la solution avec la configuration de build personnalisée.

#### <a name="to-build-the-solution"></a>Pour générer la solution

- Dans la barre de menus, choisissez **Générer**, puis **Générer la solution**.

  La fenêtre **Sortie** affiche les résultats de la génération. La génération a réussi, mais plusieurs messages d’avertissement ont été générés.

  Figure 1 : Avertissements Visual Basic

  ![Fenêtre Sortie Visual Basic](../ide/media/buildwalk-vbbuildoutputwnd.png "BuildWalk_VBBuildOutputWnd")

  Figure 2 : Avertissements Visual C#

  ![Fenêtre Sortie Visual C&#35;](../ide/media/buildwalk-csharpbuildoutputwnd.png "BuildWalk_CsharpBuildOutputWnd")

## <a name="BKMK_hidewarning"></a> Masquer les avertissements du compilateur

Vous pouvez temporairement masquer certains messages d’avertissement pendant la génération, pour éviter qu’ils n’encombrent la fenêtre Sortie.

#### <a name="to-hide-a-specific-visual-c-warning"></a>Pour masquer un avertissement Visual C#

1. Dans l’**Explorateur de solutions**, choisissez le premier nœud de projet.

2. Dans la barre de menus, sélectionnez **Afficher**, **Pages de propriétés**.

     Le **Concepteur de projets** s’ouvre.

3. Choisissez la page **Générer**, puis, dans la boîte de dialogue **Supprimer les avertissements**, spécifiez le numéro d’avertissement `1762`.

     ![Générer, page du concepteur de projets](../ide/media/buildwalk-csharpsuppresswarnings.png "BuildWalk_CsharpSuppressWarnings")

     Pour plus d’informations, consultez [Générer, page du Concepteur de projets (C#)](../ide/reference/build-page-project-designer-csharp.md).

4. Générez la solution.

     La fenêtre **Sortie** affiche uniquement le résumé de la génération.

     ![Fenêtre Sortie, avertissements de&#35; génération Visual C](../ide/media/buildwalk-visualcsharpbuildwarnings.png "BuildWalk_VisualCsharpBuildWarnings")

#### <a name="to-suppress-all-visual-basic-build-warnings"></a>Pour supprimer tous les avertissements de génération de Visual Basic

1. Dans l’**Explorateur de solutions**, choisissez le premier nœud de projet.

2. Dans la barre de menus, sélectionnez **Afficher**, **Pages de propriétés**.

    Le **Concepteur de projets** s’ouvre.

3. Dans la page **Compiler**, cochez la case **Désactiver tous les avertissements**.

    ![Page compiler, concepteur de projets](../ide/media/buildwalk-vbsuppresswarnings.png "BuildWalk_VBSuppressWarnings")

    Pour plus d’informations, consultez [Configuration d’avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).

4. Générez la solution.

   La fenêtre **Sortie** affiche uniquement le résumé de la génération.

   ![Fenêtre Sortie, Visual Basic des avertissements de génération](../ide/media/buildwalk-visualbasicbuildwarnings.png "BuildWalk_VisualBasicBuildWarnings")

   Pour plus d’informations, consultez [Guide pratique pour supprimer les avertissements du compilateur](../ide/how-to-suppress-compiler-warnings.md).

## <a name="BKMK_outputdetails"></a> Afficher des informations de build supplémentaires dans la fenêtre Sortie

Vous pouvez modifier la quantité d’informations relatives au processus de génération qui s’affichent dans la fenêtre **Sortie**. Le niveau de détail des commentaires de build est généralement défini sur la valeur minimale. Dans ce cas, la **sortie** affiche uniquement un résumé du processus de génération, ainsi que les erreurs ou avertissements de haute priorité. Vous pouvez afficher davantage d’informations sur la génération à l’aide de la [Boîte de dialogue Options, Projets et solutions, Générer et exécuter](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md).

> [!IMPORTANT]
> Si vous décidez d’afficher davantage d’informations, la génération sera plus longue.

#### <a name="to-change-the-amount-of-information-in-the-output-window"></a>Pour modifier la quantité d’informations dans la fenêtre Sortie

1. Ouvrez la boîte de dialogue **Options**.

    ![Commande Options du menu Outils](../ide/media/exploreide-toolsoptionsmenu.png "ExploreIDE-ToolsOptionsmenu")

2. Sélectionnez la catégorie **Projets et solutions**, puis la page **Générer et exécuter**.

3. Dans la liste **Commentaires relatifs à la sortie de génération du projet MSBuild**, choisissez **Normal**, puis cliquez sur le bouton **OK**.

4. Dans la barre de menus, choisissez **Générer**, puis **Nettoyer la solution**.

5. Générez la solution, puis passez en revue les informations contenues dans la fenêtre **Sortie**.

    Les informations de build comprennent l’heure à laquelle la génération a démarré (située au début), l’ordre dans lequel les fichiers ont été traités et la durée totale du processus (située à la fin). Ces informations comprennent également la syntaxe de compilateur que Visual Studio exécute pendant la génération.

    Par exemple, dans la build Visual C#, l’option [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) contient le code d’avertissement (1762) que vous avez spécifié précédemment dans cette rubrique, ainsi que les trois autres avertissements.

    Dans la build Visual Basic, [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) n’inclut pas d’avertissements à exclure, donc aucun avertissement ne s’affiche.

   > [!TIP]
   > Pour effectuer une recherche dans la fenêtre **Sortie**, affichez la boîte de dialogue **Rechercher** en appuyant sur les touches Ctrl + F.

   Pour plus d’informations, consultez l’article [Comment : afficher, enregistrer et configurer des fichiers journaux de génération](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="create-a-release-build"></a>Créer une version Release

Vous pouvez créer une version de l’exemple d’application qui soit optimisée pour sa livraison. Pour la version Release, vous allez spécifier que le fichier exécutable doit être copié vers un partage réseau avant que la génération ne démarre.

Pour plus d’informations, consultez [Guide pratique pour modifier le répertoire de sortie de la génération](../ide/how-to-change-the-build-output-directory.md) et [Génération et nettoyage de solutions et de projets dans Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md).

#### <a name="to-specify-a-release-build-for-visual-basic"></a>Pour spécifier une version Release Visual Basic

1. Ouvrez le **Concepteur de projet**.

     ![Menu Affichage, commande pages de propriétés](../ide/media/buildwalk-viewpropertypages.png "BuildWalk_ViewPropertyPages")

2. Choisissez la page **Compiler**.

3. Dans la liste **Configuration**, choisissez **Version finale**.

4. Dans la liste **Plateforme**, choisissez **x86**.

5. Dans la zone de texte **Chemin de sortie de la génération**, spécifiez un chemin réseau.

     Vous pouvez, par exemple, spécifier \\\myserver\builds.

    > [!IMPORTANT]
    > Une boîte de message peut s’afficher, indiquant que le partage réseau que vous avez spécifié n’est pas un emplacement approuvé. Si vous faites confiance à l’emplacement que vous avez spécifié, cliquez sur **OK** dans la boîte de message.

6. Générez l'application.

     ![Commande Générer la solution du menu Générer](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")

#### <a name="to-specify-a-release-build-for-visual-c"></a>Pour spécifier une version Release pour Visual C\#

1. Ouvrez le **Concepteur de projet**.

    ![Menu Affichage, commande pages de propriétés](../ide/media/buildwalk-viewpropertypages.png "BuildWalk_ViewPropertyPages")

2. Choisissez la page **Générer**.

3. Dans la liste **Configuration**, choisissez **Version finale**.

4. Dans la liste **Plateforme**, choisissez **x86**.

5. Dans la zone de texte **Chemin de sortie**, spécifiez un chemin réseau.

    Vous pouvez, par exemple, spécifier \\\myserver\builds.

   > [!IMPORTANT]
   > Une boîte de message peut s’afficher, indiquant que le partage réseau que vous avez spécifié n’est pas un emplacement approuvé. Si vous faites confiance à l’emplacement que vous avez spécifié, cliquez sur **OK** dans la boîte de message.

6. Générez l'application.

    ![Commande Générer la solution du menu Générer](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")

   Le fichier exécutable est copié sur le chemin réseau que vous avez spécifié. Dans ce cas, le chemin du fichier est \\\myserver\builds\\*nom_fichier*.exe.

   La procédure pas à pas est terminée.

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : génération d’un projet (C++)](https://msdn.microsoft.com/library/d459bc03-88ef-48d0-9f9a-82d17f0b6a4d)
- [Présentation de la précompilation de projets d’application web ASP.NET](https://msdn.microsoft.com/b940abbd-178d-4570-b441-52914fa7b887)
- [Procédure pas à pas : utilisation de MSBuild](../msbuild/walkthrough-using-msbuild.md)
