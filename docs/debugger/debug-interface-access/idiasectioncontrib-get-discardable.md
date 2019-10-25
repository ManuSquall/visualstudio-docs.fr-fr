---
title: IDiaSectionContrib::get_discardable | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_discardable method
ms.assetid: 30ca88d4-3198-4b0f-b30e-2e54b3607fe9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6048f83b2f5e01790f771ae61e7a9a0fc8f329a4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742676"
---
# <a name="idiasectioncontribget_discardable"></a>IDiaSectionContrib::get_discardable
Récupère un indicateur qui indique si la section peut être ignorée.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_discardable ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne `TRUE` si la section peut être supprimée de la mémoire en fonction des besoins ; Sinon, retourne `FALSE`.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)