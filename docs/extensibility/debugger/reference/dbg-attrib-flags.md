---
description: Décrit différents attributs pour un IDebugProperty2 ou une interface IDebugReference2.
title: DBG_ATTRIB_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DBG_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS enumerations
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f467c9ac66bc249974f919a48a1527bebb26f361
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170716"
---
# <a name="dbg_attrib_flags"></a>DBG_ATTRIB_FLAGS
Décrit différents attributs pour un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) ou une interface [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) . Membre de la structure [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) .

## <a name="syntax"></a>Syntaxe

```cpp
#define DBG_ATTRIB_NONE                 0x0000000000000000,
#define DBG_ATTRIB_ALL                  0x00000000ffffffff,

// Attributes about the object itself

#define DBG_ATTRIB_OBJ_IS_EXPANDABLE    0x0000000000000001,
#define DBG_ATTRIB_OBJ_HAS_ID           0x0000000000000002,
#define DBG_ATTRIB_OBJ_CAN_HAVE_ID      0x0000000000000004,

// Attributes about the value of the object

#define DBG_ATTRIB_VALUE_READONLY       0x0000000000000010,
#define DBG_ATTRIB_VALUE_ERROR          0x0000000000000020,
#define DBG_ATTRIB_VALUE_SIDE_EFFECT    0x0000000000000040,
#define DBG_ATTRIB_OVERLOADED_CONTAINER 0x0000000000000080,
#define DBG_ATTRIB_VALUE_BOOLEAN        0x0000000000000100,
#define DBG_ATTRIB_VALUE_BOOLEAN_TRUE   0x0000000000000200,
#define DBG_ATTRIB_VALUE_INVALID        0x0000000000000400,
#define DBG_ATTRIB_VALUE_NAT            0x0000000000000800,
#define DBG_ATTRIB_VALUE_AUTOEXPANDED   0x0000000000001000,
#define DBG_ATTRIB_VALUE_TIMEOUT        0x0000000000002000,
#define DBG_ATTRIB_VALUE_RAW_STRING     0x0000000000004000,
#define DBG_ATTRIB_VALUE_CUSTOM_VIEWER  0x0000000000008000,

// Attributes about field access types for the object

#define DBG_ATTRIB_ACCESS_NONE          0x0000000000010000,
#define DBG_ATTRIB_ACCESS_PUBLIC        0x0000000000020000,
#define DBG_ATTRIB_ACCESS_PRIVATE       0x0000000000040000,
#define DBG_ATTRIB_ACCESS_PROTECTED     0x0000000000080000,
#define DBG_ATTRIB_ACCESS_FINAL         0x0000000000100000,
#define DBG_ATTRIB_ACCESS_ALL           0x00000000001f0000,

// Attributes for the storage types of the object

#define DBG_ATTRIB_STORAGE_NONE         0x0000000001000000,
#define DBG_ATTRIB_STORAGE_GLOBAL       0x0000000002000000,
#define DBG_ATTRIB_STORAGE_STATIC       0x0000000004000000,
#define DBG_ATTRIB_STORAGE_REGISTER     0x0000000008000000,
#define DBG_ATTRIB_STORAGE_ALL          0x000000000f000000,

// Attributes for the type modifiers on the object

#define DBG_ATTRIB_TYPE_NONE            0x0000000100000000,
#define DBG_ATTRIB_TYPE_VIRTUAL         0x0000000200000000,
#define DBG_ATTRIB_TYPE_CONSTANT        0x0000000400000000,
#define DBG_ATTRIB_TYPE_SYNCHRONIZED    0x0000000800000000,
#define DBG_ATTRIB_TYPE_VOLATILE        0x0000001000000000,
#define DBG_ATTRIB_TYPE_ALL             0x0000001f00000000,

// Attributes that describe the type of object

#define DBG_ATTRIB_DATA                 0x0000010000000000,
#define DBG_ATTRIB_METHOD               0x0000020000000000,
#define DBG_ATTRIB_PROPERTY             0x0000040000000000,
#define DBG_ATTRIB_CLASS                0x0000080000000000,
#define DBG_ATTRIB_BASECLASS            0x0000100000000000,
#define DBG_ATTRIB_INTERFACE            0x0000200000000000,
#define DBG_ATTRIB_INNERCLASS           0x0000400000000000,
#define DBG_ATTRIB_MOSTDERIVED          0x0000800000000000,
#define DBG_ATTRIB_CHILD_ALL            0x0000ff0000000000,

// Miscellaneous attributes

#define DBG_ATTRIB_MULTI_CUSTOM_VIEWERS 0x0001000000000000

typedef UINT64 DBG_ATTRIB_FLAGS;
```

