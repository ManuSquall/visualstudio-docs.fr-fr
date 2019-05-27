---
title: IDebugEngine2::SetRegistryRoot | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetRegistryRoot
helpviewer_keywords:
- IDebugEngine2::SetRegistryRoot
ms.assetid: d0d81202-8a4a-4bc3-b297-30a047c5ec60
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d469dff028b0139c225b89e256896e6815f5e4fc
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66207462"
---
# <a name="idebugengine2setregistryroot"></a>IDebugEngine2::SetRegistryRoot
Définit la racine du Registre pour le moteur de débogage (dé).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetRegistryRoot( 
   LPCOLESTR pszRegistryRoot
);
```

```csharp
int SetRegistryRoot( 
   string pszRegistryRoot
);
```

## <a name="parameters"></a>Paramètres
`pszRegistryRoot`\
[in] La racine de Registre à utiliser.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode permet de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] pour spécifier une racine de Registre autre que l’Allemagne doit utiliser pour obtenir les paramètres de Registre ; par exemple, « HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp ».

## <a name="see-also"></a>Voir aussi
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)