---
title: IDiaStackWalkHelper::readMemory | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 57afd033b2d969a4ed57dc713b2c4266e0ead632
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741363"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
Lit un bloc de données à partir de l’image de l’exécutable en mémoire.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT readMemory( 
   enum MemoryTypeEnum type,
   ULONGLONG           va,
   DWORD               cbData,
   DWORD*              pcbData,
   BYTE*               pbData
);
```

#### <a name="parameters"></a>Paramètres
 `type`

dans Valeur de l’énumération d' [énumération MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md) qui spécifie le type de mémoire à lire.

 va

dans Adresse virtuelle de l’image à partir de laquelle commencer la lecture.

 `cbData`

dans Taille de la mémoire tampon de données en octets.

 `pcbData`

à Retourne le nombre d’octets réellement lus. Si `pbData` est `NULL`, il s’agit du nombre total d’octets de données disponibles.

 `pbData`

[in, out] Mémoire tampon qui est remplie avec la lecture de la mémoire.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [MemoryTypeEnum, énumération](../../debugger/debug-interface-access/memorytypeenum.md)