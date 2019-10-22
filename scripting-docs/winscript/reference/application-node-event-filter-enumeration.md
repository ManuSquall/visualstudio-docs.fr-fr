---
title: Énumération APPLICATION_NODE_EVENT_FILTER | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- APPLICATION_NODE_EVENT_FILTER Constants
ms.assetid: dccb2cf7-0598-46f8-b3eb-16b752815e96
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 481e015ec84d833f52220276bffa4ce0163f98ff
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572648"
---
# <a name="application_node_event_filter-enumeration"></a>APPLICATION_NODE_EVENT_FILTER, énumération
Spécifie les types de nœuds à exclure lors du filtrage des documents de code. Utilisé dans [IDebugApplicationNode100 :: GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) et [IDebugApplicationNode100 :: SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
> Ces constantes sont implémentées par PDM v 10.0 et versions ultérieures. Trouvée dans activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum tagAPPLICATION_NODE_EVENT_FILTER {    FILTER_EXCLUDE_NOTHING = 0,    FILTER_EXCLUDE_ANONYMOUS_CODE = 0x1,    FILTER_EXCLUDE_EVAL_CODE = 0x2} APPLICATION_NODE_EVENT_FILTER;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|valeur|Description|  
|------------|-----------|-----------------|  
|FILTER_EXCLUDE_NOTHING|0x00000000|Envoyer tous les événements.|  
|FILTER_EXCLUDE_ANONYMOUS_CODE|0x00000001|Excluez les nœuds de code anonymes. Ces nœuds sont utilisés par le runtime JScript pour `new Function([args,] <code>)'`.|  
|FILTER_EXCLUDE_EVAL_CODE|0x00000002|Exclut les nœuds de code d’évaluation. Ces nœuds sont utilisés par le runtime JScript pour la prise en charge d’eval.|  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de débogueur de script actif, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)