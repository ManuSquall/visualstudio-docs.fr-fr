---
title: 'Procédure pas à pas : générer une application'
ms.date: 09/25/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2987df6c8ed8a26c2cf95020e26f67c36721d676
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672780"
---
# <a name="walkthrough-build-an-application"></a>Procédure pas à pas : générer une application

Avec cette procédure pas à pas, vous allez vous familiariser avec plusieurs options qu’il est possible de configurer lors de la génération d’applications avec Visual Studio. Vous allez créer une configuration de build personnalisée, masquer certains messages d’avertissement et afficher davantage d’informations de sortie de build dans un exemple d’application.

## <a name="install-the-sample-application"></a>Installer l’exemple d’application

Téléchargez l’exemple [Introduction to Building WPF Applications](https://code.msdn.microsoft.com/Introduction-to-Building-b8d16419). Choisissez C# ou Visual Basic. Une fois le fichier *.zip* téléchargé, décompressez-le et ouvrez le fichier *ExpenseItIntro.sln* avec Visual Studio.

## <a name="create-a-custom-build-configuration"></a>Créer une configuration de build personnalisée

Lorsque vous créez une solution, les configurations de build Debug et Release, et leurs plateformes cibles par défaut, sont automatiquement définies pour la solution. Vous pouvez ensuite personnaliser ces configurations ou créer les vôtres. Les configurations de build spécifient le type de build. Les plateformes de build spécifient le système d’exploitation qui est ciblé par une application pour cette configuration. Pour plus d’informations, consultez [Présentation des configurations de build](../ide/understanding-build-configurations.md), [Présentation des plateformes de build](../ide/understanding-build-platforms.md) et [Comment : définir des configurations Debug et Release](../debugger/how-to-set-debug-and-release-configurations.md).

Vous pouvez modifier ou créer des configurations et des paramètres de plateforme dans la boîte de dialogue **Gestionnaire de configurations**. Dans cette procédure, vous allez créer une configuration de build à des fins de test.

### <a name="create-a-build-configuration"></a>Pour créer une configuration de build

1. Ouvrez la boîte de dialogue **Gestionnaire de configurations**.

   ![Menu Générer, commande Gestionnaire de configurations](../ide/media/buildwalk_configurationmanagerdialogbox.png)

1. Dans la liste **Configuration de la solution active**, choisissez **\<Nouveau...\>**.

1. Dans la boîte de dialogue **Nouvelle configuration de solution**, nommez la nouvelle configuration `Test`, copiez les paramètres de la configuration **Debug** existante, puis cliquez sur le bouton **OK**.

   ![Boîte de dialogue Nouvelle configuration de solution](../ide/media/buildwalk_newsolutionconfigdlgbox.png)

1. Dans la liste **Plateforme de la solution active**, choisissez **\<Nouveau...\>**.

1. Dans la boîte de dialogue **Nouvelle plateforme de solution**, choisissez **x64** et ne copiez pas les paramètres de la plateforme x86.

   ![Boîte de dialogue Nouvelle plateforme de solution](../ide/media/buildwalk_newsolutionplatform.png)

1. Sélectionnez le bouton **OK** .

   La configuration de la solution active a été changée en **Test** avec la plateforme de la solution active définie sur x64.

   ![Gestionnaire de configurations avec configuration de test](../ide/media/buildwalk_configmanagertestconfig.png)

1. Choisissez **Fermer**.

Vous pouvez rapidement vérifier ou modifier la configuration de la solution active à l’aide de la liste **Configurations de solutions** présente dans la barre d’outils **Standard**.

![Barre d'outils Standard option Configuration de solution](../ide/media/buildwalk_standardtoolbarsolutioncongfig.png)

## <a name="build-the-application"></a>Générer l’application

Ensuite, vous allez générer la solution avec la configuration de build personnalisée.

### <a name="build-the-solution"></a>Générer la solution

-   Dans la barre de menus, choisissez **Générer**  >  **Générer la solution**.

    La fenêtre **Sortie** affiche les résultats de la génération. La génération a réussi.

## <a name="hide-compiler-warnings"></a>Masquer les avertissements du compilateur

Nous présenterons ensuite du code qui provoque la génération d’un avertissement par le compilateur.

1. Dans le projet C#, ouvrez le fichier *ExpenseReportPage.xaml.cs*. Dans la méthode **ExpenseReportPage**, ajoutez le code suivant : `int i;`.

    OU

    Dans le projet Visual Basic, ouvrez le fichier *ExpenseReportPage.xaml.vb*. Dans le constructeur personnalisé **Public Sub New...**, ajoutez le code suivant : `Dim i`.

1. Générez la solution.

La fenêtre **Sortie** affiche les résultats de la génération. La génération a réussi, mais des avertissements ont été générés :

![Fenêtre Sortie Visual Basic](../ide/media/buildwalk_vbbuildoutputwnd.png)

![Fenêtre Sortie Visual C&#35;](../ide/media/buildwalk_csharpbuildoutputwnd.png)

Vous pouvez temporairement masquer certains messages d’avertissement pendant la génération, pour éviter qu’ils n’encombrent la fenêtre Sortie.

### <a name="hide-a-specific-c-warning"></a>Masquer un avertissement C# spécifique

1. Dans l’**Explorateur de solutions**, choisissez le premier nœud de projet.

1. Dans la barre de menus, sélectionnez **Afficher** > **Pages de propriétés**.

     Le **Concepteur de projets** s’ouvre.

1. Choisissez la page **Build**, puis, dans la zone **Supprimer les avertissements**, spécifiez le numéro d’avertissement **0168**.

     ![Page Générer, Concepteur de projets](../ide/media/buildwalk_csharpsuppresswarnings.png)

     Pour plus d’informations, consultez [Générer, page du Concepteur de projets (C#)](../ide/reference/build-page-project-designer-csharp.md).

1. Générez la solution.

     La fenêtre **Sortie** affiche uniquement le résumé de la génération.

     ![Fenêtre Sortie, avertissements de génération Visual C&#35;](../ide/media/buildwalk_visualcsharpbuildwarnings.png)

### <a name="suppress-all-visual-basic-build-warnings"></a>Supprimer tous les avertissements de génération Visual Basic

1. Dans l’**Explorateur de solutions**, choisissez le premier nœud de projet.

2. Dans la barre de menus, sélectionnez **Afficher** > **Pages de propriétés**.

     Le **Concepteur de projets** s’ouvre.

3. Dans la page **Compiler**, cochez la case **Désactiver tous les avertissements**.

     ![Page Compiler, Concepteur de projets](../ide/media/buildwalk_vbsuppresswarnings.png)

     Pour plus d’informations, consultez [Configurer des avertissements dans Visual Basic](../ide/configuring-warnings-in-visual-basic.md).

4. Générez la solution.

   La fenêtre **Sortie** affiche uniquement le résumé de la génération.

   ![Fenêtre Sortie, Avertissement sur la génération Visual Basic](../ide/media/buildwalk_visualbasicbuildwarnings.png)

   Pour plus d’informations, consultez [Guide pratique pour supprimer les avertissements du compilateur](../ide/how-to-suppress-compiler-warnings.md).

## <a name="display-additional-build-details-in-the-output-window"></a>Afficher des informations de génération supplémentaires dans la fenêtre Sortie

Vous pouvez modifier la quantité d’informations relatives au processus de génération qui s’affichent dans la fenêtre **Sortie**. Le niveau de détail des informations sur la build est généralement défini sur **Minimale**. Dans ce cas, la fenêtre **Sortie** affiche seulement un résumé du processus de build, ainsi que les erreurs ou avertissements de haute priorité. Vous pouvez afficher plus d’informations sur la build en utilisant la [Boîte de dialogue Options, Projets et solutions, Générer et exécuter](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md).

> [!IMPORTANT]
> Si vous décidez d’afficher davantage d’informations, la génération sera plus longue.

### <a name="change-the-amount-of-information-in-the-output-window"></a>Changer la quantité d’informations dans la fenêtre Sortie

1. Ouvrez la boîte de dialogue **Options**.

     ![Commande Options du menu Outils](../ide/media/exploreide-toolsoptionsmenu.png)

1. Sélectionnez la catégorie **Projets et solutions**, puis la page **Générer et exécuter**.

1. Dans la liste **Commentaires relatifs à la sortie de génération du projet MSBuild**, choisissez **Normal**, puis cliquez sur le bouton **OK**.

1. Dans la barre de menus, choisissez **Générer** > **Nettoyer la solution**.

1. Générez la solution, puis passez en revue les informations contenues dans la fenêtre **Sortie**.

     Les informations de build comprennent l’heure à laquelle la génération a commencé (située au début), et l’ordre dans lequel les fichiers ont été traités. Ces informations comprennent également la syntaxe de compilateur que Visual Studio exécute pendant la génération.

     Par exemple, dans la génération C#, l’option [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) contient le code d’avertissement **1762** que vous avez spécifié précédemment dans cette rubrique, ainsi que trois autres avertissements.

     Dans la build Visual Basic, comme [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) n’inclut pas d’avertissements à exclure, aucun avertissement ne s’affiche.

    > [!TIP]
    > Pour effectuer une recherche dans la fenêtre **Sortie**, affichez la boîte de dialogue **Rechercher** en appuyant sur les touches**Ctrl**+**F**.

Pour plus d’informations, consultez [Comment : afficher, enregistrer et configurer des fichiers journaux de génération](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="create-a-release-build"></a>Créer une version Release

Vous pouvez créer une version de l’exemple d’application qui soit optimisée pour sa livraison. Pour la version Release, vous allez spécifier que le fichier exécutable doit être copié vers un partage réseau avant que la génération ne démarre.

Pour plus d’informations, consultez [Guide pratique pour modifier le répertoire de sortie de la génération](../ide/how-to-change-the-build-output-directory.md) et [Générer et nettoyer des projets et des solutions dans Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md).

### <a name="specify-a-release-build-for-visual-basic"></a>Spécifier une version Release pour Visual Basic

1. Ouvrez le **Concepteur de projet**.

     ![Menu Afficher, commande Pages de propriété](../ide/media/buildwalk_viewpropertypages.png)

1. Choisissez la page **Compiler**.

1. Dans la liste **Configuration**, choisissez **Version finale**.

1. Dans la liste **Plateforme**, choisissez **x86**.

1. Dans la zone de texte **Chemin de sortie de la génération**, spécifiez un chemin réseau.

     Par exemple, vous pouvez spécifier `\\myserver\builds`.

    > [!IMPORTANT]
    > Une boîte de message peut s’afficher, indiquant que le partage réseau que vous avez spécifié n’est pas un emplacement approuvé. Si vous faites confiance à l’emplacement que vous avez spécifié, cliquez sur **OK** dans la boîte de message.

1. Générez l'application.

     ![Commande Générer la solution du menu Générer](../ide/media/exploreide-buildsolution.png)

### <a name="specify-a-release-build-for-c"></a>Spécifier une version Release pour C# #

1. Ouvrez le **Concepteur de projet**.

     ![Menu Afficher, commande Pages de propriété](../ide/media/buildwalk_viewpropertypages.png)

1. Choisissez la page **Générer**.

1. Dans la liste **Configuration**, choisissez **Version finale**.

1. Dans la liste **Plateforme**, choisissez **x86**.

1. Dans la zone de texte **Chemin de sortie**, spécifiez un chemin réseau.

     Par exemple, vous pouvez spécifier `\\myserver\builds`.

    > [!IMPORTANT]
    > Une boîte de message peut s’afficher, indiquant que le partage réseau que vous avez spécifié n’est pas un emplacement approuvé. Si vous faites confiance à l’emplacement que vous avez spécifié, cliquez sur **OK** dans la boîte de message.

1. Dans la **barre d’outils Standard**, définissez l’option Configurations de solutions sur **Release** et l’option Plateformes solution sur **x86**.

1. Générez l'application.

     ![Commande Générer la solution du menu Générer](../ide/media/exploreide-buildsolution.png)

   Le fichier exécutable est copié sur le chemin réseau que vous avez spécifié. Son chemin est `\\myserver\builds\\FileName.exe`.

Félicitations ! La procédure pas à pas est terminée.

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : générer un projet (C++)](/cpp/ide/walkthrough-building-a-project-cpp)
- [Présentation de la précompilation de projets d’application web ASP.NET](/previous-versions/aspnet/aa983464\(v\=vs.110\))
- [Procédure pas à pas : utiliser MSBuild](../msbuild/walkthrough-using-msbuild.md)