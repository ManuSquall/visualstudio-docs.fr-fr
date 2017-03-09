---
title: "How to: Publish a WPF Application with Visual Styles Enabled | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
caps.latest.revision: 3
caps.handback.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
---
# How to: Publish a WPF Application with Visual Styles Enabled
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les styles visuels permettent à l'apparence des contrôles communs d'être modifiée en fonction du thème choisi par l'utilisateur.  Par défaut, les styles visuels ne sont pas activés pour les applications Windows Presentation Foundation \(WPF\), vous devez ainsi les extraire manuellement.  Toutefois, l'activation des styles visuels dans une application WPF puis la publication de la solution provoque une erreur.  Cette rubrique décrit comment résoudre cette erreur et le processus de publication d'une application WPF avec les styles visuels activés.  Pour plus d'informations sur les styles visuels, consultez [Visual Styles Overview](http://msdn.microsoft.com/fr-fr/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e).  Pour plus d'informations sur le message d'erreur, consultez [Troubleshooting Specific Errors in ClickOnce Deployments](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md).  
  
 Pour corriger l'erreur et publier sa solution, vous devez effectuer les tâches suivantes :  
  
-   [Publiez la solution sans styles visuels activés.](#BKMK_publishsolwovs).  
  
-   [Créer un fichier manifeste](#BKMK_CreateManifest).  
  
-   [Incluez le fichier manifeste dans le fichier exécutable de la solution publiée](#BKMK_embedmanifest).  
  
-   [Signe les manifestes d'application et de déploiement](#BKMK_signappdeplyman)  
  
 Ensuite, déplacez les fichiers publiés à l'emplacement à partir duquel vous souhaitez que les utilisateurs finals installent l'application.  
  
##  <a name="BKMK_publishsolwovs"></a> Publiez la solution sans styles visuels activés.  
  
1.  Vérifiez que votre projet n'a pas les styles visuels activés.  D'abord, vérifiez le fichier manifeste de votre projet pour le XML suivant.  Puis, si le XML est présent, insérez le XML avec une balise de commentaire.  
  
     Les styles visuels ne sont pas activés par défaut.  
  
    ```  
    <dependency>    <dependentAssembly>      <assemblyIdentity          type="win32"          name="Microsoft.Windows.Common-Controls"          version="6.0.0.0"          processorArchitecture="*"          publicKeyToken="6595b64144ccf1df"          language="*"        />    </dependentAssembly>  </dependency>  
    ```  
  
     Les procédures suivantes montrent comment ouvrir le fichier manifeste associé à votre projet.  
  
    ###### Pour ouvrir le fichier manifeste dans un projet Visual Basic  
  
    1.  Dans le barre de menu, cliquez sur **Projet**, *ProjectName***Propriétés**, où *ProjectName* est le nom de votre projet de base de données.  
  
         Les pages de propriétés de votre projet WPF apparaissent.  
  
    2.  Sous l'onglet **Application**, choisissez **Afficher les paramètres Windows**.  
  
         Le fichier app.manifest s'ouvre dans **Editeur XML**  
  
    ###### Pour ouvrir le fichier manifeste dans un projet C\#  
  
    1.  Dans le barre de menu, cliquez sur **Projet**, *ProjectName***Propriétés**, où *ProjectName* est le nom de votre projet de base de données.  
  
         Les pages de propriétés de votre projet WPF apparaissent.  
  
    2.  Sous l'onglet **Application**, notez le nom qui apparaît dans le champ manifeste.  Il s'agit du nom du manifeste associé à votre projet.  
  
        > [!NOTE]
        >  Si **Manifestes incorporés aux paramètres par défaut** ou **Créez l'application sans manifeste** apparaissent dans le champ manifeste, les styles visuels ne sont pas activées.  Si le nom d'un fichier manifeste s'affiche dans le champ manifeste, passez à l'étape suivante de cette procédure.  
  
    3.  Dans **Explorateur de solutions**, choisissez **Afficher tous les fichiers** \(\).  
  
         Ce bouton affiche tous les éléments de projet, y compris ceux qui ont été exclus et ceux qui sont normalement masqués.  Le fichier manifeste apparaît comme un élément de projet.  
  
2.  Construisez et générez votre solution.  Pour plus d'informations sur la publication d'une solution, consultez [How to: Publish a ClickOnce Application using the Publish Wizard](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md).  
  
##  <a name="BKMK_CreateManifest"></a> Créer un fichier manifeste  
  
1.  Collez le code XML suivant dans un fichier Bloc\-notes.  
  
     Ce code XML décrit l'assembly qui contient des contrôles qui prennent en charge des styles visuels.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?><asmv1:assembly manifestVersion="1.0"                xmlns="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"                xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  <dependency>    <dependentAssembly>      <assemblyIdentity        type="win32"        name="Microsoft.Windows.Common-Controls"        version="6.0.0.0"        processorArchitecture="*"        publicKeyToken="6595b64144ccf1df"        language="*"        />    </dependentAssembly>  </dependency></asmv1:assembly>  
    ```  
  
2.  Dans le Bloc\-notes, cliquez sur **Fichier**, puis sur **Enregistrer sous**.  
  
3.  Dans la boîte de dialogue **Enregistrer sous**, dans la liste déroulante **Type**, sélectionnez **Tous les fichiers**.  
  
4.  Dans la zone **Nom de fichier**, nommez le fichier et ajoutez .manifest à la fin du nom de fichier.  Par exemple : themes.manifest.  
  
5.  Cliquez sur le bouton **Parcourir les dossiers**, puis sélectionnez n'importe quel dossier et cliquez sur **Enregistrer**.  
  
    > [!NOTE]
    >  Les autres procédures supposent que le nom de ce fichier est themes.manifest et que le fichier est enregistré au répertoire C:\\temp de votre ordinateur.  
  
##  <a name="BKMK_embedmanifest"></a> Incluez le fichier manifeste dans le fichier exécutable de la solution publiée  
  
1.  Ouvrez **Invite de commandes Visual Studio**.  
  
     Pour plus d'informations sur l'ouverture de **L'Invité de Commande Visual Studio**, consultez [Invites de commandes](../Topic/Developer%20Command%20Prompt%20for%20Visual%20Studio.md).  
  
    > [!NOTE]
    >  Les étapes suivantes font les hypothèses suivantes sur votre solution:  
    >   
    >  -   Le nom de la solution est MyWPFProject.  
    > -   La solution se trouve dans le répertoire suivant : `%UserProfile%\Documents\Visual Studio 2010\Projects\`.  
    >   
    >      La solution est publiée dans le répertoire suivant : `%UserProfile%\Documents\Visual Studio 2010\Projects\publish`.  
    > -   La dernière version des fichiers d'application publiés se trouve dans le répertoire suivant : `%UserProfile%\Documents\Visual Studio 2010\Projects\publish\Application Files\WPFApp_1_0_0_0`  
    >   
    >  Vous ne devez pas utiliser le nom ou les emplacements de répertoires décrits ci\-dessus.  Les nom et emplacements décrits ci\-dessus sont utilisés uniquement pour illustrer les étapes requises pour publier votre solution.  
  
2.  À l'invite de commandes, modifiez le chemin d'accès au répertoire qui contient la dernière version des fichiers d'application publiés.  L'exemple suivant illustre cette étape.  
  
    ```  
    cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"  
    ```  
  
3.  À l'invite de commandes, exécutez la commande suivante pour inclure le fichier manifeste dans le fichier exécutable de l'application.  
  
    ```  
    mt –manifest c:\temp\themes.manifest –outputresource:MyWPFApp.exe.deploy  
    ```  
  
##  <a name="BKMK_signappdeplyman"></a> Signe les manifestes d'application et de déploiement  
  
1.  À l'invite de commandes, exécutez la commande suivante pour supprimer l'extension de `.deploy` du fichier exécutable dans le répertoire actif.  
  
    ```  
    ren MyWPFApp.exe.deploy MyWPFApp.exe  
    ```  
  
    > [!NOTE]
    >  Cet exemple suppose qu'un seul fichier porte l'extension de fichier `.deploy`.  Vérifiez que vous renommez tous les fichiers dans ce répertoire qui ont l'extension de fichier `.deploy`.  
  
2.  À l'invite de commandes, exécutez la commande suivante pour signer le manifeste d'application.  
  
    ```  
    mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
    ```  
  
    > [!NOTE]
    >  Cet exemple suppose que vous signez le manifeste en utilisant le fichier `.pfx` du projet.  Si vous ne signez pas le manifeste, vous pouvez omettre le paramètre `–cf` utilisé dans cet exemple.  Si vous signez le manifeste avec un certificat qui requiert un mot de passe, spécifiez l'option `–password` \(`For example: mage –u MyWPFApp.exe.manifest –cf ..\..\..\MyWPFApp_TemporaryKey.pfx – password Password`\).  
  
3.  À l'invite de commandes, exécutez la commande suivante pour ajouter l'extension de `.deploy` le nom du fichier que vous avez renommé dans une étape précédente de cette procédure.  
  
    ```  
    ren MyWPFApp.exe MyWPFApp.exe.deploy  
    ```  
  
    > [!NOTE]
    >  Cet exemple suppose qu'un seul fichier porte l'extension de fichier `.deploy`.  Vérifiez que vous renommez tous les fichiers dans ce répertoire qui précédemment a déjà eu une extension de nom de fichier `.deploy`.  
  
4.  À l'invite de commandes, exécutez la commande suivante pour signer le manifeste de déploiement.  
  
    ```  
    mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
    ```  
  
    > [!NOTE]
    >  Cet exemple suppose que vous signez le manifeste en utilisant le fichier `.pfx` du projet.  Si vous ne signez pas le manifeste, vous pouvez omettre le paramètre `–cf` utilisé dans cet exemple.  Si vous signez le manifeste avec un certificat qui requiert un mot de passe, spécifiez l'option `–password` , comme dans l'exemple:`For example: mage –u MyWPFApp.exe.manifest –cf ..\..\..\MyWPFApp_TemporaryKey.pfx – password Password`.  
  
 Après avoir effectué ces étapes, déplacez les fichiers publiés à l'emplacement à partir duquel vous souhaitez que les utilisateurs finals installent l'application.  Si vous projetez de mettre souvent la solution à jour, entrez ces commandes dans un script et exécutez le script chaque fois que vous publiez une nouvelle version.  
  
## Voir aussi  
 [Troubleshooting Specific Errors in ClickOnce Deployments](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)   
 [Visual Styles Overview](http://msdn.microsoft.com/fr-fr/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e)   
 [Enabling Visual Styles](VS|Controls|~\controls\userex\cookbook.htm)   
 [Invites de commandes](../Topic/Developer%20Command%20Prompt%20for%20Visual%20Studio.md)