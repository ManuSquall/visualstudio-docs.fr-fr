---
title: IDebugProgramNode2::GetHostMachineName_V7 Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a8c328c83ebe52f842b1990debe07aed3fd764c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722087"
---
# <a name="idebugprogramnode2gethostmachinename_v7"></a>IDebugProgramNode2::GetHostMachineName_V7

> [!Note]
> Déconseillée. NE PAS UTILISER.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetHostMachineName_V7 (
   BSTR* pbstrHostMachineName
);
```

```csharp
int GetHostMachineName_V7 (
   out string pbstrHostMachineName
);
```

## <a name="parameters"></a>Paramètres

`pbstrHostMachineName`\
[out] Retourne le nom de la machine dans laquelle le programme est en cours d’exécution.

## <a name="return-value"></a>Valeur de retour

Une mise en `E_NOTIMPL`œuvre doit toujours revenir .

## <a name="remarks"></a>Notes

> [!WARNING]
> A partir de Visual Studio 2005, cette méthode `E_NOTIMPL`n’est plus utilisée et devrait toujours revenir .

## <a name="see-also"></a>Voir aussi

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
