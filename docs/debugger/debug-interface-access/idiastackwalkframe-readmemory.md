---
title: IDiaStackWalkFrame::readMemory | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 82ef0d25e796f9e04ecdcfd0c54a7312b9c9edad
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56628596"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
Lit la mémoire à partir de l’image.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT readMemory ( 
   MemoryTypeEnum type,
   ULONGLONG va,
   DWORD     cbData,
   DWORD*    pcbData,
   BYTE      data[]
);
```

#### <a name="parameters"></a>Paramètres
 `type`

[in] Parmi les [MemoryTypeEnum (énumération)](../../debugger/debug-interface-access/memorytypeenum.md) des valeurs d’énumération qui spécifie le type de mémoire pour accéder à.

 `va`

[in] Emplacement d’adresse virtuelle dans l’image pour commencer la lecture.

 `cbData`

[in] Taille de la mémoire tampon de données, en octets.

 `pcbData`

[out] Retourne le nombre d’octets retournés. Si `data` est `NULL`, puis `pcbData` contient le nombre total d’octets de données disponibles.

 `data`

[out] Une mémoire tampon à remplir avec des données à partir de l’emplacement spécifié.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)