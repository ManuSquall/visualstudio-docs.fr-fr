---
title: 'Procédure pas à pas : Création d’un base des Application Shell isolée | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, walkthroughs
- Shell [Visual Studio], walkthroughs
- walkthroughs [Visual Studio], isolated shell-based application
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: 55
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 68b4fb6f7bb07cbb25d2fa8552e92875c5c242bf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505933"
---
# <a name="walkthrough-creating-a-basic-isolated-shell-application"></a>Procédure pas à pas : Création d’une Application Shell isolée de base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [procédure pas à pas : création d’une Application Shell isolée de base](https://docs.microsoft.com/visualstudio/extensibility/walkthrough-creating-a-basic-isolated-shell-application).  
  
Cette procédure pas à pas montre comment créer une solution de shell isolé, personnaliser la fenêtre outil à propos d’et créer un programme d’installation qui installe le shell isolé.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Pour déployer le shell isolé, vous devez également utiliser le Package redistribuable Visual Studio Shell (isolé).  
  
## <a name="creating-an-isolated-shell-solution"></a>Création d’une Solution de Shell isolé  
 Cette section montre comment utiliser le modèle de projet Visual Studio Shell isolé pour créer une solution de shell isolé. La solution contient les projets suivants :  
  
-   Le *SolutionName*. Projet AboutBoxPackage, ce qui vous permet de personnaliser l’apparence de l’aide/à propos de la zone.  
  
-   Le projet ShellExtensionsVSIX, qui contient le fichier source.extension.vsixmanifest qui définit les différents composants de l’application de shell isolé.  
  
-   Le *SolutionName* projet, ce qui génère le fichier exécutable qui appelle l’application de shell isolé. Ce projet contient le dossier de personnalisation du Shell, ce qui permet de vous permettent de personnaliser l’apparence et le comportement de l’application de shell isolé.  
  
-   Le *SolutionName* projet d’interface utilisateur, ce qui génère un assembly satellite qui définit les commandes de menu active et les chaînes localisables.  
  
#### <a name="to-create-a-basic-isolated-shell-solution"></a>Pour créer une solution de base de shell isolé  
  
1.  Ouvrez Visual Studio et créez un projet.  
  
2.  Dans le **nouveau projet** fenêtre, développez **autres Types de projets** , puis **extensibilité**. Sélectionnez le **Visual Studio Shell isolé** modèle de projet.  
  
3.  Nommez le projet `MyVSShellStub` et spécifiez un emplacement. Assurez-vous que l’option **créer le répertoire pour la solution** est activée, puis cliquez sur **OK**.  
  
     La nouvelle solution apparaît dans **l’Explorateur de solutions**.  
  
4.  Générez la solution et démarrez le débogage de l’application de shell isolé.  
  
     Le shell isolé Visual Studio s’affiche. Lit la barre de titre **MyVSShellStub**. L’icône de barre de titre est généré à partir de \MyVSShellStub\Resource Files\ApplicationIcon.ico.  
  
## <a name="customizing-the-application-name-and-icon"></a>Personnalisation de l’icône et le nom de l’Application  
 Vous pouvez souhaiter personnaliser votre application en utilisant le nom de votre entreprise et de son logo dans la barre de titre. Les étapes suivantes montrent comment modifier le nom et l’icône qui s’affichent dans la barre de titre d’application personnalisée en modifiant le fichier de définition de package, MyVSShellStub.Application.pkgdef.  
  
#### <a name="to-customize-the-application-name-and-icon"></a>Pour personnaliser l’icône et le nom de l’application  
  
1.  Dans le projet MyVSShellStub, ouvrez \Shell Customization\MyVSShellStub.Application.pkgdef.  
  
2.  Modifier le `AppName` valeur de l’élément à **« AppName » = « éditeur de musique Fabrikam »**  
  
3.  Pour modifier l’icône d’application, copiez une autre icône dans le répertoire de \MyVSShellStub\MyVSShellStub\MyVSShellStub\. Renommez le fichier ApplicationIcon.ico existant en ApplicationIcon1.ico. Renommez le nouveau fichier à ApplicationIcon.ico.  
  
4.  Générez la solution et commencez le débogage. Le shell isolé IDE s’affiche. La barre de titre a votre nouvelle icône à côté de l’option **Fabrikam musique éditeur**.  
  
