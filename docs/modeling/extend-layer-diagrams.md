---
title: "Étendre des diagrammes de dépendance | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
ms.assetid: 83fca301-b008-485a-87eb-218050e71451
caps.latest.revision: 39
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: ad673b1bc7d3089c37717dd7e1f1fce4e86d8100
ms.lasthandoff: 02/22/2017

---
# <a name="extend-dependency-diagrams"></a>Étendre des diagrammes de dépendance
Vous pouvez écrire du code pour créer et mettre à jour des diagrammes de dépendance et pour valider la structure de votre code de programme par rapport aux diagrammes de dépendance dans Visual Studio. Vous pouvez ajouter des commandes qui s’affichent dans le menu contextuel des diagrammes, personnaliser les mouvements de glisser-déplacer et accéder au modèle de couche à partir de modèles de texte. Vous pouvez empaqueter ces extensions dans une extension d’intégration Visual Studio (VSIX) et les distribuer à d’autres utilisateurs de Visual Studio.  
  
 Pour plus d’informations sur les diagrammes de dépendance, consultez :  
  
-   [Diagrammes de dépendance : référence](../modeling/layer-diagrams-reference.md)  
  
-   [Diagrammes de dépendance : instructions](../modeling/layer-diagrams-guidelines.md)  
  
-   [Créer des diagrammes de dépendance à partir de votre code.](../modeling/create-layer-diagrams-from-your-code.md)  
  
-   [Valider le code avec des diagrammes de dépendance](../modeling/validate-code-with-layer-diagrams.md)  
  
##  <a name="a-nameprereqsa-requirements"></a><a name="prereqs"></a> Configuration requise  
 Vous devez avoir installé les éléments suivants sur l’ordinateur où vous voulez développer vos extensions de couche :  
  
-   Visual Studio  
  
-   [SDK Visual Studio](../extensibility/visual-studio-sdk.md)  
  
-   Modélisation du Kit de développement logiciel pour Visual Studio  


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

  
 Une version appropriée de Visual Studio doit être installée sur l’ordinateur où vous voulez exécuter vos extensions de couche. Pour plus d’informations, consultez [déployer une extension de modèle de couche](../modeling/deploy-a-layer-model-extension.md).  
  
 Pour connaître les versions de Visual Studio prend en charge les diagrammes de dépendance, consultez [prise en charge de Version pour l’architecture et les outils de modélisation](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Ajouter des commandes et mouvements aux diagrammes de dépendance](../modeling/add-commands-and-gestures-to-layer-diagrams.md)  
  
 [Ajouter une validation d’architecture personnalisée aux diagrammes de dépendance](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)  
  
 [Ajouter des propriétés personnalisées aux diagrammes de dépendance](../modeling/add-custom-properties-to-layer-diagrams.md)  
  
 [Parcourir et mettre à jour les modèles de couche dans le code du programme](../modeling/navigate-and-update-layer-models-in-program-code.md)  
  
 [Déployer une extension de modèle de couche](../modeling/deploy-a-layer-model-extension.md)  
  
 [Dépanner les extensions pour les diagrammes de dépendance](../modeling/troubleshoot-extensions-for-layer-diagrams.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Définir et installer une extension de modélisation](../modeling/define-and-install-a-modeling-extension.md)   
 [Diagrammes de dépendance : référence](../modeling/layer-diagrams-reference.md)   
 [Diagrammes de dépendance : instructions](../modeling/layer-diagrams-guidelines.md)   
 [Créer des diagrammes de dépendance à partir de votre code.](../modeling/create-layer-diagrams-from-your-code.md)   
 [Valider le code avec des diagrammes de dépendance](../modeling/validate-code-with-layer-diagrams.md)   

