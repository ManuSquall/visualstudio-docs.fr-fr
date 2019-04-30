---
title: IDebugMethodField::GetGlobalContainer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetGlobalContainer
helpviewer_keywords:
- IDebugMethodField::GetGlobalContainer method
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40bbee4c00425c4f46ccde35b8a8c810e1d7c8e6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62872814"
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

#### <a name="parameters"></a>Paramètres
 `ppClass`

 [out] Retourne un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) représentant le module dans lequel cette méthode est définie.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Retourné [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) objet représente l’ensemble du module et un objet artificiel, autrement dit, le module lui-même ne dispose pas d’une classe réelle, mais elle peut être représentée par un `IDebugClassField` objet, ce qui permet les différents éléments du module d’être énumérée et découvertes.

## <a name="see-also"></a>Voir aussi
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)