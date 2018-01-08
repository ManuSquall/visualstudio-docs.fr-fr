---
title: "ExtensionDataItem (élément) | Documents Microsoft"
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
helpviewer_keywords: ExtensionDataItem element
ms.assetid: 6a5fe7eb-b433-42dc-bd50-4882b780e2fb
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 018103ed0ede32b65403821e36128bca6fd083a3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="extensiondataitem-element"></a>ExtensionDataItem, élément
  Représente un élément de données personnalisé qui est associé à l’élément de projet SharePoint, au format clé/valeur. La clé et la valeur doivent être des chaînes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<ExtensionDataItem Key = "Key of the data item"  
    Value = "Value of the data item" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|**Key**|Requis **xs : String** attribut.<br /><br /> La clé qui est utilisée pour stocker et récupérer l’élément de données.|  
|**Valeur**|Requis **xs : String** attribut.<br /><br /> La valeur de l’élément de données.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Représente une collection d’éléments de données personnalisés qui sont associés à l’élément de projet SharePoint.|  
  
## <a name="remarks"></a>Notes  
 Lorsque vous associez des données personnalisées à un élément de projet SharePoint à l’aide de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propriété d’un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> Visual Studio enregistre les données dans un nouvel objet **ExtensionDataItem** élément dans le fichier .spdata pour l’élément de projet. Pour plus d’informations, consultez [l’enregistrement des données dans les Extensions du système de projet SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## <a name="element-information"></a>Informations sur les éléments  
  
|||  
|-|-|  
|**Espace de noms**|http://schemas.Microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Nom du schéma**|Schéma d’élément de projet SharePoint|  
|**Fichier de validation**|ProjectItemModelSchema.xsd|  
|**Peut être vide.**|Non|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur le schéma d’élément de projet SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  