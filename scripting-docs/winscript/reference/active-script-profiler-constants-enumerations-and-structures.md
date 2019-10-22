---
title: Constantes, énumérations et structures actives du profileur de script actif | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 6e079d84-9dde-46fc-8a6a-18e902f60ecc
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a9409799c7da2ed3f4864dea0e7785635492220
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572694"
---
# <a name="active-script-profiler-constants-enumerations-and-structures"></a>Profilage de script actif, constantes, énumérations et structures
Les énumérations suivantes sont utilisées par les interfaces du profileur de script actif.  
  
## <a name="constants-enumerations-and-structures"></a>Constantes, énumérations et structures  
  
|Constantes|Description|  
|---------------|-----------------|  
|[Type PROFILER_EXTERNAL_OBJECT_ADDRESS](../../winscript/reference/profiler-external-object-address-type.md)|Adresse d’objet externe du profileur. Utilisé dans la structure [PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) et la [structure PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Type PROFILER_HEAP_OBJECT_ID](../../winscript/reference/profiler-heap-object-id-type.md)|ID de l’objet de segment de mémoire. Utilisé dans la structure [PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md)[PROFILER_HEAP_OBJECT_SCOPE_LIST](../../winscript/reference/profiler-heap-object-scope-list-structure.md)structure, la structure [PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md)et la [structure PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Type PROFILER_HEAP_OBJECT_NAME_ID](../../winscript/reference/profiler-heap-object-name-id-type.md)|ID du nom de l’objet de segment de mémoire. Utilisé dans la [structure PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md).|  
  
|Énumérations|Description|  
|------------------|-----------------|  
|[Énumération PROFILER_EVENT_MASK](../../winscript/reference/profiler-event-mask-enumeration.md)|Indique les types d’événements qui doivent être profilés.|  
|[Énumération PROFILER_HEAP_ENUM_FLAGS](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)|Indicateurs qui représentent si des informations supplémentaires sur un objet de segment de mémoire pointées dans une relation d’objet sont exposées. Utilisé dans la [méthode IActiveScriptProfilerControl5 :: EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md).|  
|[Énumération PROFILER_HEAP_OBJECT_FLAGS](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Indicateurs qui représentent des informations de base sur l’objet segment de mémoire. Utilisé dans la [structure PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md).|  
|[Énumération PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|Représente différents types d’informations facultatives. Utilisé dans la [structure PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md).|  
|[Énumération PROFILER_RELATIONSHIP_INFO](../../winscript/reference/profiler-relationship-info-enumeration.md)|Représente des informations sur l’objet dans la relation. Utilisé dans la [structure PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Énumération PROFILER_SCRIPT_TYPE](../../winscript/reference/profiler-script-type-enumeration.md)|Spécifie le type de script.|  
  
|Structures|Description|  
|----------------|-----------------|  
|[Structure PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md)|Représente les objets de tas collectés par la [méthode IActiveScriptProfilerControl3 :: EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).|  
|[Structure PROFILER_HEAP_OBJECT_OPTIONAL_INFO ](../../winscript/reference/profiler-heap-object-optional-info-structure.md)|Représente des informations facultatives sur les objets de segment de mémoire.|  
|[Structure PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Représente une relation d’un objet segment de mémoire.|  
|[Structure PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Représente une liste de relations qui appartiennent à un objet segment de mémoire.|  
|[Structure PROFILER_HEAP_OBJECT_SCOPE_LIST](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|Cette structure est associée uniquement aux objets de fonction. La liste d’étendues représente la fermeture de la fonction sous la forme d’une liste d’étendues où chaque étendue est un objet segment de mémoire avec une liste de propriétés associée qui représente des variables dans l’étendue donnée. Dans certains cas, les noms des objets de cette portée peuvent ne pas être disponibles, uniquement leurs ID.|  
|[Structure PROFILER_PROPERTY_TYPE_SUBSTRING_INFO](../../winscript/reference/profiler-property-type-substring-info-structure.md)|Représente des informations sur le type de la sous-chaîne.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de profiler de script actif](../../winscript/reference/active-script-profiler-interfaces.md)