---
description: Définit l’alignement de l’image.
title: IDiaAddressMap::put_imageAlign | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0c3027332018441efd132cc941d16aab3bcab594
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158367"
---
# <a name="idiaaddressmapput_imagealign"></a>IDiaAddressMap::put_imageAlign
Définit l’alignement de l’image.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT put_imageAlign ( 
   DWORD NewVal
);
```

#### <a name="parameters"></a>Paramètres
 NewVal

dans Nouvelle valeur d’alignement d’image pour l’exécutable.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Les images (exécutables chargés) sont alignées sur les limites de mémoire spécifiées. Cet alignement peut être affecté par l’architecture système actuelle et par les options de compilation et de liaison temporelle. L’alignement d’image est toujours sur les limites d’octets. Les valeurs d’alignement d’image suivantes sont valides : 1, 2, 4, 8, 16, 32 et 64 limites d’octets.

 L’alignement de l’image actuelle peut être récupéré à l’aide d’un appel à la méthode [IDiaAddressMap :: get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) .

> [!NOTE]
> L’image est déjà chargée au moment où cette méthode peut être appelée. La `put_imageAlign` méthode est généralement utilisée lorsque l’image a été déplacée ou modifiée et qu’un nouvel alignement est nécessaire.

## <a name="see-also"></a>Voir aussi
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)
