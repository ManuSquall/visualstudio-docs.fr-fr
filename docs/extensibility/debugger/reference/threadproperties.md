---
title: THREADPROPERTIES - FRANCE Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd0ed4e33b1f8e0e905f3c88493c9f513c177fbc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713426"
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
 Une combinaison de drapeaux de [l’THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) énumération, décrivant les champs de cette structure sont valides.

 `dwThreadId`\
 L’ID de fil.

 `dwSuspendCount`\
 Le fil suspend le compte.

 `dwThreadState`\
 Une valeur de l’énumération [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) indiquant l’état du fil d’exploitation.

 `bstrPriority`\
 Une chaîne spécifiant la priorité de fil ; par exemple, « Au-dessus de la normale », « Normal » ou « Temps Critique ».

 `bstName`\
 Le nom du fil.

 `bstrLocation`\
 L’emplacement du thread (généralement le cadre de pile le plus haut), généralement exprimé comme le nom de la méthode où l’exécution est actuellement arrêtée.

## <a name="remarks"></a>Notes
 Cette structure est remplie par un appel à la méthode [GetThreadProperties.](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) L’information ainsi retournée est généralement utilisée dans le peuplement de la fenêtre **Threads.**

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)
- [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)
