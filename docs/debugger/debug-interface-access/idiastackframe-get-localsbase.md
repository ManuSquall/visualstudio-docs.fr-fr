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
ms.openlocfilehash: 4ae3f83469e14e826802ca82d3d58686a340d9e0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741662"
---
# <a name="idiastackframeget_localsbase"></a>IDiaStackFrame::get_localsBase
Récupère l’adresse de base des variables locales pour le frame.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_localsBase ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne l’adresse de base des variables locales.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si la propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)