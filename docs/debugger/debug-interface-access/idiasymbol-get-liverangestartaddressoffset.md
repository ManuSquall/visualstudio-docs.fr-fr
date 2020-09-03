---
title: IDiaSymbol::get_liveRangeStartAddressOffset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeStartAddressOffset
ms.assetid: f5b28914-0a14-4b22-8259-59d7f97ee610
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2563afe5c5323415c5d4c9d7f0b0fa89583f9736
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85463035"
---
# <a name="idiasymbolget_liverangestartaddressoffset"></a>IDiaSymbol::get_liveRangeStartAddressOffset
Retourne la partie de décalage de l’adresse de début de la plage dans laquelle le symbole local est valide.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_liveRangeStartAddressOffset ( 
   DWORD* offset
);
```

#### <a name="parameters"></a>Paramètres
 `offset`

à Retourne la partie de décalage de la plage d’adresses de début.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

> [!NOTE]
> Un code d’erreur retourné signifie que le symbole n’a pas d’informations de plage active.

## <a name="remarks"></a>Notes
 L’adresse formée par la section et le décalage est le début de la plage dans laquelle le symbole est valide.

 Pour récupérer la partie de l’adresse de la section, utilisez [IDiaSymbol :: get_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md).

## <a name="requirements"></a>Configuration requise
 En-tête : Dia2. h

 Bibliothèque : diaguids. lib

 DLL : msdia100.dll

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)