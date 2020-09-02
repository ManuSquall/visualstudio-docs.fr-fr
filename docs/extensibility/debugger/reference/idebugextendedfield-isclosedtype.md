---
title: 'IDebugExtendedField :: IsClosedType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IsClosedType
- IDebugExtendedField::IsClosedType
ms.assetid: 9136fc57-74ff-4fe4-a6e2-b137cb9d5b08
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4524d7c899480518e669f1f77a4756a83e0cf52f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729050"
---
# <a name="idebugextendedfieldisclosedtype"></a>IDebugExtendedField::IsClosedType
Détermine si le champ représente un type fermé.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT IsClosedType(
   void
);
```

```csharp
int IsClosedType();
```

## <a name="return-value"></a>Valeur de retour
 Si le champ est un type fermé, retourne `S_OK` ; sinon, retourne `S_FALSE` .

## <a name="see-also"></a>Voir aussi
- [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)
