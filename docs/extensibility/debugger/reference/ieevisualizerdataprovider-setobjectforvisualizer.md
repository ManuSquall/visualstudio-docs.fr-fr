---
title: IEEVisualizerDataProvider::SetObjectForVisualizer Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab63f1e74e0cd3ac64a4d7e7687a9136075b41a7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718080"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
Cette méthode modifie l’objet que représente le visualisateur.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetObjectForVisualizer(
   IDebugObject*  pNewObject,
   BSTR*          error,
   IDebugObject** pException
);
```

```csharp
int SetObjectForVisualizer(
   IDebugObject     pNewObject,
   out string       error,
   out IDebugObject pException
);
```

## <a name="parameters"></a>Paramètres
`pNewObject`\
[dans] L’objet à définir.

`error`\
[out] S’il y a eu une erreur définissant l’objet, cette chaîne contient le message d’erreur.

`pException`\
[out] S’il y a eu une erreur, cet objet contient les informations d’exception.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Il appartient à l’implémentateur de déterminer comment les informations d’erreur sont retournées. Cependant, il est possible que certains appelants ne cherchent que pour voir si un objet d’exception a été retourné pour savoir qu’il y avait une erreur, de sorte que cette méthode devrait toujours retourner un objet d’exception s’il y avait une erreur. La chaîne d’erreur doit également être fournie au cas où l’appelant veut s’en servir.

## <a name="see-also"></a>Voir aussi
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
