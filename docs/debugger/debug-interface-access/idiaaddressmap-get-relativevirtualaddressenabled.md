---
description: Indique si le calcul et l’utilisation des adresses virtuelles relatives (RVA) sont activés.
title: IDiaAddressMap::get_relativeVirtualAddressEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_relativeVirtualAddressEnabled method
ms.assetid: 4c48af81-7148-4d9a-818e-dbe62cbfc638
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5383772ca95d3dada7218643b483d2ca5d056613
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158426"
---
# <a name="idiaaddressmapget_relativevirtualaddressenabled"></a>IDiaAddressMap::get_relativeVirtualAddressEnabled
Indique si le calcul et l’utilisation des adresses virtuelles relatives (RVA) sont activés.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_relativeVirtualAddressEnabled ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 pRetVal

à Retourne `TRUE` si le calcul de RVA est activé.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Les adresses RVA sont activées si les segments ont été initialement chargés à partir d’un fichier PDB. L’utilisation de RVA peut être temporairement désactivée en appelant la méthode [IDiaAddressMap ::p ut_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) .

 En outre, de nouveaux en-têtes d’image peuvent être établis en appelant la méthode [IDiaAddressMap :: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) suivie d’un appel à la `put_relativeVirtualAddressEnabled` méthode pour permettre l’utilisation des adresses RVA à l’aide des en-têtes d’image nouveaux.

## <a name="see-also"></a>Voir aussi
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
- [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)
