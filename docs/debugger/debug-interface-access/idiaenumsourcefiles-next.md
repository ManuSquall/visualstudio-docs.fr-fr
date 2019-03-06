---
title: IDiaEnumSourceFiles::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Next method
ms.assetid: 83bf6317-ff39-4c5c-8987-cba34e7a6983
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29424c2b12884cae7f803a46e15f7183d9690d96
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56631781"
---
# <a name="idiaenumsourcefilesnext"></a>IDiaEnumSourceFiles::Next
Récupère un nombre spécifié de fichiers sources dans la séquence d’énumération.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Next ( 
   ULONG            celt,
   IDiaSourceFile** rgelt,
   ULONG*           pceltFetched
);
```

#### <a name="parameters"></a>Paramètres
 celt

[in] Le nombre de fichiers sources dans l’énumérateur à récupérer.

 rgelt

[out] Un tableau qui doit être rempli avec le [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) les objets qui représentent les fichiers source souhaitée.

 pceltFetched

[out] Retourne le nombre de fichiers sources dans l’énumérateur extraite.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si aucun fichier source plus. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)