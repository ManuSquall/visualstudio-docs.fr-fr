---
title: "&#201;l&#233;ment de bitmaps | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Éléments du schéma XML de VSCT, les Bitmaps"
  - "Bitmaps, élément (schéma XML de VSCT)"
ms.assetid: 74652e1b-fcfa-421b-aa9f-fbc081d3b476
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# &#201;l&#233;ment de bitmaps
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Groupe les éléments [Élément de bitmap](../extensibility/bitmap-element.md).  
  
## Syntaxe  
  
```  
<Bitmaps>  
  <Bitmap>... </Bitmap>  
  <Bitmap>... </Bitmap>  
</Bitmaps>  
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
|[Bitmaps Element](../extensibility/bitmaps-element.md)|Regroupe les éléments de la Bitmap.|  
|[Élément de bitmap](../extensibility/bitmap-element.md)|Définit une image bitmap.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément Commands](../extensibility/commands-element.md)|Représente la collection de commandes dans la barre d'outils VSPackage.|  
  
## Exemple  
  
```  
<Bitmaps> <Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" /> <Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS" usedList="1, 2, 3, 4"/> </Bitmaps>  
```  
  
## Voir aussi  
 [Comment ajouter des éléments d'Interface utilisateur dans les packages VS](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Commandes, Menus et barres d'outils](../extensibility/internals/commands-menus-and-toolbars.md)