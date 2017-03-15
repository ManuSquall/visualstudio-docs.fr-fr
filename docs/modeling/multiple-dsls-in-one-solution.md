---
title: "Utilisation de plusieurs langages sp&#233;cifiques &#224; un domaine dans une solution | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7e668620-6217-4e87-aea7-e9036776c8e4
caps.latest.revision: 3
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 3
---
# Utilisation de plusieurs langages sp&#233;cifiques &#224; un domaine dans une solution
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez empaqueter plusieurs DSL comme partie intégrante d'une seule solution de telle sorte qu'ils soient installés ensemble.  
  
 Il existe différentes techniques pour intégrer plusieurs DSL.  Pour plus d'informations, consultez [Intégration de modèles à l’aide de Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md), [Comment : ajouter un gestionnaire glisser\-déplacer](../modeling/how-to-add-a-drag-and-drop-handler.md) et [Personnalisation du comportement de la commande copier](../modeling/customizing-copy-behavior.md).  
  
### Pour créer plusieurs DSL dans la même solution  
  
1.  Créez au moins deux solutions DSL, ainsi qu'un projet VSIX, et ajoutez tous les projets à une solution unique.  
  
    -   Pour créer un projet VSIX : dans la boîte de dialogue **Nouveau projet**, sélectionnez **Visual C\#**, **Extensibilité**, **Projet VSIX**.  
  
    -   Créez au moins deux solutions DSL dans le répertoire de solutions VSIX.  
  
         Pour chaque DSL, ouvrez une nouvelle instance de Visual Studio.  Créez le DSL et spécifiez le même dossier de solution que la solution VSIX.  
  
         Assurez\-vous que vous créez chaque DSL avec une extension de nom de fichier différente.  
  
    -   Modifiez les noms des projets **Dsl** et **DslPackage** afin qu'ils soient tous différents.  Par exemple : `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.  
  
    -   Dans chaque **DslPackage\*\\source.extension.tt**, modifiez la ligne suivante pour corriger le nom du projet Dsl :  
  
         `string dslProjectName = "Dsl2";`  
  
    -   Dans la solution VSIX, ajoutez les projets Dsl\* et DslPackage\*.  
  
         Il se peut que vous souhaitiez placer chaque paire dans son propre dossier de solution.  
  
2.  Regroupez les manifestes VSIX des DSL :  
  
    1.  Ouvrez *YourVsixProject***\\source.extension.manifest**.  
  
    2.  Pour chaque DSL, choisissez **Ajouter du contenu** et ajoutez :  
  
        -   projet `Dsl*` comme **Composant MEF**  
  
        -   projet `DslPackage*` comme **Composant MEF**  
  
        -   projet `DslPackage*` comme **Package VS**  
  
3.  Générez la solution.  
  
 Le VSIX résultant installera les deux DSL.  Vous pouvez les tester en utilisant F5 ou déployer *YourVsixProject***\\bin\\Debug\\\*.vsix**.  
  
## Voir aussi  
 [Intégration de modèles à l’aide de Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Comment : ajouter un gestionnaire glisser\-déplacer](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Personnalisation du comportement de la commande copier](../modeling/customizing-copy-behavior.md)