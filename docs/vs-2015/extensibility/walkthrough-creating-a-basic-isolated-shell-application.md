---
title: 'Procédure pas à pas : création d’une application Shell isolée de base | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, walkthroughs
- Shell [Visual Studio], walkthroughs
- walkthroughs [Visual Studio], isolated shell-based application
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: 55
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6192eb5583e7d0bc37518e995aacccad643cc9ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850350"
---
# <a name="walkthrough-creating-a-basic-isolated-shell-application"></a>Procédure pas à pas : Création d’une application Shell isolée de base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette procédure pas à pas montre comment créer une solution de Shell isolé, personnaliser l’aide à propos de la fenêtre outil et créer un programme d’installation qui installe l’interpréteur de commandes isolé.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Kit de développement logiciel (SDK) Visual Studio](../extensibility/visual-studio-sdk.md). Pour déployer l’interpréteur de commandes isolé, vous devez également utiliser le package redistribuable Visual Studio Shell (isolé).  
  
## <a name="creating-an-isolated-shell-solution"></a>Création d’une solution de Shell isolé  
 Cette section montre comment utiliser le modèle de projet isolé Visual Studio Shell pour créer une solution de Shell isolé. La solution contient les projets suivants :  
  
- *NomSolution*. Projet AboutBoxPackage, qui vous permet de personnaliser l’apparence de la zone aide/à propos de.  
  
- Le projet ShellExtensionsVSIX, qui contient le fichier. extension. vsixmanifest source qui définit les différents composants de l’application Shell isolée.  
  
- Le projet *SolutionName* , qui produit le fichier exécutable qui appelle l’application Shell isolé. Ce projet contient le dossier de personnalisation de l’interpréteur de commandes, qui vous permet de personnaliser l’apparence et le comportement de l’application de Shell isolé.  
  
- Projet d’interface utilisateur *NomSolution* , qui produit un assembly satellite qui définit les commandes de menu actives et les chaînes localisables.  
  
#### <a name="to-create-a-basic-isolated-shell-solution"></a>Pour créer une solution Shell isolée de base  
  
1. Ouvrez Visual Studio et créez un projet.  
  
2. Dans la fenêtre **nouveau projet** , développez **autres types de projets** , puis **extensibilité**. Sélectionnez le modèle de projet **isolé Visual Studio Shell** .  
  
3. Nommez le projet `MyVSShellStub` et spécifiez un emplacement. Assurez-vous que l’option **créer le répertoire pour la solution** est cochée, puis cliquez sur **OK**.  
  
     La nouvelle solution s’affiche dans **Explorateur de solutions**.  
  
4. Générez la solution et démarrez le débogage de l’application Shell isolé.  
  
     Le shell isolé Visual Studio s’affiche. La barre de titre lit **MyVSShellStub**. L’icône de la barre de titre est générée à partir de \MyVSShellStub\Resource Files\ApplicationIcon.ico.  
  
## <a name="customizing-the-application-name-and-icon"></a>Personnalisation du nom et de l’icône de l’application  
 Vous pouvez choisir de marquer votre application en utilisant le nom de votre société et son logo dans la barre de titre. Les étapes suivantes montrent comment modifier le nom et l’icône qui s’affichent dans la barre de titre de l’application personnalisée en modifiant le fichier de définition de package, MyVSShellStub. application. pkgdef.  
  
#### <a name="to-customize-the-application-name-and-icon"></a>Pour personnaliser le nom et l’icône de l’application  
  
1. Dans le projet MyVSShellStub, ouvrez \Shell Customization\MyVSShellStub.Application.pkgdef.  
  
2. Remplacez la `AppName` valeur de l’élément par **« appname » = « Fabrikam Music Editor »**  
  
3. Pour modifier l’icône de l’application, copiez une autre icône dans le répertoire \MyVSShellStub\MyVSShellStub\MyVSShellStub\. Renommez le fichier ApplicationIcon. ico existant en ApplicationIcon1. ico. Renommez le nouveau fichier en ApplicationIcon. ico.  
  
4. Générez la solution et commencez le débogage. L’IDE de l’interpréteur de commandes isolé s’affiche. La barre de titre contient votre nouvelle icône en regard des mots « **éditeur Fabrikam Music**».  
  
## <a name="customizing-the-default-web-browser-home-page"></a>Personnalisation de la page d’hébergement par défaut du navigateur Web  
 Cette section montre comment modifier la page d’hébergement par défaut de la fenêtre de **navigateur Web** en modifiant le fichier de définition de package.  
  
