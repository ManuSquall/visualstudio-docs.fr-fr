---
title: "Friend (Kit de d&#233;veloppement logiciel de Debug&#160;Interface&#160;Access) | Microsoft Docs"
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
  - "fonctions friend (DIA SDK)"
  - "classes friend (DIA SDK)"
  - "symbole friend"
ms.assetid: 5147a170-41ce-4727-8ace-c318e8d11647
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Friend (Kit de d&#233;veloppement logiciel de Debug&#160;Interface&#160;Access)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les classes et les fonctions friend " friend " sont identifiées par des symboles d' `SymTagFriend` .  ils sont des enfants des types définis par l'utilisateur parents \(UDTs\) et ont une propriété de [IDiaSymbol::get\_classParent](../Topic/IDiaSymbol::get_classParent.md) .  
  
## Propriétés  
 Le tableau suivant affiche les propriétés valides supplémentaires pour ce type de symbole.  
  
|Propriété|Type de données|Description|  
|---------------|---------------------|-----------------|  
|[IDiaSymbol::get\_classParent](../Topic/IDiaSymbol::get_classParent.md)|`IDiaSymbol*`|symbole pour le parent de type défini par l'utilisateur.|  
|[IDiaSymbol::get\_classParentId](../Topic/IDiaSymbol::get_classParentId.md)|`DWORD`|ID du symbole de parent de classe.|  
|[IDiaSymbol::get\_name](../Topic/IDiaSymbol::get_name.md)|`BSTR`|nom de la classe ou de la fonction.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID d'index de symbole.|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|Retourne `SymTagFriend` \(une des valeurs de [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md) \).|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Symbole de la classe ou la fonction.|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|ID du symbole de type.|  
  
## Voir aussi  
 [Hiérarchie de classes des types de symboles](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)