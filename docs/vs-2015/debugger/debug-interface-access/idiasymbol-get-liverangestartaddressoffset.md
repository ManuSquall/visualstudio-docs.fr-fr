---
title: IDiaSymbol::get_liveRangeStartAddressOffset | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeStartAddressOffset
ms.assetid: f5b28914-0a14-4b22-8259-59d7f97ee610
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2ea1803e702ba7f133f9194b993464eabfcc24aa
ms.sourcegitcommit: bccc6503542e1517e0e96a9f02f5a89d69c60c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91146158"
---
# <a name="idiasymbolget_liverangestartaddressoffset"></a>IDiaSymbol::get_liveRangeStartAddressOffset
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Retourne la partie de décalage de l’adresse de début de la plage dans laquelle le symbole local est valide.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
  
## <a name="remarks"></a>Remarques  
 L’adresse formée par la section et le décalage est le début de la plage dans laquelle le symbole est valide.  
  
 Pour récupérer la partie de l’adresse de la section, utilisez [IDiaSymbol :: get_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Dia2. h  
  
 Bibliothèque : diaguids. lib  
  
 DLL : msdia100.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
