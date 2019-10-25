---
title: IDiaAddressMap::get_imageAlign | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_imageAlign method
ms.assetid: f1ba8071-669c-4cf7-9ac0-02f26d99f366
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa5394580a9b0db4600a7f1e67aa8bd7f7703542
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745089"
---
# <a name="idiaaddressmapget_imagealign"></a>IDiaAddressMap::get_imageAlign
Récupère l’alignement de l’image actuelle.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_imageAlign ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne la valeur d’alignement de l’image à partir de l’exécutable.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Les images sont alignées sur des limites de mémoire spécifiques, en fonction de la façon dont l’image a été chargée et créée. L’alignement s’effectue généralement sur des limites de 1, 2, 4, 8, 16, 32 ou 64 octets. L’alignement de l’image peut être défini à l’aide d’un appel à la méthode [IDiaAddressMap ::P ut_imagealign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md) .

## <a name="see-also"></a>Voir aussi
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)