## <a name="customizing-the-default-web-browser-home-page"></a>Personnalisation de la Page d’accueil du navigateur Web par défaut  
 Cette section montre comment modifier la page d’accueil par défaut de la **navigateur Web** fenêtre en modifiant le fichier de définition de package.  
  
#### <a name="to-customize-the-default-web-browser-home-page"></a>Pour personnaliser la page d’accueil de navigateur Web par défaut  
  
1.  Dans le fichier MyVSShellStub.Application.pkgdef, modifiez le `DefaultHomePage` valeur de l’élément « http://www.microsoft.com».  
  
2.  Régénérez le projet MyVSShellStub.  
  
3.  Générez la solution et commencez le débogage.  
  
4.  Dans **vue / autres Windows**, cliquez sur **navigateur Web**. Le **navigateur Web** fenêtre affiche la page d’accueil de Microsoft Corporation.  
  
## <a name="removing-the-print-command"></a>Suppression de la commande d’impression  
 Le fichier .vsct dans un projet de l’interface utilisateur du shell isolé se compose d’un ensemble de déclarations du formulaire `<Define name=No_` *élément*`>`, où *élément* est un des menus de Visual Studio standard et commandes.  
  
 Si une déclaration est sans commentaire, ce menu ou la commande est exclue du shell isolé. À l’inverse, si une déclaration est commentée, le menu ou la commande est inclus dans le shell isolé.  
  
 Dans les étapes suivantes, vous supprimez les commentaires de commande d’impression dans votre fichier .vsct.  
  
#### <a name="to-remove-the-print-command"></a>Pour supprimer la commande d’impression  
  
1.  Vérifiez que le **impression** commande apparaît dans le **fichier** menu dans l’application de shell isolé.  
  
2.  Dans le projet MyVSShellStubUI, ouvrez \Resource Files\MyVSShellStubUI.vsct pour la modification.  
  
3.  Supprimez les commentaires de cette ligne :  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4.  Cette opération supprime la commande d’impression.  
  
5.  Démarrez le débogage de l’application de shell isolé. Vérifiez que le **fichier / impression** commande a disparu.  
  
## <a name="removing-features-from-the-isolated-shell"></a>Suppression de fonctionnalités à partir du Shell isolé  
 Vous pouvez supprimer certains des packages qui sont chargés avec Visual Studio en modifiant le fichier .pkgundef si vous ne souhaitez pas ces fonctionnalités dans votre application de shell isolé personnalisé. Vous spécifiez le package dans une des sous-clés de la clé de Registre \Packages $RootKey$.  
  
