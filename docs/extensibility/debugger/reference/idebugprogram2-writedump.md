---
title: IDebugProgram2::WriteDump Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 333535a727d88f66346ba4c94cb08b4917b8acfd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722736"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
Écrit une décharge à un fichier.

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
[dans] Une valeur de l’énumération [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) qui spécifie le type de décharge, par exemple, courte ou longue.

`pszDumpUrl`\
[dans] L’URL pour écrire le dépotoir à. Typiquement, c’est sous `file://c:\path\filename.ext`la forme de , mais peut être toute URL valide.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Un vidage de programme inclurait typiquement le cadre actuel de pile, la pile elle-même, une liste des fils exécutant dans le programme, et peut-être n’importe quel mémoire que le programme possède.

## <a name="see-also"></a>Voir aussi
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
