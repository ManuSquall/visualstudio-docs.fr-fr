---
title: "Procédure pas à pas : Création d’un base des Application Shell isolée | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, walkthroughs
- Shell [Visual Studio], walkthroughs
- walkthroughs [Visual Studio], isolated shell-based application
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: 54
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: e007e366847ac42d3916b16cbde190e8fd755821
ms.contentlocale: fr-fr
ms.lasthandoff: 09/06/2017

---
# <a name="walkthrough-creating-a-basic-isolated-shell-application"></a>Procédure pas à pas : Création d’une Application de base de Shell isolé
Cette procédure pas à pas montre comment créer une solution de shell isolé, personnaliser la fenêtre outil à propos d’et créer un programme d’installation qui installe le shell isolé.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Pour déployer le shell isolé, vous devez également utiliser le Package redistribuable Visual Studio Shell (isolé).  
  
## <a name="creating-an-isolated-shell-solution"></a>Création d’une Solution de Shell isolé  
 Cette section montre comment utiliser le modèle de projet Visual Studio Shell isolé pour créer une solution de shell isolé. La solution contient les projets suivants :  
  
-   Le *SolutionName*. Projet AboutBoxPackage, qui vous permet de personnaliser l’apparence de l’aide/à propos de la zone.  
  
-   Le projet ShellExtensionsVSIX, qui contient le fichier source.extension.vsixmanifest qui définit les différents composants de l’application de shell isolé.  
  
-   Le *SolutionName* projet, ce qui génère le fichier exécutable qui appelle l’application de shell isolé. Ce projet contient le dossier Shell Customization, ce qui permet de vous permet de personnaliser l’apparence et comportement de l’application de shell isolé.  
  
-   Le *SolutionName* projet d’interface utilisateur, ce qui génère un assembly satellite qui définit les commandes de menu active et les chaînes localisables.  
  
#### <a name="to-create-a-basic-isolated-shell-solution"></a>Pour créer une solution de base de shell isolé  
  
1.  Ouvrez Visual Studio et créez un projet.  
  
2.  Dans le **nouveau projet** fenêtre, développez **autres Types de projets** , puis **extensibilité**. Sélectionnez le **Visual Studio Shell isolé** modèle de projet.  
  
3.  Nommez le projet `MyVSShellStub` et spécifiez un emplacement. Assurez-vous que **créer le répertoire pour la solution** est activée, puis cliquez sur **OK**.  
  
     La nouvelle solution apparaît dans **l’Explorateur de solutions**.  
  
4.  Générez la solution et démarrer le débogage de l’application de shell isolé.  
  
     Le shell isolé Visual Studio s’affiche. Lit de la barre de titre **MyVSShellStub**. L’icône de barre de titre est généré à partir de \MyVSShellStub\Resource Files\ApplicationIcon.ico.  
  
## <a name="customizing-the-application-name-and-icon"></a>Personnalisation de l’icône et le nom de l’Application  
 Vous souhaiterez personnaliser votre application en utilisant le nom de votre entreprise et de son logo dans la barre de titre. Les étapes suivantes montrent comment modifier le nom et l’icône qui s’affichent dans la barre de titre d’application personnalisée en modifiant le fichier de définition de package, MyVSShellStub.Application.pkgdef.  
  
#### <a name="to-customize-the-application-name-and-icon"></a>Pour personnaliser l’icône et le nom de l’application  
  
1.  Dans le projet MyVSShellStub, ouvrez \Shell Customization\MyVSShellStub.Application.pkgdef.  
  
2.  Modifier la `AppName` valeur de l’élément à **« AppName » = « éditeur de musique Fabrikam »**  
  
3.  Pour modifier l’icône de l’application, copiez une autre icône dans le répertoire \MyVSShellStub\MyVSShellStub\MyVSShellStub\. Renommez le fichier ApplicationIcon.ico existant en ApplicationIcon1.ico. Renommez le nouveau fichier à ApplicationIcon.ico.  
  
4.  Générez la solution et commencez le débogage. Le shell isolé IDE s’affiche. La barre de titre a votre nouvelle icône en regard de la mention **Fabrikam musique éditeur**.  
  
## <a name="customizing-the-default-web-browser-home-page"></a>Personnalisation de la Page d’accueil du navigateur Web par défaut  
 Cette section montre comment modifier la page d’accueil par défaut de la **navigateur Web** fenêtre en modifiant le fichier de définition de package.  
  
