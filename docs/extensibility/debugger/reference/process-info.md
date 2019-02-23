---
title: PROCESS_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a18d9a158e69fd18319f187274a2db7d00e24546
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56720625"
---
# <a name="processinfo"></a>PROCESS_INFO
Contient des informations relatives à un processus.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct tagPROCESS_INFO { 
   PROCESS_INFO_FIELDS Fields;
   BSTR                bstrFileName;
   BSTR                bstrBaseName;
   BSTR                bstrTitle;
   AD_PROCESS_ID       ProcessId;
   DWORD               dwSessionId;
   BSTR                bstrAttachedSessionName;
   FILETIME            CreationTime;
   PROCESS_INFO_FLAGS  Flags;
} PROCESS_INFO;
```

```csharp
public struct PROCESS_INFO { 
   public uint          Fields;
   public string        bstrFileName;
   public string        bstrBaseName;
   public string        bstrTitle;
   public AD_PROCESS_ID ProcessId;
   public uint          dwSessionId;
   public string        bstrAttachedSessionName;
   public FILETIME      CreationTime;
   public uint          Flags;
};
```

## <a name="members"></a>Membres
 Champs d’une combinaison d’indicateurs de la [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) énumération qui spécifient quels champs sont renseignés.

 bstrFileName le nom de chemin d’accès complet du processus. Équivalent à l’appel le [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) méthode avec le paramètre `GN_FILENAME`.

 bstrBaseName le nom de fichier et l’extension du processus. Équivalent à l’appel le `IDebugProcess2::Getname` méthode avec le paramètre `GN_BASENAME`.

 bstrTitle le titre du processus, le cas échéant. Équivalent à l’appel le `IDebugProcess2::Getname` méthode avec le paramètre `GN_TITLE`.

 ProcessId le [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) structure qui identifie le processus. Équivalent à l’appel le [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) (méthode).

 dwSessionId l’identificateur de la session de débogage, ce processus est en cours d’exécution dans.

 bstrAttachedSessionName le nom de session attaché. Équivalent à l’appel le [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) (méthode).

 CreationTime l’heure de que création du processus.

 Indicateurs d’une combinaison d’indicateurs de la [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) énumération qui spécifient les propriétés du processus.

## <a name="remarks"></a>Notes
 Cette structure est passée à la [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) méthode où il est renseigné.

## <a name="requirements"></a>Spécifications
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)
- [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
- [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)
- [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)