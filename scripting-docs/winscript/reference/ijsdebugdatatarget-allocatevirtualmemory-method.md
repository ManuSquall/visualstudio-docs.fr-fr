---
title: "IJsDebugDataTarget::AllocateVirtualMemory, m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.AllocateVirtualMemory
apilocation: jscript9diag.dll
ms.assetid: 1d3a77b0-c1de-4a0c-a759-3e0c68fd96dd
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::AllocateVirtualMemory, m&#233;thode
Réserve et\/ou valide une zone de mémoire dans l'espace d'adressage virtuel du processus cible.  
  
## Syntaxe  
  
```  
HRESULT AllocateVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD allocationType,  
   DWORD pageProtection,  
   UINT64 *pAllocatedAddress  
);  
```  
  
#### Paramètres  
 `address`  
 \[in\] Adresse dans le processus cible où la mémoire doit être validée ou réservée.  Cette valeur est généralement zéro, auquel cas le système choisit une adresse.  
  
 `size`  
 \[in\] Taille d'allocation de la région de mémoire, en octets.  Le système arrondira automatiquement jusqu'à la limite de page suivante.  
  
 `allocationType`  
 \[in\] Indique le type d'allocation à effectuer.  C'est généralement MEM\_COMMIT &#124; MEM\_RESERVE \(0x3000\) qui sauvegarde et valide une allocation dans une étape.  
  
 `pageProtection`  
 \[in\] Protection de la mémoire pour la région de pages à allouer.  Si les pages sont en cours de validation, vous pouvez spécifier l'une des constantes de protection de la mémoire \(par exemple, PAGE\_READWRITE, PAGE\_EXECUTE\).  
  
 `pAllocatedAddress`  
 \[out\] Adresse de base de la zone allouée des pages.  
  
## Valeur de retour  
  
## Notes  
 La fonction initialise la mémoire qu'elle alloue à zéro, sauf si MEM\_RESET est utilisé.  Pour obtenir des informations supplémentaires, consultez l'API Win32 VirtualAlloc.  
  
## Configuration requise  
 **En\-tête :** jscript9diag.h  
  
## Voir aussi  
 [IJsDebugDataTarget, interface](../../winscript/reference/ijsdebugdatatarget-interface.md)