---
title: "Mise en route avec le mod&#232;le de projet VSIX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SDK de Visual Studio, modèle de projet VSIX"
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# Mise en route avec le mod&#232;le de projet VSIX
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez utiliser le modèle de projet VSIX pour créer une extension ou une extension existante pour le déploiement du package. Le modèle de projet VSIX a des versions de Visual Basic et Visual c\# et est installé dans le cadre du SDK Visual Studio.  
  
 Le modèle de projet VSIX consiste simplement en un fichier source.extension.vsixmanifest, qui contient des informations sur l'extension et les ressources qu'il est fourni.  
  
 Pour rechercher le modèle de projet VSIX, vous devez installer le Kit de développement Visual Studio. Pour plus d'informations, consultez [Kit de développement logiciel Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## Déploiement d'un modèle de projet personnalisé à l'aide du modèle de projet VSIX  
 Les étapes suivantes montrent comment utiliser le projet VSIX pour empaqueter un modèle de projet que vous pouvez partager avec d'autres développeurs ou télécharger vers la galerie Visual Studio.  
  
1.  Créer un modèle de projet.  
  
    1.  Ouvrez le projet à partir duquel créer un modèle. Ce projet peut être de n'importe quel type de projet.  
  
    2.  Dans le menu **Fichier**, cliquez sur **Exporter le modèle**. Effectuez les étapes de l'Assistant.  
  
         Un fichier .zip est créé dans %USERPROFILE%\\My Documents\\Visual Studio *\< version \>*\\My Exported Templates\\.  
  
2.  Créez un projet VSIX vide.  
  
     Dans le menu **Fichier**, cliquez sur **Nouveau**, puis sur **Projet**. Sélectionnez **Visual Basic** ou **Visual C\#**. Sous le nœud sélectionné, sélectionnez **extensibilité**, puis sélectionnez **projet VSIX**.  
  
3.  Ajoutez le fichier .zip dans le projet. Définir son **Copier dans le répertoire de sortie de** propriété `Copy Always`.  
  
4.  Dans le **l'Explorateur de solutions**, double\-cliquez sur le `source.extension.vsixmanifest` fichier pour l'ouvrir dans le **Concepteur de manifeste VSIX**, puis apportez les modifications suivantes :  
  
    -   Définir le **nom de produit** champ **Mon modèle de projet**.  
  
    -   Définir le **ID de produit** champ **MyProjectTemplate \- 1**.  
  
    -   Définir le **auteur** champ **Fabrikam**.  
  
    -   Définir le **Description** champ **Mon modèle de projet**.  
  
    -   Dans le **actifs** ajoutez un **Microsoft.VisualStudio.ProjectTemplate** de type et définissez son chemin d'accès au nom du fichier .zip.  
  
5.  Enregistrez et fermez le fichier source.extension.vsixmanifest.  
  
6.  Générez le projet.  
  
7.  Dans le répertoire de sortie, double\-cliquez sur le fichier .vsix.  
  
8.  Un **installateur VSIX** message s'affiche. Suivez les instructions pour installer l'extension.  
  
9. Fermez Visual Studio et puis rouvrez\-le.  
  
10. Sélectionnez **Extensions et mises à jour** \(sur le **outils** menu\) et sélectionnez le **modèles** catégorie. Une des extensions disponibles doit être **Mon modèle de projet**.  
  
11. Le nouveau modèle de projet s'affiche dans le **Nouveau projet** boîte de dialogue dans le même emplacement que le modèle de projet d'origine. Par exemple, si vous avez créé un modèle nommé **VB Console** à partir d'une application console Visual Basic, **VB Console** s'affiche dans le même volet comme Visual Basic **Application Console** modèle.  
  
#### Pour spécifier l'emplacement du modèle dans la boîte de dialogue Nouveau projet  
  
1.  Dossiers de modèles se trouvent dans le *Visual Studio Installation Path*\\Common7\\IDE\\ProjectTemplates et *Visual Studio Installation Path*\\Common7\\IDE\\ItemTemplates répertoires. Les noms des sections de niveau supérieur dans la boîte de dialogue Nouveau projet ne correspondent pas exactement les noms des dossiers du modèle. Lorsqu'ils sont différents, utilisez le nom du dossier du modèle.  
  
     Remplacez l'extension de fichier .vsix par .zip, puis ouvrez le fichier.  
  
2.  Créez un dossier portant le même nom que la section de la boîte de dialogue Nouveau projet, dans que le modèle doit s'afficher.  
  
3.  Si le modèle apparaît dans une sous\-section, créez un sous\-dossier du même nom.  
  
4.  Déplacez le fichier .zip du modèle dans le nouveau dossier.  
  
5.  Modifier l'extension .zip au fichier .vsix.  
  
6.  Ouvrez le manifeste VSIX.  
  
7.  Dans le manifeste VSIX, mettez à jour le **Asset** chemin d'accès du modèle afin qu'il pointe vers la racine de l'arborescence du répertoire qui contient le fichier de modèle. Par exemple, si le modèle est \\CSharp\\Windows, la référence doit pointer vers \\CSharp.