---
title: IDiaSymbol::get_compilerGenerated | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 39c3751eb71d3d0e627946212ee5aaa54c1b5253
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56623110"
---
# <a name="idiasymbolgetcompilergenerated"></a>IDiaSymbol::get_compilerGenerated
Récupère un indicateur qui indique si le symbole a été généré par le compilateur.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_compilerGenerated ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

[out] Retourne `TRUE` si le compilateur a généré le symbole ; sinon, retourne `FALSE` si le symbole a été généré à partir de la source écrit par l’utilisateur.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou code d’erreur.

> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="requirements"></a>Spécifications

|Spécification|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK v7.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)