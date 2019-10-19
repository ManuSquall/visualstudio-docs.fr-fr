---
title: 'IJsDebugDataTarget :: FreeVirtualMemory, méthode | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.FreeVirtualMemory
apilocation:
- jscript9diag.dll
ms.assetid: ea54bad3-9ae3-436b-974d-70fc7fffefd6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 835302249e95c89625c07c6d1ef3d7cbaf2905e8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577617"
---
# <a name="ijsdebugdatatargetfreevirtualmemory-method"></a>IJsDebugDataTarget::FreeVirtualMemory, méthode
Libère et/ou annule la validation d’une région de mémoire dans l’espace d’adressage virtuel du processus cible.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT FreeVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD freeType  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `address`  
 dans Adresse dans le processus cible où la mémoire doit être libérée.  
  
 `size`  
 dans Nombre d’octets à dévalider. Pour libérer une région de mémoire, cette valeur doit être égale à zéro.  
  
 `freeType`  
 dans Indique le type d’opération libre à effectuer. Il s’agit généralement de MEM_RELEASE (0x8000), qui libère la région de pages spécifiée. Après l’opération, les pages sont dans l’État libre. MEM_DECOMMIT (0x4000) peut être utilisé à la place pour désengager les pages sans les libérer.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez l’API Win32 VirtualFree.  
  
## <a name="requirements"></a>spécifications  
 **En-tête :** jscript9diag. h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)