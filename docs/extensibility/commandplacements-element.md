---
title: "&#201;l&#233;ment de CommandPlacements | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CommandPlacements"
helpviewer_keywords: 
  - "CommandPlacements, élément (schéma XML de VSCT)"
  - "Éléments du schéma XML de VSCT, CommandPlacements"
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# &#201;l&#233;ment de CommandPlacements
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'élément CommandPlacements regroupe les éléments CommandPlacement et autres regroupements CommandPlacements.  
  
 L'élément CommandPlacements est facultatif. Si aucun commandes, des groupes ou menus ne doivent être incluses dans un emplacement secondaire, il est inutile d'inclure cette section dans le fichier .vsct.  
  
## Syntaxe  
  
```  
<CommandPlacements>  
  <CommandPlacement>... </CommandPlacement>  
  <CommandPlacement>... </CommandPlacement>  
</CommandPlacements>  
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
|CommandPlacements|Regroupe les éléments CommandPlacement et autres regroupements CommandPlacements.|  
|[Élément de CommandPlacement](../extensibility/commandplacement-element.md)|Active les boutons, les groupes et les menus être inclus dans plus d'un groupe ou un menu.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément de CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent des commandes.|  
  
## Exemple  
  
```  
<CommandPlacements> <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions" priority="0x0300"> <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/> </CommandPlacement> </CommandPlacements>  
```  
  
## Voir aussi  
 [Élément de CommandPlacement](../extensibility/commandplacement-element.md)   
 [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)