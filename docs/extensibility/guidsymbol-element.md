---
title: "&#201;l&#233;ment de GuidSymbol | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Éléments du schéma XML de VSCT, GuidSymbol"
  - "GuidSymbol, élément (schéma XML de VSCT)"
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# &#201;l&#233;ment de GuidSymbol
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le `GuidSymbol` élément contient le GUID de la paire GUID:ID qui représente un menu, un groupe ou une commande. L'ID provient d'un `IDSymbol` élément dans le `GuidSymbol` élément. Le `GuidSymbol` de l'élément est un `name` attribut qui fournit un nom convivial pour le GUID, qui est contenu dans le `value` attribut.  
  
## Syntaxe  
  
```  
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">  
  <IDSymbol>... </IDSymbol>  
  <IDSymbol>... </IDSymbol>  
</GuidSymbol>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|name|Obligatoire. Nom du symbole GUID.|  
|valeur|Obligatoire. GUID du symbole GUID.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément de IDSymbol](../extensibility/idsymbol-element.md)|Contient l'ID de la paire GUID:ID qui représente un menu, un groupe ou une commande.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément de symboles](../extensibility/symbols-element.md)|Groupes `GuidSymbol` éléments dans un fichier .vsct.|  
  
## Notes  
 En règle générale, un fichier .vsct contient trois `GuidSymbol` éléments dans son `Symbols` section, une pour le package lui\-même, un pour le jeu de commandes \(la collection des menus, les groupes et les commandes que le package met à disposition\) et un pour les bitmaps qui fournissent des icônes pour les boutons et autres composants visuels. Chaque `IDSymbol` élément dans une donnée `GuidSymbol` élément doit avoir une valeur unique `value`. Toutefois, `IDSymbol` les éléments qui ont des valeurs identiques peuvent exister dans un package tant qu'ils disposent des parents différents.  
  
## Voir aussi  
 [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)