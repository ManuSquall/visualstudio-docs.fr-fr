---
description: 'IDebugProgramNode2 :: GetProgramName obtient le nom du programme.'
title: 'IDebugProgramNode2 :: GetProgramName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetProgramName
helpviewer_keywords:
- IDebugProgramNode2::GetProgramName
ms.assetid: 510c7f5d-48ff-4d9f-ad79-fbad9f15239d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 376054406d0c127a0bbdcd5ee0a90bc694f9cd02
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087234"
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
à Retourne le nom du programme.

## <a name="return-value"></a>Valeur renvoyée
En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
Le nom d’un programme n’est pas identique au chemin d’accès au programme, même si le nom du programme peut faire partie d’un tel chemin d’accès.

## <a name="example"></a>Exemple
L’exemple suivant montre comment implémenter cette méthode pour un `CProgram` objet simple qui implémente l’interface [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) . La `MakeBstr` fonction alloue une copie de la chaîne spécifiée en tant que BSTR.

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
