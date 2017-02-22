---
title: "&#201;l&#233;ment de ButtonText | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ButtonText, élément (schéma XML de VSCT)"
  - "Éléments du schéma XML de VSCT, ButtonText"
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# &#201;l&#233;ment de ButtonText
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ce champ vous permet de spécifier le texte qui apparaît dans les différents menus. Par défaut, le `ButtonText` élément apparaît dans les contrôleurs de menu. Le `ButtonText` élément devient également la valeur par défaut si les autres champs de texte sont vides. Le `ButtonText` élément ne peut pas être vide même si les autres champs de texte sont spécifiées.  
  
## Syntaxe  
  
```  
<ButtonText>My Command</ButtonText>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun.  
  
### Éléments enfants  
 Aucun.  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément de chaînes](../extensibility/strings-element.md)|Regroupe les éléments de texte, tel que `ButtonText` et `CommandName`.|  
  
## Valeur texte  
 La valeur texte de la `ButtonText` élément fournit le texte qui est affiché pour les éléments de menu, combinés et autres éléments d'interface \(UI\) qui contiennent le texte visible.  
  
## Voir aussi  
 [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)