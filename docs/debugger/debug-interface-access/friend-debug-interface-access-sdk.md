---
title: Friend (Debug Interface Access SDK) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- friend functions [DIA SDK]
- friend classes [DIA SDK]
- Friend symbol
ms.assetid: 5147a170-41ce-4727-8ace-c318e8d11647
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c496b2b653bc1243a122f2025aa9d08b47fef7b1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="friend-debug-interface-access-sdk"></a>Friend (Kit de développement logiciel de Debug Interface Access)
Friend (classes) et des fonctions friend sont identifiées par `SymTagFriend` symboles. Ils sont des types définis par l’utilisateur (UDT) enfants du parent et avoir un [IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md) propriété.  
  
## <a name="properties"></a>Propriétés  
 Le tableau suivant montre des propriétés supplémentaires valides pour ce type de symbole.  
  
|Propriété|Type de données|Description|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Symbole pour le parent de l’UDT.|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|ID de symbole classe parent.|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nom de la classe ou fonction.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID d’index du symbole.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Retourne `SymTagFriend` (parmi les [symtagenum, énumération](../../debugger/debug-interface-access/symtagenum.md) valeurs).|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Symbole de la classe ou fonction.|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|ID de symbole du type.|  
  
## <a name="see-also"></a>Voir aussi  
 [Hiérarchie de classes des types de symboles](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)