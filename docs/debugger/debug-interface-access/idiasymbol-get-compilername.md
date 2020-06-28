---
title: IDiaSymbol::get_compilerName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_compilerName method
ms.assetid: 66eaaf72-68d4-40ee-b132-97bea9fe395c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 49491d2d9934a20e9d40c0dcd5aadeed3ef27ca7
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464078"
---
# <a name="idiasymbolget_compilername"></a>IDiaSymbol::get_compilerName
Retourne le nom du compilateur utilisé pour générer le [compiland](../../debugger/debug-interface-access/compiland.md).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_compilerName (
   BSTR *pName
);
```

#### <a name="parameters"></a>Paramètres
 `pName`Pointeur vers un BSTR qui contient le nom Unicode du compilateur.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Notes

## <a name="requirements"></a>Spécifications

|Condition requise|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK v 8.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)