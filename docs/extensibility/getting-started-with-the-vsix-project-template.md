---
title: "Mise en route avec le modèle de projet VSIX | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c87fd485a0d682dc21de21dfe32b83cfc29b520a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-with-the-vsix-project-template"></a>Mise en route avec le modèle de projet VSIX
Vous pouvez utiliser le modèle de projet VSIX pour créer une extension ou un package existant d’extension pour le déploiement. Le modèle de projet VSIX possède des versions de Visual Basic et Visual c# et est installé dans le cadre de Visual Studio SDK.  
  
 Le modèle de projet VSIX se compose uniquement d’un fichier source.extension.vsixmanifest, qui contient des informations sur l’extension et les ressources qu’il est fourni.  
  
 Pour rechercher le modèle de projet VSIX, vous devez installer le Kit de développement logiciel Visual Studio. Pour plus d’informations, consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="deploying-a-custom-project-template-using-the-vsix-project-template"></a>Déploiement d’un modèle de projet personnalisé à l’aide du modèle de projet VSIX  
 Les étapes suivantes montrent comment utiliser le projet VSIX pour empaqueter un modèle de projet que vous pouvez partager avec d’autres développeurs ou les télécharger dans la galerie Visual Studio.  
  
1.  Créer un modèle de projet.  
  
    1.  Ouvrez le projet à partir duquel créer un modèle. Ce projet peut être de n’importe quel type de projet.  
  
    2.  Dans le menu **Projet**, cliquez sur **Exporter le modèle**. Effectuez les étapes de l’Assistant.  
  
         Un fichier .zip est créé dans %USERPROFILE%\My Documents\Visual Studio  *\<version >*\My Exported Templates\\.  
  
2.  Créez un projet VSIX vide.  
  
     Dans le menu **Fichier** , cliquez sur **Nouveau** , puis sur **Projet**. Sélectionnez **Visual Basic** ou **Visual C#**. Sous le nœud sélectionné, sélectionnez **extensibilité**, puis sélectionnez **projet VSIX**.  
  
3.  Ajoutez le fichier .zip au projet. Définir son **copier dans le répertoire de sortie** propriété `Copy Always`.  
  
4.  Dans le **l’Explorateur de solutions**, double-cliquez sur le `source.extension.vsixmanifest` fichier pour l’ouvrir dans le **Concepteur de manifeste VSIX**, puis apportez les modifications suivantes :  
  
    -   Définir le **Product Name** au champ **mon modèle de projet**.  
  
    -   Définir le **ID de produit** au champ **MyProjectTemplate - 1**.  
  
    -   Définir le **auteur** au champ **Fabrikam**.  
  
    -   Définir le **Description** au champ **mon modèle de projet**.  
  
    -   Dans le **actifs** section, ajoutez un **Microsoft.VisualStudio.ProjectTemplate** de type et définissez son chemin d’accès au nom du fichier .zip.  
  
5.  Enregistrez et fermez le fichier source.extension.vsixmanifest.  
  
6.  Générez le projet.  
  
7.  Dans le répertoire de sortie, double-cliquez sur le fichier .vsix.  
  
8.  A **programme d’installation de VSIX** message s’affiche. Suivez les instructions pour installer l’extension.  
  
9. Fermez Visual Studio et puis rouvrez-le.  
  
10. Sélectionnez **Extensions et mises à jour** (sur le **outils** menu) et sélectionnez le **modèles** catégorie. Une des extensions disponibles doit être **mon modèle de projet**.  
  
11. Le nouveau modèle de projet s’affiche dans le **nouveau projet** boîte de dialogue de la même position que le modèle de projet d’origine. Par exemple, si vous avez créé un modèle nommé **VB Console** à partir d’une application console Visual Basic, **VB Console** s’affiche dans le même volet comme Visual Basic **Application de Console**modèle.  
  
#### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Pour spécifier l’emplacement du modèle dans la boîte de dialogue Nouveau projet  
  
1.  Les dossiers de modèles sont situés dans le *le chemin d’accès de Visual Studio Installation*\Common7\IDE\ProjectTemplates et *le chemin d’accès de Visual Studio Installation*\Common7\IDE\ItemTemplates répertoires. Les noms des sections de niveau supérieur dans la boîte de dialogue Nouveau projet ne correspondent pas exactement les noms des dossiers du modèle. Lorsqu’ils sont différents, utilisez le nom du dossier de modèle.  
  
     Remplacez l’extension de fichier .vsix par .zip, puis ouvrez le fichier.  
  
2.  Créer un nouveau dossier portant le même nom que la section de la boîte de dialogue Nouveau projet, dans que le modèle doit s’afficher.  
  
3.  Si le modèle apparaît dans une sous-section, créez un sous-dossier du même nom.  
  
4.  Déplacer le fichier .zip du modèle dans le nouveau dossier.  
  
5.  Remplacez l’extension .zip .vsix.  
  
6.  Ouvrez le manifeste VSIX.  
  
7.  Dans le manifeste VSIX, mettez à jour le **Asset** chemin d’accès du modèle afin qu’il pointe vers la racine de l’arborescence de répertoires qui contient le fichier de modèle. Par exemple, si le modèle est en \CSharp\Windows, la référence doit pointer vers \CSharp.