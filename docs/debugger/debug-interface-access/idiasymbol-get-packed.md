---
title: IDiaSymbol::get_packed | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_packed method
ms.assetid: e42ff368-56c4-49a2-8676-f80e349efa21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84cea5ba87c606f66bda1ee09cbf35ae6ef5a643
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56635382"
---
# <a name="idiasymbolgetpacked"></a>IDiaSymbol::get_packed
Récupère un indicateur qui spécifie si le type de données défini par l’utilisateur (UDT) est compressé.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_packed ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

[out] Retourne `TRUE` si l’UDT est empaqueté ; sinon, retourne `FALSE`.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Remarques
 Conditionnés signifie que tous les membres de l’UDT sont positionnés aussi proches que possible, sans remplissage intermédiaire pour l’aligner sur des limites de mémoire.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)