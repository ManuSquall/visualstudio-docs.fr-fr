---
title: IDiaSymbol::get_typeId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_typeId method
ms.assetid: b40be36e-10e1-463c-9c6d-21862679d29f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f0249f4e228327666e03e1a402f7f9cf69ee929
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739090"
---
# <a name="idiasymbolget_typeid"></a>IDiaSymbol::get_typeId
Récupère l’identificateur de type du symbole.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_typeId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne l’ID de type du symbole.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; Sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour de `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Notes
 L’identificateur est une valeur unique créée par le kit de développement logiciel (SDK) DIA pour marquer tous les symboles comme étant uniques.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)