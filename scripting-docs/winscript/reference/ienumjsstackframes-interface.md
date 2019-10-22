---
title: Interface IEnumJsStackFrames | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 49e7b425-df17-4d7f-87ff-0bc82715c911
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4a635a802ae84b8e839159f5e2f1c4c461e05ae
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572027"
---
# <a name="ienumjsstackframes-interface"></a>IEnumJsStackFrames, interface
Implémenté par le débogueur pour fournir le déroulement de la pile à jscript9diag. dll pour JavaScript.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
IEnumJsStackFrames : public IUnknown;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Name|Description|  
|----------|-----------------|  
|[Méthode IEnumJsStackFrames::Next](../../winscript/reference/ienumjsstackframes-next-method.md)|Obtient le nombre spécifié de frames.|  
|[Méthode IEnumJsStackFrames::Reset](../../winscript/reference/ienumjsstackframes-reset-method.md)|Rétablit la position avant le premier élément du frame de pile.|  
  
## <a name="requirements"></a>spécifications  
 **En-tête :** jscript9diag. h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence d’interfaces de script Windows](../../winscript/reference/windows-script-interfaces-reference.md)