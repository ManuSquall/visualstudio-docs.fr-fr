---
title: IDiaSymbol::get_baseType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: e1d38e39fd7687de3ff87737b49972cb389187aa
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "62837605"
---
# <a name="idiasymbolgetbasetype"></a>IDiaSymbol::get_baseType
Récupère le type de base pour ce symbole<em>.</em>

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_baseType (
    DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
`pRetVal`

[out] Retourne une valeur de la [BasicType (énumération)](../../debugger/debug-interface-access/basictype.md) énumération spécifiant le type de base du symbole.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Notes
Le type de base pour un symbole peut être déterminé par tout d’abord obtenir le type du symbole et puis en interrogeant qui a retourné le type pour le type de base. Notez que certains symboles ne peuvent pas avoir un type de base, par exemple, le nom de la structure.

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

|Prérequis|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK v7.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [BasicType, énumération](../../debugger/debug-interface-access/basictype.md)
- [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)
