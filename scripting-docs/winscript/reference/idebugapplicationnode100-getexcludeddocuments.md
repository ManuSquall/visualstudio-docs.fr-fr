---
title: 'IDebugApplicationNode100 :: GetExcludedDocuments | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100::GetExcludedDocuments
ms.assetid: d44583a7-0b0b-4799-b075-837ad1da1946
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c135aa85ca65a44f6f970e83d7975bb441ff56f5
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574754"
---
# <a name="idebugapplicationnode100getexcludeddocuments"></a>IDebugApplicationNode100::GetExcludedDocuments
Obtient les documents texte qui sont masqués par le filtre spécifié.  
  
> [!IMPORTANT]
> L' [interface IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md) est implémentée par PDM v 10.0 et versions ultérieures. Trouvée dans activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetExcludedDocuments(        [in] APPLICATION_NODE_EVENT_FILTER filter,        [out] TEXT_DOCUMENT_ARRAY* pDocuments        );  
```  
  
#### <a name="parameters"></a>Paramètres  
 `filter`  
 Filtre.  
  
 `pDocuments`  
 Ensemble de documents.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md)