```csharp
public const int DBG_ATTRIB_NONE                 = 0x0000000000000000,
public const int DBG_ATTRIB_ALL                  = 0x00000000ffffffff,

// Attributes about the object itself

public const int DBG_ATTRIB_OBJ_IS_EXPANDABLE    = 0x0000000000000001,
public const int DBG_ATTRIB_OBJ_HAS_ID           = 0x0000000000000002,
public const int DBG_ATTRIB_OBJ_CAN_HAVE_ID      = 0x0000000000000004,

// Attributes about the value of the object

public const int DBG_ATTRIB_VALUE_READONLY       = 0x0000000000000010,
public const int DBG_ATTRIB_VALUE_ERROR          = 0x0000000000000020,
public const int DBG_ATTRIB_VALUE_SIDE_EFFECT    = 0x0000000000000040,
public const int DBG_ATTRIB_OVERLOADED_CONTAINER = 0x0000000000000080,
public const int DBG_ATTRIB_VALUE_BOOLEAN        = 0x0000000000000100,
public const int DBG_ATTRIB_VALUE_BOOLEAN_TRUE   = 0x0000000000000200,
public const int DBG_ATTRIB_VALUE_INVALID        = 0x0000000000000400,
public const int DBG_ATTRIB_VALUE_NAT            = 0x0000000000000800,
public const int DBG_ATTRIB_VALUE_AUTOEXPANDED   = 0x0000000000001000,
public const int DBG_ATTRIB_VALUE_TIMEOUT        = 0x0000000000002000,
public const int DBG_ATTRIB_VALUE_RAW_STRING     = 0x0000000000004000,
public const int DBG_ATTRIB_VALUE_CUSTOM_VIEWER  = 0x0000000000008000,

// Attributes about field access types for the object

public const int DBG_ATTRIB_ACCESS_NONE          = 0x0000000000010000,
public const int DBG_ATTRIB_ACCESS_PUBLIC        = 0x0000000000020000,
public const int DBG_ATTRIB_ACCESS_PRIVATE       = 0x0000000000040000,
public const int DBG_ATTRIB_ACCESS_PROTECTED     = 0x0000000000080000,
public const int DBG_ATTRIB_ACCESS_FINAL         = 0x0000000000100000,
public const int DBG_ATTRIB_ACCESS_ALL           = 0x00000000001f0000,

// Attributes for the storage types of the object

public const int DBG_ATTRIB_STORAGE_NONE         = 0x0000000001000000,
public const int DBG_ATTRIB_STORAGE_GLOBAL       = 0x0000000002000000,
public const int DBG_ATTRIB_STORAGE_STATIC       = 0x0000000004000000,
public const int DBG_ATTRIB_STORAGE_REGISTER     = 0x0000000008000000,
public const int DBG_ATTRIB_STORAGE_ALL          = 0x000000000f000000,

// Attributes for the type modifiers on the object

public const int DBG_ATTRIB_TYPE_NONE            = 0x0000000100000000,
public const int DBG_ATTRIB_TYPE_VIRTUAL         = 0x0000000200000000,
public const int DBG_ATTRIB_TYPE_CONSTANT        = 0x0000000400000000,
public const int DBG_ATTRIB_TYPE_SYNCHRONIZED    = 0x0000000800000000,
public const int DBG_ATTRIB_TYPE_VOLATILE        = 0x0000001000000000,
public const int DBG_ATTRIB_TYPE_ALL             = 0x0000001f00000000,

// Attributes that describe the type of object

public const int DBG_ATTRIB_DATA                 = 0x0000010000000000,
public const int DBG_ATTRIB_METHOD               = 0x0000020000000000,
public const int DBG_ATTRIB_PROPERTY             = 0x0000040000000000,
public const int DBG_ATTRIB_CLASS                = 0x0000080000000000,
public const int DBG_ATTRIB_BASECLASS            = 0x0000100000000000,
public const int DBG_ATTRIB_INTERFACE            = 0x0000200000000000,
public const int DBG_ATTRIB_INNERCLASS           = 0x0000400000000000,
public const int DBG_ATTRIB_MOSTDERIVED          = 0x0000800000000000,
public const int DBG_ATTRIB_CHILD_ALL            = 0x0000ff0000000000,

// Miscellaneous attributes

public const int DBG_ATTRIB_MULTI_CUSTOM_VIEWERS = 0x0001000000000000
```

