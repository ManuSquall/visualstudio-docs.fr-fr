---
title: Interface IJsDebugStackWalker | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 3fe30394-49c8-48e9-bde9-ffe5d79b2121
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b06b8c1f9282c42599c798030440c30450ef6dd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574015"
---
# <a name="ijsdebugstackwalker-interface"></a>IJsDebugStackWalker, interface
Représente un Explorateur de piles pour un thread spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
IJsDebugStackWalker : public IUnknown;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Name|Description|  
|----------|-----------------|  
|[Méthode IJsDebugStackWalker::GetNext](../../winscript/reference/ijsdebugstackwalker-getnext-method.md)|Obtient le frame suivant.|  
  
## <a name="remarks"></a>Notes  
 Les monteurs de pile ne peuvent être créés que lorsque la cible est arrêtée et ne sont pas valides une fois que le processus cible a été de nouveau poursuivi.  
  
## <a name="requirements"></a>spécifications  
 **En-tête :** jscript9diag. h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence d’interfaces de script Windows](../../winscript/reference/windows-script-interfaces-reference.md)