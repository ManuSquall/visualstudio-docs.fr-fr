---
title: IDebugDisassemblyStream2::GetCodeLocationId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d8169d5ec4c212cbf09ff3273f0338b3e905d721
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62875786"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
Retourne un identificateur d’emplacement de code pour un contexte de code particulière.

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

#### <a name="parameters"></a>Paramètres
 `pCodeContext`

 [in] Un [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objet à convertir en un identificateur.

 `puCodeLocationId`

 [out] Retourne l’identificateur d’emplacement de code. Consultez la section Notes.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Retourne `E_CODE_CONTEXT_OUT_OF_SCOPE` si le contexte de code est valide, mais en dehors de l’étendue.

## <a name="remarks"></a>Notes
 L’identificateur d’emplacement de code est spécifique au moteur de débogage (dé) prenant en charge le code machine. Cet identificateur d’emplacement est utilisé en interne par le dé pour effectuer le suivi des positions dans le code et est généralement une adresse ou un décalage quelconque. La seule exigence est que si le contexte de code d’un emplacement est inférieur au contexte du code d’un autre emplacement, puis l’identificateur d’emplacement de code correspondant du premier contexte de code doit également être inférieure à l’identificateur d’emplacement de code de la deuxième contexte de code.

 Pour récupérer le contexte de code d’un identificateur d’emplacement de code, appelez le [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) (méthode).

## <a name="see-also"></a>Voir aussi
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)