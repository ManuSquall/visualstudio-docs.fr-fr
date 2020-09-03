---
title: 'IDebugObject :: SetValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9e4652eb3c77a1871063dfa71b464fb1f7c43f94
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726357"
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
Définit la valeur de l’objet à partir d’une série consécutive d’octets.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int SetValue(
   byte[] pValue,
   uint   nSize
);
```

## <a name="parameters"></a>Paramètres
`pValue`\
dans Tableau d’octets représentant la nouvelle valeur.

`nSize`\
dans Taille de la valeur en octets.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Les valeurs du tableau sont copiées dans cet objet [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , en remplaçant toute valeur existante. La taille de la nouvelle valeur peut être supérieure ou inférieure à la valeur existante. Il `IDebugObject` ne peut pas s’agir d’une référence null.

## <a name="see-also"></a>Voir aussi
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
