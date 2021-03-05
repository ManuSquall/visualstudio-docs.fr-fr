---
description: Cette méthode indique au moteur de débogage à propos des informations d’état JustMyCode.
title: 'IDebugEngine3 :: SetJustMyCodeState | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a81fa4bda506cf1be27f658b071910e7c8ccd8a7
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153701"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
Cette méthode indique au moteur de débogage à propos des informations d’état JustMyCode.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetJustMyCodeState(
   BOOL           fUpdate,
   DWORD          dwModules,
   JMC_CODE_SPEC* rgJMCSpec
);
```

```csharp
int SetJustMyCodeState(
   int             fUpdate,
   uint            dwModules,
   JMC_CODE_SPEC[] rgJMCSpec
);
```

## <a name="parameters"></a>Paramètres
`fUpdate`\
dans Différent de zéro ( `TRUE` ) pour mettre à jour les informations actuelles, zéro ( `FALSE` ) pour réinitialiser toutes les informations (sans tenir compte des éléments précédemment définis).

`dwModules`\
dans Nombre de structures d’informations dans `rgJMCSpec.`

`rgJMCSpec`\
dans Tableau de structures de [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) à utiliser.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne le code d’erreur.

## <a name="remarks"></a>Notes
 JustMyCode est le concept qui consiste à déboguer uniquement le code qui appartient à un utilisateur et à ignorer tout le code intermédiaire tel que le code système, même si le code source est disponible pour ce code système.

## <a name="see-also"></a>Voir aussi
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)
