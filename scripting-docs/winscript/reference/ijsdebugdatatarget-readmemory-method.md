---
title: "IJsDebugDataTarget::ReadMemory, m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.ReadMemory
apilocation: jscript9diag.dll
ms.assetid: 664e0f7d-2007-45f4-b993-36fe8b1944e5
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::ReadMemory, m&#233;thode
Lit la mémoire du processus cible.  
  
## Syntaxe  
  
```  
HRESULT ReadMemory(  
   UINT64 address,  
   JsDebugReadMemoryFlags flags,  
   BYTE *pBuffer,  
   DWORD size,  
   DWORD *pBytesRead  
);  
```  
  
#### Paramètres  
 `address`  
 \[in\] Adresse de base à partir de laquelle lire la mémoire du processus cible.  
  
 `flags`  
 \[in\] Indicateurs contrôlant le comportement de ReadMemory.  
  
 `pBuffer`  
 \[out\] Mémoire tampon qui reçoit le contenu de l'espace d'adressage du processus cible.  En cas d'échec, le contenu de cette mémoire tampon n'est pas spécifié.  
  
 `size`  
 \[in\] Nombre d'octets à lire à partir du processus.  
  
 `pBytesRead`  
 \[out\] Indique le nombre d'octets lus à partir du processus cible.  Si JsDebugAllowPartialRead est désactivé, en cas de réussite, cette valeur est toujours exactement égale à la taille d'entrée.  Si JsDebugAllowPartialRead est spécifié, en cas de réussite, cette valeur est supérieure à zéro.  
  
## Valeur de retour  
  
## Notes  
 Retourne S\_OK en cas de réussite, et les codes d'échec sont utilisés pour une erreur.  Retourne E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS si l'adresse n'est pas valide.  Pour plus d'informations, consultez JsDebugAllowPartialRead.  
  
## Configuration requise  
 **En\-tête :** jscript9diag.h  
  
## Voir aussi  
 [IJsDebugDataTarget, interface](../../winscript/reference/ijsdebugdatatarget-interface.md)