---
title: "Création de fonctionnalités SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
- features [SharePoint development in Visual Studio]
ms.assetid: 2e211fb3-94f4-4921-ba77-2ba6717a3e41
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: a6917a8909bed30319d104f45398409b4ba367f6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-sharepoint-features"></a>Création de fonctionnalités SharePoint
  Vous pouvez utiliser une fonctionnalité SharePoint pour regrouper des éléments de projet SharePoint connexes pour faciliter le déploiement. Vous pouvez créer des fonctionnalités, définir des étendues et marquer les autres fonctionnalités en tant que dépendances à l’aide du Concepteur de fonctionnalités SharePoint. Le concepteur génère également un manifeste, qui est un fichier XML qui décrit chaque fonctionnalité.  
  
## <a name="adding-features-to-the-sharepoint-solution"></a>Ajout de fonctionnalités à la Solution SharePoint  
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
|Titre|Facultatif. Le titre par défaut de la fonctionnalité est défini sur *SolutionName**FeatureName*.|  
|Description|Facultatif. La description de la fonctionnalité SharePoint.|  
|Portée|Obligatoire. Si une fonction est créée à l’aide de **l’Explorateur de solutions**, l’étendue est définie sur le Web par défaut.<br /><br /> -Batterie : Activer une fonctionnalité pour une batterie de serveurs.<br /><br /> -Site : Activer une fonctionnalité pour tous les sites web dans une collection de sites.<br /><br /> -Web : Activer une fonctionnalité pour un site web spécifique.<br /><br /> -WebApplication : Activer une fonctionnalité pour tous les sites web dans une application web.|  
|Éléments dans la Solution|Tous les éléments SharePoint peuvent être ajoutés à la fonctionnalité.|  
|Éléments dans la fonctionnalité|Les éléments de projet SharePoint qui ont été ajoutés à la fonctionnalité.|  
  
## <a name="adding-and-removing-sharepoint-project-items"></a>Ajout et suppression d’éléments de projet SharePoint  
 Vous pouvez sélectionner les éléments de projet SharePoint que vous souhaitez ajouter une fonctionnalité SharePoint pour le déploiement. Utilisez le **Concepteur de fonctionnalités** pour ajouter et supprimer des éléments de fonctionnalités et afficher le manifeste de fonctionnalité. Pour plus d’informations, consultez [Comment : ajouter et supprimer des éléments dans des fonctionnalités SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md).  
  
## <a name="adding-feature-dependencies"></a>Ajout de dépendances de fonctionnalité  
 Vous pouvez configurer le manifeste de fonctionnalité afin que le serveur SharePoint active certaines fonctionnalités avant que votre fonctionnalité est activée. Par exemple, si votre fonctionnalité SharePoint dépend d’autres fonctionnalités pour les fonctionnalités ou données, le serveur SharePoint permettre tout d’abord essayez d’activer une fonctionnalité qui dépend de votre fonctionnalité. Pour plus d’informations, consultez [Comment : ajouter et supprimer des dépendances de fonctionnalité](../sharepoint/how-to-add-and-remove-feature-dependencies.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : personnaliser une fonctionnalité SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Comment : ajouter et supprimer des éléments dans des fonctionnalités SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
 [Guide pratique pour ajouter et supprimer des dépendances de fonctionnalités](../sharepoint/how-to-add-and-remove-feature-dependencies.md)  
  
  