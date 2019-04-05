---
title: Plusieurs DSL dans une Solution | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 7e668620-6217-4e87-aea7-e9036776c8e4
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 76f34194381df92097e8dc2c42f1bf57a83f484b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58947667"
---
# <a name="multiple-dsls-in-one-solution"></a>Utilisation de plusieurs langages spécifiques à un domaine dans une solution
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez empaqueter plusieurs DSL comme partie intégrante d'une seule solution de telle sorte qu'ils soient installés ensemble.  
  
 Il existe différentes techniques pour intégrer plusieurs DSL. Pour plus d’informations, consultez [l’intégration de modèles à l’aide de Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) et [Comment : Ajouter un gestionnaire glisser-déplacer](../modeling/how-to-add-a-drag-and-drop-handler.md) et [personnalisation du comportement de copie](../modeling/customizing-copy-behavior.md).  
  
### <a name="to-build-more-than-one-dsl-in-the-same-solution"></a>Pour créer plusieurs DSL dans la même solution  
  
1. Créez au moins deux solutions DSL, ainsi qu'un projet VSIX, et ajoutez tous les projets à une solution unique.  
  
   -   Pour créer un projet VSIX : Dans le **nouveau projet** boîte de dialogue, sélectionnez **Visual C#** , **extensibilité**, **projet VSIX**.  
  
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
 [Guide pratique pour Ajouter un gestionnaire glisser-déplacer](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Personnalisation du comportement de la copie](../modeling/customizing-copy-behavior.md)
