---
title: Personnalisé (kit de développement logiciel de debug interface Access) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Custom symbol
ms.assetid: a219fc83-d2a8-4bc5-b7e1-bfafeb247f16
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5e1a1819178961ae0a4ccd02286d6a166fd18b8f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164400"
---
# <a name="custom-debug-interface-access-sdk"></a>Personnalisé (Kit de développement logiciel de Debug Interface Access)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Certains compilateurs introduisent des symboles qui ne sont pas identifiés par l’un des types de symboles lexicals standard. Ces symboles sont identifiés par une `SymTagCustom` balise.  
  
## <a name="properties"></a>Propriétés  
 Le tableau suivant présente les propriétés qui sont valides pour ce type de symbole.  
  
|Propriété|Type de données|Description|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_dataBytes](../../debugger/debug-interface-access/idiasymbol-get-databytes.md)|`BYTE`|Tableau de données associé au symbole.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID d’index du symbole.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Retourne `SymTagCustom` (l’une des valeurs d' [énumération SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) ).|  
  
## <a name="see-also"></a>Voir aussi  
 [Hiérarchie lexicale des types de symboles](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
