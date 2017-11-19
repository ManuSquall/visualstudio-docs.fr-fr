---
title: "ProjectOutputFile (élément) | Documents Microsoft"
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
helpviewer_keywords: ProjectOutputFile element
ms.assetid: 52a017bf-e19c-49e4-bb8f-cbe6958195c2
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a397648dd81ead8134777c8b36982fa6b65b687b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="projectoutputfile-element"></a>ProjectOutputFile, élément
  Représente la sortie d’un projet séparé à inclure avec l’élément de projet lorsqu’il est déployé dans SharePoint.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<ProjectOutputFile ProjectId = "GUID of the project"  
    ProjectPath = "Relative path of the project"  
    Target = "Deployment path of the project output"  
    Type = "Type of deployment for the project output" />  
```  
  
## <a name="type"></a>Type  
 **ProjectOutputFileType**  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|**ProjectId**|Requis **xs : String** attribut.<br /><br /> Le GUID du projet dépendant comportant la sortie que vous souhaitez inclure. Cela correspond à la **ProjectGuid** élément dans le fichier projet dépendant.|  
|**ProjectPath**|Requis **xs : String** attribut.<br /><br /> Le chemin d’accès relatif, y compris le nom du fichier projet, du projet dépendant comportant la sortie que vous souhaitez inclure. Ce chemin d’accès est relatif au dossier racine du projet SharePoint qui contient l’élément de projet SharePoint.|  
|**Target**|Facultatif **xs : String** attribut.<br /><br /> Le chemin d’accès où la sortie de projet dépendant doit être déployé sur le serveur SharePoint, relatif au dossier racine de déploiement. Dossier racine de déploiement est déterminé par le type de déploiement spécifié par le **Type** attribut.<br /><br /> Pour plus d’informations, consultez les descriptions pour le **le chemin de déploiement** et **racine du déploiement** propriétés de SharePoint dans les éléments de projet [développement de Solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|Requis **xs : String** attribut.<br /><br /> Le type de déploiement à utiliser pour la sortie du projet dépendant. Pour plus d’informations sur les valeurs possibles, consultez la description de la **Type de déploiement** propriété des éléments de projet SharePoint dans [développement de Solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Fichiers](../sharepoint/files-element.md)|Spécifie les fichiers à inclure avec l’élément de projet SharePoint lorsqu’elle est déployée vers SharePoint.|  
  
## <a name="remarks"></a>Remarques  
 Utilisez le **ProjectOutputFile** élément à inclure la sortie d’un projet dans le déploiement de l’élément de projet SharePoint. Vous pouvez spécifier un autre projet ou le même projet qui contient l’élément de projet. Pour plus d’informations, consultez [fournissant l’empaquetage et du déploiement dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Informations sur les éléments  
  
|||  
|-|-|  
|**Namespace**|http://schemas.Microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Nom du schéma**|Schéma d’élément de projet SharePoint|  
|**Fichier de validation**|ProjectItemModelSchema.xsd|  
|**Peut être vide.**|Non|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence du schéma élément de projet SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [En fournissant l’empaquetage et du déploiement dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Développement de solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  