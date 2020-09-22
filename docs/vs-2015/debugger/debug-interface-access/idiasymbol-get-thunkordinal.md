---
title: IDiaSymbol::get_thunkOrdinal | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_thunkOrdinal method
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 540eb49b215d06127a47df1defc436a0a307aa6d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839357"
---
# <a name="idiasymbolget_thunkordinal"></a>IDiaSymbol::get_thunkOrdinal
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère le type de thunk d’une fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_thunkOrdinal (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 à Retourne une valeur de l’énumération d' [énumération THUNK_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md) qui spécifie le type de THUNK d’une fonction.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="remarks"></a>Remarques  
 Cette propriété est valide uniquement si le symbole est une valeur d' [énumération SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) de `SymTagThunk` .  
  
 Un « thunk » est un morceau de code qui convertit un espace d’adressage de mémoire de 32 bits (également connu sous le nom d’espace d’adressage fixe) et un espace d’adressage 16 bits (appelé espace d’adressage segmenté).  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Énumération THUNK_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md)   
 [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)
