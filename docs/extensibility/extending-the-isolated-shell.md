---
title: "Extension de l’interpr&#233;teur de commandes isol&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Shell Visual Studio, en mode isolé"
ms.assetid: 9a641d8f-211e-4486-a1b1-4a89fafe7ee8
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Extension de l’interpr&#233;teur de commandes isol&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez étendre le shell Visual Studio isolé en ajoutant un VSPackage, un composant Managed Extensibility Framework \(MEF\) ou un projet VSIX générique pour votre application shell isolé.  
  
> [!NOTE]
>  La procédure suivante présuppose que vous avez créé une application de base de shell isolé en utilisant le modèle de projet Visual Studio Shell isolé. Pour plus d’informations sur ce modèle de projet, consultez [Procédure pas à pas : Création d'une Application de base de Shell isolé](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## Emplacements du modèle de projet de package Visual Studio  
 Le modèle de projet de package Visual Studio se trouve à trois emplacements différents dans la boîte de dialogue **Nouveau projet** :  
  
1.  Sous **Visual Basic**, **extensibilité**. Le langage par défaut du projet est Visual Basic.  
  
2.  Sous **Visual C\#**, **extensibilité**. Le langage par défaut du projet est C\#.  
  
3.  Sous **autres Types de projets**, **extensibilité**. Le langage par défaut du projet est C\+\+.  
  
## Ajout d’un VSPackage  
 Vous pouvez ajouter un VSPackage à votre application shell isolé. Les étapes suivantes montrent comment créer une qui ajoute des commandes de menu.  
  
#### Pour ajouter un nouveau package de VS  
  
1.  Ajoutez un projet de Package Visual Studio nommé `MenuCommandsPackage`.  
  
2.  Sur le **VSPackage des informations de base** page de l’Assistant, définissez **nom de la société** à `Fabrikam` et **Nom VSPackage** à `FabrikamMenuCommands`. Choisissez le bouton **Suivant**.  
  
3.  Sur la page suivante, sélectionnez **commande de Menu** puis **Suivant**.  
  
4.  Sur la page suivante, définissez **nom de la commande** à `Fabrikam Command` et **ID de commande** à `cmdidFabrikamCommand`, puis choisissez **Suivant**.  
  
5.  Sur le **Sélectionner les Options de projet de Test** page, désactivez les options de test, puis choisissez le **Terminer** bouton.  
  
6.  Dans le projet ShellExtensionsVSIX, ouvrez le fichier source.extension.vsixmanifest.  
  
     Le **actifs** section doit contenir une entrée pour le projet VSShellStub.AboutBoxPackage.  
  
7.  Choisissez le bouton **Nouveau**.  
  
8.  Dans le **Ajouter un nouveau composant** fenêtre, dans le **Type** liste, sélectionnez **Microsoft.VisualStudio.VsPackage**.  
  
9. Dans le **Source** liste, assurez\-vous que **un projet dans la solution actuelle** est sélectionnée. Dans le **projet** zone de liste, sélectionnez **MenuCommandsPackage**.  
  
10. Enregistrez et fermez le fichier.  
  
11. Régénérez la solution et commencer à déboguer le shell isolé.  
  
12. Dans la barre de menus, choisissez **outils** menu, puis **Fabrikam commande**.  
  
     Une boîte de message doit apparaître.  
  
13. Arrêter le débogage de l’application.  
  
## Ajout d’un composant MEF  
 Les étapes suivantes montrent comment ajouter un composant MEF à votre application de shell isolé.  
  
#### Pour ajouter un composant MEF  
  
1.  Dans le **Ajouter un nouveau projet** boîte de dialogue **Visual C\#**, **extensibilité**, utilisez le **marge de l’éditeur** modèle pour ajouter un projet. Nommez\-le `ShellEditorMargin`.  
  
2.  Dans le projet ShellExtensionsVSIX, ouvrez le fichier Source.extension.vsixmanifest dans la vue conception, pas le mode Code.  
  
3.  Dans la `Asset` choisissez **Ajouter du contenu**.  
  
4.  Dans le **Ajouter un nouveau composant** fenêtre, dans le **Type** liste, sélectionnez **Microsoft.VisualStudio.MefComponent**.  
  
5.  Dans le **Source** liste, assurez\-vous que **un projet dans la solution actuelle** est sélectionnée. Dans le **projet** zone de liste, sélectionnez **ShellEditorMargin**.  
  
6.  Enregistrez et fermez le fichier.  
  
7.  Régénérez la solution et commencer à déboguer le shell isolé.  
  
8.  Ouvrez un fichier texte.  
  
     Une marge verte contenant les mots « Hello world \! » doit être affiché en bas de la fenêtre de fichier texte.  
  
9. Arrêter le débogage de l’application.  
  
## Ajout d’un projet VSIX générique  
  
#### Pour ajouter un projet VSIX générique  
  
1.  Dans le **Ajouter un nouveau projet** boîte de dialogue **Visual C\#**, **extensibilité**, utilisez la **VSIXProject** modèle pour ajouter un projet. Nommez\-le `EmptyVSIX`.  
  
2.  Dans le projet ShellExtensionsVSIX, ouvrez le fichier Source.extensions.vsixmanifest en mode Design, pas le mode Code.  
  
3.  Dans la `Assets` choisissez **nouveau**.  
  
4.  Dans le **Ajouter un nouveau composant** fenêtre, dans le **Type** sélectionnez le type de contenu que vous souhaitez ajouter.  
  
5.  Dans **Source**, assurez\-vous que le **un projet dans la solution actuelle** option est sélectionnée. Dans la zone de liste, sélectionnez le nom de votre projet VSIX.  
  
6.  Enregistrez et fermez le fichier.  
  
7.  Si ce projet contient du code compilé, vous devez modifier le projet afin que l’assembly est inclus dans la sortie.  
  
    1.  Décharger le projet VSIX et ouvrez le fichier projet.  
  
    2.  Dans la première `<PropertyGroup>` bloquer, modifiez la valeur de `<CopyBuildOutputToOutputDirectory>` à `true`.  
  
    3.  Enregistrer et recharger le projet.  
  
8.  Générez et exécutez la solution.  
  
## Voir aussi  
 [Procédure pas à pas : Création d'une Application de base de Shell isolé](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)