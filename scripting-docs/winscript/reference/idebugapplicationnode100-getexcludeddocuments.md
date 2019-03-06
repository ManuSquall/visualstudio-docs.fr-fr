---
title: IDebugApplicationNode100::GetExcludedDocuments | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 9de24002733ddd2918e59c908502a7daf4dd8e5a
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346720"
---
# <a name="idebugapplicationnode100getexcludeddocuments"></a>IDebugApplicationNode100::GetExcludedDocuments
Obtient les documents de texte qui sont masqués par le filtre spécifié.  
  
> [!IMPORTANT]
>  [Interface IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md) est implémentée par PDM v10.0 et supérieure. Trouvée dans activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetExcludedDocuments(        [in] APPLICATION_NODE_EVENT_FILTER filter,        [out] TEXT_DOCUMENT_ARRAY* pDocuments        );  
```  
  
#### <a name="parameters"></a>Paramètres  
 `filter`  
 Filtre.  
  
 `pDocuments`  
 L’ensemble de documents.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md)