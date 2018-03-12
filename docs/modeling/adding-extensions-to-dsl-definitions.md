---
title: "Ajout d’Extensions à des définitions DSL | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 1727fbc2c3a46caacb1b57c0a0f7282956daad8b
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
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
