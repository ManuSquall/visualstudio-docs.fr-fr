---
title: Partage de Classes entre plusieurs DSL à l’aide d’une bibliothèque DSL | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 509bd96b-3e66-47f4-8642-771421d0d0d5
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 2c0192aca40c6f58468fba35ee1fd174b0445bf1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49241515"
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>Partage de classes entre plusieurs DSL à l'aide d'une bibliothèque DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Visualization and Modeling SDK, vous pouvez créer une définition DSL incomplète que vous pouvez importer dans un autre DSL. Cela vous permet de tenir compte des parties communes des modèles similaires.  
  
## <a name="creating-and-using-dsl-libraries"></a>Création et utilisation des bibliothèques DSL  
  
#### <a name="to-create-a-dsl-library"></a>Pour créer une bibliothèque DSL  
  
1.  Créez un projet DSL, puis choisissez le modèle de solution de bibliothèque DSL.  
  
     Un seul projet DSL sera créé avec un modèle vide.  
  
2.  Vous pouvez ajouter des classes de domaine, relations, formes et ainsi de suite.  
  
     Les éléments dans la bibliothèque est inutile former une arborescence d’incorporation unique.  
  
     Pour définir une relation importateurs peuvent utiliser, créer deux classes de domaine et créer la relation entre eux.  
  
     Envisagez de définir le **modificateur d’héritage** des classes de domaine pour `Abstract`.  
  
3.  Vous pouvez ajouter des éléments que vous définissez dans l’Explorateur DSL, tels que les générateurs de connexions.  
  
4.  Vous pouvez ajouter des personnalisations qui nécessitent du code supplémentaire, telles que les contraintes de validation.  
  
5.  Cliquez sur **transformer tous les modèles**.  
  
6.  Générez le projet.  
  
7.  Lorsque vous distribuez le DSL pour d’autres personnes à utiliser, vous devez fournir l’assembly compilé (DLL) et le fichier `DslDefinition.dsl`. Vous pouvez trouver l’assembly compilé dans un dossier sous `Dsl\bin\*`  
  
#### <a name="to-import-a-dsl-library"></a>Pour importer une bibliothèque DSL  
  
1.  Dans une autre définition DSL, dans **Explorateur DSL**, avec le bouton droit de la classe racine de la solution DSL, puis cliquez sur **ajouter une nouvelle importation DslLibrary**.  
  
2.  Dans la fenêtre Propriétés, définissez la **chemin d’accès du fichier** de la bibliothèque. Vous pouvez utiliser soit un un chemin relatif ou absolu.  
  
     La bibliothèque importée s’affiche dans l’Explorateur DSL, en mode lecture seule.  
  
3.  Vous pouvez utiliser les classes importées comme classes de base. Créer une classe de domaine dans la solution DSL importation, et dans les propriétés de fenêtre, définissez **une classe de Base** à une classe importée.  
  
4.  Cliquez sur Transformer tous les modèles.  
  
5.  Pour le projet DSL, ajoutez une référence à l’assembly (DLL) qui a été généré par le projet de bibliothèque DSL.  
  
6.  Générez la solution.  
  
 Une bibliothèque DSL peut importer d’autres bibliothèques. Lorsque vous importez une bibliothèque, ses importations apparaissent également automatiquement dans l’Explorateur DSL.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md)



