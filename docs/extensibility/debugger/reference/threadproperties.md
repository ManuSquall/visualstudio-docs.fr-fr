---
title: THREADPROPERTIES | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a2eb7abf897cf4891f08228dd5f0c918f580a1ce
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850659"
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
 `dwFields`\
 Combinaison d’indicateurs de l’énumération [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) , décrivant les champs de cette structure qui sont valides.

 `dwThreadId`\
 ID de thread.

 `dwSuspendCount`\
 Nombre de suspensions de thread.

 `dwThreadState`\
 Valeur de l’énumération [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) indiquant l’état du thread d’exploitation.

 `bstrPriority`\
 Chaîne spécifiant la priorité du thread ; par exemple, « supérieur à normal », « normal » ou « temps critique ».

 `bstName`\
 Nom du thread.

 `bstrLocation`\
 L’emplacement du thread (généralement le frame de pile le plus haut), généralement exprimé sous la forme du nom de la méthode dans laquelle l’exécution est actuellement interrompue.

## <a name="remarks"></a>Remarques
 Cette structure est remplie par un appel à la méthode [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) . Les informations retournées sont généralement utilisées dans le remplissage de la fenêtre **Threads** .

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)
- [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)
