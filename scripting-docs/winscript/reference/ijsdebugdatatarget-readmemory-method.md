---
title: "Ijsdebugdatatarget::ReadMemory, méthode | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.ReadMemory
apilocation: jscript9diag.dll
ms.assetid: 664e0f7d-2007-45f4-b993-36fe8b1944e5
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fc1b67b33e17761a675d6ced9e175b4206ede2e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetreadmemory-method"></a>IJsDebugDataTarget::ReadMemory, méthode
Lit la mémoire du processus cible.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ReadMemory(  
   UINT64 address,  
   JsDebugReadMemoryFlags flags,  
   BYTE *pBuffer,  
   DWORD size,  
   DWORD *pBytesRead  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `address`  
 [in] L’adresse de base à partir duquel lire la mémoire du processus de la cible.  
  
 `flags`  
 [in] Indicateurs de contrôle du comportement de ReadMemory.  
  
 `pBuffer`  
 [out] Une mémoire tampon qui reçoit le contenu à partir de l’espace d’adressage du processus cible. En cas d’échec, le contenu de cette mémoire tampon n’est pas spécifié.  
  
 `size`  
 [in] Le nombre d’octets à lire à partir du processus.  
  
 `pBytesRead`  
 [out] Indique le nombre d’octets lus à partir du processus cible. Si JsDebugAllowPartialRead est désactivée, en cas de réussite cette valeur sera toujours exactement égale à la taille d’entrée. Si JsDebugAllowPartialRead est spécifié, en cas de réussite, cette valeur sera supérieure à zéro.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="remarks"></a>Remarques  
 Retourne S_OK de réussite et les codes d’erreur est utilisées pour toutes les erreurs. Retourne E_JsDEBUG_INVALID_MEMORY_ADDRESS si l’adresse n’est pas valide. Pour plus d’informations, consultez la rubrique JsDebugAllowPartialRead.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)