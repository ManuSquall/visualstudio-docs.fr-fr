---
title: "Ijsdebugdatatarget::WriteMemory, méthode | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.WriteMemory
apilocation: jscript9diag.dll
ms.assetid: 0d3c04c3-9ef8-4842-a145-3d29bca75062
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed562c1cbdd645da6cca87e45f272c25f8bc0d4b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetwritememory-method"></a>IJsDebugDataTarget::WriteMemory, méthode
Lit la mémoire du processus cible.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT WriteMemory(  
   UINT64 address,  
   const BYTE *pMemory,  
   DWORD size  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `address`  
 [in] L’adresse de base à partir de laquelle écrire la mémoire du processus de la cible.  
  
 `pMemory`  
 [in] Les données à écrire dans l’espace d’adressage du processus spécifié.  
  
 `size`  
 [in] Nombre d’octets à écrire dans le processus.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="remarks"></a>Remarques  
 Avant le transfert de données se produit, le système vérifie que toutes les données de l’adresse de base et de la mémoire de la taille spécifiée est accessible en écriture, et si elle n’est pas accessible, la fonction génère une erreur de E_JsDEBUG_INVALID_MEMORY_ADDRESS.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)