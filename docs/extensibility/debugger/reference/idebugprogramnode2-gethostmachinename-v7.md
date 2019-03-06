---
title: IDebugProgramNode2::GetHostMachineName_V7 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b40d3350fb348afb654ae09785eb0956fb950bb
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689069"
---
# <a name="idebugprogramnode2gethostmachinenamev7"></a>IDebugProgramNode2::GetHostMachineName_V7

> [!Note]
> DÉCONSEILLÉ. N’UTILISEZ PAS.

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

#### <a name="parameters"></a>Paramètres

`pbstrHostMachineName`

 [out] Retourne le nom de l’ordinateur dans lequel le programme est en cours d’exécution.

## <a name="return-value"></a>Valeur de retour

Une implémentation doit toujours retourner `E_NOTIMPL`.

## <a name="remarks"></a>Notes

> [!WARNING]
> À compter de Visual Studio 2005, cette méthode n’est plus utilisée et doit toujours retourner `E_NOTIMPL`.

## <a name="see-also"></a>Voir aussi

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)