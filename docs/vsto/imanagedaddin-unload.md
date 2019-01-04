---
title: IManagedAddin::Unload
ms.date: 02/02/2017
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
ms.openlocfilehash: 4aa3c07ed715a6118bd053d44503607a889f3da7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53880891"
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  Appelée juste avant qu’un complément VSTO managé soit déchargé.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
HRESULT Unload();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur HRESULT qui indique si la méthode a réussi.  
  
## <a name="remarks"></a>Notes  
 Cette méthode n’est pas appelée par les versions actuelles de Microsoft Office. Cette méthode est réservée à une utilisation ultérieure.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IManagedAddin](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Load](../vsto/imanagedaddin-load.md)  
