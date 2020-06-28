---
title: IDiaSectionContrib::get_relativeVirtualAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_relativeVirtualAddress method
ms.assetid: 32f9674d-94f1-4590-99de-a2eb60da4af8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3bd8f0a4db99823b44b214891bc302290a2d141
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466132"
---
# <a name="idiasectioncontribget_relativevirtualaddress"></a>IDiaSectionContrib::get_relativeVirtualAddress
Récupère l’adresse virtuelle relative (RVA) de l’image de la contribution.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_relativeVirtualAddress ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne l’adresse RVA de l’image de la contribution.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)