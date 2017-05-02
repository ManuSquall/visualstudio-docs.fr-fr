---
title: "IJsDebugDataTarget::FreeVirtualMemory, m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.FreeVirtualMemory
apilocation: jscript9diag.dll
ms.assetid: ea54bad3-9ae3-436b-974d-70fc7fffefd6
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::FreeVirtualMemory, m&#233;thode
Libère et\/ou annule la validation d'une zone de mémoire dans l'espace d'adressage virtuel du processus cible.  
  
## Syntaxe  
  
```  
HRESULT FreeVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD freeType  
);  
```  
  
#### Paramètres  
 `address`  
 \[in\] Adresse dans le processus cible où la mémoire doit être libérée.  
  
 `size`  
 \[in\] Nombre d'octets pour annuler la validation.  Pour supprimer une zone de mémoire, cette valeur doit être égale à zéro.  
  
 `freeType`  
 \[in\] Indique le type d'opération libre à effectuer.  C'est généralement MEM\_RELEASE \(0x8000\) qui libère la zone spécifiée des pages.  Une fois l'opération terminée, les pages sont dans l'état libre.  MEM\_DECOMMIT \(0x4000\) peut être utilisé pour annuler la validation des pages sans les libérer.  
  
## Valeur de retour  
  
## Notes  
 Pour obtenir des informations supplémentaires, consultez l'API Win32 VirtualFree.  
  
## Configuration requise  
 **En\-tête :** jscript9diag.h  
  
## Voir aussi  
 [IJsDebugDataTarget, interface](../../winscript/reference/ijsdebugdatatarget-interface.md)