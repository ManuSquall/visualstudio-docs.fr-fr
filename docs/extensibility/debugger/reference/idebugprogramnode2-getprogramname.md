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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 88a4bc58f5d91cdb52482f4dc862446cfc9e7eb1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161383"
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
