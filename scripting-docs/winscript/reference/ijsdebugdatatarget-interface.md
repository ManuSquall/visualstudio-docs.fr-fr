---
title: "IJsDebugDataTarget, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: a9b784d6-958f-4d55-b3f6-c2d6b260a16b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget, interface
Implémenté par le débogueur pour fournir des fonctionnalités permettant d'accéder et de modifier l'état du processus de débogueur cible.  
  
## Syntaxe  
  
```  
IJsDebugDataTarget : public IUnknown;  
```  
  
## Membres  
  
### Méthodes publiques  
  
|Nom|Description|  
|---------|-----------------|  
|[IJsDebugDataTarget::AllocateVirtualMemory, méthode](../../winscript/reference/ijsdebugdatatarget-allocatevirtualmemory-method.md)|Réserve et\/ou valide une zone de mémoire dans l'espace d'adressage virtuel du processus cible.|  
|[IJsDebugDataTarget::CreateStackFrameEnumerator, méthode](../../winscript/reference/ijsdebugdatatarget-createstackframeenumerator-method.md)|Crée un énumérateur pour les frames de pile.|  
|[IJsDebugDataTarget::FreeVirtualMemory, méthode](../../winscript/reference/ijsdebugdatatarget-freevirtualmemory-method.md)|Libère et\/ou annule la validation d'une zone de mémoire dans l'espace d'adressage virtuel du processus cible.|  
|[IJsDebugDataTarget::GetThreadContext, méthode](../../winscript/reference/ijsdebugdatatarget-getthreadcontext-method.md)|Récupère le contexte pour un thread donné.|  
|[IJsDebugDataTarget::GetTlsValue, méthode](../../winscript/reference/ijsdebugdatatarget-gettlsvalue-method.md)|Pour le thread débogué, extrait la valeur de l'emplacement du stockage local des threads \(TLS\) pour l'index TLS spécifié.|  
|[IJsDebugDataTarget::ReadBSTR, méthode](../../winscript/reference/ijsdebugdatatarget-readbstr-method.md)|Lit un BSTR à partir de la cible de débogage.|  
|[IJsDebugDataTarget::ReadMemory, méthode](../../winscript/reference/ijsdebugdatatarget-readmemory-method.md)|Lit la mémoire du processus cible.|  
|[IJsDebugDataTarget::ReadNullTerminatedString, méthode](../../winscript/reference/ijsdebugdatatarget-readnullterminatedstring-method.md)|Lit le nombre de caractères spécifié à partir de la cible.|  
|[IJsDebugDataTarget::WriteMemory, méthode](../../winscript/reference/ijsdebugdatatarget-writememory-method.md)|Lit la mémoire du processus cible.|  
  
## Configuration requise  
 **En\-tête :** jscript9diag.h  
  
## Voir aussi  
 [Interfaces Windows Script, référence](../../winscript/reference/windows-script-interfaces-reference.md)