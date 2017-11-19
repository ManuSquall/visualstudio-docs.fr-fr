---
title: "Ijsdebugdatatarget::GetTLSValue, méthode | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.GetTlsValue
apilocation: jscript9diag.dll
ms.assetid: db575be9-7b24-45c5-9008-e4f2f76d6757
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4205adfb24a1a64d4e90f3fdcaf5a5ecbc4028de
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetgettlsvalue-method"></a>IJsDebugDataTarget::GetTlsValue, méthode
Pour le thread en cours de débogage, récupère la valeur de l’emplacement de stockage local (TLS) de thread pour l’index spécifié de TLS.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetTlsValue(  
   DWORD threadId,  
   UINT32 tlsIndex,  
   UINT64 *pValue  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `threadId`  
 [in] Thread en cours d’exécution dans le processus cible à lire.  
  
 `tlsIndex`  
 [in] L’index TLS qui a été allouée lorsque le processus cible a appelé la fonction TlsAlloc.  
  
 `pValue`  
 [out] La valeur de taille d’un pointeur qui a été stockée dans l’emplacement de thread TLS. Le thread cible est 32 bits, les supérieurs 32 bits de cette valeur correspond à zéro.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="remarks"></a>Remarques  
 Chaque thread d’un processus possède son propre emplacement pour chaque index TLS.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)