#### <a name="to-customize-the-default-web-browser-home-page"></a>Pour personnaliser la page d’hébergement par défaut du navigateur Web  
  
1. Dans le fichier MyVSShellStub. application. pkgdef, remplacez la `DefaultHomePage` valeur de l’élément par « <https://www.microsoft.com> ».  
  
2. Régénérez le projet MyVSShellStub.  
  
3. Générez la solution et commencez le débogage.  
  
4. Dans **affichage/autres fenêtres**, cliquez sur **navigateur Web**. La fenêtre du **navigateur Web** affiche la page d’accueil de Microsoft Corporation.  
  
## <a name="removing-the-print-command"></a>Suppression de la commande d’impression  
 Le fichier. vsct dans un projet d’interface utilisateur de Shell isolé se compose d’un ensemble de déclarations de l' `<Define name=No_` *élément*Form `>` , où *Element* est l’un des menus et commandes Visual Studio standard.  
  
 Si une déclaration n’est pas commentée, le menu ou la commande est exclu de l’interpréteur de commandes isolé. À l’inverse, si une déclaration est commentée, le menu ou la commande est inclus dans l’interpréteur de commandes isolé.  
  
 Dans les étapes suivantes, vous supprimez les commentaires de la commande Imprimer dans votre fichier. vsct.  
  
#### <a name="to-remove-the-print-command"></a>Pour supprimer la commande Imprimer  
  
1. Vérifiez que la commande **Imprimer** apparaît dans le menu **fichier** de l’application Shell isolé.  
  
2. Dans le projet MyVSShellStubUI, ouvrez \Resource Files\MyVSShellStubUI.vsct pour le modifier.  
  
3. Supprimer les marques de commentaire de cette ligne :  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4. Cela supprime la commande Imprimer.  
  
5. Démarrez le débogage de l’application Shell isolé. Vérifiez que la commande **fichier/imprimer** a disparu.  
  
## <a name="removing-features-from-the-isolated-shell"></a>Suppression de fonctionnalités de l’interpréteur de commandes isolé  
 Vous pouvez supprimer certains des packages qui sont chargés avec Visual Studio en modifiant le fichier. pkgundef si vous ne souhaitez pas ces fonctionnalités dans votre application Shell isolée personnalisée. Vous spécifiez le package dans l’une des sous-clés de la clé de Registre $RootKey $ \Packages.  
  
