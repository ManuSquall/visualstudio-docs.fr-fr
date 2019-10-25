---
title: IDiaStackWalkHelper::pdataForVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d51736a80021847881db164c9e176a010124638
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741398"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
Retourne le bloc de données PDATA associé à l’adresse virtuelle.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT pdataForVA( 
   ULONGLONG  va,
   DWORD      cbData,
   DWORD*     pcbData,
   BYTE*      pbData
);
```

#### <a name="parameters"></a>Paramètres
 `va`

dans Spécifie l’adresse virtuelle des données à obtenir.

 `cbData`

dans Taille des données en octets à obtenir.

 `pcbData`

à Retourne la taille réelle des données en octets qui ont été obtenues.

 `pbData`

[in, out] Mémoire tampon qui est remplie avec les données demandées. Ne peut pas être `NULL`.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` s’il n’existe aucun PDATA pour l’adresse spécifiée. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Le PDATA (la section nommée « . pdata ») d’un compiland contient des informations sur la gestion des exceptions pour les fonctions.

 L’appelant sait la quantité de données à retourner pour que l’appelant n’ait pas besoin de demander la quantité de données disponibles. Par conséquent, il est acceptable pour une implémentation de cette méthode de retourner une erreur si le paramètre `pbData` est `NULL`.

## <a name="see-also"></a>Voir aussi
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)