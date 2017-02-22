---
title: "Proc&#233;dure pas &#224; pas : Cr&#233;ation d&#39;une Application de base de Shell isol&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Shell Visual Studio, procédures pas à pas"
  - "Interface de procédures pas à pas (Visual Studio)"
  - "application d'environnement procédures pas à pas (Visual Studio), isolé"
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: 54
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 54
---
# Proc&#233;dure pas &#224; pas : Cr&#233;ation d&#39;une Application de base de Shell isol&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette procédure pas à pas montre comment créer une solution de shell isolé, personnaliser la fenêtre à propos d'et créer un programme d'installation qui installe le shell isolé.  
  
## Composants requis  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement Visual Studio. Pour plus d'informations, consultez [Kit de développement logiciel Visual Studio](../extensibility/visual-studio-sdk.md). Pour déployer l'interpréteur de commandes isolé, vous devez également utiliser le Package redistribuable Visual Studio Shell \(isolé\).  
  
## Création d'une Solution de Shell isolé  
 Cette section montre comment utiliser le modèle de projet Visual Studio Shell isolé pour créer une solution de shell isolé. La solution contient les projets suivants :  
  
-   Le *SolutionName*. Projet AboutBoxPackage, qui vous permet de personnaliser l'apparence de l'aide de\/sur la zone.  
  
-   Le projet ShellExtensionsVSIX, qui contient le fichier source.extension.vsixmanifest qui définit les différents composants de l'application shell isolé.  
  
-   Le *SolutionName* projet, ce qui génère le fichier exécutable qui appelle l'application shell isolé. Ce projet contient le dossier de personnalisation du Shell, ce qui permet de vous permettent de personnaliser l'apparence et le comportement de l'application shell isolé.  
  
-   Le *SolutionName* projet d'interface utilisateur, ce qui génère un assembly satellite qui définit les chaînes localisables et les commandes de menu active.  
  
#### Pour créer une solution de base de shell isolé  
  
1.  Ouvrez Visual Studio et créez un nouveau projet.  
  
2.  Dans le **Nouveau projet** fenêtre, développez **autres Types de projets** puis **extensibilité**. Sélectionnez le **Visual Studio Shell isolé** modèle de projet.  
  
3.  Nommez le projet `MyVSShellStub` et spécifiez un emplacement. Assurez\-vous que **créer le répertoire pour la solution** est activée, puis cliquez sur **OK**.  
  
     La nouvelle solution apparaît dans **l'Explorateur de solutions**.  
  
4.  Générez la solution et commencer à déboguer l'application shell isolé.  
  
     Visual Studio shell isolé s'affiche. Lit la barre de titre **MyVSShellStub**. L'icône de barre de titre est généré à partir de \\MyVSShellStub\\Resource Files\\ApplicationIcon.ico.  
  
## Personnalisation de l'icône et le nom de l'Application  
 Vous souhaiterez peut\-être personnaliser votre application en utilisant le nom de votre entreprise et de son logo dans la barre de titre. Les étapes suivantes montrent comment modifier le nom et l'icône qui s'affichent dans la barre de titre d'application personnalisée en modifiant le fichier de définition de package, MyVSShellStub.Application.pkgdef.  
  
#### Pour personnaliser l'icône et le nom de l'application  
  
1.  Dans le projet MyVSShellStub, ouvrez \\Shell Customization\\MyVSShellStub.Application.pkgdef.  
  
2.  Modifier la `AppName` valeur de l'élément à **« AppName » \= « éditeur de musique Fabrikam »**  
  
3.  Pour modifier l'icône d'application, copier une icône différente dans le répertoire \\MyVSShellStub\\MyVSShellStub\\MyVSShellStub\\. Renommez le fichier ApplicationIcon.ico existant en ApplicationIcon1.ico. Renommez le nouveau fichier en ApplicationIcon.ico.  
  
4.  Générez la solution et démarrer le débogage. Le shell isolé IDE s'affiche. La barre de titre comporte votre nouvelle icône en regard de la mention **Fabrikam musique éditeur**.  
  
## Personnalisation de la Page d'accueil du navigateur Web par défaut  
 Cette section montre comment modifier la page d'accueil par défaut de le **navigateur Web** fenêtre en modifiant le fichier de définition de package.  
  
#### Pour personnaliser la page d'accueil de navigateur Web par défaut  
  
