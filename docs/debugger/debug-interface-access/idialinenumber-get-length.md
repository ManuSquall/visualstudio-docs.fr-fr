---
description: Récupère le nombre d’octets dans un bloc.
title: IDiaLineNumber::get_length | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_length method
ms.assetid: 2c55a6f7-4ef5-45fb-9fd1-d72deaaa2829
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3d8fd3c4301ee49a737a71349c15502c240d9e36
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157587"
---
# <a name="idialinenumberget_length"></a>IDiaLineNumber::get_length
Récupère le nombre d’octets dans un bloc.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_length ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne le nombre d’octets dans un bloc.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Le bloc est la longueur du code source sur la ligne telle qu’elle est représentée par l’objet [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) .

## <a name="see-also"></a>Voir aussi
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
