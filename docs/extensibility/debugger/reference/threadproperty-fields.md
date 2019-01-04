---
title: THREADPROPERTY_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0d4b20621d186cf9e14538d7378a84e25c739929
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53887341"
---
# <a name="threadpropertyfields"></a>THREADPROPERTY_FIELDS
Spécifie les informations sur un thread doit être récupéré.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_THREADPROPERTY_FIELDS {   
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
public enum enum_THREADPROPERTY_FIELDS {   
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
 Initialize/utiliser le `dwThreadId` champ la [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) structure.  
  
 TPF_SUSPENDCOUNT  
 Initialize/utiliser le `dwSuspendCount` champ la `THREADPROPERTIE`structure de S.  
  
 TPF_STATE  
 Initialize/utiliser le `dwThreadState` champ la `THREADPROPERTIE`structure de S.  
  
 TPF_PRIORITY  
 Initialize/utiliser le `bstrPriority` champ la `THREADPROPERTIE`structure de S.  
  
 TPF_NAME  
 Initialize/utiliser le `bstrName` champ la `THREADPROPERTIE`structure de S.  
  
 TPF_LOCATION  
 Initialize/utiliser le `bstrLocation` champ la `THREADPROPERTIE`structure de S.  
  
 TPF_ALLFIELDS  
 Spécifie tous les champs.  
  
## <a name="remarks"></a>Notes  
 Ces valeurs sont passées en tant qu’argument à la [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) méthode pour indiquer les champs de la [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) structure doivent être initialisées.  
  
 Ces valeurs sont également utilisées dans `dwFields` membre de la `THREADPROPERTIES` structure pour indiquer quels champs sont utilisés et valide.  
  
 Ces indicateurs peuvent être combinées avec un opérateur de bits `OR`.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)