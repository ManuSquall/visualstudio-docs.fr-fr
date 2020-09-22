---
title: Extension de l’interpréteur de commandes isolé | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: 9a641d8f-211e-4486-a1b1-4a89fafe7ee8
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ea55039de769598b26868727a93cfa11726e4838
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839578"
---
# <a name="extending-the-isolated-shell"></a>Extension du Shell isolé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez étendre le shell isolé Visual Studio en ajoutant un VSPackage, une partie de composant Managed Extensibility Framework (MEF) ou un projet VSIX générique à votre application Shell isolée.  
  
> [!NOTE]
> Les étapes suivantes presupposent que vous avez créé une application Shell isolée de base à l’aide du modèle de projet isolé Visual Studio Shell. Pour plus d’informations sur ce modèle de projet, consultez [procédure pas à pas : création d’une application Shell isolée de base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Emplacements du modèle de projet de package Visual Studio  
 Le modèle de projet de package Visual Studio se trouve à trois emplacements différents dans la boîte de dialogue **Nouveau projet** :  
  
1. Sous **Visual Basic**, **extensibilité**. Le langage par défaut du projet est Visual Basic.  
  
2. Sous **Visual C#**, **extensibilité**. Le langage par défaut du projet est C#.  
  
3. Sous **autres types de projets**, **extensibilité**. Le langage par défaut du projet est C++.  
  
## <a name="adding-a-vspackage"></a>Ajout d’un VSPackage  
 Vous pouvez ajouter un VSPackage à votre application Shell isolée. Les étapes suivantes montrent comment en créer une qui ajoute des commandes de menu.  
  
#### <a name="to-add-a-new-vspackage"></a>Pour ajouter un nouveau VSPackage  
  
1. Ajoutez un projet de package Visual Studio nommé `MenuCommandsPackage` .  
  
2. Sur la page informations sur le **VSPackage de base** de l’Assistant, définissez nom de la **société** sur `Fabrikam` et **nom du VSPackage** sur `FabrikamMenuCommands` . Choisissez le bouton **Suivant**.  
  
3. Sur la page suivante, sélectionnez **commande de menu** , puis choisissez **suivant**.  
  
4. Sur la page suivante, définissez le nom de la **commande** sur `Fabrikam Command` et l’ID de **commande** sur `cmdidFabrikamCommand` , puis choisissez **suivant**.  
  
5. Dans la page **Sélectionner les options de projet de test** , désactivez les options de test, puis choisissez le bouton **Terminer** .  
  
6. Dans le projet ShellExtensionsVSIX, ouvrez le fichier source. extension. vsixmanifest.  
  
     La section **ressources** doit contenir une entrée pour le projet VSShellStub. AboutBoxPackage.  
  
7. Choisissez le bouton **nouveau** .  
  
8. Dans la fenêtre **Ajouter une nouvelle ressource** , dans la liste **type** , sélectionnez **Microsoft. VisualStudio. VSPackage**.  
  
9. Dans la liste **source** , assurez-vous qu' **un projet de la solution actuelle** est sélectionné. Dans la zone de liste **projet** , sélectionnez **MenuCommandsPackage**.  
  
10. Enregistrez et fermez le fichier.  
  
11. Régénérez la solution et démarrez le débogage de l’interpréteur de commandes isolé.  
  
12. Dans la barre de menus, choisissez menu **Outils** , puis **commande Fabrikam**.  
  
     Une boîte de message doit s’afficher.  
  
13. Arrêtez le débogage de l’application.  
  
## <a name="adding-a-mef-component-part"></a>Ajout d’une partie de composant MEF  
 Les étapes suivantes montrent comment ajouter une partie de composant MEF à votre application d’interpréteur de commandes isolé.  
  
#### <a name="to-add-a-mef-component"></a>Pour ajouter un composant MEF  
  
1. Dans la boîte de dialogue **Ajouter un nouveau projet** , sous **Visual C#**, **extensibilité**, utilisez le modèle de marge de l' **éditeur** pour ajouter un projet. Nommez-le `ShellEditorMargin`.  
  
2. Dans le projet ShellExtensionsVSIX, ouvrez le fichier source. extension. vsixmanifest dans le Mode Création, et non le mode Code.  
  
3. Dans la `Asset` section, choisissez **Ajouter du contenu**.  
  
4. Dans la fenêtre **Ajouter une nouvelle ressource** , dans la liste **type** , sélectionnez **Microsoft. VisualStudio. MEFComponent**.  
  
5. Dans la liste **source** , assurez-vous qu' **un projet de la solution actuelle** est sélectionné. Dans la zone de liste **projet** , sélectionnez **ShellEditorMargin**.  
  
6. Enregistrez et fermez le fichier.  
  
7. Régénérez la solution et démarrez le débogage de l’interpréteur de commandes isolé.  
  
8. Ouvrez un fichier texte.  
  
     Une marge verte qui contient les mots « Hello World ! » doit être affiché en bas de la fenêtre du fichier texte.  
  
9. Arrêtez le débogage de l’application.  
  
## <a name="adding-a-generic-vsix-project"></a>Ajout d’un projet VSIX générique  
  
#### <a name="to-add-a-generic-vsix-project"></a>Pour ajouter un projet VSIX générique  
  
1. Dans la boîte de dialogue **Ajouter un nouveau projet** , sous **Visual C#**, **extensibilité**, utilisez le modèle **VSIXProject** pour ajouter un projet. Nommez-le `EmptyVSIX`.  
  
2. Dans le projet ShellExtensionsVSIX, ouvrez le fichier source. extensions. vsixmanifest dans le Mode Création, et non le mode Code.  
  
3. Dans la `Assets` section, choisissez **nouveau**.  
  
4. Dans la fenêtre **Ajouter une nouvelle ressource** , dans la liste **type** , sélectionnez le type de contenu que vous souhaitez ajouter.  
  
5. Dans **source**, assurez-vous que l’option **un projet dans la solution actuelle** est sélectionnée. Dans la zone de liste, sélectionnez le nom de votre projet VSIX.  
  
6. Enregistrez et fermez le fichier.  
  
7. Si ce projet inclut du code compilé, vous devez modifier le projet afin que l’assembly soit inclus dans la sortie.  
  
    1. Déchargez le projet VSIX et ouvrez le fichier projet.  
  
    2. Dans le premier `<PropertyGroup>` bloc, remplacez la valeur de `<CopyBuildOutputToOutputDirectory>` par `true` .  
  
    3. Enregistrez et rechargez le projet.  
  
8. Créez et exécutez la solution.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Création d’une application Shell isolée de base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)
