---
description: Récupère le symbole qui représente le type de ce symbole.
title: IDiaSymbol::get_type | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_type method
ms.assetid: 1c6a4176-dd4e-4c22-8b8f-0e559fc078ba
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f0f6e86eaa78fd57d3cb62b1602111df1406f1bf
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155627"
---
# <a name="idiasymbolget_type"></a>IDiaSymbol::get_type
Récupère le symbole qui représente le type de ce symbole.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_type (
    IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Paramètres
`pRetVal`

à Retourne un objet [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) qui représente le type de ce symbole.

## <a name="return-value"></a>Valeur renvoyée
En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Notes
Pour déterminer le type d’un symbole, vous devez appeler cette méthode et examiner l’objet [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) résultant. Notez qu’il est possible qu’un symbole n’ait pas de type. Par exemple, le nom d’une structure n’a pas de type, mais il peut avoir des symboles enfants (utilisez la méthode [IDiaSymbol :: findchildren (](../../debugger/debug-interface-access/idiasymbol-findchildren.md) pour examiner ces enfants).

## <a name="example"></a>Exemple

```C++
IDiaSymbol*         pType;
CComPtr<IDiaSymbol> pBaseType;
if (SUCCEEDED(pType->get_type( &pBaseType ))) {
    BasicType btBaseType;
    if (SUCCEEDED(pBaseType->get_baseType((DWORD *)&btBaseType))) {
        // Do something with basic type.
    }
}
```

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
