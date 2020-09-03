---
title: 'IDebugProgramNode2 :: GetHostMachineName_V7 | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722087"
---
# <a name="idebugprogramnode2gethostmachinename_v7"></a>IDebugProgramNode2::GetHostMachineName_V7

> [!Note]
> Déconseillé. N’UTILISEZ PAS.

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
à Retourne le nom de l’ordinateur sur lequel le programme est en cours d’exécution.

## <a name="return-value"></a>Valeur renvoyée

Une implémentation doit toujours retourner `E_NOTIMPL` .

## <a name="remarks"></a>Notes

> [!WARNING]
> À compter de Visual Studio 2005, cette méthode n’est plus utilisée et doit toujours retourner `E_NOTIMPL` .

## <a name="see-also"></a>Voir aussi

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
