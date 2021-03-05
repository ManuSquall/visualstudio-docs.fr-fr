---
description: Récupère un indicateur qui spécifie si le type de données défini par l’utilisateur est une classe de base virtuelle.
title: IDiaSymbol::get_virtualBaseClass | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualBaseClass method
ms.assetid: 474eddc6-bf16-4731-9145-6db2f2a0b4fd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 512138b8734fb9137781da040dd5d5a591107fd8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160539"
---
# <a name="idiasymbolget_virtualbaseclass"></a>IDiaSymbol::get_virtualBaseClass
Récupère un indicateur qui spécifie si le type de données défini par l’utilisateur est une classe de base virtuelle.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_virtualBaseClass ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne `TRUE` si le type de données défini par l’utilisateur est une classe de base virtuelle ; sinon, retourne `FALSE` .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
