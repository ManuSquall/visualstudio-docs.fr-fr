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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d0e4c90034d19635993196a0cd00ffcb06f26433
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171925"
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
