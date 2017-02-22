---
title: "&#201;l&#233;ment Commands | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Commands"
helpviewer_keywords: 
  - "Élément Commands (schéma XML de VSCT)"
  - "Éléments du schéma XML de VSCT, commandes"
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# &#201;l&#233;ment Commands
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Représente la collection de commandes dans la barre d'outils VSPackage. La collection peut avoir jusqu'à cinq sous\-sections, comme suit : menus, groupes, des boutons, des combinaisons et des bitmaps.  
  
 Chaque sous\-section élément enfant, par exemple, \< Menu \>, est identifiée par un ID de commande unique qui est une paire de l'identificateur numérique et un GUID. Le GUID identifie le jeu de commandes « » et est utilisé pour regrouper les commandes logiquement liées. Le VSPackage doit définir son propre jeu pour éviter les conflits avec les ID de commande qui sont définis par d'autres packages VS de commandes.  
  
## Syntaxe  
  
```  
<Commands package="GuidMyPackage" >  
  <Menus>... </Menus>  
  <Groups>... </Groups>  
  <Buttons>... </Buttons>  
  <Combos>... </Combos>  
  <Bitmaps>... </Bitmaps>  
</Commands>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|package|GUID qui identifie le VSPackage qui fournit les commandes.<br /><br /> Par exemple, un package \= « guidVsPackage1Pkg ».|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément de menus](../extensibility/menus-element.md)|Définit tous les menus qui implémente un VSPackage.|  
|[Élément Groups](../extensibility/groups-element.md)|Contient des entrées qui définissent les groupes de commandes dans un VSPackage.|  
|[Élément de boutons](../extensibility/buttons-element.md)|Regroupe les éléments de bouton.|  
|[Élément de bitmaps](../extensibility/bitmaps-element.md)|Regroupe les éléments de la Bitmap.|  
|[Élément de combinaisons](../extensibility/combos-element.md)|Regroupe les éléments de liste déroulante.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément de CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent les commandes un VSPackage fournit à l'IDE. Éléments possibles sont les éléments de menu, des menus, des barres d'outils et des zones de liste déroulante.|  
  
## Exemple  
 L'exemple suivant montre comment utiliser un [Commands Element](../extensibility/commands-element.md).  
  
```  
<Commands package="guidMyPackage"> <Menus> <Menu Condition="'%(DEBUG)' != 'true'" guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu" priority="0x0000" type="Menu"> <Annotation> <Documentation>this is an annotation</Documentation> <AppInfo> <CustomData> <CustomSubElement>Some data</CustomSubElement> </CustomData> </AppInfo> </Annotation> <CommandFlag>AlwaysCreate</CommandFlag> <Strings> <ButtonText>MainMenu</ButtonText> </Strings> </Menu> </Menus> <Commands>  
```  
  
## Voir aussi  
 [Comment ajouter des éléments d'Interface utilisateur dans les packages VS](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Commandes, Menus et barres d'outils](../extensibility/internals/commands-menus-and-toolbars.md)