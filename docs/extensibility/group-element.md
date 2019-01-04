---
title: Group, élément | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Groups
- Groups element (VSCT XML schema)
ms.assetid: 69faee18-cbf4-470a-b952-c1919c583df8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 19bc3f44a4ba87195986327fe756e7419f259076
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53827453"
---
# <a name="group-element"></a>Élément de groupe
Définit un groupe de commande VSPackage.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Group guid="guidMyCommandSet" id="MyGroup" priority="0x101">  
  <Parent>... </Parent>  
</Group>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|GUID|Obligatoire. GUID de l’identificateur de commande/ID GUID.|  
|ID|Obligatoire. ID de l’identificateur de commande/ID GUID.|  
|priority|Facultatif. Une valeur numérique qui spécifie la priorité.|  
|Condition|Facultatif. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|Parent|Facultatif. L’élément parent du bouton.|  
|Annotation|Commentaire facultatif.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément Groups](../extensibility/groups-element.md)|Contient des entrées qui définissent les groupes de commandes d’un VSPackage.|  
  
## <a name="example"></a>Exemple  
  
```xml  
<Group guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">  
  <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_MAINMENU"/>  
</Group>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Visual Studio fichiers command table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)