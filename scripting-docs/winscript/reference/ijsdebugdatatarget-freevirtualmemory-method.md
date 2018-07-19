---
title: Ijsdebugdatatarget::FreeVirtualMemory, méthode | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 3b53d7f80227a1c4eb0ef0293093543c09c5a367
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728739"
---
# <a name="ijsdebugdatatargetfreevirtualmemory-method"></a>IJsDebugDataTarget::FreeVirtualMemory, méthode
Libère et/ou invalider une région de mémoire dans l’espace d’adressage virtuel du processus cible.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT FreeVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD freeType  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `address`  
 [in] Adresse dans le processus cible où la mémoire doit être libérée.  
  
 `size`  
 [in] Nombre d’octets à dégagement. Pour libérer une région de mémoire, cette valeur doit être zéro.  
  
 `freeType`  
 [in] Indique le type d’opération libre à effectuer. Il s’agit généralement de MEM_RELEASE (0 x 8000), ce qui libère de la région spécifiée de pages. Après l’opération, les pages sont dans l’état disponible. MEM_DECOMMIT (0 x 4000) peut servir à la place à dégagement les pages sans les relâcher.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="remarks"></a>Remarques  
 Pour plus d’informations, consultez l’API Win32 de VirtualFree.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)