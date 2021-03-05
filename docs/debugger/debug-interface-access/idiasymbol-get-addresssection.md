---
description: Récupère la partie de section d’un emplacement d’adresse.
title: IDiaSymbol::get_addressSection | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressSection method
ms.assetid: fe80d479-3bb5-4f55-9b62-1bd58d0a60ce
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3e0b6554011a29a7b90d1d7c55deefced01b27c3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156586"
---
# <a name="idiasymbolget_addresssection"></a>IDiaSymbol::get_addressSection
Récupère la partie de section d’un emplacement d’adresse. Utilisez lorsque l' [énumération LocationType (](../../debugger/debug-interface-access/locationtype.md) a la valeur `LocIsStatic` .

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_addressSection ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne la partie de la section d’un emplacement d’adresse.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Notes
 Pour les membres statiques situés dans une DLL externe, la section retournée par cette méthode peut être 0, car cette méthode s’appuie sur l’obtention de l’adresse virtuelle du membre. Les adresses virtuelles ne sont valides que si la méthode [IDiaSession ::p ut_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) de l’interface [IDiaSession](../../debugger/debug-interface-access/idiasession.md) a été appelée avec un paramètre différent de zéro spécifiant l’adresse de chargement de la dll.

 Pour récupérer la partie offset d’une adresse, appelez la méthode [IDiaSymbol :: get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md) .

## <a name="requirements"></a>Configuration requise

|Condition requise|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK v 7.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md)
