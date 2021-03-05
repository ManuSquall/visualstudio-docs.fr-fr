---
description: Récupère une référence à l’interface du processus de débogage.
title: 'IDebugCodeContext3 :: GetProcess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3::GetProcess
ms.assetid: e082e494-2255-4d9d-a5a9-6dadd904bea8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6d34409ad1d075df5520cf18124e5e3adbf16227
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164056"
---
# <a name="idebugcodecontext3getprocess"></a>IDebugCodeContext3::GetProcess
Récupère une référence à l’interface du processus de débogage.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetProcess(
    IDebugProcess2 **ppProcess
);
```

```csharp
public int GetProcess(
    out IDebugProcess2 ppProcess
);
```

## <a name="parameters"></a>Paramètres
`ppProcess`\
à Référence à l’interface du processus de débogage.

## <a name="return-value"></a>Valeur renvoyée
En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="example"></a>Exemple
L’exemple suivant montre comment implémenter cette méthode pour un objet **CDebugCodeContext** qui expose l’interface [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) .

```cpp
HRESULT CDebugCodeContext::GetProcess(IDebugProcess2** ppProcess)
{
    HRESULT hr = S_OK;
    CComPtr<CDebugEngine> pEngine;
    CComPtr<IDebugPort2> pPort2;

    IfFalseGo( ppProcess, E_INVALIDARG );
    *ppProcess = NULL;

    IfFalseGo( m_pProgram, E_FAIL );
    IfFailGo( ((CDebugProgram *)m_pProgram)->GetEngine(&pEngine) );
    IfFailGo( pEngine->GetSDMProcess(ppProcess) );

Error:

    return hr;
}
```

## <a name="see-also"></a>Voir aussi
- [IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)
