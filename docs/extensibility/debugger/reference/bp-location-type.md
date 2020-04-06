---
title: BP_LOCATION_TYPE Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_TYPE
helpviewer_keywords:
- BP_LOCATION_TYPE structure
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50e6bdc0dba8f6bcbdd55c45132dff02735786d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737943"
---
# <a name="bp_location_type"></a>BP_LOCATION_TYPE
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

## <a name="fields"></a>Champs
`BPLT_NONE`\
Spécifie aucun emplacement de point d’arrêt.

`BPLT_FILE_LINE`\
Spécifie le type d’emplacement du point d’arrêt comme une ligne de fichiers.

`BPLT_FUNC_OFFSET`\
Spécifie le type d’emplacement du point d’arrêt comme un décalage de fonction.

`BPLT_CONTEXT`\
Spécifie le type d’emplacement du point d’arrêt comme contexte.

`BPLT_STRING`\
Spécifie le type d’emplacement du point d’arrêt comme une chaîne.

`BPLT_ADDRESS`\
Spécifie le type d’emplacement du point d’arrêt comme adresse.

`BPLT_RESOLUTION`\
Spécifie le type de point d’arrêt de l’emplacement comme une résolution.

`BPLT_CODE_FILE_LINE`\
Spécifie le type de localisation du point d’arrêt comme une ligne de code source.

`BPLT_CODE_FUNC_OFFSET`\
Spécifie le type de localisation du point d’arrêt comme un décalage de fonction de code.

`BPLT_CODE_CONTEXT`\
Spécifie le type de localisation du point d’arrêt comme contexte de code.

`BPLT_CODE_STRING`\
Spécifie le type d’emplacement du point d’arrêt comme une chaîne de code.

`BPLT_CODE_ADDRESS`\
Spécifie le type de localisation du point d’arrêt comme une adresse de code.

`BPLT_DATA_STRING`\
Spécifie le type de localisation du point d’arrêt comme chaîne de données.

`BPLT_TYPE_MASK`\
Spécifie un peu de masque, de sorte que le type de point d’arrêt peut être extrait de la valeur.

`BPLT_LOCATION_TYPE_MASK`\
Spécifie un peu de masque, de sorte que le type de localisation de point de rupture peut être extrait de la valeur.

## <a name="remarks"></a>Notes
Passé comme paramètre à la méthode [GetLocationType.](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)

Un type de localisation de point d’arrêt est composé d’un type de point d’arrêt et d’un type d’emplacement. Cela signifie qu’un type d’emplacement de point d’arrêt n’est jamais seulement un type de point d’arrêt (par exemple, `BPT_CODE`) ou un type d’emplacement (par exemple, `BPLT_FILE_LINE`). Les constantes prédéfinies pour tous les types de localisation`BPLT_CODE_FILE_LINE` `BPLT_DATA_STRING`de point de rupture actuellement pris en charge sont incluses dans cette énumération (à travers ).

`BPT_CODE`et `BPT_DATA` sont membres de [l’énumération BP_TYPE.](../../../extensibility/debugger/reference/bp-type.md)

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
