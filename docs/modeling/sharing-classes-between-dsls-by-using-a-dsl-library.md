---
title: Partage de Classes entre plusieurs DSL à l’aide d’une bibliothèque DSL | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: f1164b0a96a10e7fa9cda3f8082bb052a0b445e5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>Partage de classes entre plusieurs DSL à l'aide d'une bibliothèque DSL
Dans la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Visualization and Modeling SDK, vous pouvez créer une définition DSL incomplète que vous pouvez importer dans un autre DSL. Cela vous permet de tenir compte des parties communes des modèles similaires.  
  
## <a name="creating-and-using-dsl-libraries"></a>Création et utilisation des bibliothèques de DSL  
  
#### <a name="to-create-a-dsl-library"></a>Pour créer une bibliothèque DSL  
  
1.  Créez un nouveau projet DSL, puis choisissez le modèle de solution de bibliothèque DSL.  
  
     Un seul projet DSL sera créé avec un modèle vide.  
  
2.  Vous pouvez ajouter des classes de domaine, des relations, des formes et ainsi de suite.  
  
     Les éléments dans la bibliothèque n’ont pas former une arborescence d’incorporation unique.  
  
     Pour définir une relation qui permettent des importateurs, créer deux classes de domaine et créer la relation entre eux.  
  
     Envisagez d’affecter le **modificateur d’héritage** des classes de domaine pour `Abstract`.  
  
3.  Vous pouvez ajouter des éléments que vous définissez dans l’Explorateur DSL, tels que des générateurs de connexion.  
  
4.  Vous pouvez ajouter des personnalisations qui requièrent un code supplémentaire, telles que les contraintes de validation.  
  
5.  Cliquez sur **transformer tous les modèles**.  
  
6.  Générez le projet.  
  
7.  Lorsque vous distribuez du DSL pour d’autres personnes à utiliser, vous devez fournir l’assembly compilé (DLL) et le fichier `DslDefinition.dsl`. Vous pouvez trouver l’assembly compilé dans un dossier sous `Dsl\bin\*`  
  
#### <a name="to-import-a-dsl-library"></a>Pour importer une bibliothèque DSL  
  
1.  Dans une autre définition DSL, dans **Explorateur DSL**, avec le bouton droit de la classe racine de la DSL, puis cliquez sur **ajouter une nouvelle importation DslLibrary**.  
  
2.  Dans la fenêtre Propriétés, définissez la **chemin d’accès du fichier** de la bibliothèque. Vous pouvez utiliser un chemin d’accès absolu ou relatif.  
  
     La bibliothèque importée apparaît dans l’Explorateur DSL, en mode lecture seule.  
  
3.  Vous pouvez utiliser les classes importées comme classes de base. Créer une classe de domaine dans l’importation DSL, et dans les propriétés de fenêtre, définissez **une classe de Base** à une classe importée.  
  
4.  Cliquez sur Transformer tous les modèles.  
  
5.  Ajouter une référence à l’assembly (DLL) qui a été généré par le projet de bibliothèque DSL au projet DSL.  
  
6.  Générez la solution.  
  
 Une bibliothèque DSL peut importer d’autres bibliothèques. Lorsque vous importez une bibliothèque, ses importations s’affichent automatiquement dans l’Explorateur de DSL.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
