---
title: Méthode IJsDebugDataTarget::AllocateVirtualMemory | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.AllocateVirtualMemory
apilocation:
- jscript9diag.dll
ms.assetid: 1d3a77b0-c1de-4a0c-a759-3e0c68fd96dd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c04bf21882ec39054c74f060eaa2c6f65ac0b4d6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583065"
---
# <a name="ijsdebugdatatargetallocatevirtualmemory-method"></a>IJsDebugDataTarget::AllocateVirtualMemory, méthode
Réserve et/ou valide une région de mémoire dans l’espace d’adressage virtuel du processus cible.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT AllocateVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD allocationType,  
   DWORD pageProtection,  
   UINT64 *pAllocatedAddress  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `address`  
 [in] L’adresse dans le processus cible où la mémoire doit être validée ou réservée. Cette valeur est généralement zéro, dans lequel cas le système choisit une adresse.  
  
 `size`  
 [in] La taille de la région de mémoire à allouer, en octets. Le système arrondira automatiquement jusqu'à à la limite de page suivante.  
  
 `allocationType`  
 [in] Indique le type d’allocation à effectuer. C’est généralement MEM_COMMIT &#124; MEM_RESERVE (0 x 3000) qui et valide une allocation en une seule étape.  
  
 `pageProtection`  
 [in] La protection de la mémoire pour la région de pages à allouer. Si les pages sont validées, vous pouvez spécifier l’une des constantes de protection de mémoire (par exemple, PAGE_READWRITE, PAGE_EXECUTE).  
  
 `pAllocatedAddress`  
 [out] Adresse de base de la zone allouée des pages.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="remarks"></a>Notes  
 La fonction initialise la mémoire allouée à zéro, sauf si MEM_RESET est utilisé. Pour plus d’informations, consultez l’API Win32 VirtualAlloc.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)