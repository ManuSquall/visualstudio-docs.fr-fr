---
title: IDiaSymbol::get_slot | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_slot method
ms.assetid: 97e405b8-483f-4da0-91e7-ca4d88251ecd
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b668d11c48185d8daac5d8b17ff8848e5f9c1fd6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839685"
---
# <a name="idiasymbolget_slot"></a>IDiaSymbol::get_slot
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère le numéro d’emplacement de l’emplacement. Utilisez lorsque l' [énumération LocationType (](../../debugger/debug-interface-access/locationtype.md) est `LocIsSlot` .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_slot (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 à Retourne le numéro d’emplacement de l’emplacement.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md)
