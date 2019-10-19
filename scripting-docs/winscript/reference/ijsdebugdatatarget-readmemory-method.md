---
title: 'IJsDebugDataTarget :: ReadMemory (, méthode | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadMemory
apilocation:
- jscript9diag.dll
ms.assetid: 664e0f7d-2007-45f4-b993-36fe8b1944e5
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 84da36433cf3546b34d3e044bb113916c9798117
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572433"
---
# <a name="ijsdebugdatatargetreadmemory-method"></a>IJsDebugDataTarget::ReadMemory, méthode
Lit la mémoire du processus cible.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
 dans Adresse de base à partir de laquelle lire la mémoire du processus cible.  
  
 `flags`  
 dans Indicateurs contrôlant le comportement de ReadMemory (.  
  
 `pBuffer`  
 à Mémoire tampon qui reçoit le contenu de l’espace d’adressage du processus cible. En cas d’échec, le contenu de cette mémoire tampon n’est pas spécifié.  
  
 `size`  
 dans Nombre d’octets à lire à partir du processus.  
  
 `pBytesRead`  
 à Indique le nombre d’octets lus à partir du processus cible. Si JsDebugAllowPartialRead est Clear, en cas de réussite, cette valeur est toujours exactement égale à la taille d’entrée. Si JsDebugAllowPartialRead est spécifié, en cas de réussite, cette valeur est supérieure à zéro.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="remarks"></a>Notes  
 Retourne S_OK en cas de réussite, et les codes d’échec sont utilisés pour toute erreur. Retourne E_JsDEBUG_INVALID_MEMORY_ADDRESS si l’adresse n’est pas valide. Pour plus d’informations, consultez JsDebugAllowPartialRead.  
  
## <a name="requirements"></a>spécifications  
 **En-tête :** jscript9diag. h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)