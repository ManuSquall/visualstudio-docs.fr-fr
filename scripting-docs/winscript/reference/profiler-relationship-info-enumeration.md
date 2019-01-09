---
title: Énumération PROFILER_RELATIONSHIP_INFO | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: fae69317-6224-4a6a-8e9e-ccaa6a330818
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e95b11537873d3bfe02bf3fa793b61ace10938aa
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095808"
---
# <a name="profilerrelationshipinfo-enumeration"></a>PROFILER_RELATIONSHIP_INFO, énumération
Représente des informations sur l’objet dans la relation. Utilisé dans [profiler_heap_object_relationship, Structure](../../winscript/reference/profiler-heap-object-relationship-structure.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef [v1_enum] enum {    PROFILER_PROPERTY_TYPE_NUMBER = 0x01,    PROFILER_PROPERTY_TYPE_STRING = 0x02,    PROFILER_PROPERTY_TYPE_HEAP_OBJECT = 0x03,    PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT = 0x04,    PROFILER_PROPERTY_TYPE_BSTR = 0x05,} PROFILER_RELATIONSHIP_INFO;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Value|Description|  
|------------|-----------|-----------------|  
|PROFILER_PROPERTY_TYPE_NUMBER|0 x 01|L’objet est un nombre.|  
|PROFILER_PROPERTY_TYPE_STRING|0 x 02|L’objet est une chaîne.|  
|PROFILER_PROPERTY_TYPE_HEAP_OBJECT|0 x 03|L’objet est un objet de segment de mémoire.|  
|PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT|0 x 04|L’objet est externe, autrement dit, pas sur le tas de garbage collection.|  
|PROFILER_PROPERTY_TYPE_BSTR|0 x 05|L’objet est un BSTR.|  
|PROFILER_PROPERTY_TYPE_SUBSTRING|0 x 06|L’objet est une sous-chaîne.|