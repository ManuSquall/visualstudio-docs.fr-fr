---
description: Pour une valeur de balise correspondante donnée, cette méthode retourne une énumération des symboles contenus dans une fonction stub d’accélérateur parente spécifiée à une adresse virtuelle relative spécifiée.
title: IDiaSession::findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: a073cc45-0c7b-417e-b5fc-a3b08beccdbc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 50545be4b99c273b7019931463883efacbb683fb
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157062"
---
# <a name="idiasessionfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSession::findSymbolsByRVAForAcceleratorPointerTag
Pour une valeur de balise correspondante donnée, cette méthode retourne une énumération des symboles contenus dans une fonction stub d’accélérateur parente spécifiée à une adresse virtuelle relative spécifiée.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findSymbolsByRVAForAcceleratorPointerTag ( 
   IDiaSymbol*           parent,
   DWORD                 tagValue,
   DWORD                 rva,
   IDiaEnumSymbols**     ppResult
);
```

#### <a name="parameters"></a>Paramètres
 `parent`

dans `IDiaSymbol` Qui correspond à la fonction stub d’accélérateur dans laquelle effectuer la recherche.

 `tagValue`

dans Valeur de balise de pointeur.

 `rva`

dans Adresse virtuelle relative.

 `ppResult`

à Pointeur vers un `IDiaEnumSymbols` pointeur d’interface qui est initialisé avec le résultat.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Appelez cette méthode uniquement sur une `IDiaSymbol` interface qui correspond à une fonction stub d’accélérateur.

## <a name="see-also"></a>Voir aussi
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
