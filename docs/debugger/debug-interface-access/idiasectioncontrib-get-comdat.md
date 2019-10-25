---
title: IDiaSectionContrib::get_comdat | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_comdat method
ms.assetid: 8bd9be8d-59ee-4698-b055-daba354b8dcc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef38d5c4afcb065f7a095501e2bf5d95ee493789
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742730"
---
# <a name="idiasectioncontribget_comdat"></a>IDiaSectionContrib::get_comdat
Récupère un indicateur qui signale si la section est un enregistrement COMDAT.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_comdat ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne `TRUE` si la section est un enregistrement COMDAT ; Sinon, retourne `FALSE`.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Un enregistrement COMDAT est un enregistrement COFF (Common Object File Format) qui rend les fonctions empaquetées visibles à l’éditeur de liens.

## <a name="see-also"></a>Voir aussi
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)