---
title: IDebugEngine2::RemoveSetException | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveSetException
helpviewer_keywords:
- IDebugEngine2::RemoveSetException
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 52d2d628f9fcbc2279096a12117951f4c02f8bf4
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66207575"
---
# <a name="idebugengine2removesetexception"></a>IDebugEngine2::RemoveSetException
Supprime l’exception spécifiée, donc il n’est n’est plus géré par le moteur de débogage.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT RemoveSetException( 
   EXCEPTION_INFO* pException
);
```

```csharp
int RemoveSetException( 
   EXCEPTION_INFO[] pException
);
```

## <a name="parameters"></a>Paramètres
`pException`\
[in] Un [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) structure qui décrit l’exception à supprimer.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 L’exception en cours de suppression doit avoir été précédemment définie par un appel antérieur à la [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) (méthode).

 Pour supprimer toutes les exceptions de jeu à la fois, appelez le [RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md) (méthode).

## <a name="see-also"></a>Voir aussi
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)