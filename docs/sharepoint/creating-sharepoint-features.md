---
title: Création de fonctionnalités SharePoint | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
- features [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ec6f0ef523733a0737b6d762d2835073ed1f3c06
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766387"
---
# <a name="create-sharepoint-features"></a>Créer des fonctionnalités SharePoint
  Vous pouvez utiliser une fonctionnalité SharePoint pour regrouper des éléments de projet SharePoint connexes pour faciliter le déploiement. Vous pouvez créer des fonctionnalités, définir des étendues et marquer les autres fonctionnalités en tant que dépendances à l’aide du Concepteur de fonctionnalités SharePoint. Le concepteur génère également un manifeste, qui est un fichier XML qui décrit chaque fonctionnalité.  
  
## <a name="add-features-to-the-sharepoint-solution"></a>Ajouter des fonctionnalités à la solution SharePoint
 Vous pouvez ajouter une fonctionnalité à la solution SharePoint à l’aide de l’Explorateur de solutions ou l’Explorateur de package. Vous pouvez utiliser une des méthodes suivantes pour ajouter une fonctionnalité.  
  
-   Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour **fonctionnalités**, puis choisissez **ajouter une fonctionnalité**.  
  
-   Dans **Explorateur de package**, ouvrez le menu contextuel pour le package, puis choisissez **ajouter une fonctionnalité**.  
  
## <a name="using-the-feature-designer"></a>À l’aide du Concepteur de fonctionnalités
 Une solution SharePoint peut contenir une ou plusieurs fonctionnalités SharePoint, lesquelles sont regroupées sous le nœud de fonction dans l’Explorateur de solutions. Chaque fonctionnalité possède son propre **Concepteur de fonctionnalités** que vous pouvez utiliser pour personnaliser les propriétés de fonctionnalité. Pour plus d’informations, consultez [Comment : personnaliser une fonctionnalité SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md). Pour distinguer les unes des autres fonctionnalités, vous pouvez configurer les propriétés telles que le titre, la description, la version et la portée.  
  
### <a name="feature-designer-options"></a>Options du Concepteur de fonctionnalités
 Après avoir créé une fonctionnalité, vous pouvez utiliser le Concepteur de fonctionnalités pour la personnaliser.  
  
 Le tableau suivant décrit les propriétés qui sont affichent dans le Concepteur de fonctionnalités.  
  
|Propriété|Description|  
|--------------|-----------------|  
|Titre|Facultatif. Le titre par défaut de la fonctionnalité est défini sur *SolutionName* *FeatureName*.|  
|Description|Facultatif. La description de la fonctionnalité SharePoint.|  
|Portée|Obligatoire. Si une fonction est créée à l’aide de **l’Explorateur de solutions**, l’étendue est définie sur le Web par défaut.<br /><br /> -Batterie : Activer une fonctionnalité pour une batterie de serveurs.<br /><br /> -Site : Activer une fonctionnalité pour tous les sites web dans une collection de sites.<br /><br /> -Web : Activer une fonctionnalité pour un site web spécifique.<br /><br /> -WebApplication : Activer une fonctionnalité pour tous les sites web dans une application web.|  
|Éléments dans la Solution|Tous les éléments SharePoint peuvent être ajoutés à la fonctionnalité.|  
|Éléments dans la fonctionnalité|Les éléments de projet SharePoint qui ont été ajoutés à la fonctionnalité.|  
  
## <a name="add-and-remove-sharepoint-project-items"></a>Ajouter et supprimer des éléments de projet SharePoint
 Vous pouvez sélectionner les éléments de projet SharePoint que vous souhaitez ajouter une fonctionnalité SharePoint pour le déploiement. Utilisez le **Concepteur de fonctionnalités** pour ajouter et supprimer des éléments de fonctionnalités et afficher le manifeste de fonctionnalité. Pour plus d’informations, consultez [Comment : ajouter et supprimer des éléments dans des fonctionnalités SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md).  
  
## <a name="add-feature-dependencies"></a>Ajouter des dépendances de fonctionnalité
 Vous pouvez configurer le manifeste de fonctionnalité afin que le serveur SharePoint active certaines fonctionnalités avant que votre fonctionnalité est activée. Par exemple, si votre fonctionnalité SharePoint dépend d’autres fonctionnalités pour les fonctionnalités ou données, le serveur SharePoint permettre tout d’abord essayez d’activer une fonctionnalité qui dépend de votre fonctionnalité. Pour plus d’informations, consultez [Comment : ajouter et supprimer des dépendances de fonctionnalité](../sharepoint/how-to-add-and-remove-feature-dependencies.md).  
  
## <a name="see-also"></a>Voir aussi
 [Comment : personnaliser une fonctionnalité SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Comment : ajouter et supprimer des éléments dans des fonctionnalités SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
 [Guide pratique pour ajouter et supprimer des dépendances de fonctionnalités](../sharepoint/how-to-add-and-remove-feature-dependencies.md)  
  
  
