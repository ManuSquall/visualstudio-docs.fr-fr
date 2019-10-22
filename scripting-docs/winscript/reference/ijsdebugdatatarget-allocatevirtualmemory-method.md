---
title: 'IJsDebugDataTarget :: AllocateVirtualMemory, méthode | Microsoft Docs'
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
ms.openlocfilehash: 30ad8a3eb277823271fbfb4c2e10364b8602775c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577645"
---
# <a name="ijsdebugdatatargetallocatevirtualmemory-method"></a>IJsDebugDataTarget::AllocateVirtualMemory, méthode
Réserve et/ou valide une zone de mémoire dans l’espace d’adressage virtuel du processus cible.  
  
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
 dans Adresse dans le processus cible où la mémoire doit être validée ou réservée. Cette valeur est généralement zéro, auquel cas le système choisit une adresse.  
  
 `size`  
 dans Taille de la zone de mémoire à allouer, en octets. Le système arrondit automatiquement à la limite de page suivante.  
  
 `allocationType`  
 dans Indique le type d’allocation à effectuer. Il s’agit généralement &#124; de MEM_COMMIT MEM_RESERVE (0x3000) qui réserve et valide une allocation en une seule étape.  
  
 `pageProtection`  
 dans Protection de la mémoire pour la région de pages à allouer. Si les pages sont en cours de validation, vous pouvez spécifier l’une des constantes de protection de la mémoire (par exemple, PAGE_READWRITE, PAGE_EXECUTE).  
  
 `pAllocatedAddress`  
 à Adresse de base de la région allouée de pages.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="remarks"></a>Notes  
 La fonction initialise la mémoire qu’elle alloue à zéro, sauf si MEM_RESET est utilisé. Pour plus d’informations, consultez l’API Win32 VirtualAlloc.  
  
## <a name="requirements"></a>spécifications  
 **En-tête :** jscript9diag. h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)