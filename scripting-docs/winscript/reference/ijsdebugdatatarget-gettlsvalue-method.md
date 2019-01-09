---
title: Méthode IJsDebugDataTarget::GetTlsValue | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 8f81e9ea6cca9bf54753a496e07903d23bb913fc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095327"
---
# <a name="ijsdebugdatatargetgettlsvalue-method"></a>IJsDebugDataTarget::GetTlsValue, méthode
Pour le thread en cours de débogage, récupère la valeur dans l’emplacement de stockage local (TLS) de thread pour l’index TLS spécifié.  
  
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
 [in] En cours d’exécution dans le processus cible pour lire à partir du thread.  
  
 `tlsIndex`  
 [in] L’index TLS qui a été alloué lorsque le processus cible a appelé la fonction TlsAlloc.  
  
 `pValue`  
 [out] La valeur de taille d’un pointeur qui a été stockée dans l’emplacement de thread TLS. Si le thread cible est 32 bits, les 32 bits supérieur de cette valeur sera égal à zéro.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="remarks"></a>Notes  
 Chaque thread d’un processus possède son propre emplacement pour chaque index TLS.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)