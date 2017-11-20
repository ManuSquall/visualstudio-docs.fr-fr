---
title: IDiaSymbol::get_liveRangeStartAddressSection | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_liveRangeStartAddressSection
ms.assetid: 892b80ff-5957-4233-b4d7-6144167be289
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 01bd3d099bc714aa20a9066c414b4222d3894f5e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
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
 [out] Retourne la partie de la section de la plage d’adresses départ.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
> [!NOTE]
>  Un code d’erreur signifie que le symbole n’a pas d’informations sur la plage dynamique.  
  
## <a name="remarks"></a>Remarques  
 L’adresse formée par la section et le décalage est le début de la plage dans laquelle le symbole est valide.  
  
 Pour obtenir la partie décalage de l’adresse, utilisez [IDiaSymbol::get_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Dia2.h  
  
 Bibliothèque : diaguids.lib  
  
 DLL : msdia100.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)