---
title: IDebugProgramProvider2::GetProviderProgramNode Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd8ca7d5120ba20695caef2e9021ee25869df72f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721795"
---
# <a name="idebugprogramprovider2getproviderprogramnode"></a>IDebugProgramProvider2::GetProviderProgramNode
Récupère le nœud du programme pour un programme spécifique.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetProviderProgramNode(
   PROVIDER_FLAGS       Flags,
   IDebugDefaultPort2*  pPort,
   AD_PROCESS_ID        processId,
   REFGUID              guidEngine,
   UINT64               programId,
   IDebugProgramNode2** ppProgramNode
);
```

```csharp
int GetProviderProgramNode(
   enum_PROVIDER_FLAGS    Flags,
   IDebugDefaultPort2     pPort,
   AD_PROCESS_ID          ProcessId,
   ref Guid               guidEngine,
   ulong                  programId,
   out IDebugProgramNode2 ppProgramNode
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

`pPort`\
[dans] Le port le processus d’appel est en cours d’exécution.

`processId`\
[dans] Une structure [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) qui détient la pièce d’identité du processus qui contient le programme en question.

`guidEngine`\
[dans] GUID du moteur de débogé que le programme est attaché à (le cas échéant).

`programId`\
[dans] ID du programme pour lequel obtenir le nœud de programme.

`ppProgramNode`\
[out] Un objet [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) représentant le nœud de programme demandé.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
