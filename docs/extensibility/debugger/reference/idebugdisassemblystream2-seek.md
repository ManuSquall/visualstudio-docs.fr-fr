---
title: IDebugDisassemblyStream2::Seek Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4954b3b278b3c7a6b798a4ffda3856ab8bb200c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732088"
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
Déplace le pointeur de lecture dans le flux démontage un nombre donné d’instructions par rapport à une position spécifiée.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Seek( 
   SEEK_START          dwSeekStart,
   IDebugCodeContext2* pCodeContext,
   UINT64              uCodeLocationId,
   INT64               iInstructions
);
```

```csharp
int Seek( 
   enum_SEEK_START    dwSeekStart,
   IDebugCodeContext2 pCodeContext,
   ulong              uCodeLocationId,
   long               iInstructions
);
```

## <a name="parameters"></a>Paramètres
`dwSeekStart`\
[dans] Une valeur de [l’énumération SEEK_START](../../../extensibility/debugger/reference/seek-start.md) qui spécifie la position relative pour commencer le processus de recherche.

`pCodeContext`\
[dans] [L’objet IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) représentant le contexte de code à laquelle l’opération de recherche est relative. Ce paramètre n’est utilisé que si `dwSeekStart`  =  `SEEK_START_CODECONTEXT`; autrement, ce paramètre est ignoré et peut être une valeur nulle.

`uCodeLocationId`\
[dans] L’identifiant de localisation de code à laquelle l’opération de recherche est relatif. Ce paramètre `dwSeekStart`  =  `SEEK_START_CODELOCID`est utilisé si ; autrement, ce paramètre est ignoré et peut être réglé à 0. Consultez la section Remarques pour la méthode [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) pour une description d’un identifiant de localisation de code.

`iInstructions`\
[dans] Nombre d’instructions de déplacement par `dwSeekStart`rapport à la position spécifiée dans . Cette valeur peut être négative pour reculer.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si la position de recherche était à un point au-delà de la liste des instructions disponibles. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Si la recherche était à un poste avant le début de la liste, la position de lecture est définie à la première instruction dans la liste. Si le voir était à une position après la fin de la liste, la position de lecture est définie à la dernière instruction dans la liste.

## <a name="see-also"></a>Voir aussi
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
