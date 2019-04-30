---
title: IDebugAlias::GetICorDebugValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59506af5ad48bd18c454f4c59367921eed1e679a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62924075"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
Récupère une interface en code managé qui représente la valeur associée à cet alias.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetICorDebugValue(
   IUnknown** ppUnk
);
```

```csharp
int GetICorDebugValue(
   out object ppUnk
);
```

#### <a name="parameters"></a>Paramètres
 `ppUnk`

 [out] `IUnknown` interface qui représente la valeur associée à cet alias. Cette interface peut être interrogée pour la `ICorDebugValue` interface.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode s’applique uniquement aux valeurs gérés (les `ICorDebugValue` une interface n’est disponible dans le [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] et est défini dans le [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] SDK dans le fichier cordebug.idl).

## <a name="see-also"></a>Voir aussi
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)