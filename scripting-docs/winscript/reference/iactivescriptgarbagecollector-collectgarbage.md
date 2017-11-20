---
title: IActiveScriptGarbageCollector::CollectGarbage | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 75f77c49-2190-4d49-a3e0-9dcf847c502b
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07d5a00e04939331f85c4c74727aaf03b62814fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgarbagecollectorcollectgarbage"></a>IActiveScriptGarbageCollector::CollectGarbage
L’hôte de Script actif appelle cette méthode pour démarrer l’opération garbage collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CollectGarbage(        SCRIPTGCTYPE scriptgctype    );  
```  
  
#### <a name="parameters"></a>Paramètres  
 `scriptgctype`  
 [in] Le [scriptgctype, énumération](../../winscript/reference/scriptgctype-enumeration.md) qui spécifie s’il faut effectuer un nettoyage normal ou exhaustive.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une valeur HRESULT.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptGarbageCollector](../../winscript/reference/iactivescriptgarbagecollector-interface.md)