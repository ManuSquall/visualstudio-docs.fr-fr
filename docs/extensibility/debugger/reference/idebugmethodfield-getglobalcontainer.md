---
title: 'IDebugMethodField :: GetGlobalContainer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetGlobalContainer
helpviewer_keywords:
- IDebugMethodField::GetGlobalContainer method
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 197490cde12e0c7dd9cee14d11c3ec2f0b165d86
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936871"
---
# <a name="idebugmethodfieldgetglobalcontainer"></a>IDebugMethodField::GetGlobalContainer
Obtient le conteneur global de la méthode.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetGlobalContainer(
   IDebugClassField** ppClass
);
```

```csharp
int GetGlobalContainer(
   out IDebugClassField ppClass
);
```

## <a name="parameters"></a>Paramètres
`ppClass`\
à Retourne un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) représentant le module dans lequel cette méthode est définie.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 L’objet [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) retourné représente l’intégralité du module et est un objet artificiel, autrement dit, le module lui-même n’a pas de classe réelle, mais il peut être représenté par un `IDebugClassField` objet, ce qui permet aux différents éléments du module d’être énumérés et découverts.

## <a name="see-also"></a>Voir aussi
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