## <a name="members"></a>Membres
 `DBG_ATTRIB_NONE`\
 Indique l'absence d'attribut.

 `DBG_ATTRIB_ALL`\
 Indique tous les attributs.

 `DBG_ATTRIB_OBJ_IS_EXPANDABLE`\
 Indique que la référence ou la propriété a des enfants.

 `DBG_ATTRIB_OBJ_HAS_ID`\
 Indique qu’un ID a été créé pour cet objet.

 `DBG_ATTRIB_OBJ_CAN_HAVE_ID`\
 Indique qu’un ID pour cet objet peut être créé.

 `DBG_ATTRIB_VALUE_READONLY`\
 Indique que la valeur est en lecture seule.

 `DBG_ATTRIB_VALUE_ERROR`\
 Indique que la valeur est une erreur.

 `DBG_ATTRIB_VALUE_SIDE_EFFECT`\
 Indique que l’évaluation a un effet secondaire.

 `DBG_ATTRIB_OVERLOADED_CONTAINER`\
 Indique que cette propriété est véritablement un conteneur de surcharges.

 `DBG_ATTRIB_VALUE_BOOLEAN`\
 Indique que la valeur de `DEBUG_PROPERTY_INFO::bstrValue` est booléenne.

 `DBG_ATTRIB_VALUE_BOOLEAN_TRUE`\
 Indique que la valeur de `DEBUG_PROPERTY_INFO::bstrValue` est booléenne et `TRUE` .

 `DBG_ATTRIB_VALUE_INVALID`\
 Indique que la valeur de `DEBUG_PROPERTY_INFO::bstrValue` n'est pas valide.

 `DBG_ATTRIB_VALUE_NAT`\
 Indique que la valeur de `DEBUG_PROPERTY_INFO::bstrValue` n’est *pas un élément*(NAT). NAT décrit un indicateur de Registre dans les processeurs Intel 64 bits qui indiquent des exceptions spéculatives différées.

 `DBG_ATTRIB_VALUE_AUTOEXPANDED`\
 Indique que la valeur dans `DEBUG_PROPERTY_INFO::bstrValue` a peut-être été développée automatiquement.

 `DBG_ATTRIB_VALUE_TIMEOUT`\
 Indique qu’une évaluation a dépassé le délai d’attente.

 `DBG_ATTRIB_VALUE_RAW_STRING`\
 Indique que la valeur de `DEBUG_PROPERTY_INFO::bstrValue` peut être représentée par une chaîne brute.

 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER`\
 Indique qu’au moins une visionneuse personnalisée est associée à cette propriété.

 `DBG_ATTRIB_ACCESS_NONE`\
 Indique un objet qui n’a ni `public` , `private` ni `protected` accès de type.

 `DBG_ATTRIB_ACCESS_PUBLIC`\
 Indique un objet qui possède un accès public.

 `DBG_ATTRIB_ACCESS_PRIVATE`\
 Indique un objet qui possède un accès privé.

 `DBG_ATTRIB_ACCESS_PROTECTED`\
 Indique un objet qui possède un accès protégé.

 `DBG_ATTRIB_ACCESS_FINAL`\
 Indique un objet qui possède un accès final.

 `DBG_ATTRIB_ACCESS_ALL`\
 Masque à partir duquel extraire les attributs d’accès `DBG_ATTRIB_FLAGS` .

 `DBG_ATTRIB_STORAGE_NONE`\
 Indique qu’il n’existe aucun type de stockage spécifié.

 `DBG_ATTRIB_STORAGE_GLOBAL`\
 Indique un stockage global.

 `DBG_ATTRIB_STORAGE_STATIC`\
 Indique un stockage statique.

 `DBG_ATTRIB_STORAGE_REGISTER`\
 Indique le stockage dans le registre.

 `DBG_ATTRIB_STORAGE_ALL`\
 Masque à partir duquel extraire les attributs de stockage `DBG_ATTRIB_FLAGS` .

 `DBG_ATTRIB_TYPE_NONE`\
 Indique qu’il n’y a pas de modificateur de type.

 `DBG_ATTRIB_TYPE_VIRTUAL`\
 Indique que le type d’objet est virtuel.

 `DBG_ATTRIB_TYPE_CONSTANT`\
 Indique que le type d'objet est constant.

 `DBG_ATTRIB_TYPE_SYNCHRONIZED`\
 Indique que le type d’objet est synchronisé.

 `DBG_ATTRIB_TYPE_VOLATILE`\
 Indique que le type d’objet est volatile.

 `DBG_ATTRIB_TYPE_ALL`\
 Masque à partir duquel extraire les attributs de type `DBG_ATTRIB_FLAGS` .

 `DBG_ATTRIB_DATA`\
 Indique que cet objet est un champ de données.

 `DBG_ATTRIB_METHOD`\
 Indique que cet objet est une méthode.

 `DBG_ATTRIB_PROPERTY`\
 Indique que cet objet est une propriété.

 `DBG_ATTRIB_CLASS`\
 Indique que cet objet est une classe.

 `DBG_ATTRIB_BASECLASS`\
 Indique que cet objet est une classe de base.

 `DBG_ATTRIB_INTERFACE`\
 Indique que cet objet est une interface.

 `DBG_ATTRIB_INNERCLASS`\
 Indique que cet objet est une classe interne.

 `DBG_ATTRIB_MOSTDERIVED`\
 Indique que cet objet est « le *plus dérivé*». Le terme « le *plus dérivé*» signifie le type réel de l’objet, et non le type de sa référence.

 `DBG_ATTRIB_CHILD_ALL`\
 Indique un masque de `DBG_ATTRIB_DATA` par le biais de `DBG_ATTRIB_MOSTDERIVED` .

 `DBG_ATTRIB_MULTI_CUSTOM_VIEWERS`\
 Indique que plusieurs visionneuses personnalisées sont associées à l’objet.

## <a name="remarks"></a>Notes

> [!NOTE]
> Les valeurs de cette énumération ne sont pas réellement définies dans l’assembly pour C#. Au lieu de cela, vous devez copier les définitions dans votre fichier source.

 Ces indicateurs sont également utilisés pour filtrer les enfants d’un objet, par exemple, lorsqu’ils sont passés en tant qu’argument à [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md). Les valeurs peuvent être combinées avec une opération de bits `OR` .

 L' `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` indicateur est une indication de l' [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] obtention de l’interface [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) à partir de l’interface [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) et de l’appel de [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) pour obtenir une liste de visionneuses personnalisées.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
