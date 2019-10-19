---
title: 'IActiveScriptGarbageCollector :: CollectGarbage | Microsoft Docs'
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
ms.openlocfilehash: 0539ed2cb3540cf33ceaaa15827c3ca08c156698
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573580"
---
# <a name="iactivescriptgarbagecollectorcollectgarbage"></a>IActiveScriptGarbageCollector::CollectGarbage
L’hôte de script actif appelle cette méthode pour démarrer garbage collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CollectGarbage(        SCRIPTGCTYPE scriptgctype    );  
```  
  
#### <a name="parameters"></a>Paramètres  
 `scriptgctype`  
 dans [Énumération SCRIPTGCTYPE](../../winscript/reference/scriptgctype-enumeration.md) qui spécifie s’il faut effectuer une garbage collection normale ou exhaustive.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un HRESULT.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptGarbageCollector](../../winscript/reference/iactivescriptgarbagecollector-interface.md)