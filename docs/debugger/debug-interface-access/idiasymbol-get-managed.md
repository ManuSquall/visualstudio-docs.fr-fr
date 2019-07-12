---
title: IDiaSymbol::get_managed | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_managed method
ms.assetid: a69d00be-2a89-415c-b116-385c422e2fd5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1096487cc154e0c6addd87d3e051078bfbc84f16
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "64824878"
---
# <a name="idiasymbolgetmanaged"></a>IDiaSymbol::get_managed
Récupère un indicateur qui spécifie si le symbole fait référence au code managé.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_managed ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

[out] Retourne `TRUE` si le symbole fait référence au code managé ; sinon, retourne `FALSE`.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)