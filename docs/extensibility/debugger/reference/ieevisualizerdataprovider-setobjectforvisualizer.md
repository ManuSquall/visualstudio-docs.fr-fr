---
title: IEEVisualizerDataProvider::SetObjectForVisualizer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a55328c4148aa911d86b8f2daf05ba84a50ff444
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56711539"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
Cette méthode modifie l’objet qui représente le visualiseur.

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

#### <a name="parameters"></a>Paramètres
 `pNewObject`

 [in] Objet à définir.

 `error`

 [out] S’il existait une erreur de paramétrage de l’objet, cette chaîne conserve le message d’erreur.

 `pException`

 [out] Si une erreur s’est produite, cet objet contient des informations sur l’exception.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Il est à l’implémenteur pour déterminer la façon dont les informations d’erreur sont retournées. Toutefois, il est possible que certaines les appelants ne peuvent être pour voir si un objet d’exception a été retourné savoir il était une erreur, donc cette méthode doit toujours retourner un objet d’exception si une erreur s’est produite. La chaîne d’erreur doit également être fournie dans le cas où l’appelant veut s’utiliser de celui-ci.

## <a name="see-also"></a>Voir aussi
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)