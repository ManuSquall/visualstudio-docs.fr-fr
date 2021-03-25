---
description: Supprime l’exception spécifiée afin qu’elle ne soit plus gérée par le moteur de débogage.
title: 'IDebugEngine2 :: RemoveSetException | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveSetException
helpviewer_keywords:
- IDebugEngine2::RemoveSetException
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b763291fccd39d46b32347d89df1a11e1b3d09f2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095405"
---
# <a name="idebugengine2removesetexception"></a>IDebugEngine2::RemoveSetException
Supprime l’exception spécifiée afin qu’elle ne soit plus gérée par le moteur de débogage.

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
dans Structure [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) qui décrit l’exception à supprimer.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 L’exception en cours de suppression doit avoir été précédemment définie par un appel antérieur à la méthode [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) .

 Pour supprimer toutes les exceptions de jeu à la fois, appelez la méthode [RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md) .

## <a name="see-also"></a>Voir aussi
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