1.  Dans le fichier MyVSShellStub.Application.pkgdef, modifiez le `DefaultHomePage` valeur de l'élément « http:\/\/www.Microsoft.com ».  
  
2.  Régénérez le projet MyVSShellStub.  
  
3.  Générez la solution et démarrer le débogage.  
  
4.  Dans **affichage \/ autres fenêtres**, cliquez sur **navigateur Web**. Le **navigateur Web** affiche la page d'accueil de Microsoft Corporation.  
  
## Suppression de la commande d'impression  
 Le fichier .vsct dans un projet de l'interface utilisateur du shell isolé se compose d'un ensemble de déclarations du formulaire `<Define name=No_`*élément*`>`, où *élément* est un des menus de Visual Studio standard et des commandes.  
  
 Si une déclaration est retirée, ce menu ou une commande est exclue à partir du shell isolé. À l'inverse, si une déclaration est commentée, le menu ou la commande est inclus dans le shell isolé.  
  
 Dans les étapes suivantes, vous supprimez les commentaires de commande d'impression dans votre fichier .vsct.  
  
#### Pour supprimer la commande d'impression  
  
1.  Vérifiez que le **Print** commande apparaît sur le **fichier** menu de l'application shell isolé.  
  
2.  Dans le projet MyVSShellStubUI, ouvrez \\Resource Files\\MyVSShellStubUI.vsct pour la modification.  
  
3.  Supprimez les commentaires de cette ligne :  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4.  Cela supprime la commande d'impression.  
  
5.  Démarrez le débogage de l'application shell isolé. Vérifiez que le **fichier \/ impression** commande a disparu.  
  
## Suppression de fonctionnalités à partir du Shell isolé  
 Vous pouvez supprimer certains packages qui sont chargés avec Visual Studio en modifiant le fichier .pkgundef si vous ne souhaitez pas ces fonctionnalités dans votre application personnalisée shell isolé. Vous spécifiez le package dans une des sous\-clés de la clé de Registre \\Packages $RootKey$.  
  
