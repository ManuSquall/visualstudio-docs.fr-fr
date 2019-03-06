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
ms.openlocfilehash: 530b6c3f6873724f8a8ca06ea4228b017de281f9
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56694463"
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

[in] Une valeur comprise entre le [MemoryTypeEnum (énumération)](../../debugger/debug-interface-access/memorytypeenum.md) énumération spécifiant le type de mémoire à lire.

 va

[in] Adresse virtuelle dans l’image à partir duquel commencer la lecture.

 `cbData`

[in] La taille du tampon de données en octets.

 `pcbData`

[out] Retourne le nombre d’octets réellement lus. Si `pbData` est `NULL`, puis il s’agit du nombre total d’octets de données disponibles.

 `pbData`

[in, out] Une mémoire tampon est remplie avec la mémoire à lire.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [MemoryTypeEnum, énumération](../../debugger/debug-interface-access/memorytypeenum.md)