---
title: Interface IEnumJsStackFrames | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 49e7b425-df17-4d7f-87ff-0bc82715c911
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c26470e02f6c7e5d8911df7e743bce0cb0e560bb
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087878"
---
# <a name="ienumjsstackframes-interface"></a>IEnumJsStackFrames, interface
Implémenté par le débogueur pour fournir une pile de désempilage à jscript9diag.dll pour JavaScript.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
IEnumJsStackFrames : public IUnknown;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[Méthode IEnumJsStackFrames::Next](../../winscript/reference/ienumjsstackframes-next-method.md)|Obtient le nombre spécifié de frames.|  
|[Méthode IEnumJsStackFrames::Reset](../../winscript/reference/ienumjsstackframes-reset-method.md)|Réinitialise le frame de pile à la position avant le premier élément.|  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence d’interfaces de script Windows](../../winscript/reference/windows-script-interfaces-reference.md)