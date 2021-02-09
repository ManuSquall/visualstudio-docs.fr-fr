---
title: IDiaLineNumber::get_columnNumber | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_columnNumber method
ms.assetid: e317f29a-6525-46a7-8421-33985392f8fd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ec9075be8ab003cda087b37c13a0f2ef9c481dff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864802"
---
# <a name="idialinenumberget_columnnumber"></a>IDiaLineNumber::get_columnNumber
Récupère le numéro de colonne où l’expression ou l’instruction commence.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT get_columnNumber ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne le numéro de la colonne où l’expression ou l’instruction commence. Si la valeur est égale à zéro, les informations sur les colonnes ne sont pas présentes.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Remarques
 La valeur de colonne retournée par cette méthode est un offset d’octet dans la ligne jusqu’au premier caractère de l’instruction sur la ligne.

## <a name="see-also"></a>Voir aussi
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)