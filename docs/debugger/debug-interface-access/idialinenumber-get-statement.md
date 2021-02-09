---
title: IDiaLineNumber::get_statement | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_statement method
ms.assetid: 22b8ee29-79ef-427f-bd05-00d255ab836b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0baad9c254efad1fff772cfae27828e3597d078b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864732"
---
# <a name="idialinenumberget_statement"></a>IDiaLineNumber::get_statement
Récupère un indicateur qui spécifie que ces informations de ligne décrivent le début d’une instruction, plutôt qu’une expression, dans la source du programme.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_statement ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne `TRUE` si ces informations de ligne décrivent le début d’une instruction dans la source du programme.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Remarques
 Les instructions peuvent s’étendre sur plusieurs lignes. Cette méthode indique si le numéro de ligne associé marque le début d’une telle instruction multiligne.

## <a name="see-also"></a>Voir aussi
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)