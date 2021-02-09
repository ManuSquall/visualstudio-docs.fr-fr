---
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
ms.openlocfilehash: 265c77acdb15069c1fcd7f33d93d4ff74a528eca
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896147"
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

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Remarques
 Un vidage de programme inclut généralement le frame de pile actuel, la pile elle-même, une liste des threads en cours d’exécution dans le programme et éventuellement la mémoire dont le programme est propriétaire.

## <a name="see-also"></a>Voir aussi
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
