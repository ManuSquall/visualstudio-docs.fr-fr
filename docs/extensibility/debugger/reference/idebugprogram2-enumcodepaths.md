---
title: IDebugProgram2::EnumCodePaths ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b99651811cedbdb8ec0eca5b766e6d75651dd5d7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723036"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
Récupère une liste des chemins de code pour une position donnée dans un fichier source.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumCodePaths( 
   LPCOLESTR            pszHint,
   IDebugCodeContext2*  pStart,
   IDebugStackFrame2*   pFrame,
   BOOL                 fSource,
   IEnumCodePaths2**    ppEnum,
   IDebugCodeContext2** ppSafety
);
```

```csharp
int EnumCodePaths( 
   string                 pszHint,
   IDebugCodeContext2     pStart,
   IDebugStackFrame2      pFrame,
   Int                    fSource,
   out IEnumCodePaths2    ppEnum,
   out IDebugCodeContext2 ppSafety
);
```

## <a name="parameters"></a>Paramètres
`pszHint`\
[dans] Le mot sous le curseur dans la **vue source** ou **démontage** dans l’IDE.

`pStart`\
[dans] Un objet [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) représentant le contexte code actuel.

`pFrame`\
[dans] Un objet [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) représentant le cadre de pile associé au point d’arrêt actuel.

`fSource`\
[dans] Nonzero`TRUE`( ) si dans la`FALSE`vue **source,** ou zéro ( ) si dans la vue **démontée.**

`ppEnum`\
[out] Retourne un objet [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) contenant une liste des chemins de code.

`ppSafety`\
[out] Renvoie un objet [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) représentant un contexte de code supplémentaire à définir comme point d’arrêt au cas où la trajectoire de code choisie serait ignorée. Cela peut se produire dans le cas d’une expression Boolean court-circuité, par exemple.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Un chemin de code décrit le nom d’une méthode ou d’une fonction qui a été appelée pour arriver au point actuel dans l’exécution du programme. Une liste de chemins de code représente la pile d’appels.

## <a name="see-also"></a>Voir aussi
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