> [!NOTE]
> Pour trouver les GUID des fonctionnalités de Visual Studio, consultez [GUID de package des fonctionnalités Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
 La procédure suivante montre comment supprimer l’éditeur XML de l’interpréteur de commandes isolé.  
  
#### <a name="to-remove-the-xml-editor"></a>Pour supprimer l’éditeur XML  
  
1. Ouvrez le fichier MyVSShellStub. pkgundef dans le dossier de personnalisation de l’interpréteur de commandes du projet MyVSShellStub.  
  
2. Supprimez les marques de commentaire de la ligne suivante :  
  
     [$RootKey $ \Packages \\ {87569308-4813-40a0-9cd0-d7a30838ca3f}]  
  
3. Régénérez la solution et démarrez le débogage de l’interpréteur de commandes isolé. Ouvrez un fichier XML, par exemple, \MyVSShellStub\MyVSShellStub\MyVSShellStubUI\MyVSShellStubUI.vsct. Vérifiez que les mots clés XML dans le fichier ne sont pas coloriés et que la saisie de « < » sur une ligne ne fait pas apparaître les info-bulles XML.  
  
## <a name="customizing-the-helpabout-box"></a>Personnalisation de la zone aide/à propos de  
 Vous pouvez personnaliser la zone aide/à propos, qui est créée dans le cadre du modèle de projet d’interpréteur de commandes isolé.  
  
#### <a name="to-customize-the-company-name"></a>Pour personnaliser le nom de la société  
  
1. Le nom de la société, les informations de copyright, la version du produit et la description du produit se trouvent dans le projet MyVSShellStub. AboutBoxPackage, dans le fichier \Properties\AssemblyInfo.cs. Ouvrez ce fichier.  
  
2. Remplacez la `AssemblyCompany` valeur par **Fabrikam**, les `AssemblyProduct` `AssemblyTitle` valeurs et par **Fabrikam Music Editor**, et la `AssemblyCopyright` valeur par **Copyright © Fabrikam 2015**:  
  
    ```  
    [assembly: AssemblyTitle("Fabrikam Music Editor")]  
    [assembly: AssemblyDescription("")]  
    [assembly: AssemblyConfiguration("")]  
    [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")] [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor ")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015”)]  
    ```  
  
3. Pour ajouter une description du produit, remplacez la `AssemblyDescription` valeur par **la description de Fabrikam Music Editor.**:  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.”)]  
    ```  
  
4. Démarrez le débogage et, dans l’application Shell isolé, ouvrez la zone **aide/à propos** de. Vous devez voir les chaînes modifiées. Le titre de la zone aide/à propos de est identique à la `AssemblyTitle` valeur dans AssemblyInfo.cs.  
  
5. Les propriétés de la zone **aide/à propos** de se trouvent dans le fichier MyVSShellStub. AboutBoxPackage\AboutBox.Xaml. Pour modifier la largeur de la zone aide/à propos de, accédez au `AboutDialogStyle` bloc et définissez la `Width` propriété sur 200 :  
  
    ```  
    <Style x:Key="AboutDialogStyle" TargetType="Window">  
        <Setter Property="Height" Value="Auto" />  
        <Setter Property="Width" Value="200" />  
        <Setter Property="ShowInTaskbar" Value="False" />  
        <Setter Property="ResizeMode" Value="NoResize" />  
        <Setter Property="WindowStyle" Value="SingleBorderWindow" />  
        <Setter Property="SizeToContent" Value="Height" />  
    </Style>  
    ```  
  
6. Régénérez la solution et démarrez le débogage de l’interpréteur de commandes isolé. La zone aide/à propos de doit être approximativement carrée.  
  
## <a name="before-you-deploy-the-isolated-shell-application"></a>Avant de déployer l’application Shell isolé  
 Votre application d’interpréteur de commandes isolé peut être installée sur n’importe quel ordinateur disposant du package redistribuable Visual Studio Shell (isolé). Pour plus d’informations sur le package redistribuable, consultez le site Web téléchargements de l' [extensibilité Visual Studio](https://msdn.microsoft.com/vstudio/bb984878.aspx) .  
  
## <a name="deploying-the-isolated-shell-application"></a>Déploiement de l’application Shell isolée  
 Vous déployez votre application Shell isolée sur un ordinateur cible en créant un projet d’installation. Vous devez spécifier les éléments suivants :  
  
- Disposition des dossiers et des fichiers sur l’ordinateur cible.  
  
- Les conditions de lancement qui garantissent que le .NET Framework et le runtime du shell Visual Studio sont installés sur l’ordinateur cible.  
  
  Dans la procédure suivante, vous devez installer InstallShield Limited Edition sur votre ordinateur.  
  
#### <a name="to-create-the-setup-project"></a>Pour créer le projet d’installation  
  
1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de la solution, puis cliquez sur **Ajouter un nouveau projet**.  
  
2. Dans la boîte de dialogue **nouveau projet** , développez **autres types de projets** , puis sélectionnez **configuration et déploiement**. Sélectionnez le modèle InstallShield. Nommez le nouveau projet `MySetup` , puis cliquez sur **OK**.  
  
3. Si InstallShield Limited Edition est déjà installé, passez à l’étape suivante.  
  
    Si InstallShield Limited Edition n’est pas déjà installé, la page de téléchargement d’InstallShield s’affiche. Suivez les instructions pour télécharger et installer le produit, en choisissant la version d’InstallShield qui est compatible avec votre version de Visual Studio. Vous devez décider si vous souhaitez inscrire votre installation d’InstallShield ou l’utiliser en tant qu’évaluation. Vous devez redémarrer Visual Studio une fois l’installation terminée.  
  
   > [!IMPORTANT]
   > Vous devez démarrer Visual Studio en tant qu’administrateur avant de créer un projet InstallShield. Si vous ne le faites pas, vous obtiendrez une erreur lors de la génération du projet.  
  
   Les étapes suivantes montrent comment configurer le projet d’installation.  
  
> [!IMPORTANT]
> Assurez-vous que vous avez créé la configuration Release de votre projet Shell isolé au moins une fois avant de configurer le projet d’installation.  
  
#### <a name="to-configure-the-setup-project"></a>Pour configurer le projet d’installation  
  
1. Dans le **Explorateur de solutions**, sous le projet **mySetup** , choisissez **Assistant projet**. Sur la ligne inférieure de la fenêtre **Assistant projet** , choisissez **informations sur l’application**. Entrez **Fabrikam** comme nom de société et **éditeur Fabrikam Music** comme nom d’application. Choisissez la flèche suivant en bas à droite de l' **Assistant projet**.  
  
2. Sélectionnez **Oui** sous si **votre application nécessite l’installation d’un logiciel sur l’ordinateur** , puis sélectionnez **Microsoft .net Package complet de l’infrastructure 4,5**.  
  
3. Choisissez le bouton **fichiers d’application** en bas de la fenêtre, puis vérifiez que le dossier de l' **éditeur Fabrikam Music** est sélectionné.  
  
4. Choisissez le bouton **Ajouter des fichiers** . Dans la boîte de dialogue **Ajouter des fichiers** , ajoutez les fichiers suivants à partir du dossier **MyVSShellStub\Release** :  
  
    1. MyVSShellStub.exe.config  
  
    2. DebuggerProxy.dll  
  
    3. DebuggerProxy.dll. manifest  
  
    4. MyVSShellStub. pkgdef  
  
    5. MyVSShellStub. pkgundef  
  
    6. MyVSShellStub.winprf  
  
    7. Splash.bmp  
  
5. Cliquez sur le bouton **Ajouter des sorties de projet** et ajoutez la **sortie MyVSShellStub/Primary**. Cliquez sur **OK**.  
  
6. Dans le volet gauche, sous **ordinateur de destination**, cliquez avec le bouton droit sur le nœud **éditeur Fabrikam Music [INSTALLDIR]** , puis ajoutez un **nouveau dossier** nommé **Extensions**.  
  
7. Cliquez avec le bouton droit sur le nœud **Extensions** dans le volet gauche et ajoutez un nouveau dossier nommé **application**.  
  
8. Sélectionnez le dossier de l' **application** , cliquez sur le bouton **Ajouter les sorties du projet** , puis sélectionnez la sortie principale du projet MyVSShellStub. AboutBoxPackage.  
  
9. Cliquez sur le bouton **Ajouter des fichiers** et, dans le dossier \MyVSShellStub\Release\Extensions\Application\, ajoutez les fichiers suivants :  
  
    - MyVSShellStub. AboutBoxPackage. pkgdef  
  
    - MyVSShellStub. application. pkgdef  
  
10. Cliquez avec le bouton droit sur le nœud de l' **éditeur Fabrikam Music [INSTALLDIR]** dans le volet gauche et ajoutez un nouveau dossier nommé **1033**.  
  
11. Sélectionnez le dossier 1033, puis cliquez sur le bouton **Ajouter des sorties de projet** , puis sélectionnez la sortie principale du projet MyVSShellStubUI.  
  
12. Accédez à la fenêtre raccourcis de l' **application** .  
  
13. Cliquez sur **nouveau** pour créer un raccourci et sélectionnez **[ProgramFilesFolder] \Fabrikam\Fabrikam Music Editor\MyVSShellStub.Primary output**.  
  
14. Accédez au volet **interview d’installation** .  
  
15. Affectez à tous les éléments la valeur **non**.  
  
16. Dans **Explorateur de solutions**, dans le projet mySetup, ouvrez **définir la configuration requise et actions \ spécifications**. La fenêtre **spécifications** s’ouvre.  
  
17. Cliquez avec le bouton droit sur **configuration logicielle requise pour le système** et sélectionnez **créer une nouvelle condition de lancement**. L' **Assistant recherche de système** s’affiche.  
  
18. Dans le volet **que voulez-vous trouver ?** , choisissez **entrée de registre** dans la liste déroulante, puis cliquez sur **suivant**.  
  
19. Dans le volet **Comment voulez-vous le Rechercher ?** , sélectionnez **HKEY_LOCAL_MACHINE** comme racine du Registre. Entrez **SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** pour les systèmes 64 bits ou **SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** pour les systèmes 32 bits, puis entrez **install** comme valeur de registre. Cliquez sur **Suivant**.  
  
20. Dans le volet **que voulez-vous faire avec la valeur ?** , entrez **ce produit nécessite l’installation du package redistribuable Visual Studio 2015 isolated Shell.** comme texte d’affichage, puis cliquez sur **Terminer**.  
  
21. Régénérez la solution d’interpréteur de commandes isolé pour créer le projet d’installation.  
  
     Vous pouvez trouver le fichier setup.exe dans le dossier suivant :  
  
     \MyVSShellStub\MySetup\MySetup\Express\SingleImage\DiskImages\DISK1  
  
## <a name="testing-the-installation-program"></a>Test du programme d’installation  
 Pour tester l’installation, copiez le fichier setup.exe sur un autre ordinateur et exécutez le programme d’installation exécutable. Vous devez être en mesure d’exécuter l’application Shell isolé.
