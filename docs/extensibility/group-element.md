---
title: "&#201;l&#233;ment de groupe | Microsoft Docs"
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
ms.assetid: 69faee18-cbf4-470a-b952-c1919c583df8
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# &#201;l&#233;ment de groupe
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Définit un groupe de commande VSPackage.  
  
## Syntaxe  
  
```  
<Group guid="guidMyCommandSet" id="MyGroup" priority="0x101">  
  <Parent>... </Parent>  
</Group>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|GUID|Obligatoire. GUID de l'identificateur de commande\/ID GUID.|  
|ID|Obligatoire. ID de l'identificateur de commande\/ID GUID.|  
|priority|Facultatif. Une valeur numérique qui spécifie la priorité.|  
|Condition|Facultatif. Consultez [Attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|Parent|Facultatif. L'élément parent du bouton.|  
|Annotation|Commentaire facultatif.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément Groups](../extensibility/groups-element.md)|Contient des entrées qui définissent les groupes de commande d'un VSPackage.|  
  
## Exemple  
  
```  
<Group guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit"> <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_MAINMENU"/> </Group>  
```  
  
## Voir aussi  
 [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)