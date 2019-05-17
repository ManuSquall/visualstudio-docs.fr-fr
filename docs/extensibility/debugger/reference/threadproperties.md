---
title: THREADPROPERTIES | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59b0fd83202ea8a5514d1ed637404d4864bf6b57
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65460724"
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
 Une combinaison d’indicateurs de la [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) énumération, décrivant les champs de cette structure sont valides.

 `dwThreadId`\
 L’ID de thread.

 `dwSuspendCount`\
 Compteur de suspension du thread.

 `dwThreadState`\
 Une valeur comprise entre le [des États du thread](../../../extensibility/debugger/reference/threadstate.md) énumération indiquant l’état du thread d’exploitation.

 `bstrPriority`\
 Une chaîne qui spécifie la priorité de thread ; par exemple, « Ci-dessus Normal », « Normal » ou « Temps critiques ».

 `bstName`\
 Le nom du thread.

 `bstrLocation`\
 L’emplacement de thread (et généralement le frame de pile au premier plan), généralement exprimé sous la forme du nom de la méthode où l’exécution est actuellement interrompue.

## <a name="remarks"></a>Notes
 Cette structure est remplie par un appel à la [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) (méthode). Les informations retournées par conséquent, sont généralement utilisées dans remplissant la **Threads** fenêtre.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)
- [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)