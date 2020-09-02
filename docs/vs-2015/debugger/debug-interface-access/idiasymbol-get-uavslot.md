---
title: IDiaSymbol::get_uavSlot | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: a70648f2-3b25-439f-8099-239ac602515a
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a9762b21677f0eccf39ce248b23510d72e556728
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151446"
---
# <a name="idiasymbolget_uavslot"></a>IDiaSymbol::get_uavSlot
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère l’emplacement UAV.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT get_uavSlot(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 à Pointeur vers un `DWORD` qui contient l’emplacement UAV.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
