---
title: "&#201;l&#233;ment Groups | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Éléments du schéma XML de VSCT, groupes"
  - "Élément Groups (schéma XML de VSCT)"
ms.assetid: 740ca4ec-79fa-4b98-8f9a-2a137f9f7f98
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# &#201;l&#233;ment Groups
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contient des entrées qui définissent les groupes de commande d'un VSPackage.  
  
## Syntaxe  
  
```  
<Groups>  
  <Group>... </Group>  
  <Group>... </Group>  
</Groups>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|Condition|Facultatif. Consultez [Attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément de groupe](../extensibility/group-element.md)|Représente un groupe d'une commande unique.|  
|[Groups Element](../extensibility/groups-element.md)|Contient des entrées qui définissent les groupes de commande d'un VSPackage.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément Commands](../extensibility/commands-element.md)|Représente la collection de commandes dans la barre d'outils VSPackage.|  
  
## Exemple  
  
```  
<Groups> <Group guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit"> <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_MAINMENU"/> </Group> </Groups>  
```  
  
## Voir aussi  
 [Comment ajouter des éléments d'Interface utilisateur dans les packages VS](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Commandes, Menus et barres d'outils](../extensibility/internals/commands-menus-and-toolbars.md)