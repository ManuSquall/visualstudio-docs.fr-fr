---
title: IDiaSession::findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a073cc45-0c7b-417e-b5fc-a3b08beccdbc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb1b24d24de35de30b24937a6cfbf59d12f69482
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742002"
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

dans @No__t_0 qui correspond à la fonction stub d’accélérateur dans laquelle effectuer la recherche.

 `tagValue`

dans Valeur de balise de pointeur.

 `rva`

dans Adresse virtuelle relative.

 `ppResult`

à Pointeur vers un pointeur d’interface `IDiaEnumSymbols` qui est initialisé avec le résultat.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Appelez cette méthode uniquement sur une interface `IDiaSymbol` qui correspond à une fonction stub d’accélérateur.

## <a name="see-also"></a>Voir aussi
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)