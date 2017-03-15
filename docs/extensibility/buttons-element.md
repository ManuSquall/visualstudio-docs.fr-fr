---
title: "&#201;l&#233;ment de boutons | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Élément de boutons (schéma XML de VSCT)"
  - "Éléments du schéma XML de VSCT, boutons"
ms.assetid: 9f2cf94d-dec5-4776-a836-9a89c75f0c87
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# &#201;l&#233;ment de boutons
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Groupes [bouton](../extensibility/button-element.md) éléments qui représentent des commandes individuelles.  
  
## Syntaxe  
  
```  
<Buttons>  
  <Button>... </Button>  
  <Button>... </Button>  
</Buttons>  
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
|[Buttons Element](../extensibility/buttons-element.md)|Regroupe les éléments de bouton.|  
|[Élément de bouton](../extensibility/button-element.md)|Définit une commande que l'utilisateur peut interagir avec.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément Commands](../extensibility/commands-element.md)|Représente la collection de commandes dans la barre d'outils VSPackage.|  
  
## Exemple  
  
```  
<Buttons> <Button guid="guidMenuAndCommandsCmdSet" id="cmdidMyCommand"     priority="0x100" type="Button"> <Parent guid="guidMenuAndCommandsCmdSet" id="MyMenuGroup"/> <Icon guid="guidGenericCmdBmp" id="bmpArrow"/> <Strings> <ButtonText>C# Command Sample</ButtonText> </Strings> </Button> </Buttons>  
```  
  
## Voir aussi  
 [Comment ajouter des éléments d'Interface utilisateur dans les packages VS](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Commandes, Menus et barres d'outils](../extensibility/internals/commands-menus-and-toolbars.md)