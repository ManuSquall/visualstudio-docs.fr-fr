---
title: ProjectOutputFile, élément | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectOutputFile element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ea476c2d2b73ec9c59f7d3f7cfbc9a0b0cab5bd7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53948613"
---
# <a name="projectoutputfile-element"></a>ProjectOutputFile (élément)
  Représente la sortie d’un projet séparé à inclure avec l’élément de projet lorsqu’elle est déployée vers SharePoint.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
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
|**Target**|Facultatif **xs : String** attribut.<br /><br /> Le chemin d’accès où la sortie du projet dépendant doit être déployé sur le serveur SharePoint, relatif au dossier racine de déploiement. Le dossier racine de déploiement est déterminé par le type de déploiement spécifié par le **Type** attribut.<br /><br /> Pour plus d’informations, consultez les descriptions pour le **Deployment Path** et **Deployment Root** propriétés de SharePoint éléments de projet des [SharePoint de développer des solutions](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|Requis **xs : String** attribut.<br /><br /> Le type de déploiement à utiliser pour la sortie du projet dépendant. Pour plus d’informations sur les valeurs possibles, consultez la description de la **Type de déploiement** propriété des éléments de projet SharePoint dans [SharePoint de développer des solutions](../sharepoint/developing-sharepoint-solutions.md).|  
  
### <a name="child-elements"></a>Éléments enfants
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents
  
|Élément|Description|  
|-------------|-----------------|  
|[Fichiers](../sharepoint/files-element.md)|Spécifie les fichiers à inclure avec l’élément de projet SharePoint lorsqu’elle est déployée vers SharePoint.|  
  
## <a name="remarks"></a>Notes  
 Utilisez le **ProjectOutputFile** élément pour inclure la sortie d’un projet dans le déploiement de l’élément de projet SharePoint. Vous pouvez spécifier un autre projet ou le même projet qui contient l’élément de projet. Pour plus d’informations, consultez [fournissent des informations d’empaquetage et de déploiement dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Informations sur les éléments
  
|||  
|-|-|  
|**Espace de noms**|HTTP<nolink>: //schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**Nom de schéma**|Schéma d’élément de projet SharePoint|  
|**Fichier de validation**|ProjectItemModelSchema.xsd|  
|**Peut être vide**|Aucune|  
  
## <a name="see-also"></a>Voir aussi
 [Référence de schéma élément de projet SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Fournir des informations d’empaquetage et de déploiement dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
