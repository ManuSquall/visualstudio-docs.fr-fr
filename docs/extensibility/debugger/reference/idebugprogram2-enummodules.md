---
title: IDebugProgram2::EnumModules | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumModules
helpviewer_keywords:
- IDebugProgram2::EnumModules
ms.assetid: 876ac9da-3b7c-4156-b79a-8f340e9fcea6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e8de1f98cb6953ba713796e1dbd74de849a0aaf7
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56715932"
---
# <a name="idebugprogram2enummodules"></a>IDebugProgram2::EnumModules
Récupère une liste des modules de ce programme a chargé et s’exécute.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumModules( 
   IEnumDebugModules2** ppEnum
);
```

```csharp
int EnumModules( 
   out IEnumDebugModules2 ppEnum
);
```

#### <a name="parameters"></a>Paramètres
 `ppEnum`

 [out] Retourne un [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) objet qui contient une liste des modules.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Un module est un fichier DLL ou un assembly et se trouve généralement dans le **Modules** fenêtre de débogage.

## <a name="see-also"></a>Voir aussi
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)