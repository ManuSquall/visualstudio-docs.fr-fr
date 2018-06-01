---
title: ExtensionDataItem (élément) | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionDataItem element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 48c29cb41c80d75c6f873171b7e9c758a2513612
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34691935"
---
# <a name="extensiondataitem-element"></a>ExtensionDataItem, élément
  Un élément de données personnalisé qui est associé à l’élément de projet SharePoint, au format clé/valeur. La clé et la valeur doivent être des chaînes.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<ExtensionDataItem Key = "Key of the data item"  
    Value = "Value of the data item" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|**Key**|Requis **xs : string** attribut.<br /><br /> La clé qui est utilisée pour stocker et récupérer l’élément de données.|  
|**Valeur**|Requis **xs : String** attribut.<br /><br /> La valeur de l’élément de données.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Représente une collection d’éléments de données personnalisés qui sont associés à l’élément de projet SharePoint.|  
  
## <a name="remarks"></a>Notes  
 Lorsque vous associez des données personnalisées à un élément de projet SharePoint à l’aide de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propriété d’un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> Visual Studio enregistre les données dans un nouvel objet **ExtensionDataItem** élément dans le `.spdata` du fichier pour le élément de projet. Pour plus d’informations, consultez [l’enregistrement des données dans les Extensions du système de projet SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## <a name="element-information"></a>Informations sur les éléments  
  
|||  
|-|-|  
|**Espace de noms**|HTTP<nolink>: //schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel| 
|**Nom du schéma**|Schéma d’élément de projet SharePoint|  
|**Fichier de validation**|ProjectItemModelSchema.xsd|  
|**Peut être vide.**|Non|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur le schéma d’élément de projet SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  