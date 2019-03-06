---
title: Personnalisé (SDK Debug Interface Access) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Custom symbol
ms.assetid: a219fc83-d2a8-4bc5-b7e1-bfafeb247f16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 15e0d58c49a66416371c7e66e12f469e6d224c91
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56637163"
---
# <a name="custom-debug-interface-access-sdk"></a>Personnalisé (Kit de développement logiciel de Debug Interface Access)
Certains compilateurs introduisent de symboles qui ne sont pas identifiées par les types de symboles lexicale standard. Ces symboles sont identifiés par un `SymTagCustom` balise.

## <a name="properties"></a>Propriétés
 Le tableau suivant présente les propriétés qui sont valides pour ce type de symbole.

|Property|Type de données|Description|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_dataBytes](../../debugger/debug-interface-access/idiasymbol-get-databytes.md)|`BYTE`|Tableau de données associées au symbole.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID d’index de symbole.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Retourne `SymTagCustom` (parmi les [SymTagEnum (énumération)](../../debugger/debug-interface-access/symtagenum.md) valeurs).|

## <a name="see-also"></a>Voir aussi
- [Hiérarchie lexicale des types de symboles](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)