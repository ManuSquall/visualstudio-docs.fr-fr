---
title: IDiaSymbol::get_baseType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_baseType method
ms.assetid: 5c69a241-a8d3-48ed-8b36-27463a196572
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aea1205abf5c7a4bf7e4fd6b035651cc7ad52be6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85464204"
---
# <a name="idiasymbolget_basetype"></a>IDiaSymbol::get_baseType
Récupère le type de base pour ce symbole<em>.</em>

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_baseType (
    DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
`pRetVal`

à Retourne une valeur de l’énumération d' [énumération BasicType](../../debugger/debug-interface-access/basictype.md) qui spécifie le type de base du symbole.

## <a name="return-value"></a>Valeur renvoyée
En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Notes
Le type de base pour un symbole peut être déterminé en obtenant tout d’abord le type du symbole, puis en interrogeant ce type retourné pour le type de base. Notez que certains symboles peuvent ne pas avoir de type de base (par exemple, un nom de structure).

## <a name="example"></a>Exemple

```C++
IDiaSymbol* pType;
CComPtr<IDiaSymbol> pBaseType;
if (pType->get_type( &pBaseType ) == S_OK)
{
    BasicType btBaseType;
    if (pBaseType->get_baseType((DWORD *)&btBaseType) == S_OK)
    {
        // Do something with basic type.
    }
}
```

## <a name="requirements"></a>Configuration requise

|Condition requise|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK v 7.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [BasicType, énumération](../../debugger/debug-interface-access/basictype.md)
- [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)