#### <a name="to-customize-the-default-web-browser-home-page"></a>Pour personnaliser la page d’accueil de navigateur Web par défaut  
  
1.  Dans le fichier MyVSShellStub.Application.pkgdef, modifiez le `DefaultHomePage` valeur de l’élément à « http://www.microsoft.com ».  
  
2.  Régénérez le projet MyVSShellStub.  
  
3.  Générez la solution et commencez le débogage.  
  
4.  Dans **affichage / autres fenêtres**, cliquez sur **navigateur Web**. Le **navigateur Web** fenêtre affiche la page d’accueil de Microsoft Corporation.  
  
## <a name="removing-the-print-command"></a>Suppression de la commande d’impression  
 Le fichier .vsct dans un projet de l’interface utilisateur du shell isolé se compose d’un ensemble de déclarations du formulaire `<Define name=No_` *élément*`>`, où *élément* est un des menus de Visual Studio standard et des commandes.  
  
 Si une déclaration est retirée, ce menu ou une commande est exclue à partir du shell isolé. À l’inverse, si une déclaration est commentée, le menu ou la commande est inclus dans le shell isolé.  
  
 Dans les étapes suivantes, vous supprimez les commentaires de commande d’impression dans votre fichier .vsct.  
  
#### <a name="to-remove-the-print-command"></a>Pour supprimer la commande d’impression  
  
1.  Vérifiez que le **impression** commande s’affiche sur le **fichier** menu de l’application de shell isolé.  
  
2.  Dans le projet MyVSShellStubUI, ouvrez \Resource Files\MyVSShellStubUI.vsct pour la modification.  
  
3.  Supprimez les commentaires de cette ligne :  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4.  Cette opération supprime la commande d’impression.  
  
5.  Démarrez le débogage de l’application de shell isolé. Vérifiez que le **fichier, d’impression** commande a disparu.  
  
## <a name="removing-features-from-the-isolated-shell"></a>Suppression de fonctionnalités à partir du Shell isolé  
 Vous pouvez supprimer certains des packages qui sont chargées avec Visual Studio en modifiant le fichier .pkgundef si vous ne souhaitez pas que ces fonctionnalités dans votre application de shell isolé personnalisé. Vous spécifiez le package de l’une des sous-clés de la clé de Registre \Packages $RootKey$.  
  
