---
title: IDebugProgram2::EnumCodePaths | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 09245f131e8295203c37cbe6cf21c48235dc87b9
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66200320"
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
[in] Le mot sous le curseur dans le **Source** ou **désassemblage** vue dans l’IDE.

`pStart`\
[in] Un [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objet représentant le contexte de code actuel.

`pFrame`\
[in] Un [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) représentant le frame de pile associée au point d’arrêt en cours de l’objet.

`fSource`\
[in] Différent de zéro (`TRUE`) dans le cas le **Source** vue, ou zéro (`FALSE`) dans le cas le **désassemblage** vue.

`ppEnum`\
[out] Retourne un [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) objet contenant une liste des chemins de code.

`ppSafety`\
[out] Retourne un [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) de l’objet représentant un contexte de code supplémentaires à définir comme un point d’arrêt en cas de chemin d’accès du code choisi est ignorée. Cela peut se produire dans le cas d’une expression booléenne court-circuitée, par exemple.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Un chemin d’accès du code décrit le nom d’une méthode ou une fonction qui a été appelée pour accéder à la position actuelle dans l’exécution du programme. Une liste de chemins d’accès du code représente la pile des appels.

## <a name="see-also"></a>Voir aussi
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)