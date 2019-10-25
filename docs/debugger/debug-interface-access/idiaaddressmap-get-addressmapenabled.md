---
title: IDiaAddressMap::get_addressMapEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_addressMapEnabled method
ms.assetid: 6183dc5e-befa-4e5a-ae5a-f4aa24f3ed9e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b518cf3728279ea8db267d01867fa66ceae35b21
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745177"
---
# <a name="idiaaddressmapget_addressmapenabled"></a>IDiaAddressMap::get_addressMapEnabled
Indique si un mappage d’adresses a été établi pour une session particulière.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_addressMapEnabled ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 pRetVal

à Retourne `TRUE` si le mappage d’adresse est activé.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Les après-processeurs exécutables mettent parfois à jour l’exécutable. DIA contient un mécanisme qui permet de prendre en charge la traduction de symboles vers la nouvelle disposition.

 Les applications clientes peuvent définir le mappage d’adresses pour une session particulière en obtenant l’interface [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md) à partir de l’interface [IDiaSession](../../debugger/debug-interface-access/idiasession.md) et en appelant la méthode [IDiaAddressMap :: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) suivie d’un appel à la [méthode IDiaAddressMap ::p méthode ut_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) . La méthode `get_addressMapEnabled` retourne les résultats de l’appel de la méthode `put_addressMapEnabled`.

## <a name="see-also"></a>Voir aussi
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)