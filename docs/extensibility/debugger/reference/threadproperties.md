---
title: THREADPROPERTIES | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 86fc5231f8d577e0456ce2d9f76c7b6d7f831280
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="threadproperties"></a>THREADPROPERTIES
Décrit les propriétés d’un thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _tagTHREADPROPERTIES {   
   THREADPROPERTY_FIELDS dwFields;  
   DWORD                 dwThreadId;  
   DWORD                 dwSuspendCount;  
   DWORD                 dwThreadState;  
   BSTR                  bstrPriority;  
   BSTR                  bstrName;  
   BSTR                  bstrLocation;  
} THREADPROPERTIES;  
```  
  
```csharp  
public struct THREADPROPERTIES {   
   public uint   dwFields;  
   public uint   dwThreadId;  
   public uint   dwSuspendCount;  
   public uint   dwThreadState;  
   public string bstrPriority;  
   public string bstrName;  
   public string bstrLocation;  
};  
```  
  
## <a name="members"></a>Membres  
 dwFields  
 Une combinaison d’indicateurs à partir de la [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) énumération, qui décrit les champs de cette structure sont valides.  
  
 dwThreadId  
 L’ID de thread.  
  
 dwSuspendCount  
 Compteur de suspension du thread.  
  
 dwThreadState  
 Une valeur à partir de la [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) énumération indiquant l’état du thread d’opération.  
  
 bstrPriority  
 Une chaîne qui spécifie la priorité de thread ; par exemple, « ci-dessus Normal », « Normal » ou « Temps critiques ».  
  
 bstName  
 Le nom du thread.  
  
 bstrLocation  
 L’emplacement de thread (généralement le frame de pile au premier plan), exprimé en général sous le nom de la méthode dans laquelle l’exécution est interrompue d’actuellement.  
  
## <a name="remarks"></a>Notes  
 Cette structure est remplie par un appel à la [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) (méthode). Les informations retournées par conséquent, sont généralement utilisées dans le remplissage de la **Threads** fenêtre.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)   
 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)