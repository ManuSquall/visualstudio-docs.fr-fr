---
description: Récupère l’adresse de chargement du fichier exécutable qui correspond aux symboles dans ce magasin de symboles.
title: IDiaSession::get_loadAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::get_loadAddress method
ms.assetid: 5162ae1a-38e3-4571-8995-4ed9be1dec3e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 38336d238451f40a285595e166f2896eabe203e4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157041"
---
# <a name="idiasessionget_loadaddress"></a>IDiaSession::get_loadAddress
Récupère l’adresse de chargement du fichier exécutable qui correspond aux symboles dans ce magasin de symboles.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_loadAddress ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne une adresse virtuelle (VA) où un fichier. exe ou. dll est chargé.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 L’adresse de chargement retournée est toujours égale à zéro, sauf si elle est définie spécifiquement à l’aide de la méthode [IDiaSession ::p ut_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) .

## <a name="see-also"></a>Voir aussi
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)
