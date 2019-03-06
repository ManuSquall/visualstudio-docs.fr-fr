---
title: Méthode IJsDebug::OpenVirtualProcess | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: daa5414153ee55a431294afaf7b167ee91839bfc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093988"
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
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebug](../../winscript/reference/ijsdebug-interface.md)