> [!NOTE]
>  Pour rechercher les fonctionnalités de GUID de Visual Studio, consultez [Package GUID de fonctionnalités de Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
 La procédure suivante montre comment supprimer le code XML de l’éditeur à partir du shell isolé.  
  
#### <a name="to-remove-the-xml-editor"></a>Pour supprimer l’éditeur XML  
  
1.  Ouvrez le fichier MyVSShellStub.pkgundef dans le dossier de personnalisation du Shell du projet MyVSShellStub.  
  
2.  Supprimez les commentaires de la ligne suivante :  
  
     [$RootKey$ \Packages\\{87569308-4813-40a0-9cd0-d7a30838ca3f}]  
  
3.  Régénérez la solution et démarrez le débogage du shell isolé. Ouvrez un fichier XML, par exemple, \MyVSShellStub\MyVSShellStub\MyVSShellStubUI\MyVSShellStubUI.vsct. Vérifiez que les mots clés XML dans le fichier ne sont pas colorisées et qu’une pression sur « < » sur une ligne n’a pas à rendre des info-bulles XML.  
  
## <a name="customizing-the-helpabout-box"></a>Personnalisation de l’aide/à propos de la zone  
 Vous pouvez personnaliser l’aide/à propos de la zone, qui est créé en tant que partie du modèle de projet shell isolé.  
  
#### <a name="to-customize-the-company-name"></a>Pour personnaliser le nom de l’entreprise  
  
1.  Le nom de la société, les informations de copyright, version du produit et description du produit sont trouvent dans le projet MyVSShellStub.AboutBoxPackage, dans le fichier \Properties\AssemblyInfo.cs. Ouvrez ce fichier.  
  
2.  Modification la `AssemblyCompany` valeur **Fabrikam**, le `AssemblyProduct` et `AssemblyTitle` valeurs **Fabrikam musique éditeur**et le `AssemblyCopyright` valeur **Copyright © Fabrikam 2015**:  
  
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
  
3.  Pour ajouter une description du produit, modifiez le `AssemblyDescription` valeur **la description de l’éditeur de musique de Fabrikam.**:  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.”)]  
    ```  
  
4.  Démarrer le débogage et dans l’application de shell isolé, ouvrez le **vous aider à propos** boîte. Vous devez voir les chaînes modifiées. Le titre de l’aide/à propos de la zone est identique à la `AssemblyTitle` valeur dans AssemblyInfo.cs.  
  
5.  Les propriétés de la **aide/à propos** zone elle-même se trouvent dans le fichier MyVSShellStub.AboutBoxPackage\AboutBox.xaml. Pour modifier la largeur de l’aide/à propos de la zone, accédez à la `AboutDialogStyle` bloquer et définir le `Width` propriété à 200 :  
  
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
  
6.  Régénérez la solution et démarrez le débogage du shell isolé. L’aide/à propos de la zone doit être environ carré.  
  
## <a name="before-you-deploy-the-isolated-shell-application"></a>Avant de déployer l’Application de Shell isolé  
 Votre application de shell isolé peut être installée sur n’importe quel ordinateur sur lequel le Package redistribuable Visual Studio Shell (isolé). Pour plus d’informations sur le package redistribuable, consultez le [téléchargements de Visual Studio Extensibility](http://go.microsoft.com/fwlink/?LinkID=119298) site Web.  
  
## <a name="deploying-the-isolated-shell-application"></a>Déploiement de l’Application de Shell isolé  
 Vous déployez votre application de shell isolé sur un ordinateur cible en créant un projet d’installation. Vous devez spécifier les opérations suivantes :  
  
-   La disposition des dossiers et des fichiers sur l’ordinateur cible.  
  
-   Les conditions de lancement qui garantissent que le .NET Framework et Visual Studio shell runtime sont installées sur l’ordinateur cible.  
  
 Dans la procédure suivante, vous devrez installer InstallShield Limited Edition sur votre ordinateur.  
  
#### <a name="to-create-the-setup-project"></a>Pour créer le projet d’installation  
  
1.  Dans **l’Explorateur de solutions**, cliquez sur le nœud de solution, puis sur **ajouter un nouveau projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue, développez **autres Types de projets** , puis sélectionnez **le programme d’installation et de déploiement**. Sélectionnez le modèle de InstallShield. Nommez le nouveau projet `MySetup` puis cliquez sur **OK**.  
  
3.  Si InstallShield Limited Edition est déjà installé, passez à l’étape suivante.  
  
     Si InstallShield Limited Edition n’est pas déjà installé, la page de téléchargement d’InstallShield s’affiche. Suivez les instructions pour télécharger et installer le produit, le choix de la version de InstallShield qui est compatible avec votre version de Visual Studio. Vous devez décider s’il faut inscrire votre installation de InstallShield ou l’utiliser en tant qu’évaluation. Vous devez redémarrer Visual Studio après avoir terminé l’installation.  
  
    > [!IMPORTANT]
    >  Avant de créer un projet InstallShield, vous devez démarrer Visual Studio en tant qu’administrateur. Si vous ne le faites pas, vous obtiendrez une erreur lorsque vous générez le projet.  
  
 Les étapes suivantes montrent comment configurer le projet d’installation.  
  
> [!IMPORTANT]
>  Assurez-vous que vous avez créé au moins une fois la configuration release de votre projet de shell isolé avant de configurer le projet d’installation.  
  
#### <a name="to-configure-the-setup-project"></a>Pour configurer le projet d’installation  
  
1.  Dans le **l’Explorateur de solutions**, sous le **MySetup** de projet, choisissez **Assistant projet**. Sur la ligne inférieure de la **Assistant projet** fenêtre, choisissez **informations sur l’Application**. Entrez **Fabrikam** en tant que nom de votre société et **Fabrikam musique éditeur** comme nom de votre application. Choisissez la flèche suivant en bas à droite de la **Assistant projet**.  
  
2.  Sélectionnez **Oui** sous **votre application nécessite-t-elle un logiciel à installer sur l’ordinateur ?** , puis sélectionnez **Package complet de Microsoft .NET Framework 4.5**.  
  
3.  Choisissez le **fichiers d’Application** bouton en bas de la fenêtre et vous assurer que le **Fabrikam musique éditeur** dossier est sélectionné.  
  
4.  Choisissez le **ajouter des fichiers** bouton. Dans le **ajouter des fichiers** boîte de dialogue zone, ajoutez les fichiers suivants à partir de la **MyVSShellStub\Release** dossier :  
  
    1.  MyVSShellStub.exe.config  
  
    2.  DebuggerProxy.dll  
  
    3.  DebuggerProxy.dll.manifest  
  
    4.  MyVSShellStub.pkgdef  
  
    5.  MyVSShellStub.pkgundef  
  
    6.  MyVSShellStub.winprf  
  
    7.  Splash.bmp  
  
5.  Cliquez sur le **ajouter les sorties du projet** bouton et ajoutez **MyVSShellStub/primaire sortie**. Cliquez sur **OK**.  
  
6.  Dans le volet gauche, sous **ordinateur de Destination**, avec le bouton droit le **Fabrikam musique éditeur [INSTALLDIR]** nœud et ajouter un **nouveau dossier** nommé **Extensions** .  
  
7.  Cliquez sur le **Extensions** nœud dans le volet gauche et ajoutez un nouveau dossier nommé **Application**.  
  
8.  Sélectionnez le **Application** dossier puis cliquez sur le **ajouter les sorties du projet** , puis sélectionnez la sortie principale du projet MyVSShellStub.AboutBoxPackage.  
  
9. Cliquez sur le **ajouter des fichiers** bouton et à partir du dossier \MyVSShellStub\Release\Extensions\Application\ ajouter les fichiers suivants :  
  
    -   MyVSShellStub.AboutBoxPackage.pkgdef  
  
    -   MyVSShellStub.Application.pkgdef  
  
10. Avec le bouton droit le **Fabrikam musique éditeur [INSTALLDIR]** nœud dans le volet gauche et ajoutez un nouveau dossier nommé **1033**.  
  
11. Sélectionnez le dossier 1033 et puis cliquez sur le **ajouter les sorties du projet** bouton, puis sélectionnez la sortie principale du projet MyVSShellStubUI.  
  
12. Déplacer vers le **raccourcis d’Application** fenêtre.  
  
13. Cliquez sur **New** à créer un raccourci, puis sélectionnez **[ProgramFilesFolder] \Fabrikam\Fabrikam Music Editor\MyVSShellStub.Primary Output**.  
  
14. Déplacer vers le **Installation Interview** volet.  
  
15. Tous les éléments de la valeur **non**.  
  
16. Dans **l’Explorateur de solutions**, dans le projet MySetup, ouvrez **définir la configuration requise et les Actions \ exigences**. Le **exigences** fenêtre s’ouvre.  
  
17. Bouton droit sur **configuration système logicielle requise** et sélectionnez **créer une nouvelle Condition de lancement**. Le **système recherche Assistant** s’affiche.  
  
18. Dans le **que voulez-vous rechercher ?** volet, choisissez **entrée de Registre** dans la liste déroulante, cliquez sur **suivant**.  
  
19. Dans le **comment vous voulez chercher ?** volet, sélectionnez **HKEY_LOCAL_MACHINE** comme la racine du Registre. Entrez **SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** pour systèmes 64 bits ou **SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** pour les systèmes 32 bits, puis entrez  **Installer** en tant que la valeur de Registre. Cliquez sur **Suivant**.  
  
20. Dans le **que voulez-vous faire avec la valeur ?** volet, entrez **ce produit requiert Visual Studio 2015 isolé Shell Redistributable doit être installé.** comme le texte d’affichage et cliquez sur **Terminer**.  
  
21. Régénérez la solution de shell isolé pour créer le projet d’installation.  
  
     Vous pouvez trouver le fichier setup.exe dans le dossier suivant :  
  
     \MyVSShellStub\MySetup\MySetup\Express\SingleImage\DiskImages\DISK1  
  
## <a name="testing-the-installation-program"></a>Le programme d’Installation de test  
 Pour tester le programme d’installation, copiez le fichier setup.exe vers un autre ordinateur et exécuter l’exécutable d’installation. Soyez en mesure d’exécuter l’application de shell isolé.

