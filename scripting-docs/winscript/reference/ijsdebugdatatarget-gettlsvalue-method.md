---
title: "IJsDebugDataTarget::GetTlsValue, m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.GetTlsValue
apilocation: jscript9diag.dll
ms.assetid: db575be9-7b24-45c5-9008-e4f2f76d6757
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::GetTlsValue, m&#233;thode
Pour le thread débogué, extrait la valeur de l'emplacement du stockage local des threads \(TLS\) pour l'index TLS spécifié.  
  
## Syntaxe  
  
```  
HRESULT GetTlsValue(  
   DWORD threadId,  
   UINT32 tlsIndex,  
   UINT64 *pValue  
);  
```  
  
#### Paramètres  
 `threadId`  
 \[in\] Thread s'exécutant dans le processus cible où lire.  
  
 `tlsIndex`  
 \[in\] L'index TLS qui a été alloué lors de l'appel de la fonction TlsAlloc par le processus cible.  
  
 `pValue`  
 \[out\] Valeur à taille de pointeur qui a été enregistrée dans l'emplacement TLS du thread.  Si le thread cible est 32 bits, le thread 32 bits supérieur de cette valeur est zéro.  
  
## Valeur de retour  
  
## Notes  
 Chaque thread d'un processus possède son propre emplacement pour chaque index TLS.  
  
## Configuration requise  
 **En\-tête :** jscript9diag.h  
  
## Voir aussi  
 [IJsDebugDataTarget, interface](../../winscript/reference/ijsdebugdatatarget-interface.md)