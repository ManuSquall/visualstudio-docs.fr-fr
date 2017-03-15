---
title: "&#201;l&#233;ment de combinaisons | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Élément combinés (schéma XML de VSCT)"
  - "Éléments du schéma XML de VSCT, combinés"
ms.assetid: ef48d2d2-0c47-4f93-8cfe-52026b6c463e
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# &#201;l&#233;ment de combinaisons
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Groupe les éléments [Élément de liste déroulante](../extensibility/combo-element.md).  
  
## Syntaxe  
  
```  
<Combos>  
  <Combo>... </Combo>  
  <Combo>... </Combo>  
</Combos>  
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
|[Combos Element](../extensibility/combos-element.md)|Regroupe les éléments de liste déroulante.|  
|[Élément de liste déroulante](../extensibility/combo-element.md)|Définit les commandes qui apparaissent dans une zone de liste déroulante.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément Commands](../extensibility/commands-element.md)|Représente la collection de commandes dans la barre d'outils VSPackage.|  
  
## Exemple  
  
```  
<Combos> <Combo guid="guidWidgetPackage" id="cmdidInsertOptions" defaultWidth="100" idCommandList="cmdidGetInsertOptionsList"> <CommandFlag>DynamicVisibility</CommandFlag> <Strings> <ButtonText>Select Insert Options</ButtonText> </Strings> </Combo> <Combo guid="guidWidgetPackage" id="cmdidInsertOptions" priority="0x0500" type="DropDownCombo" defaultWidth="100" idCommandList="cmdidGetInsertOptionsList"> <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit"> <CommandFlag>DynamicVisibility</CommandFlag> <Strings> <ButtonText>Select Insert Options</ButtonText> </Strings> </Combo> </Combos>  
```  
  
## Voir aussi  
 [Comment ajouter des éléments d'Interface utilisateur dans les packages VS](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Commandes, Menus et barres d'outils](../extensibility/internals/commands-menus-and-toolbars.md)