---
title: IDiaSymbol::get_sizeInUdt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a82ab896-0185-46a4-b4d5-babfcc660fe1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 147368e19bb1bcc1ccaa0bf94823df2e3f73a4be
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62428363"
---
# <a name="idiasymbolgetsizeinudt"></a>IDiaSymbol::get_sizeInUdt
Récupère la taille d’un membre d’un type défini par l’utilisateur.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_sizeInUdt(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

[out] Un pointeur vers un `DWORD` qui spécifie la taille du membre.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)