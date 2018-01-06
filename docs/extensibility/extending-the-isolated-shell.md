---
redirect_url: shell/extending-the-isolated-shell
title: "Étendre le Shell isolé | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode
ms.assetid: 9a641d8f-211e-4486-a1b1-4a89fafe7ee8
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fffa21e0351b6516920700d8dde0ba8b43243a9a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="extending-the-isolated-shell"></a>Étendre le Shell isolé
Vous pouvez étendre le shell isolé Visual Studio en ajoutant un VSPackage, un composant de Managed Extensibility Framework (MEF) ou un projet VSIX générique à votre application de shell isolé.  
  
> [!NOTE]
>  Les étapes suivantes présuppose que vous avez créé une application de shell isolé base à l’aide du modèle de projet Visual Studio Shell isolé. Pour plus d’informations sur ce modèle de projet, consultez [procédure pas à pas : création d’une Application de Shell isolé base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Emplacements du modèle de projet de package Visual Studio  
 Le modèle de projet de package Visual Studio se trouve à trois emplacements différents dans la boîte de dialogue **Nouveau projet** :  
  
1.  Sous **Visual Basic**, **extensibilité**. Le langage par défaut du projet est Visual Basic.  
  
2.  Sous **Visual C#**, **extensibilité**. Le langage par défaut du projet est C#.  
  
3.  Sous **autres Types de projet**, **extensibilité**. Le langage par défaut du projet est C++.  
  
## <a name="adding-a-vspackage"></a>Ajout d’un VSPackage  
 Vous pouvez ajouter un VSPackage à votre application de shell isolé. Les étapes suivantes montrent comment créer un objet qui ajoute les commandes de menu.  
  
#### <a name="to-add-a-new-vspackage"></a>Pour ajouter un nouveau VSPackage  
  
1.  Ajoutez un projet de Package Visual Studio nommé `MenuCommandsPackage`.  
  
2.  Sur le **des informations de base VSPackage** page de l’Assistant, définir **nom de la société** à `Fabrikam` et **Nom VSPackage** à `FabrikamMenuCommands`. Choisissez le bouton **Suivant**.  
  
3.  Sur la page suivante, sélectionnez **commande de Menu** , puis **suivant**.  
  
4.  Sur la page suivante, définissez **nom de la commande** à `Fabrikam Command` et **ID de commande** à `cmdidFabrikamCommand`, puis choisissez **suivant**.  
  
5.  Sur le **sélectionner les Options de projet de Test** page, désactivez les options de test, puis choisissez le **Terminer** bouton.  
  
6.  Dans le projet ShellExtensionsVSIX, ouvrez le fichier source.extension.vsixmanifest.  
  
     Le **actifs** section doit contenir une entrée pour le projet VSShellStub.AboutBoxPackage.  
  
7.  Choisissez le **nouveau** bouton.  
  
8.  Dans le **ajouter un nouveau composant** fenêtre, dans le **Type** liste, sélectionnez **Microsoft.VisualStudio.VsPackage**.  
  
9. Dans le **Source** liste, assurez-vous que **un projet dans la solution actuelle** est sélectionnée. Dans le **projet** zone de liste, sélectionnez **MenuCommandsPackage**.  
  
10. Enregistrez et fermez le fichier.  
  
11. Régénérez la solution et démarrer le débogage du shell isolé.  
  
12. Dans la barre de menus, choisissez **outils** menu, puis **Fabrikam commande**.  
  
     Une boîte de message doit apparaître.  
  
13. Arrêter le débogage de l’application.  
  
## <a name="adding-a-mef-component-part"></a>Ajout d’une partie du composant MEF  
 Les étapes suivantes montrent comment ajouter un composant MEF à votre application de shell isolé.  
  
#### <a name="to-add-a-mef-component"></a>Pour ajouter un composant MEF  
  
1.  Dans le **ajouter un nouveau projet** boîte de dialogue **Visual C#**, **extensibilité**, utilisez le **marge de l’éditeur** modèle pour ajouter un projet. Nommez-le `ShellEditorMargin`.  
  
2.  Dans le projet ShellExtensionsVSIX, ouvrez le fichier Source.extension.vsixmanifest dans la vue conception, pas le mode Code.  
  
3.  Dans le `Asset` , choisissez **ajouter du contenu**.  
  
4.  Dans le **ajouter un nouveau composant** fenêtre, dans le **Type** liste, sélectionnez **Microsoft.VisualStudio.MefComponent**.  
  
5.  Dans le **Source** liste, assurez-vous que **un projet dans la solution actuelle** est sélectionnée. Dans le **projet** zone de liste, sélectionnez **ShellEditorMargin**.  
  
6.  Enregistrez et fermez le fichier.  
  
7.  Régénérez la solution et démarrer le débogage du shell isolé.  
  
8.  Ouvrez un fichier texte.  
  
     Une marge verte qui contient les mots « Hello world ! » doit être affiché en bas de la fenêtre de fichier texte.  
  
9. Arrêter le débogage de l’application.  
  
## <a name="adding-a-generic-vsix-project"></a>Ajout d’un projet VSIX générique  
  
#### <a name="to-add-a-generic-vsix-project"></a>Pour ajouter un projet VSIX générique  
  
1.  Dans le **ajouter un nouveau projet** boîte de dialogue **Visual C#**, **extensibilité**, utilisez le **VSIXProject** modèle pour ajouter un projet. Nommez-le `EmptyVSIX`.  
  
2.  Dans le projet ShellExtensionsVSIX, ouvrez le fichier Source.extensions.vsixmanifest en mode Design, pas le mode Code.  
  
3.  Dans le `Assets` , choisissez **nouveau**.  
  
4.  Dans le **ajouter un nouveau composant** fenêtre, dans le **Type** , sélectionnez le type de contenu que vous souhaitez ajouter.  
  
5.  Dans **Source**, assurez-vous que le **un projet dans la solution actuelle** option est sélectionnée. Dans la zone de liste, sélectionnez le nom de votre projet VSIX.  
  
6.  Enregistrez et fermez le fichier.  
  
7.  Si ce projet contient du code compilé, vous devez modifier le projet afin que l’assembly est inclus dans la sortie.  
  
    1.  Décharger le projet VSIX et ouvrez le fichier projet.  
  
    2.  Dans la première `<PropertyGroup>` bloquer, modifiez la valeur de `<CopyBuildOutputToOutputDirectory>` à `true`.  
  
    3.  Enregistrer et recharger le projet.  
  
8.  Générez et exécutez la solution.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Création d’une application Shell isolée de base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)