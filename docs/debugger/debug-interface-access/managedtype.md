---
title: ManagedType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SymTagManagedType symbol
- managed type symbol
- ManagedType symbol
ms.assetid: 5db99e2a-4f2e-4796-89b7-b401b151826f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0c121e996972b47a91a018d910a5d3677cb4cffa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62855202"
---
# <a name="managedtype"></a>ManagedType
Un type managé (n’importe quel symbole défini par les métadonnées ou du format natif vers les fonctionnalités de gestion de mémoire et de ressources de langages tels que c#) est identifié par un `SymTagManagedType` symbole.

## <a name="properties"></a>Properties
 Le tableau suivant montre des propriétés supplémentaires valides pour ce type de symbole.

|Propriété|Type de données|Description|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nom du symbole managé.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID d’index de symbole.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Retourne `SymTagManagedType` (parmi les [SymTagEnum (énumération)](../../debugger/debug-interface-access/symtagenum.md) valeurs).|

## <a name="see-also"></a>Voir aussi
- [Hiérarchie de classes des types de symboles](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)