---
description: Récupère une liste des programmes en cours d’exécution à partir d’un processus spécifié.
title: 'IDebugProgramProvider2 :: GetProviderProcessData | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b878a6731a9a7f2bf58bf55530d0b5f83cc978de
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151556"
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
Récupère une liste des programmes en cours d’exécution à partir d’un processus spécifié.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetProviderProcessData(
   PROVIDER_FLAGS         Flags,
   IDebugDefaultPort2*    pPort,
   AD_PROCESS_ID          processId,
   CONST_GUID_ARRAY       EngineFilter,
   PROVIDER_PROCESS_DATA* pProcess
);
```

```csharp
int GetProviderProcessData(
   enum_PROVIDER_FLAGS     Flags,
   IDebugDefaultPort2      pPort,
   AD_PROCESS_ID           ProcessId,
   CONST_GUID_ARRAY        EngineFilter,
   PROVIDER_PROCESS_DATA[] pProcess
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
|`PFLAG_GET_PROGRAM_NODES`|L’appelant demande une liste de nœuds de programme à retourner.|

`pPort`\
dans Port sur lequel le processus appelant s’exécute.

`processId`\
dans Structure [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) contenant l’ID du processus qui contient le programme en question.

`EngineFilter`\
dans Tableau de GUID pour les moteurs de débogage affectés au débogage de ce processus (ceux-ci sont utilisés pour filtrer les programmes qui sont réellement retournés en fonction de ce que les moteurs fournis prennent en charge ; si aucun moteur n’est spécifié, tous les programmes sont retournés).

`pProcess`\
à Structure [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) qui est renseignée avec les informations demandées.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette méthode est normalement appelée par un processus pour obtenir une liste de programmes en cours d’exécution dans ce processus. Les informations retournées sont une liste d’objets [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) .

## <a name="see-also"></a>Voir aussi
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
