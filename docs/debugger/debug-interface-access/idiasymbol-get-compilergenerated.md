---
title: IDiaSymbol::get_compilerGenerated | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_compilerGenerated method
ms.assetid: 864d9249-f0c8-4a34-b391-eb785f7e8865
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29d7255fd0e2c769a1b7d318e56982ba739915d2
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464085"
---
# <a name="idiasymbolget_compilergenerated"></a>IDiaSymbol::get_compilerGenerated
Récupère un indicateur qui signale si le symbole a été généré par le compilateur.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_compilerGenerated ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne `TRUE` si le compilateur a généré le symbole ; sinon, retourne `FALSE` si le symbole a été généré à partir de la source écrite par l’utilisateur.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou code d’erreur.

> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="requirements"></a>Configuration requise

|Condition requise|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK v 7.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)