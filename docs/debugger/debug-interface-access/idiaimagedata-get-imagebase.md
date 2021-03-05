---
description: Récupère l’emplacement de mémoire dans lequel l’image doit être basée.
title: IDiaImageData::get_imageBase | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 82f80f95689a176118d5be6dcc5cfe4fdb903e0f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148450"
---
# <a name="idiaimagedataget_imagebase"></a>IDiaImageData::get_imageBase
Récupère l’emplacement de mémoire dans lequel l’image doit être basée.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_imageBase ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne la valeur de base de l’image suggérée.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 En raison de conflits de base d’image, une image peut être rebasé automatiquement sur un emplacement mémoire inutilisé lorsqu’elle est chargée. Cette méthode retourne l’indicateur de base (emplacement mémoire suggéré) qui était stocké dans le module au moment de la compilation.

## <a name="see-also"></a>Voir aussi
- [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)
