---
title: IDebugEngine3:SetJustMyCodeState ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9930f8ecf0c2f9b6fff4ce1c9e3edb935c5a7912
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730675"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
Cette méthode informe le moteur de débogé sur les informations d’état JustMyCode.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetJustMyCodeState(
   BOOL           fUpdate,
   DWORD          dwModules,
   JMC_CODE_SPEC* rgJMCSpec
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
[dans] Nonzero`TRUE`( ) pour mettre`FALSE`à jour les informations actuelles, zéro ( ) pour réinitialiser toutes les informations (ignorant tout ce qui avait été précédemment défini).

`dwModules`\
[dans] Nombre de structures d’information dans`rgJMCSpec.`

`rgJMCSpec`\
[dans] Array de [structures JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) à utiliser.

## <a name="return-value"></a>Valeur de retour
 En cas `S_OK`de succès, les retours; autrement, renvoie le code d’erreur.

## <a name="remarks"></a>Notes
 JustMyCode est le concept de déboguer uniquement le code qui appartient à un utilisateur et d’ignorer tout code intermédiaire tel que le code système, même si le code source est disponible pour ce code système.

## <a name="see-also"></a>Voir aussi
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)
