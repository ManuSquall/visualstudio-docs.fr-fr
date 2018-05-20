---
title: IManagedAddin::Unload
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Unload method
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 283fd069e0de72af92f7999871190c6c8a0d345b
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  Appelée juste avant qu’un complément VSTO managé soit déchargé.  
  
## <a name="syntax"></a>Syntaxe  
  
```c++
HRESULT Unload();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur HRESULT qui indique si la méthode a réussi.  
  
## <a name="remarks"></a>Notes  
 Cette méthode n’est pas appelée par les versions actuelles de Microsoft Office. Cette méthode est réservée à une utilisation ultérieure.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IManagedAddin](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Load](../vsto/imanagedaddin-load.md)  
  
  