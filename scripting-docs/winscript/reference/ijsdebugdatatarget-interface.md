---
title: Interface IJsDebugDataTarget | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a9b784d6-958f-4d55-b3f6-c2d6b260a16b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 85c77209230abfe261c9ec0b884ad0a677cfbf07
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572449"
---
# <a name="ijsdebugdatatarget-interface"></a>IJsDebugDataTarget, interface
Implémenté par le débogueur pour fournir des fonctionnalités permettant d’accéder et de modifier l’état du processus du débogueur cible.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
IJsDebugDataTarget : public IUnknown;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Name|Description|  
|----------|-----------------|  
|[Méthode IJsDebugDataTarget::AllocateVirtualMemory](../../winscript/reference/ijsdebugdatatarget-allocatevirtualmemory-method.md)|Réserve et/ou valide une zone de mémoire dans l’espace d’adressage virtuel du processus cible.|  
|[Méthode IJsDebugDataTarget::CreateStackFrameEnumerator](../../winscript/reference/ijsdebugdatatarget-createstackframeenumerator-method.md)|Crée un énumérateur pour les frames de pile.|  
|[Méthode IJsDebugDataTarget::FreeVirtualMemory](../../winscript/reference/ijsdebugdatatarget-freevirtualmemory-method.md)|Libère et/ou annule la validation d’une région de mémoire dans l’espace d’adressage virtuel du processus cible.|  
|[Méthode IJsDebugDataTarget::GetThreadContext](../../winscript/reference/ijsdebugdatatarget-getthreadcontext-method.md)|Récupère le contexte du thread donné.|  
|[Méthode IJsDebugDataTarget::GetTlsValue](../../winscript/reference/ijsdebugdatatarget-gettlsvalue-method.md)|Pour le thread en cours de débogage, récupère la valeur de l’emplacement de stockage local des threads (TLS) pour l’index TLS spécifié.|  
|[Méthode IJsDebugDataTarget::ReadBSTR](../../winscript/reference/ijsdebugdatatarget-readbstr-method.md)|Lit un BSTR à partir de la cible de débogage.|  
|[Méthode IJsDebugDataTarget::ReadMemory](../../winscript/reference/ijsdebugdatatarget-readmemory-method.md)|Lit la mémoire du processus cible.|  
|[Méthode IJsDebugDataTarget::ReadNullTerminatedString](../../winscript/reference/ijsdebugdatatarget-readnullterminatedstring-method.md)|Lit le nombre spécifié de caractères à partir de la cible.|  
|[Méthode IJsDebugDataTarget::WriteMemory](../../winscript/reference/ijsdebugdatatarget-writememory-method.md)|Lit la mémoire du processus cible.|  
  
## <a name="requirements"></a>spécifications  
 **En-tête :** jscript9diag. h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence d’interfaces de script Windows](../../winscript/reference/windows-script-interfaces-reference.md)