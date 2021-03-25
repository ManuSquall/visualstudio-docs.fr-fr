---
description: Détruit l’ID unique associé à cette propriété, indiquant que l’appelant n’est plus soucieux d’identifier cette propriété de manière unique à partir de toutes les autres propriétés.
title: IDebugProperty3 ::D estroyObjectID | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 071af90af5fe22d6f6cfa662458be660edc5d39f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064824"
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
Détruit l’ID unique associé à cette propriété, indiquant que l’appelant n’est plus soucieux d’identifier cette propriété de manière unique à partir de toutes les autres propriétés.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT DestroyObjectID(
   void
);
```

```csharp
int DestroyObjectID();
```

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Si le moteur de débogage n’a pas besoin de prendre en charge des ID uniques pour une propriété (parce qu’il les suit déjà de façon unique), il peut simplement retourner `E_NOTIMPL` pour cette méthode.

 Les ID uniques sont créés avec un appel à la méthode [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) lorsque l’appelant souhaite s’assurer que cette propriété est identifiée de manière unique parmi toutes les autres propriétés.

## <a name="see-also"></a>Voir aussi
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)
