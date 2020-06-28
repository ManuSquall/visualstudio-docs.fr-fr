---
title: IDiaSymbol::get_isDataAligned | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isDataAligned method
ms.assetid: ddd11a41-6c00-4829-acf4-aa1ace8c21a7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00507b5d69f46657968407170d9633f1d84c8e4f
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85463427"
---
# <a name="idiasymbolget_isdataaligned"></a>IDiaSymbol::get_isDataAligned
Récupère un indicateur qui spécifie si le type défini par l’utilisateur (UDT) a été aligné sur une limite de mémoire spécifique.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_isDataAligned(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Paramètres
 `pFlag`

à Retourne `TRUE` si le type défini par l’utilisateur a été aligné sur une limite de la mémoire ; sinon, retourne `FALSE` .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou code d’erreur.

> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Remarques
 Cette propriété est généralement définie lorsque l’exécutable est compilé avec un alignement de données non défini par défaut. Par exemple, le compilateur Microsoft C++ peut modifier l’alignement des données avec l’option de ligne de commande/ZP <em>#</em> , où *#* est une valeur d’octet.

## <a name="requirements"></a>Configuration requise

|Condition requise|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK v 8.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)