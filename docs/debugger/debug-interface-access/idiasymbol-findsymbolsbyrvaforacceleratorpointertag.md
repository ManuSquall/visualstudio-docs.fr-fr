---
description: Pour une valeur de balise correspondante donnée, cette méthode retourne une énumération des symboles contenus dans cette fonction stub à une adresse virtuelle relative spécifiée.
title: IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 024ccd78-5867-4ca7-bc26-548758e9ac53
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 05d468eca9d924fc9c87ed48e01ddee7aa9d3894
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156621"
---
# <a name="idiasymbolfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag
Pour une valeur de balise correspondante donnée, cette méthode retourne une énumération des symboles contenus dans cette fonction stub à une adresse virtuelle relative spécifiée.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findSymbolsByRVAForAcceleratorPointerTag (
   DWORD             tagValue,
   DWORD             rva,
   IDiaEnumSymbols** ppResult);
```

#### <a name="parameters"></a>Paramètres
 `tagValue`

dans Valeur de balise de pointeur pour laquelle les enregistrements de symboles de pointee sont trouvés.

 `rva`

dans RVA utilisé pour filtrer les symboles qui correspondent à la variable pointee avec la valeur de balise spécifiée.

 `ppResult`

à Pointeur vers un `IDiaEnumSymbols` pointeur d’interface qui est initialisé avec le résultat.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.

## <a name="remarks"></a>Notes
 Appelez cette méthode uniquement sur une `IDiaSymbol` interface qui correspond à une fonction stub d’accélérateur.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
