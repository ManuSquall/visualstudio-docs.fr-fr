---
title: Méthode IJsDebugDataTarget::AllocateVirtualMemory | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 4eaf448e0be224f853674084a18f7aa2a6bd5ed7
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086911"
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
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)