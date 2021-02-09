---
title: 'IDebugEngine2 :: CreatePendingBreakpoint | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 93534a40d523c7b67a769ebea319463cf59e4b7a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879018"
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
Crée un point d’arrêt en attente dans le moteur de débogage (DE).

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
dans Objet [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) qui décrit le point d’arrêt en attente à créer.

`ppPendingBP`\
à Retourne un objet [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) qui représente le point d’arrêt en attente.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur. Retourne généralement `E_FAIL` la valeur si le `pBPRequest` paramètre ne correspond à aucun langage pris en charge par le de si le `pBPRequest` paramètre n’est pas valide ou est incomplet.

## <a name="remarks"></a>Remarques
Un point d’arrêt en attente est essentiellement une collection de toutes les informations nécessaires pour lier un point d’arrêt au code. Le point d’arrêt en attente retourné par cette méthode n’est pas lié au code tant que la méthode de [liaison](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) n’est pas appelée.

Pour chaque point d’arrêt en attente défini par l’utilisateur, le gestionnaire de débogage de session appelle cette méthode dans chaque attachement DE. C’est à la valeur de de vérifier que le point d’arrêt est valide pour les programmes en cours d’exécution dans ce.

Lorsque l’utilisateur définit un point d’arrêt sur une ligne de code, le DE est libre de lier le point d’arrêt à la ligne la plus proche dans le document qui correspond à ce code. Cela permet à l’utilisateur de définir un point d’arrêt sur la première ligne d’une instruction multiligne, mais de le lier à la dernière ligne (où tout le code est attribué dans les informations de débogage).

## <a name="example"></a>Exemple
L’exemple suivant montre comment implémenter cette méthode pour un `CProgram` objet simple. L’implémentation de de l' `IDebugEngine2::CreatePendingBreakpoint` peut ensuite transférer tous les appels à cette implémentation de la méthode dans chaque programme.

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
- [Établis](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
