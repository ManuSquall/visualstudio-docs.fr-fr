---
title: IDiaSymbol::get_unmodifiedType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_unmodifiedType method
ms.assetid: bf914dc0-ff84-4f5d-9f75-1733b17f3be0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6fb271a03a8932989d6201329c441a21a226f559
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56614283"
---
# <a name="idiasymbolgetunmodifiedtype"></a>IDiaSymbol::get_unmodifiedType
Récupère le type d’origine pour ce symbole. Quand utiliser le [SymTagEnum (énumération)](../../debugger/debug-interface-access/symtagenum.md) est définie sur un type.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_unmodifiedType( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

[out] Retourne un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objet qui représente le type d’origine de ce symbole.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Remarques
 Le type actuel est une modification du type d’origine retourné. Le type d’origine pour un symbole peut être déterminé par tout d’abord obtenir le type du symbole et puis en interrogeant qui a retourné le type pour le type d’origine. Notez que certains symboles n’aient pas un type modifié du type d’origine.

## <a name="requirements"></a>Spécifications
 En-tête : Dia2.h

 Bibliothèque : diaguids.lib

 DLL : msdia100.dll

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)