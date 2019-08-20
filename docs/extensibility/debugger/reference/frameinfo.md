---
title: FRAMEINFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO
helpviewer_keywords:
- FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eb6a4a9f7408e5bcd03da464bfbc8ade3fa39e7e
ms.sourcegitcommit: 5694c5236fa32ba7f5bc1236a853f725ec7557e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68681097"
---
# <a name="frameinfo"></a>FRAMEINFO
Décrit un frame de pile.

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
Combinaison d’indicateurs de l’énumération [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) qui spécifie les champs à renseigner.

`m_bstrFuncName`\
Nom de fonction associé au frame de pile.

`m_bstrReturnType`\
Type de retour associé au frame de pile.

`m_bstrArgs`\
Arguments de la fonction associée au frame de pile.

`m_bstrLanguage`\
Langage dans lequel la fonction est implémentée.

`m_bstrModule`\
Nom du module associé au frame de pile.

`m_addrMin`\
Adresse de pile physique minimale.

`m_addrMAX`\
Adresse physique maximale de la pile.

`m_pFrame`\
Objet [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) qui représente ce frame de pile.

`m_pModule`\
Objet [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) qui représente le module qui contient ce frame de pile.

`m_fHasDebugInfo`\
Valeur différente de zéro`TRUE`() si les informations de débogage existent dans le frame donné.

`m_fStaleCode`\
Valeur différente de zéro`TRUE`() si le frame de pile est associé à du code qui n’est plus valide.

`m_fAnnotatedFrame`\
Différent de zéro (`TRUE`) si le frame de pile est annoté par le gestionnaire de débogage de session (SDM).

## <a name="remarks"></a>Notes
Cette structure est transmise à la méthode [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) à remplir. Cette structure est également contenue dans une liste contenue dans l’interface [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) qui, à son tour, est retournée à partir d’un appel à la méthode [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) .

## <a name="requirements"></a>Configuration requise
En-tête: msdbg. h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
