---
description: Récupère la taille de remplissage supplémentaire ajoutée à chaque fonction.
title: 'IDiaSymbol :: get_framePadSize | Microsoft Docs'
ms.date: 04/27/2021
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_framePadSize method
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d361ec3e144730e49345d3560f815ee5fe0be469
ms.sourcegitcommit: 30c404655fb83ea28f96ab1edb1c09b4d8d7eec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2021
ms.locfileid: "108217231"
---
# <a name="idiasymbolget_framepadsize"></a>IDiaSymbol :: get_framePadSize

Récupère la taille de remplissage supplémentaire ajoutée à chaque fonction.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_framePadSize ( 
   DWORD* pPadSize
);
```

#### <a name="parameters"></a>Paramètres

 `pPadSize`

à Retourne la taille de remplissage supplémentaire ajoutée à chaque fonction.

## <a name="return-value"></a>Valeur renvoyée

 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou code d’erreur.

> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Notes

La taille de remplissage supplémentaire est généralement utilisée par modifier & continuer.

Cette méthode est prise en charge à partir de Visual Studio 2019 version 16,10 Preview 2.

## <a name="requirements"></a>Spécifications

|Condition requise|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK v 7.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
