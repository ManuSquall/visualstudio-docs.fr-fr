---
title: IDiaSymbol::get_targetRelativeVirtualAddress | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_targetRelativeVirtualAddress method
ms.assetid: 49a159f3-6943-44d3-90a3-0dba51e8a7ec
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2b472b7a92f7b8e56aa8cfaaba52829812694823
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839997"
---
# <a name="idiasymbolget_targetrelativevirtualaddress"></a>IDiaSymbol::get_targetRelativeVirtualAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère l’adresse virtuelle relative (RVA) d’une cible de thunk.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_targetRelativeVirtualAddress (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 à Retourne l’adresse RVA d’une cible de thunk.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="remarks"></a>Remarques  
 Cette propriété est valide uniquement si le symbole est une valeur d' [énumération SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) de `SymTagThunk` .  
  
 Un « thunk » est un morceau de code qui convertit un espace d’adressage de mémoire de 32 bits (également connu sous le nom d’espace d’adressage fixe) et un espace d’adressage 16 bits (appelé espace d’adressage segmenté).  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)
