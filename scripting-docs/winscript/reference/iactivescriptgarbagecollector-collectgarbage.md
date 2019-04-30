---
title: IActiveScriptGarbageCollector::CollectGarbage | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 75f77c49-2190-4d49-a3e0-9dcf847c502b
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: db8683534e449b2cdd8fcdb344c245d93da8fafc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62954970"
---
# <a name="iactivescriptgarbagecollectorcollectgarbage"></a>IActiveScriptGarbageCollector::CollectGarbage
L’hôte de Script actif appelle cette méthode pour démarrer le garbage collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CollectGarbage(        SCRIPTGCTYPE scriptgctype    );  
```  
  
#### <a name="parameters"></a>Paramètres  
 `scriptgctype`  
 [in] Le [scriptgctype, énumération](../../winscript/reference/scriptgctype-enumeration.md) qui spécifie s’il faut effectuer un nettoyage normal ou exhaustive.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une valeur HRESULT.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptGarbageCollector](../../winscript/reference/iactivescriptgarbagecollector-interface.md)