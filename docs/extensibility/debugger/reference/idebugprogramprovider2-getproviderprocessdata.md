---
title: IDebugProgramProvider2::GetProviderProcessData (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4e958900307f5f7915f58679709c88f80c2abfc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721852"
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
Récupère une liste des programmes en cours d’exécution à partir d’un processus spécifié.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetProviderProcessData(
   PROVIDER_FLAGS         Flags,
   IDebugDefaultPort2*    pPort,
   AD_PROCESS_ID          processId,
   CONST_GUID_ARRAY       EngineFilter,
   PROVIDER_PROCESS_DATA* pProcess
);
```

```csharp
int GetProviderProcessData(
   enum_PROVIDER_FLAGS     Flags,
   IDebugDefaultPort2      pPort,
   AD_PROCESS_ID           ProcessId,
   CONST_GUID_ARRAY        EngineFilter,
   PROVIDER_PROCESS_DATA[] pProcess
);
```

## <a name="parameters"></a>Paramètres
`Flags`\
[dans] Une combinaison de drapeaux de [l’PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) énumération. Les drapeaux suivants sont typiques de cet appel :

|Indicateur|Description|
|----------|-----------------|
|`PFLAG_REMOTE_PORT`|L’appelant fonctionne sur une machine à distance.|
|`PFLAG_DEBUGGEE`|L’appelant est actuellement en cours de déboc rédaction (des informations supplémentaires sur le rassemblement seront retournées pour chaque nœud).|
|`PFLAG_ATTACHED_TO_DEBUGGEE`|L’appelant a été attaché à mais pas lancé par le débbugger.|
|`PFLAG_GET_PROGRAM_NODES`|L’appelant demande que la liste des nœuds de programme soit retournée.|

`pPort`\
[dans] Le port le processus d’appel est en cours d’exécution.

`processId`\
[dans] Une structure [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) qui détient la pièce d’identité du processus qui contient le programme en question.

`EngineFilter`\
[dans] Un éventail de GUIDs pour les moteurs débogés affectés à déboiffer ce processus (ceux-ci seront utilisés pour filtrer les programmes qui sont effectivement retournés en fonction de ce que les moteurs fournis support; si aucun moteur fourni n’est spécifié, alors tous les programmes seront retournés).

`pProcess`\
[out] Une [structure PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) qui est remplie avec les informations demandées.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette méthode est normalement appelée par un processus pour obtenir une liste de programmes en cours d’exécution dans ce processus. L’information retournée est une liste d’objets [IDebugProgramNode2.](../../../extensibility/debugger/reference/idebugprogramnode2.md)

## <a name="see-also"></a>Voir aussi
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
