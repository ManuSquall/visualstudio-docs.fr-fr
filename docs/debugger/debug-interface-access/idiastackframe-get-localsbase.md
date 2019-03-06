---
title: IDiaStackFrame::get_localsBase | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_localsBase method
ms.assetid: eb0bd73e-d92d-468e-a0b1-fbc279919f54
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cbe6dd1d5b72faea57ecb015b0da294798527c0b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56642727"
---
# <a name="idiastackframegetlocalsbase"></a>IDiaStackFrame::get_localsBase
Récupère l’adresse de base des variables locales pour le frame.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_localsBase ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

[out] Retourne l’adresse de base des variables locales.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si la propriété n’est pas pris en charge. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)