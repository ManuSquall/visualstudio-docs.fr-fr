---
title: IDebugProperty2::GetSize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetSize
helpviewer_keywords:
- IDebugProperty2::GetSize
ms.assetid: 0deb8ec5-d6fb-4622-bb14-0c46b9459cc6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 26281ea175936429f1be5ac2620802c9d2cd5aa1
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66211419"
---
# <a name="idebugproperty2getsize"></a>IDebugProperty2::GetSize
Obtient la taille, en octets, de la valeur de propriété.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetSize ( 
   DWORD* pdwSize
);
```

```csharp
int GetSize ( 
   out uint pdwSize
);
```

## <a name="parameters"></a>Paramètres
`pdwSize`\
[out] Retourne la taille, en octets, de la valeur de propriété.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon retourne le code d’erreur. Retourne `S_GETSIZE_NO_SIZE` si la propriété n’a pas de taille.

## <a name="see-also"></a>Voir aussi
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)