> [!NOTE]
>  Pour rechercher les fonctionnalités de GUID de Visual Studio, consultez [Package GUID de fonctionnalités Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
 La procédure suivante montre comment supprimer le code XML éditeur à partir du shell isolé.  
  
#### <a name="to-remove-the-xml-editor"></a>Pour supprimer l’éditeur XML  
  
1.  Ouvrez le fichier MyVSShellStub.pkgundef dans le dossier Shell Customization du projet MyVSShellStub.  
  
2.  Supprimez les commentaires de la ligne suivante :  
  
     [$RootKey$ \Packages\\{87569308-4813-40a0-9cd0-d7a30838ca3f}]  
  
3.  Régénérez la solution et démarrer le débogage du shell isolé. Ouvrez un fichier XML, par exemple, \MyVSShellStub\MyVSShellStub\MyVSShellStubUI\MyVSShellStubUI.vsct. Vérifiez que les mots clés XML dans le fichier ne sont pas colorés et ce en tapant « < » sur une ligne ne met pas des info-bulles XML.  
  
## <a name="customizing-the-helpabout-box"></a>Personnalisation de l’aide/à propos de zone  
 Vous pouvez personnaliser à l’aide/à propos de la zone, qui est créé en tant que partie du modèle de projet de shell isolé.  
  
#### <a name="to-customize-the-company-name"></a>Pour personnaliser le nom de la société  
  
1.  Le nom de la société, les informations de copyright, version du produit et description du produit sont trouvent dans le projet MyVSShellStub.AboutBoxPackage, dans le fichier \Properties\AssemblyInfo.cs. Ouvrez ce fichier.  
  
2.  Modifier la `AssemblyCompany` de la valeur **Fabrikam**, le `AssemblyProduct` et `AssemblyTitle` valeurs **Fabrikam musique éditeur**et le `AssemblyCopyright` valeur **Copyright © Fabrikam 2015**:  
  
    ```  
    [assembly: AssemblyTitle("Fabrikam Music Editor")]  
    [assembly: AssemblyDescription("")]  
    [assembly: AssemblyConfiguration("")]  
    [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")] [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor ")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")]  
    ```  
  
3.  Pour ajouter une description du produit, modifiez le `AssemblyDescription` valeur **la description de l’éditeur de Fabrikam musique.**:  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.")]  
    ```  
  
4.  Démarrer le débogage et dans l’application de shell isolé, ouvrez le **aide / sur** boîte. Vous devez voir les chaînes modifiés. Le titre de l’aide/à propos de la zone est le même que le `AssemblyTitle` valeur AssemblyInfo.cs.  
  
5.  Les propriétés de la **propos** zone se trouvent dans le fichier MyVSShellStub.AboutBoxPackage\AboutBox.xaml. Pour modifier la largeur de l’aide/à propos de la zone, accédez à la `AboutDialogStyle` bloquer et définir le `Width` propriété à 200 :  
  
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
  
6.  Régénérez la solution et démarrer le débogage du shell isolé. L’aide/à propos de la zone doit être sensiblement carrée.  
  
## <a name="before-you-deploy-the-isolated-shell-application"></a>Avant de déployer l’Application de Shell isolé  
 Votre application de shell isolé peut être installée sur n’importe quel ordinateur sur lequel le Package redistribuable Visual Studio Shell (isolé). Pour plus d’informations sur le package redistribuable, consultez le [téléchargements d’extensibilité Visual Studio](http://go.microsoft.com/fwlink/?LinkID=119298) site Web.  
  
## <a name="deploying-the-isolated-shell-application"></a>Déploiement de l’Application de Shell isolé  
 Vous déployez votre application de shell isolé sur un ordinateur cible en créant un projet d’installation. Vous devez spécifier les opérations suivantes :  
  
-   La disposition des dossiers et des fichiers sur l’ordinateur cible.  
  
-   Les conditions de lancement qui garantissent que le .NET Framework et Visual Studio shell runtime sont installées sur l’ordinateur cible.  
  
 Dans la procédure suivante, vous devrez installer InstallShield Limited Edition sur votre ordinateur.  
  
#### <a name="to-create-the-setup-project"></a>Pour créer le projet d’installation  
  
1.  Dans **l’Explorateur de solutions**, cliquez sur le nœud solution, puis sur **ajouter un nouveau projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue, développez **autres Types de projets** , puis sélectionnez **le programme d’installation et de déploiement**. Sélectionnez le modèle d’InstallShield. Nommez le nouveau projet `MySetup` puis cliquez sur **OK**.  
  
3.  Si InstallShield Limited Edition est déjà installé, passez à l’étape suivante.  
  
     Si InstallShield Limited Edition n’est pas déjà installé, la page de téléchargement d’InstallShield s’affiche. Suivez les instructions pour télécharger et installer le produit, en choisissant la version d’InstallShield qui est compatible avec votre version de Visual Studio. Vous devez décider s’il faut enregistrer votre installation de InstallShield ou l’utiliser en tant qu’évaluation. Vous devez redémarrer Visual Studio après avoir terminé l’installation.  
  
    > [!IMPORTANT]
    >  Avant de créer un projet InstallShield, vous devez démarrer Visual Studio en tant qu’administrateur. Si vous ne le faites pas, vous obtiendrez une erreur lorsque vous générez le projet.  
  
 Les étapes suivantes montrent comment configurer le projet d’installation.  
  
> [!IMPORTANT]
>  Assurez-vous que vous avez créé au moins une fois la configuration release de votre projet de shell isolé avant de configurer le projet d’installation.  
  
#### <a name="to-configure-the-setup-project"></a>Pour configurer le projet d’installation  
  
1.  Dans le **l’Explorateur de solutions**, sous le **MySetup** de projet, choisissez **Assistant projet**. Sur la ligne inférieure de la **Assistant projet** fenêtre, choisissez **informations de l’Application**. Entrez **Fabrikam** en tant que nom de votre société et **Fabrikam musique éditeur** en tant que nom de votre application. Choisissez la flèche suivant en bas à droite de la **Assistant projet**.  
  
2.  Sélectionnez **Oui** sous **votre application requiert un logiciel à installer sur l’ordinateur ?** , puis sélectionnez **Package complète de Microsoft .NET Framework 4.5**.  
  
3.  Choisissez le **fichiers d’Application** situé en bas de la fenêtre et vous assurer que le **Fabrikam musique éditeur** dossier est sélectionné.  
  
4.  Choisissez le **ajouter des fichiers** bouton. Dans le **ajouter des fichiers** boîte de dialogue zone, ajouter les fichiers suivants à partir de la **MyVSShellStub\Release** dossier :  
  
    1.  MyVSShellStub.exe.config  
  
    2.  DebuggerProxy.dll  
  
    3.  DebuggerProxy.dll.manifest  
  
    4.  MyVSShellStub.pkgdef  
  
    5.  MyVSShellStub.pkgundef  
  
    6.  MyVSShellStub.winprf  
  
    7.  Splash.bmp  
  
5.  Cliquez sur le **ajouter les sorties du projet** bouton et ajoutez **MyVSShellStub/primaire sortie**. Cliquez sur **OK**.  
  
6.  Dans le volet gauche, sous **ordinateur de Destination**, avec le bouton droit le **Fabrikam musique éditeur [INSTALLDIR]** nœud et ajouter un **nouveau dossier** nommé **Extensions**.  
  
7.  Avec le bouton droit le **Extensions** nœud dans le volet gauche et ajouter un nouveau dossier nommé **Application**.  
  
8.  Sélectionnez le **Application** dossier puis cliquez sur le **ajouter les sorties du projet** bouton, puis sélectionnez la sortie principale du projet MyVSShellStub.AboutBoxPackage.  
  
9. Cliquez sur le **ajouter des fichiers** bouton et à partir du dossier \MyVSShellStub\Release\Extensions\Application\ ajouter les fichiers suivants :  
  
    -   MyVSShellStub.AboutBoxPackage.pkgdef  
  
    -   MyVSShellStub.Application.pkgdef  
  
10. Avec le bouton droit le **Fabrikam musique éditeur [INSTALLDIR]** nœud dans le volet gauche et ajouter un nouveau dossier nommé **1033**.  
  
11. Sélectionnez le dossier 1033 et puis cliquez sur le **ajouter les sorties du projet** bouton, puis sélectionnez la sortie principale du projet MyVSShellStubUI.  
  
12. Déplacer vers le **raccourcis d’applications** fenêtre.  
  
13. Cliquez sur **nouveau** à créer un raccourci, puis sélectionnez **[ProgramFilesFolder] \Fabrikam\Fabrikam Music Editor\MyVSShellStub.Primary Output**.  
  
14. Déplacer vers le **Installation Interview** volet.  
  
15. Tous les éléments de la valeur **non**.  
  
16. Dans **l’Explorateur de solutions**, dans le projet MySetup, ouvrez **définir la configuration requise et les Actions \ exigences**. Le **exigences** fenêtre s’ouvre.  
  
17. Bouton droit sur **configuration système requise du logiciel** et sélectionnez **créer une nouvelle Condition de lancement**. Le **système recherche Assistant** s’affiche.  
  
18. Dans le **ce que vous souhaitez trouver ?** volet, choisissez **entrée de Registre** dans la liste déroulante, cliquez sur **suivant**.  
  
19. Dans le **Comment souhaitez-vous rechercher ?** volet, sélectionnez **HKEY_LOCAL_MACHINE** comme la racine du Registre. Entrez **SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** pour les systèmes 64 bits ou **SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** pour les systèmes 32 bits et entrez **installer** en tant que la valeur de Registre. Cliquez sur **Suivant**.  
  
20. Dans le **que voulez-vous faire avec la valeur ?** volet, entrez **ce produit nécessite la 2015 isolé Shell redistribuable de Visual Studio soit installé.** en tant que le texte d’affichage et cliquez sur **Terminer**.  
  
21. Régénérez la solution de shell isolé pour créer le projet d’installation.  
  
     Vous pouvez trouver le fichier setup.exe dans le dossier suivant :  
  
     \MyVSShellStub\MySetup\MySetup\Express\SingleImage\DiskImages\DISK1  
  
## <a name="testing-the-installation-program"></a>Le programme d’Installation de test  
 Pour tester le programme d’installation, copiez le fichier setup.exe vers un autre ordinateur et lancez l’exécutable de programme d’installation. Vous devez être en mesure d’exécuter l’application de shell isolé.
