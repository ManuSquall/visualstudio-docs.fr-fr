---
title: "Étendre des diagrammes de dépendance | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 076964379f0903945767110a3c19edb87d3c7092
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2018
---
# <a name="extend-dependency-diagrams"></a>Étendre des diagrammes de dépendance
Vous pouvez écrire du code pour créer et mettre à jour des diagrammes de dépendance et pour valider la structure de votre code de programme par rapport aux diagrammes de dépendance dans Visual Studio. Vous pouvez ajouter des commandes qui s’affichent dans le menu contextuel des diagrammes, personnaliser les mouvements de glisser-déplacer et accéder au modèle de couche à partir de modèles de texte. Vous pouvez empaqueter ces extensions dans une extension d’intégration Visual Studio (VSIX) et les distribuer à d’autres utilisateurs de Visual Studio.  
  
 Pour plus d’informations sur les diagrammes de dépendance, consultez :  
  
-   [Diagrammes de dépendance : référence](../modeling/layer-diagrams-reference.md)  
  
-   [Diagrammes de dépendance : recommandations](../modeling/layer-diagrams-guidelines.md)  
  
-   [Créer des diagrammes de dépendance à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md)  
  
-   [Validation du code avec des diagrammes de dépendance](../modeling/validate-code-with-layer-diagrams.md)  
  
##  <a name="prereqs"></a> Spécifications  
 Vous devez avoir installé les éléments suivants sur l’ordinateur où vous voulez développer vos extensions de couche :  
  
-   Visual Studio  
  
-   [SDK Visual Studio](../extensibility/visual-studio-sdk.md)  
  
-   Kit de développement logiciel de modélisation pour Visual Studio  


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

  
 Une version appropriée de Visual Studio doit être installée sur l’ordinateur où vous voulez exécuter vos extensions de couche. Pour plus d’informations, consultez [déployer une extension de modèle de couche](../modeling/deploy-a-layer-model-extension.md).  
  
 Pour connaître les versions de Visual Studio prend en charge les diagrammes de dépendance, consultez [prise en charge de la Version pour l’architecture et les outils de modélisation](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Ajout de commandes et de mouvements aux diagrammes de dépendance](../modeling/add-commands-and-gestures-to-layer-diagrams.md)  
  
 [Ajout d’une validation d’architecture personnalisée aux diagrammes de dépendance](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)  
  
 [Ajout de propriétés personnalisées à des diagrammes de dépendance](../modeling/add-custom-properties-to-layer-diagrams.md)  
  
 [Parcourir et mettre à jour les modèles de couche dans le code du programme](../modeling/navigate-and-update-layer-models-in-program-code.md)  
  
 [Déployer une extension de modèle de couche](../modeling/deploy-a-layer-model-extension.md)  
  
 [Dépannage des extensions pour des diagrammes de dépendance](../modeling/troubleshoot-extensions-for-layer-diagrams.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Diagrammes de dépendance : référence](../modeling/layer-diagrams-reference.md)   
 [Diagrammes de dépendance : instructions](../modeling/layer-diagrams-guidelines.md)   
 [Créer des diagrammes de dépendance à partir de votre code.](../modeling/create-layer-diagrams-from-your-code.md)   
 [Validation du code avec des diagrammes de dépendance](../modeling/validate-code-with-layer-diagrams.md)   
