---
title: IDiaInjectedSource::get_length | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_length method
ms.assetid: 38b88b8b-c2e0-4b2d-8b8b-9ff373733e78
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 73beb6fea872da74bdce6f94e05d1c8ddc8915b7
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467063"
---
# <a name="idiainjectedsourceget_length"></a>IDiaInjectedSource::get_length
Récupère le nombre d’octets de code.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_length ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne le nombre d’octets de code.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Remarques
 La valeur retournée par cette méthode est la longueur du code source et est la même valeur que celle retournée par la méthode [IDiaInjectedSource :: get_Source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md) .

## <a name="see-also"></a>Voir aussi
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
- [IDiaInjectedSource::get_source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md)