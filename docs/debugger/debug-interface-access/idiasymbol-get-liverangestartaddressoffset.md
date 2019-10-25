---
title: IDiaSymbol::get_liveRangeStartAddressOffset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: b39bf1e73d8b056c1cfcbfafd41dcbbb464c40ce
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739919"
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

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur.

> [!NOTE]
> Un code d’erreur retourné signifie que le symbole n’a pas d’informations de plage active.

## <a name="remarks"></a>Notes
 L’adresse formée par la section et le décalage est le début de la plage dans laquelle le symbole est valide.

 Pour récupérer la partie de l’adresse de la section, utilisez [IDiaSymbol :: get_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md).

## <a name="requirements"></a>spécifications
 En-tête : Dia2. h

 Bibliothèque : diaguids. lib

 DLL : msdia100. dll

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)