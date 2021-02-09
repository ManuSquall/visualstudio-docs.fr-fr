---
title: IDiaLineNumber::get_lineNumberEnd | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_lineNumberEnd method
ms.assetid: b101853e-2bcf-47c1-acef-e13984c7ea9d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 93bb9e6cf42966b80bd2512a0cdc488ef91c7429
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864781"
---
# <a name="idialinenumberget_linenumberend"></a>IDiaLineNumber::get_lineNumberEnd
Récupère le numéro de ligne source de base 1 où l’instruction ou l’expression se termine.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_lineNumberEnd ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne le numéro de ligne où l’instruction ou l’expression se termine. Si la valeur est égale à zéro, les informations de fin ne sont pas présentes.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)