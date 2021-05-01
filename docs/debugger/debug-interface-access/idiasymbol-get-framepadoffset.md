---
description: Récupère le décalage du bloc de pile à partir du registre de pointeur de frame.
title: 'IDiaSymbol :: get_framePadOffset | Microsoft Docs'
ms.date: 04/27/2021
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_framePadOffset method
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 455e617188a58090f3bd6229ab008847912b1f19
ms.sourcegitcommit: 30c404655fb83ea28f96ab1edb1c09b4d8d7eec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2021
ms.locfileid: "108217235"
---
# <a name="idiasymbolget_framepadoffset"></a>IDiaSymbol :: get_framePadOffset

Récupère le décalage du bloc de pile à partir du registre de pointeur de frame.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_framePadOffset ( 
   DWORD* pPadOffset
);
```

#### <a name="parameters"></a>Paramètres

 `pPadOffset`

à Retourne le décalage du bloc de pile.

## <a name="return-value"></a>Valeur renvoyée

 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou code d’erreur.

> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Notes

Cette méthode est prise en charge à partir de Visual Studio 2019 version 16,10 Preview 2.

## <a name="requirements"></a>Spécifications

|Condition requise|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK v 7.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
