---
title: "Ajout d’Extensions à des définitions DSL | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: 6
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: f335db9f22392c4d0293a51111efff88c25c3145
ms.lasthandoff: 02/22/2017

---
# <a name="adding-extensions-to-dsl-definitions"></a>Ajout d'extensions à des définitions DSL
Extension de définition DSL vous permet de créer un package d’extensions à un langage spécifique à un domaine (DSL). L’extension DSL, qui est contenue dans une Extension d’intégration Visual Studio (VSIX), peut être installée sur l’ordinateur d’un utilisateur de la même manière que DSL. Les fonctionnalités supplémentaires peuvent être activées et désactivées au moment de l’exécution dynamique. DSL n’ont pas à être explicitement conçus pour l’extension et extensions peuvent être conçues par des tiers ou ultérieurement sans modifier l’étendue DSL.  
  
 Les fonctionnalités supplémentaires peuvent être les suivants :  
  
-   Propriétés des éléments de modèle et de présentation  
  
-   Décorateurs pour des formes et connecteurs  
  
-   Les classes, les relations, les formes et connecteurs  
  
-   Contraintes de validation  
  
-   Onglets et des éléments de boîte à outils  
  
 Un utilisateur d’un DSL étendu peut créer et enregistrer un modèle qui contient les instances des fonctionnalités supplémentaires, et elles peuvent être lues par d’autres utilisateurs qui ont installé l’extension appropriée. Les utilisateurs qui n’ont pas installé l’extension ne peut pas utiliser les fonctionnalités supplémentaires, mais ils peuvent mettre à jour et enregistrer un modèle sans perdre les fonctionnalités supplémentaires.  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Voir aussi  
 [Billets de blog connexes](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)

