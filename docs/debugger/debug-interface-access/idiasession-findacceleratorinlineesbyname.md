---
title: IDiaSession::findAcceleratorInlineesByName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1a2ce0d808a21a793115c6f065ca4ab95b1507e5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855234"
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
Retourne une énumération de symboles pour les frames insérés correspondant au nom de fonction inline spécifié.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findAcceleratorInlineeLinesByName ( 
   LPCOLESTR             name,
   DWORD                 option,
   IDiaEnumSymbols**     ppResult
);
```

#### <a name="parameters"></a>Paramètres
 `name`

dans Nom de la fonction inline dans lequel effectuer la recherche.

 `option`

dans Options de recherche de nom à utiliser lors de la recherche de frames Inline correspondant à `name` . Pour plus d’informations, consultez [énumération NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md).

 `ppResult`

à Pointeur vers un `IDiaEnumSymbols` pointeur d’interface qui est initialisé avec le résultat.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Remarques
 Cette fonction recherche des Inlines uniquement dans les fonctions d’accélérateur. Elle ignore les enregistrements de procédures C++ natifs.

## <a name="see-also"></a>Voir aussi
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)