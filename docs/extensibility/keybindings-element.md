---
title: "&#201;l&#233;ment de th&#232;mes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "KeyBindings"
helpviewer_keywords: 
  - "Éléments du schéma XML de VSCT, thèmes"
  - "Thèmes, élément (schéma XML de VSCT)"
ms.assetid: 26a15d5c-ddea-4977-af7f-d795ff09c7ad
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# &#201;l&#233;ment de th&#232;mes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les éléments de thèmes élément groupes KeyBinding et autres regroupements de thèmes.  
  
## Syntaxe  
  
```  
<KeyBindings>  
  <KeyBinding>... </KeyBinding>  
  <KeyBinding>... </KeyBinding>  
</KeyBindings>  
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
|[Élément de KeyBinding](../extensibility/keybinding-element.md)|Spécifie les raccourcis clavier des commandes.|  
|[KeyBindings](../extensibility/keybindings-element.md)|Regroupe les éléments KeyBinding et autres regroupements de thèmes.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément de CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent des commandes.|  
  
## Exemple  
  
```  
<KeyBindings> <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget" editor="guidWidgetEditor" key1="VK_F5"/> <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget" editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/> </KeyBindings>  
```  
  
## Voir aussi  
 [Élément de KeyBinding](../extensibility/keybinding-element.md)   
 [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)