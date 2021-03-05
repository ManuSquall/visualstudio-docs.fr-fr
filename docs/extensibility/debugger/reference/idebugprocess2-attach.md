---
description: Joint le gestionnaire de débogage de session (SDM) au processus.
title: 'IDebugProcess2 :: Attach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 73dbe76a32e67794736fd26595378485879b00b8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161442"
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
Joint le gestionnaire de débogage de session (SDM) au processus.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   GUID*                 rgguidSpecificEngines,
   DWORD                 celtSpecificEngines,
   HRESULT*              rghrEngineAttach
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   Guid[]               rgguidSpecificEngines,
   uint                 celtSpecificEngines,
   int[]                rghrEngineAttach
);
```

## <a name="parameters"></a>Paramètres
`pCallback`\
dans Objet [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) utilisé pour la notification d’événements de débogage.

`rgguidSpecificEngines`\
dans Tableau de GUID des moteurs de débogage à utiliser pour déboguer les programmes en cours d’exécution dans le processus. Ce paramètre peut être une valeur null. Pour plus de détails, consultez la section Notes.

`celtSpecificEngines`\
dans Le nombre de moteurs de débogage dans le `rgguidSpecificEngines` tableau et la taille du `rghrEngineAttach` tableau.

`rghrEngineAttach`\
[in, out] Tableau de codes HRESULT retournés par les moteurs de débogage. La taille de ce tableau est spécifiée dans le `celtSpecificEngines` paramètre. Chaque code est généralement `S_OK` ou `S_ATTACH_DEFERRED` . Ce dernier indique que le DE est actuellement attaché à aucun programme.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur. Le tableau suivant présente d’autres valeurs possibles.

|Valeur|Description|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Le processus spécifié est déjà attaché au débogueur.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Une violation de sécurité s’est produite pendant la procédure d’attachement.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Un processus de bureau ne peut pas être attaché au débogueur.|

## <a name="remarks"></a>Notes
 L’attachement à un processus joint le SDM à tous les programmes qui s’exécutent dans ce processus et qui peuvent être débogués par les moteurs DE débogage (DE) spécifiés dans le `rgguidSpecificEngines` tableau. Définissez le `rgguidSpecificEngines` paramètre sur une valeur null ou incluez-le `GUID_NULL` dans le tableau à attacher à tous les programmes dans le processus.

 Tous les événements de débogage qui se produisent dans le processus sont envoyés à l’objet [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) donné. Cet `IDebugEventCallback2` objet est fourni lorsque le SDM appelle cette méthode.

## <a name="see-also"></a>Voir aussi
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
