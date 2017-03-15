---
title: "&#201;l&#233;ment de CommandPlacement | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CommandPlacements, élément (schéma XML de VSCT)"
  - "Éléments du schéma XML de VSCT, CommandPlacements"
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# &#201;l&#233;ment de CommandPlacement
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'élément CommandPlacement permet des boutons, des groupes et des menus être inclus dans plus d'un groupe ou un menu. À l'aide de l'élément CommandPlacement, il est inutile de redéfinir intégralement ces éléments afin de modifier l'apparence de l'interface utilisateur.  
  
 Pour plus d'informations, consultez [Création de groupes de boutons réutilisables](../extensibility/creating-reusable-groups-of-buttons.md).  
  
## Syntaxe  
  
```  
<CommandPlacement guid=guidMyCommandSet" id="MyCommand" priority="0x001" >  
  <Parent>... </Parent>  
</CommandPlacement>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|GUID|Obligatoire. Le guid de l'ensemble de commandes, comme défini dans le [Élément de symboles](../extensibility/symbols-element.md).|  
|ID|Obligatoire. L'id du menu, du groupe ou de la commande doit être placé, tel que défini dans le `Symbols Element`.|  
|priority|Obligatoire. Détermine la position visuelle de l'élément dans son élément parent.|  
|Condition|Facultatif. Consultez [Attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|Parent|Obligatoire. Le menu ou le groupe qui héberge l'élément doit être placé.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément de CommandPlacements](../extensibility/commandplacements-element.md)|Spécifie les groupes d'éléments CommandPlacements et CommandPlacement.|  
  
## Exemple  
  
```  
<CommandPlacements> <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions" priority="0x0300"> <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/> </CommandPlacement> </CommandPlacements>  
```  
  
## Voir aussi  
 [Élément de CommandPlacements](../extensibility/commandplacements-element.md)   
 [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)