---
title: 'IJsDebugDataTarget :: GetTLSValue,, méthode | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.GetTlsValue
apilocation:
- jscript9diag.dll
ms.assetid: db575be9-7b24-45c5-9008-e4f2f76d6757
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eecf9acf370656d5310a03d68ed74e10671a0bc2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577605"
---
# <a name="ijsdebugdatatargetgettlsvalue-method"></a>IJsDebugDataTarget::GetTlsValue, méthode
Pour le thread en cours de débogage, récupère la valeur de l’emplacement de stockage local des threads (TLS) pour l’index TLS spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetTlsValue(  
   DWORD threadId,  
   UINT32 tlsIndex,  
   UINT64 *pValue  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `threadId`  
 dans Thread s’exécutant dans le processus cible à lire.  
  
 `tlsIndex`  
 dans Index TLS qui a été alloué lorsque le processus cible a appelé la fonction TlsAlloc.  
  
 `pValue`  
 à Valeur de taille de pointeur qui a été stockée dans l’emplacement TLS du thread. Si le thread cible est 32 bits, les 32 bits supérieurs de cette valeur seront nuls.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="remarks"></a>Notes  
 Chaque thread d’un processus possède son propre emplacement pour chaque index TLS.  
  
## <a name="requirements"></a>spécifications  
 **En-tête :** jscript9diag. h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)