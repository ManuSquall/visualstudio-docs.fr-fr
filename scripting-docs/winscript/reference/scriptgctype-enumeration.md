---
title: "Scriptgctype, énumération | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f289cc7d-2a69-4720-bee0-ea27d054f308
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d42187cc7467bea9d777f35bb208c4e42cabb31
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="scriptgctype-enumeration"></a>SCRIPTGCTYPE, énumération
Le type de garbage collection à effectuer. Utilisé dans le [IActiveScriptGarbageCollector::CollectGarbage](../../winscript/reference/iactivescriptgarbagecollector-collectgarbage.md) (méthode).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum tagSCRIPTGCTYPE {    SCRIPTGCTYPE_NORMAL           = 0,    SCRIPTGCTYPE_EXHAUSTIVE       = 1,} SCRIPTGCTYPE;  
```  
  
## <a name="enumeration-values"></a>Valeurs d’énumération  
  
|||  
|-|-|  
|SCRIPTGCTYPE_NORMAL|Effectuer un nettoyage normal. La valeur entière est 0.|  
|SCRIPTGCTYPE_EXHAUSTIVE|Effectuer un nettoyage exhaustive. La valeur entière est 1.|  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de script actives, énumérations et codes d’erreur](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)