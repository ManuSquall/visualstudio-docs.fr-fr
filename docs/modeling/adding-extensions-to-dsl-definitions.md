---
title: "Ajout d’Extensions à des définitions DSL | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: "6"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 77a631d7f245dfe6d324e2b392349b559447212f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="adding-extensions-to-dsl-definitions"></a>Ajout d'extensions à des définitions DSL
Extension de définition DSL vous permet de créer un package d’extensions à un langage spécifique à un domaine (DSL). L’extension DSL, qui est contenue dans une Extension d’intégration Visual Studio (VSIX), peut être installée sur l’ordinateur d’un utilisateur de la même manière que DSL. Les fonctionnalités supplémentaires peuvent être activées et désactivées au moment de l’exécution dynamique. DSL n’ont pas à être explicitement conçus pour l’extension, et extensions peuvent être conçues ultérieurement, ou par des tiers sans modifier l’étendue DSL.  
  
 Les fonctionnalités supplémentaires peuvent être les suivants :  
  
-   Propriétés des éléments de modèle et de présentation  
  
-   Décorateurs pour des formes et connecteurs  
  
-   Classes, des relations, des formes et connecteurs  
  
-   Contraintes de validation  
  
-   Onglets et des éléments de boîte à outils  
  
 Un utilisateur d’un langage DSL étendu peut créer et enregistrer un modèle qui contient les instances des fonctionnalités supplémentaires, et ils peuvent être lus par d’autres utilisateurs qui ont installé l’extension appropriée. Les utilisateurs qui n’ont pas installé l’extension ne peut pas utiliser les fonctionnalités supplémentaires, mais ils peuvent mettre à jour et enregistrez un modèle sans perdre les fonctionnalités supplémentaires.  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Voir aussi  
 [Billets de blog connexes](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)
