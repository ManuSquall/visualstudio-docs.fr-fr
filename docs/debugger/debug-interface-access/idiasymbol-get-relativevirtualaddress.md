---
title: IDiaSymbol::get_relativeVirtualAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_relativeVirtualAddress method
ms.assetid: e37219e3-c021-4057-9ec8-4f7cf3c13a15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7aa2fa4288a6af460cfd373a2a3aa74a1ad461e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56636435"
---
# <a name="idiasymbolgetrelativevirtualaddress"></a>IDiaSymbol::get_relativeVirtualAddress
Récupère l’adresse virtuelle relative (RVA) de l’emplacement. Quand utiliser le [LocationType (énumération)](../../debugger/debug-interface-access/locationtype.md) est défini sur `LocIsStatic`.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_relativeVirtualAddress ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

[out] Retourne l’adresse virtuelle relative de l’emplacement.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="example"></a>Exemple

```C++
IDiaSymbol* pSymbol;
DWORD       rva;
pSymbol->get_relativeVirtualAddress( &rva );
```

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md)