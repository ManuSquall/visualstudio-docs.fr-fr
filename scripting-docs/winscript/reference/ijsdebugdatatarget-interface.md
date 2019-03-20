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
ms.openlocfilehash: 3cbb4b0b54fb9a3821d3033ef0e65fd0bafbc246
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159283"
---
# <a name="ijsdebugdatatarget-interface"></a>IJsDebugDataTarget, interface
Implémenté par le débogueur pour fournir des fonctionnalités permettant d’accéder et de modifier l’état du processus de débogueur cible.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
IJsDebugDataTarget : public IUnknown;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[Méthode IJsDebugDataTarget::AllocateVirtualMemory](../../winscript/reference/ijsdebugdatatarget-allocatevirtualmemory-method.md)|Réserve et/ou valide une région de mémoire dans l’espace d’adressage virtuel du processus cible.|  
|[Méthode IJsDebugDataTarget::CreateStackFrameEnumerator](../../winscript/reference/ijsdebugdatatarget-createstackframeenumerator-method.md)|Crée un énumérateur pour les frames de pile.|  
|[Méthode IJsDebugDataTarget::FreeVirtualMemory](../../winscript/reference/ijsdebugdatatarget-freevirtualmemory-method.md)|Libère et/ou annule la validation d’une région de mémoire dans l’espace d’adressage virtuel du processus cible.|  
|[Méthode IJsDebugDataTarget::GetThreadContext](../../winscript/reference/ijsdebugdatatarget-getthreadcontext-method.md)|Récupère le contexte pour un thread donné.|  
|[Méthode IJsDebugDataTarget::GetTlsValue](../../winscript/reference/ijsdebugdatatarget-gettlsvalue-method.md)|Pour le thread en cours de débogage, récupère la valeur dans l’emplacement de stockage local (TLS) de thread pour l’index TLS spécifié.|  
|[Méthode IJsDebugDataTarget::ReadBSTR](../../winscript/reference/ijsdebugdatatarget-readbstr-method.md)|Lit un BSTR à partir de la cible de débogage.|  
|[Méthode IJsDebugDataTarget::ReadMemory](../../winscript/reference/ijsdebugdatatarget-readmemory-method.md)|Lit la mémoire du processus cible.|  
|[Méthode IJsDebugDataTarget::ReadNullTerminatedString](../../winscript/reference/ijsdebugdatatarget-readnullterminatedstring-method.md)|Lit le nombre spécifié de caractères à partir de la cible.|  
|[Méthode IJsDebugDataTarget::WriteMemory](../../winscript/reference/ijsdebugdatatarget-writememory-method.md)|Lit la mémoire du processus cible.|  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence d’interfaces de script Windows](../../winscript/reference/windows-script-interfaces-reference.md)