---
title: 'IDebugFunctionObject2 :: CreateStringObjectWithLength | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CreateStringObjectWithLength
- IDebugFunctionObject2::CreateStringObjectWithLength
ms.assetid: 1f43ec66-1615-4a4c-8b9d-e933f549f96d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 937d325f8637a3260121def189d472dcfb3e1309
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80728466"
---
# <a name="idebugfunctionobject2createstringobjectwithlength"></a>IDebugFunctionObject2::CreateStringObjectWithLength
Crée un objet String qui a la longueur spécifiée.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateStringObjectWithLength (
   LPCOLESTR      pcstrString,
   UINT           uiLength,
   IDebugObject** ppObject
);
```

```csharp
int CreateStringObjectWithLength (
   string           pcstrString,
   uint             uiLength,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Paramètres
`pcstrString`\
dans Valeur de chaîne de l’objet String.

`uiLength`\
dans Longueur de la chaîne en octets.

`ppObject`\
à Retourne un objet [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) qui représente l’objet String nouvellement créé.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
