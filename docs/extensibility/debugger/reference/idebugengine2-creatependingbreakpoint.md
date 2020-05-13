---
title: IDebugEngine2::CréerPendingBreakpoint (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f88cae3610487b92fed0d8390d44c55d3f536c4b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731117"
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
Crée un point d’arrêt en attente dans le moteur de débogé (DE).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreatePendingBreakpoint(
    IDebugBreakpointRequest2*  pBPRequest,
    IDebugPendingBreakpoint2** ppPendingBP
);
```

```csharp
int CreatePendingBreakpoint(
    IDebugBreakpointRequest2     pBPRequest,
    out IDebugPendingBreakpoint2 ppPendingBP
);
```

## <a name="parameters"></a>Paramètres
`pBPRequest`\
[dans] Un objet [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) qui décrit le point d’arrêt en attente pour créer.

`ppPendingBP`\
[out] Retourne un objet [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) qui représente le point d’arrêt en attente.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur. Rendements `E_FAIL` généralement `pBPRequest` si le paramètre ne correspond à `pBPRequest` aucune langue prise en charge par le DE de si le paramètre est invalide ou incomplet.

## <a name="remarks"></a>Notes
Un point d’arrêt en attente est essentiellement une collection de toutes les informations nécessaires pour lier un point d’arrêt au code. Le point d’arrêt en attente retourné de cette méthode n’est pas lié au code jusqu’à ce que la méthode [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) est appelée.

Pour chaque point d’arrêt en attente, l’utilisateur définit, le gestionnaire de débogé de session (SDM) appelle cette méthode dans chaque DE joint. C’est au DE de vérifier que le point d’arrêt est valide pour les programmes en cours d’exécution dans ce DE.

Lorsque l’utilisateur définit un point d’arrêt sur une ligne de code, le DE est libre de lier le point d’arrêt à la ligne la plus proche du document qui correspond à ce code. Cela permet à l’utilisateur de définir un point d’arrêt sur la première ligne d’une déclaration multi-lignes, mais le lier sur la dernière ligne (où tout le code est attribué dans les informations de débogé).

## <a name="example"></a>Exemple
L’exemple suivant montre comment implémenter cette méthode pour un objet simple. `CProgram` La mise en œuvre par le `IDebugEngine2::CreatePendingBreakpoint` DE pourrait alors transmettre tous les appels à cette mise en œuvre de la méthode dans chaque programme.

```
HRESULT CProgram::CreatePendingBreakpoint(IDebugBreakpointRequest2* pBPRequest, IDebugPendingBreakpoint2** ppPendingBP)
{
    // Create and initialize the CPendingBreakpoint object.
    CComObject<CPendingBreakpoint> *pPending;
    CComObject<CPendingBreakpoint>::CreateInstance(&pPending);
    pPending->Initialize(pBPRequest, m_pInterp, m_pCallback, m_pEngine);
    return pPending->QueryInterface(ppPendingBP);
}
```

## <a name="see-also"></a>Voir aussi
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [Lier](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
