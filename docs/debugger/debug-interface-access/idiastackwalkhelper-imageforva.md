---
description: Retourne le début de l’image d’un exécutable en mémoire en fonction d’une adresse virtuelle quelque part dans l’espace mémoire de l’exécutable.
title: IDiaStackWalkHelper::imageForVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::imageForVA method
ms.assetid: 8d4edabf-3c01-4fef-8b61-4779f3371067
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2459ed59f4b34befd893d25848de9482b39f9d70
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156845"
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

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
