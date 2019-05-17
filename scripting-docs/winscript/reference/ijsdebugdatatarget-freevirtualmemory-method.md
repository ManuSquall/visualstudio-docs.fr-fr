---
title: Méthode IJsDebugDataTarget::FreeVirtualMemory | Microsoft Docs
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
ms.openlocfilehash: bf450c03d996a47f9dcd00899ddee46b75d6df32
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583039"
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
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)