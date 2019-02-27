---
title: IDiaStackFrame::get_registerValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_registerValue method
ms.assetid: cbe3d8ac-319a-40ac-bc3e-4eb81b2d7807
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a819293863b658f6e12609b2c1cd83c37532e02d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56637631"
---
# <a name="idiastackframegetregistervalue"></a>IDiaStackFrame::get_registerValue
Récupère la valeur d’un registre spécifié, tel que stocké dans le frame de pile.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_registerValue(
   ULONG      registerIndex,
   ULONGLONG *pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `registerIndex`

[in] Parmi les [CV_HREG_e (énumération)](../../debugger/debug-interface-access/cv-hreg-e.md) valeurs d’énumération.

 `pRetVal`

[out] Valeur stockée dans le Registre.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne le code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [CV_HREG_e, énumération](../../debugger/debug-interface-access/cv-hreg-e.md)