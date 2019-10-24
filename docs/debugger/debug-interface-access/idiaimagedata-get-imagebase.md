---
title: IDiaImageData::get_imageBase | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7887fea30b04f4ebb6605169c58551122eccf73d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743435"
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

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 En raison de conflits de base d’image, une image peut être rebasé automatiquement sur un emplacement mémoire inutilisé lorsqu’elle est chargée. Cette méthode retourne l’indicateur de base (emplacement mémoire suggéré) qui était stocké dans le module au moment de la compilation.

## <a name="see-also"></a>Voir aussi
- [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)