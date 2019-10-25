---
title: IDiaStackFrame::get_cplusplusExceptionHandling | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_cplusplusExceptionHandling method
ms.assetid: f2631820-c986-40ca-b61e-230d7a9c426c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d78a4c73d7954f48c87c1eafec4d0b35fc1292ef
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741752"
---
# <a name="idiastackframeget_cplusplusexceptionhandling"></a>IDiaStackFrame::get_cplusplusExceptionHandling
Récupère un indicateur qui signale si C++ la gestion des exceptions est en vigueur.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_cplusplusExceptionHandling ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne `TRUE` si C++ la gestion des exceptions est appliquée pour ce frame ; Sinon, retourne`FALSE`.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si la propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 C++la gestion des exceptions n’est pas identique à la gestion structurée ou à la gestion des exceptions système.

 Pour déterminer si la gestion structurée des exceptions est en vigueur, appelez la méthode [IDiaStackFrame :: get_systemExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-systemexceptionhandling.md) .

## <a name="see-also"></a>Voir aussi
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackFrame::get_systemExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-systemexceptionhandling.md)