---
title: IDiaSymbol::get_hasEHa | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasEHa method
ms.assetid: cb61dfd9-fe69-461c-8185-288440454864
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 95df7b4a5783ce858a4c3c13352ae9140f40f201
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "64826910"
---
# <a name="idiasymbolgethaseha"></a>IDiaSymbol::get_hasEHa
Récupère un indicateur qui spécifie si la fonction contient des exceptions asynchrones (structurées).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_hasEHa(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Paramètres
 `pFlag`

[out] Retourne `TRUE` si la fonction a des exceptions asynchrones ; sinon, retourne `FALSE`.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Notes
 Il est possible de combiner asynchrone ou structurée des exceptions avec gestion des exceptions de style C++, mais elle nécessite un commutateur de compilateur spécifique, /EHa, pour l’activer.

## <a name="requirements"></a>Configuration requise

|Prérequis|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK 8.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)