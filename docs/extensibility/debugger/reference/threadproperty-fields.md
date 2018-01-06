---
title: THREADPROPERTY_FIELDS | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: THREADPROPERTY_FIELDS
helpviewer_keywords: THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9ff443fc655c18600ff90536d6e7ee5b8aa1ab7f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="threadpropertyfields"></a>THREADPROPERTY_FIELDS
Spécifie les informations sur un thread doit être récupéré.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD THREADPROPERTY_FIELDS;  
```  
  
```csharp  
public enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
```  
  
## <a name="members"></a>Membres  
 TPF_ID  
 Initialisation/utiliser le `dwThreadId` champ le [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) structure.  
  
 TPF_SUSPENDCOUNT  
 Initialisation/utiliser le `dwSuspendCount` champ le `THREADPROPERTIE`structure de S.  
  
 TPF_STATE  
 Initialisation/utiliser le `dwThreadState` champ le `THREADPROPERTIE`structure de S.  
  
 TPF_PRIORITY  
 Initialisation/utiliser le `bstrPriority` champ le `THREADPROPERTIE`structure de S.  
  
 TPF_NAME  
 Initialisation/utiliser le `bstrName` champ le `THREADPROPERTIE`structure de S.  
  
 TPF_LOCATION  
 Initialisation/utiliser le `bstrLocation` champ le `THREADPROPERTIE`structure de S.  
  
 TPF_ALLFIELDS  
 Spécifie tous les champs.  
  
## <a name="remarks"></a>Notes  
 Ces valeurs sont passées en tant qu’argument à la [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) méthode pour indiquer les champs de la [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) structure doivent être initialisées.  
  
 Ces valeurs sont également utilisées dans `dwFields` membre de la `THREADPROPERTIES` structure pour indiquer les champs qui sont utilisés et valide.  
  
 Ces indicateurs peuvent être combinées avec une opération de bits `OR`.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)