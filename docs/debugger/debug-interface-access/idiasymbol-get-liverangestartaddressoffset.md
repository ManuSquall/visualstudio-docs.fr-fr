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
ms.openlocfilehash: a3a7bf8786f2ca066248ada3f1a0473b85681315
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986993"
---
# <a name="idiasymbolgetliverangestartaddressoffset"></a>IDiaSymbol::get_liveRangeStartAddressOffset
Retourne la partie décalage de l’adresse de départ de la plage dans laquelle le symbole local est valide.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_liveRangeStartAddressOffset (   
   DWORD* offset  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `offset`  
 [out] Retourne la partie décalage de la plage d’adresses de départ.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
> [!NOTE]
>  Un code d’erreur renvoyé signifie que le symbole n’a pas d’informations sur la plage dynamique.  
  
## <a name="remarks"></a>Notes  
 L’adresse formée par la section et le décalage est le début de la plage dans laquelle le symbole est valide.  
  
 Pour obtenir la partie de la section de l’adresse, utilisez [IDiaSymbol::get_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Dia2.h  
  
 Bibliothèque : diaguids.lib  
  
 DLL : msdia100.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)