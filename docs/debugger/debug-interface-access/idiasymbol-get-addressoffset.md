---
title: IDiaSymbol::get_addressOffset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressOffset method
ms.assetid: c15639b0-7f37-46c7-891b-40273b7f6319
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5971b5d7cf55e75c3350c72575856326be62feba
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464372"
---
# <a name="idiasymbolget_addressoffset"></a>IDiaSymbol::get_addressOffset
Récupère la partie de décalage d’un emplacement d’adresse. Utilisez lorsque l' [énumération LocationType (](../../debugger/debug-interface-access/locationtype.md) a la valeur `LocIsStatic` .

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_addressOffset ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne la partie de décalage d’un emplacement d’adresse.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Remarques
 Pour les membres statiques situés dans une DLL externe, l’offset retourné par cette méthode peut être 0, car cette méthode s’appuie sur l’obtention de l’adresse virtuelle du membre. Les adresses virtuelles ne sont valides que si la méthode [IDiaSession ::p ut_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) de l’interface [IDiaSession](../../debugger/debug-interface-access/idiasession.md) a été appelée avec un paramètre différent de zéro spécifiant l’adresse de chargement de la dll.

 Pour accéder à la partie de section d’une adresse, appelez la méthode [IDiaSymbol :: get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md) .

## <a name="requirements"></a>Configuration requise

|Condition requise|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK v 7.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md)
- [IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)
- [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)