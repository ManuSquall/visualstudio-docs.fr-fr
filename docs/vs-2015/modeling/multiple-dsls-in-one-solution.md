---
title: Plusieurs DSL dans une Solution | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7e668620-6217-4e87-aea7-e9036776c8e4
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 8bf5e3d69b67cf51c1e70ec8ffe9e91d87a1dcbe
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49820172"
---
# <a name="multiple-dsls-in-one-solution"></a>Utilisation de plusieurs langages spécifiques à un domaine dans une solution
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez empaqueter plusieurs DSL comme partie intégrante d'une seule solution de telle sorte qu'ils soient installés ensemble.  
  
 Il existe différentes techniques pour intégrer plusieurs DSL. Pour plus d’informations, consultez [l’intégration de modèles à l’aide de Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) et [Comment : ajouter un gestionnaire glisser-déplacer](../modeling/how-to-add-a-drag-and-drop-handler.md) et [personnalisation du comportement de copie](../modeling/customizing-copy-behavior.md).  
  
### <a name="to-build-more-than-one-dsl-in-the-same-solution"></a>Pour créer plusieurs DSL dans la même solution  
  
1. Créez au moins deux solutions DSL, ainsi qu'un projet VSIX, et ajoutez tous les projets à une solution unique.  
  
   -   Pour créer un projet VSIX : dans le **nouveau projet** boîte de dialogue, sélectionnez **Visual C#**, **extensibilité**, **projet VSIX**.  
  
   -   Créez au moins deux solutions DSL dans le répertoire de solutions VSIX.  
  
        Pour chaque DSL, ouvrez une nouvelle instance de Visual Studio. Créez le DSL et spécifiez le même dossier de solution que la solution VSIX.  
  
        Assurez-vous que vous créez chaque DSL avec une extension de nom de fichier différente.  
  
   -   Modifier les noms de la **Dsl** et **DslPackage** projets afin qu’ils soient tous différents. Par exemple : `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.  
  
   -   Dans chaque **DslPackage\*\source.extension.tt**, mettre à jour de cette ligne vers le nom du projet Dsl correct :  
  
        `string dslProjectName = "Dsl2";`  
  
   -   Dans la solution VSIX, ajoutez les Dsl * et DslPackage\* projets.  
  
        Il se peut que vous souhaitiez placer chaque paire dans son propre dossier de solution.  
  
2. Regroupez les manifestes VSIX des DSL :  
  
   1.  Ouvrez _YourVsixProject_**\source.extension.manifest**.  
  
   2.  Pour chaque DSL, choisissez **ajouter du contenu** et ajoutez :  
  
       -   `Dsl*` projet comme un **composant MEF**  
  
       -   `DslPackage*` projet comme un **composant MEF**  
  
       -   `DslPackage*` projet comme un **Package VS**  
  
3. Générez la solution.  
  
   Le VSIX résultant installera les deux DSL. Vous pouvez les tester en utilisant F5 ou déployer _YourVsixProject_**\bin\Debug\\\*.vsix**.  
  
## <a name="see-also"></a>Voir aussi  
 [Intégration de modèles à l’aide de Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Comment : ajouter un gestionnaire glisser-déplacer](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Personnalisation du comportement de la copie](../modeling/customizing-copy-behavior.md)



