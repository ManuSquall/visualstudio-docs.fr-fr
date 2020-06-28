---
title: IDiaStackWalkHelper::pdataForVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: d6e9b3e812311ef3d9555584d72ebb966098232a
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464708"
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

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` s’il n’existe aucun pData pour l’adresse spécifiée. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Remarques
 Le PDATA (la section nommée « . pdata ») d’un compiland contient des informations sur la gestion des exceptions pour les fonctions.

 L’appelant sait la quantité de données à retourner pour que l’appelant n’ait pas besoin de demander la quantité de données disponibles. Par conséquent, il est acceptable pour une implémentation de cette méthode de retourner une erreur si le `pbData` paramètre est `NULL` .

## <a name="see-also"></a>Voir aussi
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)