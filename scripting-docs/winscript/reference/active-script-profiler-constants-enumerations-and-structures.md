---
title: Générateur de profils de Script actif, constantes, énumérations et Structures | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 6e079d84-9dde-46fc-8a6a-18e902f60ecc
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a37f64b14d0d732e48de66bb5268d47c95426937
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24642049"
---
# <a name="active-script-profiler-constants-enumerations-and-structures"></a>Profilage de script actif, constantes, énumérations et structures
Les énumérations suivantes sont utilisées par le Générateur de profils de Script actif, Interfaces.  
  
## <a name="constants-enumerations-and-structures"></a>Constantes, énumérations et structures  
  
|Constantes|Description|  
|---------------|-----------------|  
|[Type PROFILER_EXTERNAL_OBJECT_ADDRESS](../../winscript/reference/profiler-external-object-address-type.md)|L’adresse de l’objet externe du profileur. Utilisé dans [profiler_heap_object, Structure](../../winscript/reference/profiler-heap-object-structure.md) et [profiler_heap_object_relationship, Structure](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Type PROFILER_HEAP_OBJECT_ID](../../winscript/reference/profiler-heap-object-id-type.md)|L’ID de l’objet de segment de mémoire. Utilisé dans [profiler_heap_object, Structure](../../winscript/reference/profiler-heap-object-structure.md)[profiler_heap_object_scope_list, Structure](../../winscript/reference/profiler-heap-object-scope-list-structure.md), [profiler_heap_object_optional_info, Structure](../../winscript/reference/profiler-heap-object-optional-info-structure.md)et [Profiler_heap_object_relationship, Structure](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Type PROFILER_HEAP_OBJECT_NAME_ID](../../winscript/reference/profiler-heap-object-name-id-type.md)|L’ID du nom de l’objet de tas. Utilisé dans [profiler_heap_object, Structure](../../winscript/reference/profiler-heap-object-structure.md).|  
  
|Énumérations|Description|  
|------------------|-----------------|  
|[Énumération PROFILER_EVENT_MASK](../../winscript/reference/profiler-event-mask-enumeration.md)|Indique les types d’événements doivent être définis.|  
|[Énumération PROFILER_HEAP_ENUM_FLAGS](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)|Indicateurs qui représentent des si des informations supplémentaires sur un objet de tas pointé dans une relation d’objet sont exposées. Utilisé dans le [iactivescriptprofilercontrol5::enumheap2, méthode](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md).|  
|[Énumération PROFILER_HEAP_OBJECT_FLAGS](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Indicateurs qui représentent des informations de base sur l’objet de tas. Utilisé dans le [profiler_heap_object, Structure](../../winscript/reference/profiler-heap-object-structure.md).|  
|[Énumération PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|Représente les différents types d’informations facultatives. Utilisé dans [profiler_heap_object_optional_info, Structure](../../winscript/reference/profiler-heap-object-optional-info-structure.md).|  
|[Énumération PROFILER_RELATIONSHIP_INFO](../../winscript/reference/profiler-relationship-info-enumeration.md)|Représente des informations sur l’objet dans la relation. Utilisé dans [profiler_heap_object_relationship, Structure](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Énumération PROFILER_SCRIPT_TYPE](../../winscript/reference/profiler-script-type-enumeration.md)|Spécifie le type de script.|  
  
|Structures|Description|  
|----------------|-----------------|  
|[Structure PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md)|Représente les objets du tas, regroupés en [iactivescriptprofilercontrol3::enumheap, méthode](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).|  
|[Structure PROFILER_HEAP_OBJECT_OPTIONAL_INFO ](../../winscript/reference/profiler-heap-object-optional-info-structure.md)|Représente des informations facultatives sur les objets du tas.|  
|[Structure PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Représente une relation entre un objet de segment de mémoire.|  
|[Structure PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Représente une liste de relations qui appartiennent à un objet de segment de mémoire.|  
|[Structure PROFILER_HEAP_OBJECT_SCOPE_LIST](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|Cette structure est associée aux objets de fonction uniquement. La liste de l’étendue représente la fermeture de la fonction sous la forme d’une liste d’étendues, où chaque étendue est un objet de segment de mémoire avec une liste de propriétés associée qui représente les variables dans chaque étendue donnée. Dans certains cas, les noms des objets dans cette étendue ne peuvent pas être disponibles, seulement leurs ID.|  
|[Structure PROFILER_PROPERTY_TYPE_SUBSTRING_INFO](../../winscript/reference/profiler-property-type-substring-info-structure.md)|Représente des informations sur le type de la sous-chaîne.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de profiler de script actif](../../winscript/reference/active-script-profiler-interfaces.md)