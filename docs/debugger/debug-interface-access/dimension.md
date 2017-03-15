---
title: "Dimension | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "symbole de dimension"
ms.assetid: 94f791da-bfea-454f-8a14-da31e8e1596a
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Dimension
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Chaque tableau FORTRAN possède une dimension qui est identifiée par un symbole d' `SymTagDimension` .  
  
## Propriétés  
 Le tableau suivant affiche les propriétés valides supplémentaires pour ce type de symbole.  
  
|Propriété|Type de données|Description|  
|---------------|---------------------|-----------------|  
|[IDiaSymbol::get\_lowerBound](../Topic/IDiaSymbol::get_lowerBound.md)|`IDiaSymbol*`|Limite inférieure d'une dimension de tableau FORTRAN.|  
|[IDiaSymbol::get\_lowerBoundId](../Topic/IDiaSymbol::get_lowerBoundId.md)|`DWORD`|ID du symbole limite inférieure.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID d'index de symbole.|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|Retourne `SymTagDimension` \(une des valeurs de [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md) \).|  
|[IDiaSymbol::get\_upperBound](../../debugger/debug-interface-access/idiasymbol-get-upperbound.md)|`IDiaSymbol*`|Limite supérieure d'une dimension de tableau FORTRAN.|  
|[IDiaSymbol::get\_upperBoundId](../../debugger/debug-interface-access/idiasymbol-get-upperboundid.md)|`DWORD`|ID du symbole stimulant\-lié.|  
  
## Voir aussi  
 [ArrayType](../../debugger/debug-interface-access/arraytype.md)   
 [Hiérarchie de classes des types de symboles](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)