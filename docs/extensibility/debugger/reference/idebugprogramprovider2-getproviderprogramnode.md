---
description: Récupère le nœud de programme pour un programme spécifique.
title: 'IDebugProgramProvider2 :: GetProviderProgramNode | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 07e7184c189d501b2fcb604590eeb121bae8ccdc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065279"
---
# <a name="idebugprogramprovider2getproviderprogramnode"></a>IDebugProgramProvider2::GetProviderProgramNode
Récupère le nœud de programme pour un programme spécifique.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetProviderProgramNode(
   PROVIDER_FLAGS       Flags,
   IDebugDefaultPort2*  pPort,
   AD_PROCESS_ID        processId,
   REFGUID              guidEngine,
   UINT64               programId,
   IDebugProgramNode2** ppProgramNode
);
```

```csharp
int GetProviderProgramNode(
   enum_PROVIDER_FLAGS    Flags,
   IDebugDefaultPort2     pPort,
   AD_PROCESS_ID          ProcessId,
   ref Guid               guidEngine,
   ulong                  programId,
   out IDebugProgramNode2 ppProgramNode
);
```

## <a name="parameters"></a>Paramètres
`Flags`\
dans Combinaison d’indicateurs de l’énumération [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) . Les indicateurs suivants sont typiques pour cet appel :

|Indicateur|Description|
|----------|-----------------|
|`PFLAG_REMOTE_PORT`|L’appelant est en cours d’exécution sur l’ordinateur distant.|
|`PFLAG_DEBUGGEE`|L’appelant est actuellement en cours de débogage (des informations supplémentaires sur le marshaling seront retournées pour chaque nœud).|
|`PFLAG_ATTACHED_TO_DEBUGGEE`|L’appelant a été attaché à, mais il n’a pas été lancé par le débogueur.|

`pPort`\
dans Port sur lequel le processus appelant s’exécute.

`processId`\
dans Structure [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) contenant l’ID du processus qui contient le programme en question.

`guidEngine`\
dans GUID du moteur de débogage auquel le programme est attaché (le cas échéant).

`programId`\
dans ID du programme pour lequel obtenir le nœud de programme.

`ppProgramNode`\
à Objet [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) qui représente le nœud de programme demandé.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
