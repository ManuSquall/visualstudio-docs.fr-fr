---
title: Énumération PROFILER_RELATIONSHIP_INFO | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: fae69317-6224-4a6a-8e9e-ccaa6a330818
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0aa0a94668d06f75b959de2ee933ab079feba596
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148111"
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
|PROFILER_PROPERTY_TYPE_NUMBER|0x01|L’objet est un nombre.|  
|PROFILER_PROPERTY_TYPE_STRING|0x02|L’objet est une chaîne.|  
|PROFILER_PROPERTY_TYPE_HEAP_OBJECT|0x03|L’objet est un objet de segment de mémoire.|  
|PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT|0x04|L’objet est externe, autrement dit, pas sur le tas de garbage collection.|  
|PROFILER_PROPERTY_TYPE_BSTR|0x05|L’objet est un BSTR.|  
|PROFILER_PROPERTY_TYPE_SUBSTRING|0x06|L’objet est une sous-chaîne.|