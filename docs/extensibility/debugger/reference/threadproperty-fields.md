---
title: THREADPROPERTY_FIELDS Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713399"
---
# <a name="threadproperty_fields"></a>THREADPROPERTY_FIELDS
Précise quelles informations sur un thread doivent être récupérées.

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
 Initialiser/utiliser `dwThreadId` le champ de la structure [THREADPROPERTIES.](../../../extensibility/debugger/reference/threadproperties.md)

 `TPF_SUSPENDCOUNT`\
 Initialiser/utiliser `dwSuspendCount` le champ `THREADPROPERTIE`de la structure S.

 `TPF_STATE`\
 Initialiser/utiliser `dwThreadState` le champ `THREADPROPERTIE`de la structure S.

 `TPF_PRIORITY`\
 Initialiser/utiliser `bstrPriority` le champ `THREADPROPERTIE`de la structure S.

 `TPF_NAME`\
 Initialiser/utiliser `bstrName` le champ `THREADPROPERTIE`de la structure S.

 `TPF_LOCATION`\
 Initialiser/utiliser `bstrLocation` le champ `THREADPROPERTIE`de la structure S.

 `TPF_ALLFIELDS`\
 Spécifie tous les champs.

## <a name="remarks"></a>Notes
 Ces valeurs sont transmises comme argument à la méthode [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) pour indiquer quels domaines de la structure [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) doivent être parasésés.

 Ces valeurs sont `dwFields` également utilisées `THREADPROPERTIES` dans le membre de la structure pour indiquer quels champs sont utilisés et valides.

 Ces drapeaux peuvent être combinés avec un peu plus. `OR`

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
