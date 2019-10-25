---
title: IDiaStackWalkHelper::imageForVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::imageForVA method
ms.assetid: 8d4edabf-3c01-4fef-8b61-4779f3371067
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 609a9370181937323f2bc3e8ca0a0765cd1f4a12
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741387"
---
# <a name="idiastackwalkhelperimageforva"></a>IDiaStackWalkHelper::imageForVA
Retourne le début de l’image d’un exécutable en mémoire en fonction d’une adresse virtuelle quelque part dans l’espace mémoire de l’exécutable.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT imageForVA(
   ULONGLONG  vaContext,
   ULONGLONG *pvaImageStart
);
```

#### <a name="parameters"></a>Paramètres
 `vaContext`

dans Adresse virtuelle qui se trouve dans l’espace de l’exécutable.

 `pvaImageStart`

à Retourne l’adresse virtuelle de début de l’image de l’exécutable.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)