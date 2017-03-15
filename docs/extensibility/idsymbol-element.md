---
title: "&#201;l&#233;ment de IDSymbol | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDSymbol, élément (schéma XML de VSCT)"
  - "Éléments du schéma XML de VSCT, IDSymbol"
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# &#201;l&#233;ment de IDSymbol
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le `IDSymbol` élément contient l'ID de la paire GUID:ID qui représente un menu, un groupe ou une commande. Le GUID est fourni à partir du parent `GuidSymbol` élément. Le `IDSymbol` de l'élément est un `name` attribut qui fournit un nom convivial pour l'ID, qui est contenue dans le `value` attribut.  
  
## Syntaxe  
  
```  
<IDSymbol name=ElementName value="0x0010" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|name|Obligatoire. Nom du symbole ID.|  
|valeur|Obligatoire. Valeur d'ID numérique du symbole de code.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément de GuidSymbol](../extensibility/guidsymbol-element.md)|Contient le GUID de la paire GUID:ID qui représente un menu, un groupe ou une commande. Groupe les éléments `IDSymbol`.|  
  
## Notes  
 Chaque `IDSymbol` élément dans une donnée `GuidSymbol` élément doit avoir une valeur unique `value`. Toutefois, `IDSymbol` les éléments qui ont des valeurs identiques peuvent exister dans un package tant qu'ils disposent des parents différents.  
  
## Voir aussi  
 [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)