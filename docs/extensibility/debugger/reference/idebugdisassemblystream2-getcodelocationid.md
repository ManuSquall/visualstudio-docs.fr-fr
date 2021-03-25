---
description: Retourne un identificateur d’emplacement du code pour un contexte de code particulier.
title: 'IDebugDisassemblyStream2 :: GetCodeLocationId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f68ee6ff0495fe36d8de8ccf0e3c2c81f3d05ac5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067086"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
Retourne un identificateur d’emplacement du code pour un contexte de code particulier.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetCodeLocationId( 
   IDebugCodeContext2* pCodeContext,
   UINT64*             puCodeLocationId
);
```

```csharp
int GetCodeLocationId( 
   IDebugCodeContext2 pCodeContext,
   out ulong          puCodeLocationId
);
```

## <a name="parameters"></a>Paramètres
`pCodeContext`\
dans Objet [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) à convertir en identificateur.

`puCodeLocationId` à Retourne l’identificateur de l’emplacement du code. Consultez la section Notes.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur. Retourne `E_CODE_CONTEXT_OUT_OF_SCOPE` si le contexte de code est valide mais en dehors de la portée.

## <a name="remarks"></a>Notes
 L’identificateur d’emplacement du code est spécifique au moteur DE débogage (DE) qui prend en charge le code machine. Cet identificateur d’emplacement est utilisé en interne par le DE pour effectuer le suivi des positions dans le code et est généralement une adresse ou un décalage d’un genre. La seule exigence est que si le contexte de code d’un emplacement est inférieur au contexte de code d’un autre emplacement, l’identificateur de l’emplacement du code correspondant du premier contexte de code doit également être inférieur à l’identificateur de l’emplacement du code du deuxième contexte de code.

 Pour récupérer le contexte de code d’un identificateur d’emplacement du code, appelez la méthode [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) .

## <a name="see-also"></a>Voir aussi
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
