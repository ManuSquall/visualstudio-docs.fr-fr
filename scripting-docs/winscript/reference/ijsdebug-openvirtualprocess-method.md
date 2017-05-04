---
title: "IJsDebug::OpenVirtualProcess, m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJSDebug.OpenVirtualProcess
apilocation: jscript9diag.dll
ms.assetid: 5612bf1b-a4e3-4eaf-ac5e-c2e1f147c395
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebug::OpenVirtualProcess, m&#233;thode
Méthode de fabrique utilisée pour créer un objet processus virtuel.  
  
## Syntaxe  
  
```  
 HRESULT OpenVirtualProcess(  
   DWORD processId,  
   UINT64 runtimeJsBaseAddress,  
   IJsDebugDataTarget *pDataTarget,  
   IJsDebugProcess **ppProcess  
);  
```  
  
#### Paramètres  
 `processId`  
 \[in\] ID de processus auquel associer le débogueur.  
  
 `runtimeJsBaseAddress`  
 \[in\] Adresse de base à laquelle le runtime JavaScript s'est chargé dans le processus cible.  
  
 `pDataTarget`  
 \[in\] Interface fournie par le débogueur pour demander l'état du processus.  
  
 `ppProcess`  
 \[out\] Nouvel objet de processus de débogage  
  
## Valeur de retour  
  
## Notes  
 Retourne E\_JsDEBUG\_MISMATCHED\_RUNTIME si Jscript9diag et Jscript9 ne correspondent pas.  
  
## Configuration requise  
 **En\-tête :** jscript9diag.h  
  
## Voir aussi  
 [IJsDebug, interface](../../winscript/reference/ijsdebug-interface.md)