---
title: IDebugProgramNode2::GetProgramName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetProgramName
helpviewer_keywords:
- IDebugProgramNode2::GetProgramName
ms.assetid: 510c7f5d-48ff-4d9f-ad79-fbad9f15239d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dc941f0bf88a6e41b81bfdbf6f6c948c34e8e477
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66203817"
---
# <a name="idebugprogramnode2getprogramname"></a>IDebugProgramNode2::GetProgramName
Obtient le nom du programme.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetProgramName (
    BSTR* pbstrProgramName
);
```

```csharp
int GetProgramName (
    out string pbstrProgramName
);
```

## <a name="parameters"></a>Paramètres
`pbstrProgramName`\
[out] Retourne le nom du programme.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
Le nom d’un programme n’est pas la même chose que le chemin d’accès au programme, bien que le nom du programme peut faire partie d’un chemin d’accès.

## <a name="example"></a>Exemple
L’exemple suivant montre comment implémenter cette méthode pour une simple `CProgram` objet qui implémente le [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) interface. Le `MakeBstr` fonction alloue une copie de la chaîne spécifiée en tant que BSTR.

```cpp
HRESULT CProgram::GetProgramName(BSTR* pbstrProgramName) {
    if (!pbstrProgramName)
        return E_INVALIDARG;

    // Assign the member program name to the passed program name.
    *pbstrProgramName = MakeBstr(m_pszProgramName);
    return NOERROR;
}
```

## <a name="see-also"></a>Voir aussi
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
