---
title: IDiaSectionContrib::get_code | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_code method
ms.assetid: f9ccf7a6-46e7-4a1d-9d5c-97272e17bbbb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c5c9952b5f3b5e1f4748c064d37c842aece1600
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85466384"
---
# <a name="idiasectioncontribget_code"></a>IDiaSectionContrib::get_code
Récupère un indicateur qui signale si la section contient du code exécutable.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_code ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne `TRUE` si la section contient du code exécutable ; sinon, retourne `FALSE` .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)