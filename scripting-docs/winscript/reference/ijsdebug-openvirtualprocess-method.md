---
title: Méthode IJsDebug::OpenVirtualProcess | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebug.OpenVirtualProcess
apilocation:
- jscript9diag.dll
ms.assetid: 5612bf1b-a4e3-4eaf-ac5e-c2e1f147c395
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 97a055bf1550d74dc6b86d93ffdb9ca406afb43d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583592"
---
# <a name="ijsdebugopenvirtualprocess-method"></a>IJsDebug::OpenVirtualProcess, méthode
Méthode de fabrique utilisé pour créer un nouvel objet processus virtuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OpenVirtualProcess(  
   DWORD processId,  
   UINT64 runtimeJsBaseAddress,  
   IJsDebugDataTarget *pDataTarget,  
   IJsDebugProcess **ppProcess  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `processId`  
 [in] Id de processus à attacher le débogueur.  
  
 `runtimeJsBaseAddress`  
 [in] L’adresse de base à laquelle le runtime JavaScript a chargé dans le processus cible.  
  
 `pDataTarget`  
 [in] Interface fournie pour interroger l’état du processus du débogueur.  
  
 `ppProcess`  
 [out] Nouvel objet de processus de débogage  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="remarks"></a>Notes  
 Retourne E_JsDEBUG_MISMATCHED_RUNTIME si Jscript9diag et Jscript9 ne correspondent pas.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebug](../../winscript/reference/ijsdebug-interface.md)