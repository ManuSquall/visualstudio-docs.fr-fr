---
title: IDiaSession::findAcceleratorInlineesByName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fb3caa5574605864a0dd16b59b6f451530b8e631
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56632236"
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
Retourne une énumération de symboles pour les frames en ligne correspondant au nom de fonction inline spécifiés.

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

[in] Le nom de fonction inline à rechercher.

 `option`

[in] Les options de recherche de nom à utiliser lors de la recherche d’inline des frames qui correspondent aux `name`. Pour plus d’informations, consultez [NameSearchOptions (énumération)](../../debugger/debug-interface-access/namesearchoptions.md).

 `ppResult`

[out] Un pointeur vers un `IDiaEnumSymbols` pointeur d’interface qui est initialisé avec le résultat.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Remarques
 Cette fonction recherche les éléments inline uniquement dans les fonctions de stub d’accélérateur. Il ignore les enregistrements de procédure C++ natifs.

## <a name="see-also"></a>Voir aussi
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)