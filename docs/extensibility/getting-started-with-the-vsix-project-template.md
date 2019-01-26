---
title: Mise en route avec le modèle de projet VSIX | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e0862ee1ca9c9c8fc21771469bf1baddfc2e8d3d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54942566"
---
# <a name="get-started-with-the-vsix-project-template"></a>Bien démarrer avec le modèle de projet VSIX
Vous pouvez utiliser le modèle de projet VSIX pour créer une extension ou un package existant d’extension pour le déploiement. Le modèle de projet VSIX a des versions de Visual Basic et Visual c# et est installé dans le cadre du SDK Visual Studio.  

 Le modèle de projet VSIX consiste en un *source.extension.vsixmanifest* fichier qui contient des informations sur l’extension et les ressources qu’il est fourni.  

 Pour rechercher le modèle de projet VSIX, vous devez installer le SDK Visual Studio. Pour plus d’informations, consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  

## <a name="deploy-a-custom-project-template-using-the-vsix-project-template"></a>Déployer un modèle de projet personnalisé à l’aide du modèle de projet VSIX  
 Les étapes suivantes montrent comment utiliser le projet VSIX pour empaqueter un modèle de projet que vous pouvez partager avec d’autres développeurs ou les charger dans la galerie Visual Studio.  

1.  Créer un modèle de projet.  

    1.  Ouvrez le projet à partir duquel créer un modèle. Ce projet peut être de n’importe quel type de projet.  

    2.  Dans le menu **Projet**, cliquez sur **Exporter le modèle**. Effectuez les étapes de l’Assistant.  

         Un *.zip* fichier est créé dans *%USERPROFILE%\My Documents\Visual Studio \<version > \My Exported Templates\\*.  

2.  Créez un projet VSIX vide.  

     Dans le menu **Fichier** , cliquez sur **Nouveau** , puis sur **Projet**. Sélectionnez **Visual Basic** ou **Visual C#**. Sous le nœud sélectionné, sélectionnez **extensibilité**, puis sélectionnez **projet VSIX**.  

3.  Ajouter le *.zip* fichier au projet. Définissez ses **Copy to Output Directory** propriété `Copy Always`.  

4.  Dans le **l’Explorateur de solutions**, double-cliquez sur le *source.extension.vsixmanifest* fichier pour l’ouvrir dans le **Concepteur de manifeste VSIX**, puis apportez les modifications suivantes :  

    -   Définir le **Product Name** champ **mon modèle de projet**.  

    -   Définir le **Id_produit** champ **MyProjectTemplate - 1**.  

    -   Définir le **auteur** champ **Fabrikam**.  

    -   Définir le **Description** champ **mon modèle de projet**.  

    -   Dans le **actifs** , ajoutez un **Microsoft.VisualStudio.ProjectTemplate** de type et définissez son chemin d’accès au nom de la *.zip* fichier.  

5.  Enregistrez et fermez le *source.extension.vsixmanifest* fichier.  

6.  Générez le projet.  

7.  Dans le répertoire de sortie, double-cliquez sur le *.vsix* fichier.  

8.  Un **programme d’installation VSIX** message s’affiche. Suivez les instructions pour installer l’extension.  

9. Fermez Visual Studio, puis le rouvrez.  

10. Sélectionnez **Extensions et mises à jour** (sur le **outils** menu) et sélectionnez le **modèles** catégorie. L’une des extensions disponibles doit être **mon modèle de projet**.  

11. Le nouveau modèle de projet apparaît dans le **nouveau projet** boîte de dialogue dans la même place que le modèle de projet d’origine. Par exemple, si vous avez créé un modèle nommé **VB Console** à partir d’une application de console Visual Basic, **VB Console** s’affiche dans le même volet comme Visual Basic **Application Console**modèle.  

### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Pour spécifier l’emplacement du modèle dans la boîte de dialogue Nouveau projet  

1. Dossiers de modèles se trouvent dans le *{Visual Studio Installation Path} \Common7\IDE\ProjectTemplates* et <em>{Visual Studio Installation Path} \Common7\IDE\ItemTemplates} répertoires. Les noms de haut niveau des sections de la **nouveau projet</em>*  boîte de dialogue ne correspondent pas exactement les noms des dossiers du modèle. Où ces éléments diffèrent, utilisez le nom du dossier de modèle.  

    Modifier le *.vsix* extension de fichier à *.zip*, puis ouvrez le fichier.  

2. Créez un dossier portant le même nom que la section de la **nouveau projet** le modèle doit apparaître dans un boîte de dialogue.  

3. Si le modèle apparaît dans une sous-section, créez un sous-dossier du même nom.  

4. Déplacer le modèle *.zip* fichier dans le nouveau dossier.  

5. Modifier le *.zip* extension *.vsix*.  

6. Ouvrez le manifeste VSIX.  

7. Dans le manifeste VSIX, mettez à jour le **Asset** chemin d’accès du modèle afin qu’il pointe vers la racine de l’arborescence de répertoires qui contient le fichier de modèle. Par exemple, si le modèle est en cours *\CSharp\Windows*, la référence doit pointer vers *\CSharp*.
