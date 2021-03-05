---
description: Lit la mémoire à partir de l’image.
title: IDiaStackWalkFrame::readMemory | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: edfe15c8303236f31ab50a948a8b5506cee0356b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158921"
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

dans L’une des valeurs d’énumération d' [énumération MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md) qui spécifie le type de mémoire à laquelle accéder.

 `va`

dans Emplacement d’adresse virtuelle dans l’image pour commencer la lecture.

 `cbData`

dans Taille de la mémoire tampon de données, en octets.

 `pcbData`

à Retourne le nombre d’octets retournés. Si `data` a `NULL` la valeur, `pcbData` contient le nombre total d’octets de données disponibles.

 `data`

à Mémoire tampon qui doit être remplie avec des données provenant de l’emplacement spécifié.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
