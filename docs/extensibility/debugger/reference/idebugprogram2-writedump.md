---
title: IDebugProgram2::WriteDump | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 941a04d42c52051078a4fe4d0075a27c358cb15f
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212629"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
Écrit un fichier de vidage dans un fichier.

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
[in] Une valeur comprise entre le [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) énumération qui spécifie le type d’image, par exemple, short ou long.

`pszDumpUrl`\
[in] L’URL pour l’écriture de l’image mémoire. En règle générale, il s’agit dans le formulaire de `file://c:\path\filename.ext`, mais il peut être n’importe quelle URL valide.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Un vidage de programme inclut généralement le frame de pile actuel, la pile proprement dit, une liste des threads en cours d’exécution dans le programme et éventuellement de mémoire qui possède le programme.

## <a name="see-also"></a>Voir aussi
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)