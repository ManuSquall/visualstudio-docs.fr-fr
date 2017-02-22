---
title: "DBG_ATTRIB_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DBG_ATTRIB_FLAGS"
helpviewer_keywords: 
  - "Énumérations DBGPROP_ATTRIB_FLAGS"
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# DBG_ATTRIB_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Décrit plusieurs attributs pour [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) ou une interface d' [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) .  membre de la structure de [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) .  
  
## Syntaxe  
  
```cpp#  
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
  
```c#  
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
  
## Membres  
 DBG\_ATTRIB\_NONE  
 N'indique pas d'attributs.  
  
 DBG\_ATTRIB\_ALL  
 indique tous les attributs.  
  
 DBG\_ATTRIB\_OBJ\_IS\_EXPANDABLE  
 indique que la référence ou la propriété a des enfants.  
  
 DBG\_ATTRIB\_OBJ\_HAS\_ID  
 Indique qu'un ID pour cet objet a été créé.  
  
 DBG\_ATTRIB\_OBJ\_CAN\_HAVE\_ID  
 Indique qu'un ID pour cet objet peut être créé.  
  
 DBG\_ATTRIB\_VALUE\_READONLY  
 indique que la valeur est en lecture seule.  
  
 DBG\_ATTRIB\_VALUE\_ERROR  
 indique que la valeur est une erreur.  
  
 DBG\_ATTRIB\_VALUE\_SIDE\_EFFECT  
 indique que l'évaluation a eu un effet secondaire.  
  
 DBG\_ATTRIB\_OVERLOADED\_CONTAINER  
 indique que cette propriété est vraiment un conteneur de surcharges.  
  
 DBG\_ATTRIB\_VALUE\_BOOLEAN  
 indique que la valeur dans `DEBUG_PROPERTY_INFO::bstrValue` est booléenne.  
  
 DBG\_ATTRIB\_VALUE\_BOOLEAN\_TRUE  
 indique que la valeur dans `DEBUG_PROPERTY_INFO::bstrValue` est booléenne et `TRUE`.  
  
 DBG\_ATTRIB\_VALUE\_INVALID  
 Indique que la valeur dans `DEBUG_PROPERTY_INFO::bstrValue` est pas valide.  
  
 DBG\_ATTRIB\_VALUE\_NAT  
 Indique que la valeur dans `DEBUG_PROPERTY_INFO::bstrValue` ne se*trouve une chaîne* » \(\(NAT\)\).  \(NAT\) décrit une balise de registre dans les processeurs 64 bits Intel qui indique des exceptions spéculatives différées.  
  
 DBG\_ATTRIB\_VALUE\_AUTOEXPANDED  
 Indique que la valeur dans `DEBUG_PROPERTY_INFO::bstrValue` utilisent probablement été développée.  
  
 DBG\_ATTRIB\_VALUE\_TIMEOUT  
 indique qu'une évaluation a chronométré\-.  
  
 DBG\_ATTRIB\_VALUE\_RAW\_STRING  
 Indique que la valeur dans `DEBUG_PROPERTY_INFO::bstrValue` peut être représentée par une chaîne brut.  
  
 DBG\_ATTRIB\_VALUE\_CUSTOM\_VIEWER  
 Indique que cette propriété contient au moins une visionneuse personnalisée associée.  
  
 DBG\_ATTRIB\_ACCESS\_NONE  
 indique un objet qui n'a ni `public`, `private`, ni accès de type d' `protected` .  
  
 DBG\_ATTRIB\_ACCESS\_PUBLIC  
 indique un objet qui a accès public.  
  
 DBG\_ATTRIB\_ACCESS\_PRIVATE  
 Indique un objet qui a un accès privé.  
  
 DBG\_ATTRIB\_ACCESS\_PROTECTED  
 indique un objet qui a protégé l'accès.  
  
 DBG\_ATTRIB\_ACCESS\_FINAL  
 indique un objet qui a accès final.  
  
 DBG\_ATTRIB\_ACCESS\_ALL  
 Masque pour récupérer les attributs d'accès d' `DBG_ATTRIB_FLAGS`.  
  
 DBG\_ATTRIB\_STORAGE\_NONE  
 Indique qu'il n'existe pas de type de stockage spécifié.  
  
 DBG\_ATTRIB\_STORAGE\_GLOBAL  
 indique le stockage global.  
  
 DBG\_ATTRIB\_STORAGE\_STATIC  
 indique le stockage statique.  
  
 DBG\_ATTRIB\_STORAGE\_REGISTER  
 indique le stockage dans le registre.  
  
 DBG\_ATTRIB\_STORAGE\_ALL  
 Masque pour récupérer les attributs de stockage d' `DBG_ATTRIB_FLAGS`.  
  
 DBG\_ATTRIB\_TYPE\_NONE  
 indique qu'il n'y a aucun modificateur de type.  
  
 DBG\_ATTRIB\_TYPE\_VIRTUAL  
 Indique le type d'objet est virtuel.  
  
 DBG\_ATTRIB\_TYPE\_CONSTANT  
 Indique le type d'objet est constante.  
  
 DBG\_ATTRIB\_TYPE\_SYNCHRONIZED  
 Indique le type d'objet est synchronisé.  
  
 DBG\_ATTRIB\_TYPE\_VOLATILE  
 Indique le type d'objet est volatile.  
  
 DBG\_ATTRIB\_TYPE\_ALL  
 Masque pour récupérer les attributs de type d' `DBG_ATTRIB_FLAGS`.  
  
 DBG\_ATTRIB\_DATA  
 indique que cet objet est un champ de données.  
  
 DBG\_ATTRIB\_METHOD  
 indique que cet objet est une méthode.  
  
 DBG\_ATTRIB\_PROPERTY  
 indique que cet objet est une propriété.  
  
 DBG\_ATTRIB\_CLASS  
 indique que cet objet est une classe.  
  
 DBG\_ATTRIB\_BASECLASS  
 indique que cet objet est une classe de base.  
  
 DBG\_ATTRIB\_INTERFACE  
 indique que cet objet est une interface.  
  
 DBG\_ATTRIB\_INNERCLASS  
 indique que cet objet est une classe interne.  
  
 DBG\_ATTRIB\_MOSTDERIVED  
 Indique que cet objet est « *plus* ».  Signifie que les « *plus\-dérivés* » term le type réel de l'objet, et pas le type de sa référence.  
  
 DBG\_ATTRIB\_CHILD\_ALL  
 Indique un masque d' `DBG_ATTRIB_DATA` via `DBG_ATTRIB_MOSTDERIVED`.  
  
 DBG\_ATTRIB\_MULTI\_CUSTOM\_VIEWERS  
 Indique que l'objet a plusieurs visionneuses personnalisées qui lui sont associées.  
  
## Notes  
  
> [!NOTE]
>  Les valeurs de cette énumération ne sont pas définies réellement dans l'assembly pour c\#.  À la place, vous devez copier les définitions à votre fichier source.  
  
 Ces indicateurs sont également utilisées pour filtrer les enfants d'un objet, par exemple, lorsqu'elles sont passées en tant qu'argument à [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md).  Les valeurs peuvent être combinées avec `OR`de bits.  
  
 La balise d' `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` indique à [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] d'obtenir l'interface d' [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) de l'interface d' [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) et d'appeler [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) pour obtenir la liste des visionneuses personnalisées.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)