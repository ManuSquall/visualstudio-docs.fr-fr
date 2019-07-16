---
title: THREADPROPERTY_FIELDS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dc0e0f7cae4aed887809c22bda0cd6a9ed50307f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204800"
---
# <a name="threadpropertyfields"></a>THREADPROPERTY_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Spécifie les informations sur un thread doit être récupéré.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
