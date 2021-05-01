---
description: Récupère une valeur qui indique si la fonction a été compilée avec la vérification des erreurs au moment de l’exécution du frame de pile. Il s’agit de l’indicateur/RTCs.
title: 'IDiaSymbol :: get_isRTCs | Microsoft Docs'
ms.date: 04/27/2021
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isRTCs method
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9a297abe6326af6f04058e6095f59f880f526adb
ms.sourcegitcommit: 30c404655fb83ea28f96ab1edb1c09b4d8d7eec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2021
ms.locfileid: "108217234"
---
# <a name="idiasymbolget_isrtcs"></a>IDiaSymbol :: get_isRTCs

Retourne une valeur qui indique si la fonction a été compilée avec la vérification des erreurs au moment de l’exécution du frame de pile. Il s’agit de l’indicateur/RTCs.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_isRTCs ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres

 `pRetVal`

à Pointeur vers un booléen qui spécifie si la fonction a été compilée avec la vérification des erreurs au moment de l’exécution du frame de pile.

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
