---
title: Méthode IJsDebugDataTarget::FreeVirtualMemory | Microsoft Docs
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
ms.openlocfilehash: ed5fabfca8ac9b0e9fe0dfba346b0354f4c0576f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086799"
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
 [in] Adresse dans le processus cible où la mémoire doit être libérée.  
  
 `size`  
 [in] Nombre d’octets pour annuler la validation. Pour supprimer une zone de mémoire, cette valeur doit être égal à zéro.  
  
 `freeType`  
 [in] Indique le type d’opération libre à effectuer. Il s’agit généralement MEM_RELEASE (0 x 8000), ce qui libère de la région spécifiée de pages. Après l’opération, les pages sont dans l’état libre. MEM_DECOMMIT (0 x 4000) peut être utilisé pour annuler la validation les pages sans les relâcher.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez l’API Win32 VirtualFree.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)