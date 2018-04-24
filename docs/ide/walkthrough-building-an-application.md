---
title: 'Procédure pas à pas : Génération d’une application | Microsoft Docs'
ms.custom: ''
ms.date: 09/25/2017
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b94f9b9ba60279c359ce7c6cc3c9646bfbbe7c5a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-building-an-application"></a>Procédure pas à pas : génération d'une application

Avec cette procédure pas à pas, vous allez vous familiariser avec plusieurs options qu’il est possible de configurer lors de la génération d’applications avec Visual Studio. Vous allez créer une configuration de build personnalisée, masquer certains messages d’avertissement et afficher davantage d’informations de sortie de build dans un exemple d’application.

## <a name="install-the-sample-application"></a>Installer l’exemple d’application

Téléchargez l’exemple [Introduction to Building WPF Applications](https://code.msdn.microsoft.com/Introduction-to-Building-b8d16419). Choisissez C# ou Visual Basic. Une fois le fichier .zip téléchargé, extrayez-le et ouvrez le fichier **ExpenseItIntro.sln** à l’aide de Visual Studio.

## <a name="create-a-custom-build-configuration"></a>Créer une configuration de build personnalisée

Lorsque vous créez une solution, les configurations de build Debug et Release, et leurs plateformes cibles par défaut, sont automatiquement définies pour la solution. Vous pouvez ensuite personnaliser ces configurations ou créer les vôtres. Les configurations de build spécifient le type de build. Les plateformes de build spécifient le système d’exploitation qui est ciblé par une application pour cette configuration. Pour plus d’informations, consultez [Présentation des configurations de build](../ide/understanding-build-configurations.md), [Présentation des plateformes de générations](../ide/understanding-build-platforms.md) et [Comment : définir des configurations Debug et Release](../debugger/how-to-set-debug-and-release-configurations.md).

Vous pouvez modifier ou créer des configurations et des paramètres de plateforme dans la boîte de dialogue **Gestionnaire de configurations**. Dans cette procédure, vous allez créer une configuration de build à des fins de test.

### <a name="to-create-a-build-configuration"></a>Pour créer une configuration de build

1. Ouvrez la boîte de dialogue **Gestionnaire de configurations**.

   ![Menu Générer, commande Gestionnaire de configurations](../ide/media/buildwalk_configurationmanagerdialogbox.png "BuildWalk_ConfigurationManagerDialogBox")  

1. Dans la liste **Configuration de la solution active**, choisissez **\<Nouveau...\>**.

1. Dans la boîte de dialogue **Nouvelle configuration de solution**, attribuez à la nouvelle configuration le nom de `Test`, copiez les paramètres de la configuration Debug existante, puis cliquez sur le bouton **OK**.

   ![Boîte de dialogue Nouvelle configuration de solution](../ide/media/buildwalk_newsolutionconfigdlgbox.png "BuildWalk_NewSolutionConfigDlgBox")  

1. Dans la liste **Plateforme de la solution active**, choisissez **\<Nouveau...\>**.

1. Dans la boîte de dialogue **Nouvelle plateforme de solution**, choisissez **x64** et ne copiez pas les paramètres de la plateforme x86.

   ![Boîte de dialogue Nouvelle plateforme de solution](../ide/media/buildwalk_newsolutionplatform.png "BuildWalk_NewSolutionPlatform")  

1. Sélectionnez le bouton **OK** .

   La configuration de la solution active a été remplacée par la configuration de test et la plateforme de la solution active a été définie sur x64.

   ![Gestionnaire de configurations avec la configuration de test](../ide/media/buildwalk_configmanagertestconfig.png "BuildWalk_ConfigManagerTestconfig")  

1. Choisissez **Fermer**.

Vous pouvez rapidement vérifier ou modifier la configuration de la solution active à l’aide de la liste **Configurations de solutions** présente dans la barre d’outils **Standard**.
  
![Option Configurations de solutions de la barre d’outils Standard](../ide/media/buildwalk_standardtoolbarsolutioncongfig.png "BuildWalk_StandardToolbarSolutionCongfig")  
  
## <a name="build-the-application"></a>Générer l'application

Ensuite, vous allez générer la solution avec la configuration de build personnalisée.
  
### <a name="to-build-the-solution"></a>Pour générer la solution
  
-   Dans la barre de menus, choisissez **Générer**  >  **Générer la solution**.
  
    La fenêtre **Sortie** affiche les résultats de la génération. La génération a réussi.
  
## <a name="hide-compiler-warnings"></a>Masquer les avertissements du compilateur

Nous présenterons ensuite du code qui provoque la génération d’un avertissement par le compilateur.

1. Dans le projet C#, ouvrez le fichier **ExpenseReportPage.xaml.cs**. Dans la méthode **ExpenseReportPage**, ajoutez le code suivant : `int i;`.

    OU

    Dans le projet Visual Basic, ouvrez le fichier **ExpenseReportPage.xaml.vb**. Dans le constructeur personnalisé **Public Sub New...**, ajoutez le code suivant : `Dim i`.

1. Générez la solution.

La fenêtre **Sortie** affiche les résultats de la génération. La génération a réussi, mais des avertissements ont été générés :

![Fenêtre Sortie Visual Basic](../ide/media/buildwalk_vbbuildoutputwnd.png "BuildWalk_VBBuildOutputWnd")

![Fenêtre Sortie Visual C#](../ide/media/buildwalk_csharpbuildoutputwnd.png "BuildWalk_CsharpBuildOutputWnd")

Vous pouvez temporairement masquer certains messages d’avertissement pendant la génération, pour éviter qu’ils n’encombrent la fenêtre Sortie.

### <a name="to-hide-a-specific-c-warning"></a>Pour masquer un avertissement C# spécifique

1. Dans l’**Explorateur de solutions**, choisissez le premier nœud de projet.

1. Dans la barre de menus, sélectionnez **Afficher**, **Pages de propriétés**.
  
     Le **Concepteur de projets** s’ouvre.

1. Choisissez la page **Build**, puis, dans la zone **Supprimer les avertissements**, spécifiez le numéro d’avertissement **0168**.
  
     ![Page Générer, Concepteur de projets](../ide/media/buildwalk_csharpsupresswarnings.png "BuildWalk_CsharpSupressWarnings")  
  
     Pour plus d’informations, consultez [Générer, page du Concepteur de projets (C#)](../ide/reference/build-page-project-designer-csharp.md).

1. Générez la solution.
  
     La fenêtre **Sortie** affiche uniquement le résumé de la génération.
  
     ![Fenêtre Sortie, avertissements de génération Visual C#](../ide/media/buildwalk_visualcsharpbuildwarnings.png "BuildWalk_VisualCsharpBuildWarnings")  
  
### <a name="to-suppress-all-visual-basic-build-warnings"></a>Pour supprimer tous les avertissements de génération de Visual Basic

1. Dans l’**Explorateur de solutions**, choisissez le premier nœud de projet.

1. Dans la barre de menus, sélectionnez **Afficher**, **Pages de propriétés**.
  
     Le **Concepteur de projets** s’ouvre.

1. Dans la page **Compiler**, cochez la case **Désactiver tous les avertissements**.
  
     ![Page Compiler, Concepteur de projets](../ide/media/buildwalk_vbsupresswarnings.png "BuildWalk_VBSupressWarnings")  
  
     Pour plus d’informations, consultez [Configuration d’avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).

1. Générez la solution.
  
 La fenêtre **Sortie** affiche uniquement le résumé de la génération.
  
 ![Fenêtre Sortie, avertissements de génération de Visual Basic](../ide/media/buildwalk_visualbasicbuildwarnings.png "BuildWalk_VisualBasicBuildWarnings")  
  
 Pour plus d’informations, consultez [Guide pratique pour supprimer les avertissements du compilateur](../ide/how-to-suppress-compiler-warnings.md).
  
## <a name="display-additional-build-details-in-the-output-window"></a>Afficher des informations de build supplémentaires dans la fenêtre Sortie

Vous pouvez modifier la quantité d’informations relatives au processus de génération qui s’affichent dans la fenêtre **Sortie**. Le niveau de détail des commentaires de build est généralement défini sur la valeur minimale. Dans ce cas, la **sortie** affiche uniquement un résumé du processus de génération, ainsi que les erreurs ou avertissements de haute priorité. Vous pouvez afficher davantage d’informations sur la génération à l’aide de la [Boîte de dialogue Options, Projets et solutions, Générer et exécuter](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md).
  
> [!IMPORTANT]
>  Si vous décidez d’afficher davantage d’informations, la génération sera plus longue.
  
### <a name="to-change-the-amount-of-information-in-the-output-window"></a>Pour modifier la quantité d’informations dans la fenêtre Sortie

1. Ouvrez la boîte de dialogue **Options**.
  
     ![Options de commande dans le menu outils](../ide/media/exploreide-toolsoptionsmenu.png "ExploreIDE-ToolsOptionsmenu")  

1. Sélectionnez la catégorie **Projets et solutions**, puis la page **Générer et exécuter**.

1. Dans la liste **Commentaires relatifs à la sortie de génération du projet MSBuild**, choisissez **Normal**, puis cliquez sur le bouton **OK**.

1. Dans la barre de menus, choisissez **Générer**, puis **Nettoyer la solution**.

1. Générez la solution, puis passez en revue les informations contenues dans la fenêtre **Sortie**.
  
     Les informations de build comprennent l’heure à laquelle la génération a commencé (située au début), et l’ordre dans lequel les fichiers ont été traités. Ces informations comprennent également la syntaxe de compilateur que Visual Studio exécute pendant la génération.
  
     Par exemple, dans la build C#, l’option [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) contient le code d’avertissement (1762) que vous avez spécifié précédemment dans cette rubrique, ainsi que les trois autres avertissements.
  
     Dans la build Visual Basic, comme [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) n’inclut pas d’avertissements à exclure, aucun avertissement ne s’affiche.
  
    > [!TIP]
    > Pour effectuer une recherche dans la fenêtre **Sortie**, affichez la boîte de dialogue **Rechercher** en appuyant sur les touches Ctrl + F.

Pour plus d’informations, consultez l’article [Comment : afficher, enregistrer et configurer des fichiers journaux de génération](../ide/how-to-view-save-and-configure-build-log-files.md).
  
## <a name="create-a-release-build"></a>Créer une version Release

Vous pouvez créer une version de l’exemple d’application qui soit optimisée pour sa livraison. Pour la version Release, vous allez spécifier que le fichier exécutable doit être copié vers un partage réseau avant que la génération ne démarre.

Pour plus d’informations, consultez [Guide pratique pour modifier le répertoire de sortie de la génération](../ide/how-to-change-the-build-output-directory.md) et [Génération et nettoyage de solutions et de projets dans Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md).

### <a name="to-specify-a-release-build-for-visual-basic"></a>Pour spécifier une version Release Visual Basic

1. Ouvrez le **Concepteur de projet**.
  
     ![Menu Affichage, commande Pages de propriétés](../ide/media/buildwalk_viewpropertypages.png "BuildWalk_ViewPropertyPages")  

1. Choisissez la page **Compiler**.

1. Dans la liste **Configuration**, choisissez **Version finale**.

1. Dans la liste **Plateforme**, choisissez **x86**.

1. Dans la zone de texte **Chemin de sortie de la génération**, spécifiez un chemin réseau.

     Vous pouvez, par exemple, spécifier \\\myserver\builds.

    > [!IMPORTANT]
    > Une boîte de message peut s’afficher, indiquant que le partage réseau que vous avez spécifié n’est pas un emplacement approuvé. Si vous faites confiance à l’emplacement que vous avez spécifié, cliquez sur **OK** dans la boîte de message.

1. Générez l'application.

     ![Commande Générer la solution du menu Générer](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")  

### <a name="to-specify-a-release-build-for-c"></a>Pour spécifier une version Release C# #

1. Ouvrez le **Concepteur de projet**.
  
     ![Menu Affichage, commande Pages de propriétés](../ide/media/buildwalk_viewpropertypages.png "BuildWalk_ViewPropertyPages")  

1. Choisissez la page **Générer**.

1. Dans la liste **Configuration**, choisissez **Version finale**.

1. Dans la liste **Plateforme**, choisissez **x86**.

1. Dans la zone de texte **Chemin de sortie**, spécifiez un chemin réseau.
  
     Vous pouvez, par exemple, spécifier \\\myserver\builds.
  
    > [!IMPORTANT]
    > Une boîte de message peut s’afficher, indiquant que le partage réseau que vous avez spécifié n’est pas un emplacement approuvé. Si vous faites confiance à l’emplacement que vous avez spécifié, cliquez sur **OK** dans la boîte de message.

1. Dans la **barre d’outils Standard**, définissez l’option Configurations de solutions sur **Release** et l’option Plateformes solution sur **x86**.

1. Générez l'application.

     ![Commande Générer la solution du menu Générer](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")  

   Le fichier exécutable est copié sur le chemin réseau que vous avez spécifié. Dans ce cas, le chemin du fichier est \\\myserver\builds\\*nom_fichier*.exe.

La procédure pas à pas est terminée.
  
## <a name="see-also"></a>Voir aussi

[Procédure pas à pas : génération d’un projet (C++)](/cpp/ide/walkthrough-building-a-project-cpp)  
[Présentation de la précompilation de projets d’application web ASP.NET](http://msdn.microsoft.com/b940abbd-178d-4570-b441-52914fa7b887)  
[Procédure pas à pas : utilisation de MSBuild](../msbuild/walkthrough-using-msbuild.md)
