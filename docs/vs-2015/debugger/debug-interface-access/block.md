---
title: Block | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- SymTagBlock symbol
- nested scopes
- Block symbol
ms.assetid: 95b7b0c1-ecc9-405f-8456-5f9cfb866498
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 84ef374a54470685dcfc0985f79fd2182513a3a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62580477"
---
# <a name="block"></a>Bloquer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Chaque bloc de code est identifié par un `SymTagBlock` symbole. Les symboles de bloc sont utilisés pour identifier les étendues imbriquées dans les fonctions.  
  
## <a name="properties"></a>Propriétés  
 Le tableau suivant présente les propriétés qui sont valides pour ce type de symbole.  
  
|Propriété|Type de données|Description|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Partie décalage de l’emplacement ; Pour plus d’informations, consultez l' [énumération LocationType (](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Partie section de l’emplacement ; Pour plus d’informations, consultez l' [énumération LocationType (](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Nombre d’octets de code dans le bloc.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbole du bloc ou de la fonction englobant.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Retourne l’ID du symbole parent lexical.|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Les blocs ont des emplacements statiques ; Pour plus d’informations, consultez [emplacements des symboles](../../debugger/debug-interface-access/symbol-locations.md).|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Retourne le nom du bloc (qui est généralement une chaîne vide).|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Retourne l’adresse virtuelle de ce bloc par rapport à son parent lexical.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID d’index du symbole.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Retourne `SymTagBlock` (l’une des valeurs d' [énumération SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) ).|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Retourne l’adresse virtuelle de ce bloc dans l’exécutable.|  
  
## <a name="see-also"></a>Voir aussi  
 [Hiérarchie lexicale des types de symboles](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Énumération LocationType (](../../debugger/debug-interface-access/locationtype.md)   
 [Emplacements des symboles](../../debugger/debug-interface-access/symbol-locations.md)
