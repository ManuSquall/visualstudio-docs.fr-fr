---
description: Retourne les GUID pour tous les moteurs de débogage possibles (DE) qui peuvent déboguer ce programme.
title: 'IDebugProgramEngines2 :: EnumPossibleEngines | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e5719728637f26ed61283578565470b39fc60455
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151582"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
Retourne les GUID pour tous les moteurs de débogage possibles (DE) qui peuvent déboguer ce programme.

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
dans Nombre de de GUID à retourner. Cela spécifie également la taille maximale du `rgguidEngines` tableau.

`rgguidEngines`\
[in, out] Tableau de de DE GUID à remplir.

`pceltEngines`\
à Retourne le nombre réel de de GUID retournés.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur. Retourne [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` ou [C#] 0x8007007A si la mémoire tampon n’est pas assez grande.

## <a name="remarks"></a>Notes
 Pour déterminer le nombre de moteurs, appelez cette méthode une fois avec le `celtBuffer` paramètre défini sur 0 et le `rgguidEngines` paramètre défini sur une valeur null. Cela retourne `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` (0x8007007A pour C#) et le `pceltEngines` paramètre retourne la taille nécessaire de la mémoire tampon.

## <a name="see-also"></a>Voir aussi
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
