---
title: IDebugProcess2::Attach Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fb6ea896285c784021402400597ba168f6ccf716
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724193"
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
Attache le gestionnaire de débogé de session (SDM) au processus.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   GUID*                 rgguidSpecificEngines,
   DWORD                 celtSpecificEngines,
   HRESULT*              rghrEngineAttach
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   Guid[]               rgguidSpecificEngines,
   uint                 celtSpecificEngines,
   int[]                rghrEngineAttach
);
```

## <a name="parameters"></a>Paramètres
`pCallback`\
[dans] Un objet [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) qui est utilisé pour la notification de l’événement de débog.

`rgguidSpecificEngines`\
[dans] Un éventail de GUIDs de moteurs débogés à utiliser pour déboguer les programmes en cours d’exécution dans le processus. Ce paramètre peut être une valeur nulle. Pour plus de détails, consultez la section Notes.

`celtSpecificEngines`\
[dans] Le nombre de moteurs débogé dans `rgguidSpecificEngines` le `rghrEngineAttach` tableau et la taille du tableau.

`rghrEngineAttach`\
[dans, dehors] Une gamme de codes HRESULT retournés par les moteurs de débogé. La taille de ce tableau `celtSpecificEngines` est spécifiée dans le paramètre. Chaque code est `S_OK` `S_ATTACH_DEFERRED`généralement soit ou . Ce dernier indique que le DE n’est actuellement rattaché à aucun programme.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur. Le tableau suivant montre d’autres valeurs possibles.

|Valeur|Description|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Le processus spécifié est déjà attaché au débbuggeur.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Une violation de la sécurité s’est produite pendant la procédure d’attachement.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Un processus de bureau ne peut pas être attaché au débbugger.|

## <a name="remarks"></a>Notes
 L’attachement à un processus attache le SDM à tous les programmes en cours d’exécution dans ce `rgguidSpecificEngines` processus qui peuvent être débogés par les moteurs de déboguer (DE) spécifiés dans le tableau. Définissez `rgguidSpecificEngines` le paramètre à `GUID_NULL` une valeur nulle ou incluez dans le tableau à attacher à tous les programmes du processus.

 Tous les événements de débaillement qui se produisent dans le processus sont envoyés à l’objet [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) donné. Cet `IDebugEventCallback2` objet est fourni lorsque le SDM appelle cette méthode.

## <a name="see-also"></a>Voir aussi
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
