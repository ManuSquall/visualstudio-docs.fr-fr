---
title: IDiaSymbol::get_liveRangeStartAddressSection | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeStartAddressSection
ms.assetid: 892b80ff-5957-4233-b4d7-6144167be289
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c99b5a14a321a28bdbe7337dcc7cdfa5febdad5d
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "64786528"
---
# <a name="idiasymbolgetliverangestartaddresssection"></a>IDiaSymbol::get_liveRangeStartAddressSection
Retourne la partie de la section de l’adresse de départ de la plage dans laquelle le symbole local est valide.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_liveRangeStartAddressSection ( 
   DWORD* section
);
```

#### <a name="parameters"></a>Paramètres
 `section`

[out] Retourne la partie de la section de la plage d’adresses de départ.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

> [!NOTE]
> Un code d’erreur renvoyé signifie que le symbole n’a pas d’informations sur la plage dynamique.

## <a name="remarks"></a>Notes
 L’adresse formée par la section et le décalage est le début de la plage dans laquelle le symbole est valide.

 Pour obtenir la partie décalage de l’adresse, utilisez [IDiaSymbol::get_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md).

## <a name="requirements"></a>Configuration requise
 En-tête : Dia2.h

 Bibliothèque : diaguids.lib

 DLL : msdia100.dll

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)