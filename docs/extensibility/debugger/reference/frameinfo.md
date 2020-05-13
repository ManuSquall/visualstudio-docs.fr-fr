---
title: FRAMEINFO - FRANCE Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO
helpviewer_keywords:
- FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c40361a9739bf468de2038df4325fa1ac98337c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736785"
---
# <a name="frameinfo"></a>FRAMEINFO
Décrit un cadre de pile.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct tagFRAMEINFO {
    FRAMEINFO_FLAGS    m_dwValidFields;
    BSTR               m_bstrFuncName;
    BSTR               m_bstrReturnType;
    BSTR               m_bstrArgs;
    BSTR               m_bstrLanguage;
    BSTR               m_bstrModule;
    UINT64             m_addrMin;
    UINT64             m_addrMax;
    IDebugStackFrame2* m_pFrame;
    IDebugModule2*     m_pModule;
    BOOL               m_fHasDebugInfo;
    BOOL               m_fStaleCode;
    BOOL               m_fAnnotatedFrame;
} FRAMEINFO;
```

```csharp
public struct FRAMEINFO {
    public uint              m_dwValidFields;
    public string            m_bstrFuncName;
    public string            m_bstrReturnType;
    public string            m_bstrArgs;
    public string            m_bstrLanguage;
    public string            m_bstrModule;
    public ulong             m_addrMin;
    public ulong             m_addrMax;
    public IDebugStackFrame2 m_pFrame;
    public IDebugModule2     m_pModule;
    public int               m_fHasDebugInfo;
    public int               m_fStaleCode;
    public int               m_fAnnotatedFrame;
} FRAMEINFO;
```

## <a name="members"></a>Membres
`m_dwValidFields`\
Une combinaison de drapeaux de [l’FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) énumération qui précise quels champs sont remplis.

`m_bstrFuncName`\
Le nom de fonction associé au cadre de pile.

`m_bstrReturnType`\
Le type de retour associé au cadre de pile.

`m_bstrArgs`\
Les arguments de la fonction associée au cadre de pile.

`m_bstrLanguage`\
Le langage dans lequel la fonction est mise en œuvre.

`m_bstrModule`\
Le nom du module associé au cadre de la pile.

`m_addrMin`\
L’adresse de pile physique minimale.

`m_addrMAX`\
L’adresse de pile physique maximale.

`m_pFrame`\
[L’objet IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) qui représente ce cadre de pile.

`m_pModule`\
[L’objet IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) qui représente le module qui contient ce cadre de pile.

`m_fHasDebugInfo`\
Non-zéro`TRUE`( ) si l’information de débagé existe dans le cadre donné.

`m_fStaleCode`\
Non-zéro`TRUE`( ) si le cadre de pile est associé au code qui n’est plus valide.

`m_fAnnotatedFrame`\
Non-zéro`TRUE`( ) si le cadre de pile est annoté par le gestionnaire de débogé de session (SDM).

## <a name="remarks"></a>Notes
Cette structure est transmise à la méthode [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) à remplir. Cette structure est également contenue dans une liste qui est contenue dans [l’interface IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) qui, à son tour, est retourné d’un appel à la méthode [EnumFrameInfo.](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
