---
title: 'IJsDebug :: OpenVirtualProcess, méthode | Microsoft Docs'
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
ms.openlocfilehash: 3de39beb28a68ec3b8e0d76b17a7e914a464ecfe
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577746"
---
# <a name="ijsdebugopenvirtualprocess-method"></a>IJsDebug::OpenVirtualProcess, méthode
Méthode de fabrique utilisée pour créer un objet de processus virtuel.  
  
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
 dans ID de processus auquel le débogueur doit être attaché.  
  
 `runtimeJsBaseAddress`  
 dans Adresse de base à laquelle le runtime JavaScript a chargé dans le processus cible.  
  
 `pDataTarget`  
 dans Interface fournie par le débogueur pour interroger l’état du processus.  
  
 `ppProcess`  
 à Nouvel objet de processus de débogage  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="remarks"></a>Notes  
 Retourne E_JsDEBUG_MISMATCHED_RUNTIME si Jscript9diag et Jscript9 ne correspondent pas.  
  
## <a name="requirements"></a>spécifications  
 **En-tête :** jscript9diag. h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebug](../../winscript/reference/ijsdebug-interface.md)