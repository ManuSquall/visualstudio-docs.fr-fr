---
title: "FeatureProperty (élément) | Documents Microsoft"
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
helpviewer_keywords: FeatureProperty element
ms.assetid: 36a771a6-98d0-4a40-a278-d76baea82452
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 97575a32aa3498787a5b81f1ade49c74e290854e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="featureproperty-element"></a>FeatureProperty, élément
  Représente une propriété personnalisée qui est incluse avec une fonctionnalité lorsqu’elle est déployée vers SharePoint. Après le déployée d’une fonctionnalité, vous pouvez accéder à la propriété dans votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<FeatureProperty Key = "Key of the property value"  
    Value = "Property value" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|**Key**|Requis **xs : String** attribut.<br /><br /> La clé est utilisée pour stocker et récupérer la valeur de propriété. Chaque propriété doit avoir une clé qui est unique au sein de la fonctionnalité.|  
|**Valeur**|Requis **xs : String** attribut.<br /><br /> Valeur de la propriété.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Représente une collection de valeurs de propriété qui sont inclus avec une fonctionnalité lorsqu’elle est déployée vers SharePoint.|  
  
## <a name="remarks"></a>Remarques  
 Pour plus d’informations sur les propriétés de fonctionnalité, consultez [fournissant l’empaquetage et du déploiement dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Informations sur les éléments  
  
|||  
|-|-|  
|**Namespace**|http://schemas.Microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Nom du schéma**|Schéma d’élément de projet SharePoint|  
|**Fichier de validation**|ProjectItemModelSchema.xsd|  
|**Peut être vide.**|Non|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence du schéma élément de projet SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Fourniture d’informations de création de packages et de déploiement dans des éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
  
  