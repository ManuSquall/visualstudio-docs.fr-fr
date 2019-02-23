---
title: BP_LOCATION_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_TYPE
helpviewer_keywords:
- BP_LOCATION_TYPE structure
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1695c61a829cf1439ed773e48088430f36f8c653
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56715659"
---
# <a name="bplocationtype"></a>BP_LOCATION_TYPE
Spécifie le type d’emplacement du point d’arrêt pour une demande de point d’arrêt.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_BP_LOCATION_TYPE {
    BPLT_NONE               = 0x00000000,
    BPLT_FILE_LINE          = 0x00010000,
    BPLT_FUNC_OFFSET        = 0x00020000,
    BPLT_CONTEXT            = 0x00030000,
    BPLT_STRING             = 0x00040000,
    BPLT_ADDRESS            = 0x00050000,
    BPLT_RESOLUTION         = 0x00060000,
    BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,
    BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,
    BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,
    BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,
    BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,
    BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,
    BPLT_TYPE_MASK          = 0x0000FFFF,
    BPLT_LOCATION_TYPE_MASK = 0xFFFF0000
};
typedef DWORD BP_LOCATION_TYPE;
```

```csharp
public enum enum_BP_LOCATION_TYPE {
    BPLT_NONE               = 0x00000000,
    BPLT_FILE_LINE          = 0x00010000,
    BPLT_FUNC_OFFSET        = 0x00020000,
    BPLT_CONTEXT            = 0x00030000,
    BPLT_STRING             = 0x00040000,
    BPLT_ADDRESS            = 0x00050000,
    BPLT_RESOLUTION         = 0x00060000,
    BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,
    BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,
    BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,
    BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,
    BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,
    BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,
    BPLT_TYPE_MASK          = 0x0000FFFF,
    BPLT_LOCATION_TYPE_MASK = 0xFFFF0000
};
```

## <a name="members"></a>Membres
BPLT_NONE ne spécifie aucun emplacement de point d’arrêt.

BPLT_FILE_LINE Spécifie le type d’emplacement du point d’arrêt comme une ligne du fichier.

BPLT_FUNC_OFFSET Spécifie le type d’emplacement du point d’arrêt comme un décalage de fonction.

BPLT_CONTEXT Spécifie le type d’emplacement du point d’arrêt comme un contexte.

BPLT_STRING Spécifie le type d’emplacement du point d’arrêt sous forme de chaîne.

BPLT_ADDRESS Spécifie le type d’emplacement du point d’arrêt en tant qu’adresse.

BPLT_RESOLUTION Spécifie le type d’emplacement du point d’arrêt comme une résolution.

BPLT_CODE_FILE_LINE Spécifie le type d’emplacement du point d’arrêt comme une ligne de code source.

BPLT_CODE_FUNC_OFFSET Spécifie le type d’emplacement du point d’arrêt comme un décalage de fonction de code.

BPLT_CODE_CONTEXT Spécifie le type d’emplacement du point d’arrêt comme un contexte de code.

BPLT_CODE_STRING Spécifie le type d’emplacement du point d’arrêt comme une chaîne de code.

BPLT_CODE_ADDRESS Spécifie le type d’emplacement du point d’arrêt comme une adresse de code.

BPLT_DATA_STRING Spécifie le type d’emplacement du point d’arrêt comme une chaîne de données.

BPLT_TYPE_MASK spécifie un masque de bits, afin que le type de point d’arrêt peut être extraites en dehors de la valeur.

BPLT_LOCATION_TYPE_MASK spécifie un masque de bits, afin que le type d’emplacement de point d’arrêt permettre être extraites de la valeur.

## <a name="remarks"></a>Notes
Passé en tant que paramètre à la [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md) (méthode).

Un type d’emplacement de point d’arrêt se compose d’un type de point d’arrêt et un type d’emplacement. Cela signifie qu’un type d’emplacement de point d’arrêt n’est jamais simplement un type de point d’arrêt (par exemple, `BPT_CODE`) ou un type d’emplacement (par exemple, `BPLT_FILE_LINE`). Les constantes prédéfinies pour tous les types d’emplacement de point d’arrêt actuellement pris en charge sont incluses dans cette énumération (`BPLT_CODE_FILE_LINE` via `BPLT_DATA_STRING`).

`BPT_CODE` et `BPT_DATA` sont membres de la [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) énumération.

## <a name="requirements"></a>Spécifications
En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
