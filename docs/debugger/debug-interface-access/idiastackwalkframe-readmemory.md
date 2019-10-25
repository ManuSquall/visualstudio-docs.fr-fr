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
ms.openlocfilehash: ae1201fca1fc25cce19b40b47d6435d02d80e1b4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741482"
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

à Retourne le nombre d’octets retournés. Si `data` est `NULL`, `pcbData` contient le nombre total d’octets de données disponibles.

 `data`

à Mémoire tampon qui doit être remplie avec des données provenant de l’emplacement spécifié.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; Sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)