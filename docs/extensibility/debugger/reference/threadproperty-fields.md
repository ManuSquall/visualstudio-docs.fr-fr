---
title: THREADPROPERTY_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b31c43187d1136f7a194c42749c430de6cd064a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713399"
---
# <a name="threadproperty_fields"></a>THREADPROPERTY_FIELDS
Spécifie les informations sur un thread à récupérer.

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

## <a name="fields"></a>Champs
 `TPF_ID`\
 Initialisez/utilisez le `dwThreadId` champ de la structure [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) .

 `TPF_SUSPENDCOUNT`\
 Initialisez/utilisez le `dwSuspendCount` champ de la `THREADPROPERTIE` structure S.

 `TPF_STATE`\
 Initialisez/utilisez le `dwThreadState` champ de la `THREADPROPERTIE` structure S.

 `TPF_PRIORITY`\
 Initialisez/utilisez le `bstrPriority` champ de la `THREADPROPERTIE` structure S.

 `TPF_NAME`\
 Initialisez/utilisez le `bstrName` champ de la `THREADPROPERTIE` structure S.

 `TPF_LOCATION`\
 Initialisez/utilisez le `bstrLocation` champ de la `THREADPROPERTIE` structure S.

 `TPF_ALLFIELDS`\
 Spécifie tous les champs.

## <a name="remarks"></a>Notes
 Ces valeurs sont passées en tant qu’arguments à la méthode [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) pour indiquer les champs de la structure [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) à initialiser.

 Ces valeurs sont également utilisées dans `dwFields` le membre de la `THREADPROPERTIES` structure pour indiquer les champs qui sont utilisés et valides.

 Ces indicateurs peuvent être combinés avec une opération au niveau du bit `OR` .

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
