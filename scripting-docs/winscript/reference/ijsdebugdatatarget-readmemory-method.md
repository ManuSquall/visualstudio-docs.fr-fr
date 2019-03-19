---
title: Méthode IJsDebugDataTarget::ReadMemory | Microsoft Docs
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
ms.openlocfilehash: 705fff3bf2d4be78897c18c5a4c61bd74a8c2230
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58147759"
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
 [in] L’adresse de base à partir duquel lire la cible mémoire du processus.  
  
 `flags`  
 [in] Indicateurs contrôlant le comportement de ReadMemory.  
  
 `pBuffer`  
 [out] Une mémoire tampon qui reçoit le contenu de l’espace d’adressage du processus cible. En cas d’échec, le contenu de cette mémoire tampon n’est pas spécifié.  
  
 `size`  
 [in] Le nombre d’octets à lire à partir du processus.  
  
 `pBytesRead`  
 [out] Indique le nombre d’octets lus à partir du processus cible. Si JsDebugAllowPartialRead est désactivé, en cas de réussite cette valeur sera toujours exactement égale à la taille d’entrée. Si JsDebugAllowPartialRead est spécifié, en cas de réussite, cette valeur sera supérieure à zéro.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="remarks"></a>Notes  
 Retourne S_OK en cas de réussite et les codes d’échec est utilisés pour une erreur. Retourne E_JsDEBUG_INVALID_MEMORY_ADDRESS si l’adresse n’est pas valide. Pour plus d’informations, consultez JsDebugAllowPartialRead.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)