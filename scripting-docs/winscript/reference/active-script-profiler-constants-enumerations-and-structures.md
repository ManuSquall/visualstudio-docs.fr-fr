---
title: "Profilage de script actif, constantes, &#233;num&#233;rations et structures | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 6e079d84-9dde-46fc-8a6a-18e902f60ecc
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Profilage de script actif, constantes, &#233;num&#233;rations et structures
Les énumérations suivantes sont utilisées par les interfaces de profileur de script actif.  
  
## Constantes, énumérations, et structures  
  
|Constantes|Description|  
|----------------|-----------------|  
|[PROFILER\_EXTERNAL\_OBJECT\_ADDRESS, type](../../winscript/reference/profiler-external-object-address-type.md)|L'adresse externe d'objet du profileur.  Utilisé dans [PROFILER\_HEAP\_OBJECT, structure](../../winscript/reference/profiler-heap-object-structure.md) et [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP, structure](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[PROFILER\_HEAP\_OBJECT\_ID, type](../../winscript/reference/profiler-heap-object-id-type.md)|ID de l'objet soucier.  Utilisé dans [PROFILER\_HEAP\_OBJECT, structure](../../winscript/reference/profiler-heap-object-structure.md), [PROFILER\_HEAP\_OBJECT\_SCOPE\_LIST, structure](../../winscript/reference/profiler-heap-object-scope-list-structure.md), [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO, structure](../../winscript/reference/profiler-heap-object-optional-info-structure.md)et [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP, structure](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[PROFILER\_HEAP\_OBJECT\_NAME\_ID, type](../../winscript/reference/profiler-heap-object-name-id-type.md)|L'ID du nom de l'objet soucier.  Utilisé dans [PROFILER\_HEAP\_OBJECT, structure](../../winscript/reference/profiler-heap-object-structure.md).|  
  
|Énumérations|Description|  
|------------------|-----------------|  
|[PROFILER\_EVENT\_MASK, énumération](../../winscript/reference/profiler-event-mask-enumeration.md)|Indique les types d'événements qui doivent être profilés.|  
|[PROFILER\_HEAP\_OBJECT\_FLAGS, énumération](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)|Indicateurs qui représentent si des informations supplémentaires relatives à un objet segment de mémoire désigné dans une relation d'objet est exposée.  Utilisé dans [IActiveScriptProfilerControl5::EnumHeap2, méthode](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md).|  
|[PROFILER\_HEAP\_OBJECT\_FLAGS, énumération](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Indicateurs qui représentent des informations de base sur l'objet soucier.  Utilisé dans [PROFILER\_HEAP\_OBJECT, structure](../../winscript/reference/profiler-heap-object-structure.md).|  
|[PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_TYPE, énumération](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|Représente des types différents d'informations facultatives.  Utilisé dans [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO, structure](../../winscript/reference/profiler-heap-object-optional-info-structure.md).|  
|[PROFILER\_RELATIONSHIP\_INFO, énumération](../../winscript/reference/profiler-relationship-info-enumeration.md)|Représente des informations sur l'objet dans la relation.  Utilisé dans [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP, structure](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[PROFILER\_SCRIPT\_TYPE, énumération](../../winscript/reference/profiler-script-type-enumeration.md)|Spécifie le type de script.|  
  
|Structures|Description|  
|----------------|-----------------|  
|[PROFILER\_HEAP\_OBJECT, structure](../../winscript/reference/profiler-heap-object-structure.md)|Représente les objets soucier rassemblés par [IActiveScriptProfilerControl3::EnumHeap, méthode](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).|  
|[PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO, structure](../../winscript/reference/profiler-heap-object-optional-info-structure.md)|Représente des informations facultatives sur les objets soucier.|  
|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP, structure](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Représente une relation d'un objet soucier.|  
|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST, structure](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Représente une liste de relations qui appartiennent à un objet soucier.|  
|[PROFILER\_HEAP\_OBJECT\_SCOPE\_LIST, structure](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|Cette structure est associée aux objets de fonction uniquement.  La liste de portée représente la fermeture de la fonction comme une liste de portées où chaque portée est un objet soucier avec une liste de propriétés associée représentant des variables dans chaque portée donnée.  Dans certains cas, les noms des objets dans cette portée peuvent ne pas être disponibles, seules les ID.|  
  
## Voir aussi  
 [Profilage de script actif, interfaces](../../winscript/reference/active-script-profiler-interfaces.md)