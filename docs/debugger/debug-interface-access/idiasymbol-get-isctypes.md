---
title: IDiaSymbol::get_isCTypes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2 interface
ms.assetid: 00c73cf9-2933-472e-bc1d-d041f4d7e412
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 264e8dfb784af75a8138aa1b606e0f4a926f8d65
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85463448"
---
# <a name="idiasymbolget_isctypes"></a>IDiaSymbol::get_isCTypes
Récupère un indicateur qui spécifie si le fichier de symboles contient des types C.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_isCTypes(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Paramètres
 `pFlag`

à Retourne `TRUE` si le fichier de symboles contient des types C ; sinon, retourne `FALSE` .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Remarques
 Cette propriété est disponible à partir du `SymTagExe` type de symbole (consultez [exe](../../debugger/debug-interface-access/exe.md)).

## <a name="requirements"></a>Configuration requise

|Condition requise|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK v 8.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Exécutable](../../debugger/debug-interface-access/exe.md)