> [!NOTE]
>  Pour découvrir les fonctionnalités de GUID de Visual Studio, consultez [GUID du package de fonctionnalités de Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
 La procédure suivante montre comment supprimer le code XML éditeur à partir du shell isolé.  
  
#### Pour supprimer l'éditeur XML  
  
1.  Ouvrez le fichier MyVSShellStub.pkgundef dans le dossier de personnalisation du Shell du projet MyVSShellStub.  
  
2.  Supprimez les commentaires de la ligne suivante :  
  
     \[$RootKey$ \\Packages\\ {87569308\-4813\-40a0\-9cd0\-d7a30838ca3f}\]  
  
3.  Régénérez la solution et commencer à déboguer le shell isolé. Ouvrez un fichier XML, par exemple, \\MyVSShellStub\\MyVSShellStub\\MyVSShellStubUI\\MyVSShellStubUI.vsct. Vérifiez que les mots clés dans le fichier XML sont colorisés pas et ce en tapant « \< » sur une ligne n'a pas à rendre des info\-bulles XML.  
  
## Personnalisation de l'aide\/à propos de la zone  
 Vous pouvez personnaliser l'aide\/à propos de la zone, qui est créé dans le cadre du modèle de projet shell isolé.  
  
#### Pour personnaliser le nom de la société  
  
1.  Le nom de la société, les informations de copyright, version du produit et description du produit sont trouvent dans le projet MyVSShellStub.AboutBoxPackage, dans le fichier \\Properties\\AssemblyInfo.cs. Ouvrez ce fichier.  
  
2.  Modifier la `AssemblyCompany` valeur **Fabrikam**, le `AssemblyProduct` et `AssemblyTitle` des valeurs de **Fabrikam musique éditeur**, et le `AssemblyCopyright` valeur **Copyright © Fabrikam 2015**:  
  
    ```  
    [assembly: AssemblyTitle("Fabrikam Music Editor")] [assembly: AssemblyDescription("")] [assembly: AssemblyConfiguration("")] [assembly: AssemblyCompany("Fabrikam")] [assembly: AssemblyProduct("Fabrikam Music Editor")] [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")] [assembly: AssemblyCompany("Fabrikam")] [assembly: AssemblyProduct("Fabrikam Music Editor ")] [assembly: AssemblyCopyright("Copyright © Fabrikam 2015”)]  
    ```  
  
3.  Pour ajouter une description du produit, modifiez la `AssemblyDescription` valeur **la description de l'éditeur de musique de Fabrikam.**:  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.”)]  
    ```  
  
4.  Démarrer le débogage et dans l'application shell isolé, ouvrez le **vous aider à propos** boîte. Vous devez voir les chaînes modifiés. Le titre de l'aide\/à propos de la zone est identique à la `AssemblyTitle` valeur dans AssemblyInfo.cs.  
  
5.  Les propriétés de la **propos** zone se trouvent dans le fichier MyVSShellStub.AboutBoxPackage\\AboutBox.xaml. Pour modifier la largeur de l'aide de\/sur la zone, accédez à la `AboutDialogStyle` bloquer et définir le `Width` propriété à 200 :  
  
    ```  
    <Style x:Key="AboutDialogStyle" TargetType="Window"> <Setter Property="Height" Value="Auto" /> <Setter Property="Width" Value="200" /> <Setter Property="ShowInTaskbar" Value="False" /> <Setter Property="ResizeMode" Value="NoResize" /> <Setter Property="WindowStyle" Value="SingleBorderWindow" /> <Setter Property="SizeToContent" Value="Height" /> </Style>  
    ```  
  
6.  Régénérez la solution et commencer à déboguer le shell isolé. L'aide\/à propos de la zone doit être sensiblement carrée.  
  
## Avant de déployer l'Application Shell isolé  
 Votre application shell isolé peut être installée sur n'importe quel ordinateur sur lequel le Package redistribuable Visual Studio Shell \(isolé\). Pour plus d'informations sur le package redistribuable, consultez le [téléchargements d'extensibilité Visual Studio](http://go.microsoft.com/fwlink/?LinkID=119298) site Web.  
  
## Déploiement de l'Application Shell isolé  
 Vous déployez votre application shell isolé sur un ordinateur cible en créant un projet d'installation. Vous devez spécifier les éléments suivants :  
  
-   La disposition des dossiers et des fichiers sur l'ordinateur cible.  
  
-   Les conditions de lancement qui garantissent que le .NET Framework et Visual Studio shell runtime sont installées sur l'ordinateur cible.  
  
 Dans la procédure suivante, vous devrez installer InstallShield Limited Edition sur votre ordinateur.  
  
#### Pour créer le projet d'installation  
  
1.  Dans **l'Explorateur de solutions**, cliquez sur le nœud de solution, puis **Ajouter un nouveau projet**.  
  
2.  Dans le **Nouveau projet** boîte de dialogue, développez **autres Types de projets** puis sélectionnez **le programme d'installation et de déploiement**. Sélectionnez le modèle de InstallShield. Nommez le nouveau projet `MySetup` puis **OK**.  
  
3.  Si InstallShield Limited Edition est déjà installé, passez à l'étape suivante.  
  
     Si InstallShield Limited Edition n'est pas déjà installé, la page de téléchargement d'InstallShield s'affiche. Suivez les instructions pour télécharger et installer le produit, en choisissant la version de InstallShield qui est compatible avec votre version de Visual Studio. Vous devez décider s'il faut enregistrer votre installation de InstallShield ou l'utiliser comme une évaluation. Vous devez redémarrer Visual Studio après avoir terminé l'installation.  
  
    > [!IMPORTANT]
    >  Avant de créer un projet InstallShield, vous devez démarrer Visual Studio en tant qu'administrateur. Si vous ne le faites pas, vous obtiendrez une erreur lorsque vous générez le projet.  
  
 Les étapes suivantes montrent comment configurer le projet d'installation.  
  
> [!IMPORTANT]
>  Assurez\-vous que vous avez créé au moins une fois la configuration release de votre projet d'environnement isolé avant de configurer le projet d'installation.  
  
#### Pour configurer le projet d'installation  
  
1.  Dans le **l'Explorateur de solutions**, sous la **MySetup** du projet, choisissez **Assistant projet**. Sur la ligne inférieure de la **Assistant projet** fenêtre, choisissez **informations sur l'Application**. Entrez **Fabrikam** comme nom de votre société et **Fabrikam musique éditeur** comme nom de votre application. Cliquez sur la flèche suivant en bas à droite de la **Assistant projet**.  
  
2.  Sélectionnez **Oui** sous **votre application requiert un logiciel soit installé sur l'ordinateur?** puis sélectionnez **Package complet de Microsoft .NET Framework 4.5**.  
  
3.  Choisissez le **fichiers d'Application** bouton au bas de la fenêtre et vous assurer que les **Fabrikam musique éditeur** dossier est sélectionné.  
  
4.  Choisissez le **Ajouter des fichiers** bouton. Dans le **Ajouter des fichiers** boîte de dialogue zone, ajoutez les fichiers suivants à partir de la **MyVSShellStub\\Release** dossier :  
  
    1.  MyVSShellStub.exe.config  
  
    2.  DebuggerProxy.dll  
  
    3.  DebuggerProxy.dll.manifest  
  
    4.  MyVSShellStub.pkgdef  
  
    5.  MyVSShellStub.pkgundef  
  
    6.  MyVSShellStub.winprf  
  
    7.  Splash.bmp  
  
5.  Cliquez sur le **Ajouter les sorties du projet** bouton et ajoutez **MyVSShellStub\/primaire sortie**. Cliquez sur **OK**.  
  
6.  Dans le volet gauche, sous **ordinateur de Destination**, avec le bouton droit le **Fabrikam musique éditeur \[INSTALLDIR\]** nœud et ajouter un **Nouveau dossier** nommé **Extensions**.  
  
7.  Avec le bouton droit le **Extensions** nœud dans le volet gauche et ajoutez un nouveau dossier nommé **Application**.  
  
8.  Sélectionnez le **Application** dossier, cliquez sur le **Ajouter les sorties du projet** bouton, puis sélectionnez la sortie principale du projet MyVSShellStub.AboutBoxPackage.  
  
9. Cliquez sur le **Ajouter des fichiers** bouton et à partir du dossier \\MyVSShellStub\\Release\\Extensions\\Application\\, ajoutez les fichiers suivants :  
  
    -   MyVSShellStub.AboutBoxPackage.pkgdef  
  
    -   MyVSShellStub.Application.pkgdef  
  
10. Avec le bouton droit le **Fabrikam musique éditeur \[INSTALLDIR\]** nœud dans le volet gauche et ajoutez un nouveau dossier nommé **1033**.  
  
11. Sélectionnez le dossier 1033, puis le **Ajouter les sorties du projet** bouton, puis sélectionnez la sortie principale du projet MyVSShellStubUI.  
  
12. Déplacer vers le **raccourcis d'Application** fenêtre.  
  
13. Cliquez sur **nouveau** pour créer un raccourci et sélectionnez **\[ProgramFilesFolder\] \\Fabrikam\\Fabrikam Music Editor\\MyVSShellStub.Primary Output**.  
  
14. Déplacer vers le **Installation Interview** volet.  
  
15. Tous les éléments de la valeur **non**.  
  
16. Dans **l'Explorateur de solutions**, dans le projet MySetup, ouvrez **définir la configuration requise et les Actions \\ exigences**. Le **exigences** fenêtre s'ouvre.  
  
17. Cliquez avec le bouton droit **configuration système requise du logiciel** et sélectionnez **créer une nouvelle Condition de lancement**. Le **Assistant de recherche système** s'affiche.  
  
18. Dans le **que voulez\-vous rechercher?** volet, choisissez **entrée de Registre** dans la liste déroulante, cliquez sur **Suivant**.  
  
19. Dans le **Comment souhaitez\-vous chercher?** volet, sélectionnez **HKEY\_LOCAL\_MACHINE** sous la racine du Registre. Entrez **SOFTWARE\\Wow6432Node\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\isoshell** pour les systèmes 64 bits ou **SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\isoshell** pour les systèmes 32 bits, puis entrez **installer** en tant que la valeur de Registre. Cliquez sur **Suivant**.  
  
20. Dans le **que voulez\-vous faire avec la valeur?** volet, entrez **ce produit requiert Visual Studio 2015 isolé Shell Redistributable doit être installé.** comme texte d'affichage et cliquez sur **Terminer**.  
  
21. Régénérez la solution shell isolé pour créer le projet d'installation.  
  
     Vous pouvez trouver le fichier setup.exe dans le dossier suivant :  
  
     \\MyVSShellStub\\MySetup\\MySetup\\Express\\SingleImage\\DiskImages\\DISK1  
  
## Le programme d'Installation de test  
 Pour tester le programme d'installation, copiez le fichier setup.exe vers un autre ordinateur et lancez l'exécutable d'installation. Soyez en mesure d'exécuter l'application shell isolé.