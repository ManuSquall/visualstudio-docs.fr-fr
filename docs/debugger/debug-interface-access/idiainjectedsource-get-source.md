---
title: IDiaInjectedSource::get_source | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_source method
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2f44f30b063a34a0d5d5549cd1923b66c1dde9cb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864865"
---
# <a name="idiainjectedsourceget_source"></a>IDiaInjectedSource::get_source
Récupère les octets de code source.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_source ( 
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>Paramètres
 `cbData`

dans Nombre d’octets qui représente la taille de la mémoire tampon de données.

 `pcbData`

à Retourne le nombre d’octets qui représente les octets retournés. Si `data` est `NULL` , `pcbData` est le nombre total d’octets de données disponibles.

 `data[]`

à Mémoire tampon qui doit être remplie avec les octets sources.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)