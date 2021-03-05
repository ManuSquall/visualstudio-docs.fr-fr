---
description: Récupère la valeur d’un registre spécifié, telle qu’elle est stockée dans le frame de pile.
title: IDiaStackFrame::get_registerValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_registerValue method
ms.assetid: cbe3d8ac-319a-40ac-bc3e-4eb81b2d7807
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 92ada384d6e231a33dc2b1bbccfafa1e790f1c9c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147435"
---
# <a name="idiastackframeget_registervalue"></a>IDiaStackFrame::get_registerValue
Récupère la valeur d’un registre spécifié, telle qu’elle est stockée dans le frame de pile.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_registerValue(
   ULONG      registerIndex,
   ULONGLONG *pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `registerIndex`

dans L’une des CV_HREG_e valeurs d’énumération d' [énumération](../../debugger/debug-interface-access/cv-hreg-e.md) .

 `pRetVal`

à Valeur stockée dans le registre.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne le code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [CV_HREG_e, énumération](../../debugger/debug-interface-access/cv-hreg-e.md)
