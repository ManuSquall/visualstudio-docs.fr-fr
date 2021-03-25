---
description: Écrit un dump dans un fichier.
title: 'IDebugProgram2 :: WriteDump | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8eca50eb6e828841a247ed51d7f73f61cb63e0e9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084426"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
Écrit un dump dans un fichier.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WriteDump( 
   DUMPTYPE  DumpType,
   LPCOLESTR pszDumpUrl
);
```

```csharp
int WriteDump( 
   enum_DUMPTYPE  DumpType,
   string         pszDumpUrl
);
```

## <a name="parameters"></a>Paramètres
`DumpType`\
dans Valeur de l’énumération [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) qui spécifie le type de vidage, par exemple short ou long.

`pszDumpUrl`\
dans URL vers laquelle écrire le vidage. En général, il se présente sous la forme de `file://c:\path\filename.ext` , mais peut être une URL valide.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Un vidage de programme inclut généralement le frame de pile actuel, la pile elle-même, une liste des threads en cours d’exécution dans le programme et éventuellement la mémoire dont le programme est propriétaire.

## <a name="see-also"></a>Voir aussi
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
