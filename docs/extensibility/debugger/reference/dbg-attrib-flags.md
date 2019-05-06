---
title: DBG_ATTRIB_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DBG_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS enumerations
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 831d1326d88e70ffaba2cc0c242c55d7325be705
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689328"
---
# <a name="dbgattribflags"></a>DBG_ATTRIB_FLAGS
Décrit les différents attributs pour un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) ou un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) interface. Membre de la [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) structure.

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
 DBG_ATTRIB_NONE n’indique aucun attribut.

 DBG_ATTRIB_ALL indique tous les attributs.

 DBG_ATTRIB_OBJ_IS_EXPANDABLE indique que la référence ou la propriété a des enfants.

 DBG_ATTRIB_OBJ_HAS_ID indique qu’un ID pour cet objet a été créé.

 DBG_ATTRIB_OBJ_CAN_HAVE_ID indique qu’un ID pour cet objet peut être créé.

 DBG_ATTRIB_VALUE_READONLY indique que la valeur est en lecture seule.

 DBG_ATTRIB_VALUE_ERROR indique que la valeur est une erreur.

 DBG_ATTRIB_VALUE_SIDE_EFFECT indique que la version d’évaluation avait un effet secondaire.

 DBG_ATTRIB_OVERLOADED_CONTAINER indique que cette propriété est vraiment un conteneur de surcharges.

 DBG_ATTRIB_VALUE_BOOLEAN indique que la valeur de `DEBUG_PROPERTY_INFO::bstrValue` est la valeur booléenne.

 DBG_ATTRIB_VALUE_BOOLEAN_TRUE indique que la valeur dans `DEBUG_PROPERTY_INFO::bstrValue` est booléen et `TRUE`.

 DBG_ATTRIB_VALUE_INVALID indique que la valeur de `DEBUG_PROPERTY_INFO::bstrValue` n’est pas valide.

 DBG_ATTRIB_VALUE_NAT indique que la valeur dans `DEBUG_PROPERTY_INFO::bstrValue` est «*pas une chose*» (NAT). NAT décrit un indicateur de Registre dans les processeurs Intel 64 bits qui indique les exceptions spéculatives différées.

 DBG_ATTRIB_VALUE_AUTOEXPANDED indique que la valeur de `DEBUG_PROPERTY_INFO::bstrValue` a été éventuellement développé en automatique.

 DBG_ATTRIB_VALUE_TIMEOUT indique qu’un formulaire d’évaluation a expiré.

 DBG_ATTRIB_VALUE_RAW_STRING indique que la valeur de `DEBUG_PROPERTY_INFO::bstrValue` peut être représenté par une chaîne brute.

 DBG_ATTRIB_VALUE_CUSTOM_VIEWER indique que cette propriété a au moins une visionneuse personnalisée associée.

 DBG_ATTRIB_ACCESS_NONE indique un objet qui ne possède aucun `public`, `private`, ni `protected` type d’accès.

 DBG_ATTRIB_ACCESS_PUBLIC indique un objet qui possède un accès public.

 DBG_ATTRIB_ACCESS_PRIVATE indique un objet qui possède un accès privé.

 DBG_ATTRIB_ACCESS_PROTECTED indique un objet qui possède un accès protégé.

 DBG_ATTRIB_ACCESS_FINAL indique un objet qui a accès final.

 Masque DBG_ATTRIB_ACCESS_ALL pour extraire l’accès aux attributs de `DBG_ATTRIB_FLAGS`.

 DBG_ATTRIB_STORAGE_NONE indique qu’il n’existe aucun type de stockage spécifié.

 Stockage global DBG_ATTRIB_STORAGE_GLOBAL indique.

 DBG_ATTRIB_STORAGE_STATIC indique un stockage statique.

 DBG_ATTRIB_STORAGE_REGISTER indique le stockage dans le Registre.

 Masque DBG_ATTRIB_STORAGE_ALL pour extraire le stockage des attributs à partir de `DBG_ATTRIB_FLAGS`.

 DBG_ATTRIB_TYPE_NONE indique qu’il n’existe aucun modificateur de type.

 DBG_ATTRIB_TYPE_VIRTUAL indique que le type d’objet est virtuel.

 DBG_ATTRIB_TYPE_CONSTANT indique que le type d’objet est constant.

 DBG_ATTRIB_TYPE_SYNCHRONIZED indique que le type d’objet est synchronisé.

 DBG_ATTRIB_TYPE_VOLATILE indique que le type d’objet est volatil.

 Masque DBG_ATTRIB_TYPE_ALL pour extraire le type des attributs à partir de `DBG_ATTRIB_FLAGS`.

 DBG_ATTRIB_DATA indique que cet objet est un champ de données.

 DBG_ATTRIB_METHOD indique que cet objet est une méthode.

 DBG_ATTRIB_PROPERTY indique que cet objet est une propriété.

 DBG_ATTRIB_CLASS indique que cet objet est une classe.

 DBG_ATTRIB_BASECLASS indique que cet objet est une classe de base.

 DBG_ATTRIB_INTERFACE indique que cet objet est une interface.

 DBG_ATTRIB_INNERCLASS indique que cet objet est une classe interne.

 DBG_ATTRIB_MOSTDERIVED indique que cet objet est «*plus dérivé*». Le terme «*plus dérivé*» signifie que le type réel de l’objet et non le type de sa référence.

 DBG_ATTRIB_CHILD_ALL indique un masque de `DBG_ATTRIB_DATA` via `DBG_ATTRIB_MOSTDERIVED`.

 DBG_ATTRIB_MULTI_CUSTOM_VIEWERS indique que l’objet a plusieurs visionneuses personnalisées associées.

## <a name="remarks"></a>Notes

> [!NOTE]
>  Les valeurs dans cette énumération ne sont pas réellement définies dans l’assembly pour C#. Au lieu de cela, vous devez copier les définitions dans votre fichier source.

 Ces indicateurs sont également utilisés pour filtrer les enfants d’un objet, par exemple, quand il est passé en tant qu’argument à [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md). Les valeurs peuvent être combinées avec un opérateur de bits `OR`.

 Le `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` indicateur est une indication à [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] pour obtenir le [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) de l’interface à partir de la [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interface et appelez [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) pour une liste des visionneuses personnalisées.

## <a name="requirements"></a>Spécifications
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)