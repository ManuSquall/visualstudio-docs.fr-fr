---
title: IDebugProgramEngines2::EnumPossibleEngines Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 45916edbef4368c58f83426d6c73f3c692236cb9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722433"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
Retourne les GUIDs pour tous les moteurs de débogé (DE) possibles qui peuvent déboiffer ce programme.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumPossibleEngines( 
   DWORD  celtBuffer,
   GUID*  rgguidEngines,
   DWORD* pceltEngines
);
```

```csharp
int EnumPossibleEngines( 
   uint      celtBuffer,
   GUID[]    rgguidEngines,
   ref DWORD pceltEngines
);
```

## <a name="parameters"></a>Paramètres
`celtBuffer`\
[dans] Le nombre de DE GUIDs à revenir. Cela spécifie également `rgguidEngines` la taille maximale de la gamme.

`rgguidEngines`\
[dans, dehors] Un éventail de DE GUIDs à remplir.

`pceltEngines`\
[out] Retourne le nombre réel de GUIDs DE qui sont retournés.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur. Retourne [C] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` ou [C] 0x8007007A si le tampon n’est pas assez grand.

## <a name="remarks"></a>Notes
 Afin de déterminer combien de moteurs il ya, `celtBuffer` appelez cette méthode `rgguidEngines` une fois avec le paramètre réglé à 0 et le paramètre réglé à une valeur nulle. Cela `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` revient (0x8007007A pour `pceltEngines` C), et le paramètre renvoie la taille nécessaire du tampon.

## <a name="see-also"></a>Voir aussi
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
