---
title: IPerPropertyBrowsing2::GetDisplayString | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.GetDisplayString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::GetDisplayString
ms.assetid: 8f75c6a9-86a9-4e2d-8cb4-74e7b1c0a524
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4947ebdeac26ae759fb739dd417607dea885ee5
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091571"
---
# <a name="iperpropertybrowsing2getdisplaystring"></a>IPerPropertyBrowsing2::GetDisplayString
Obtient une chaîne à afficher des types qui ne sont pas visibles, par nature, le texte retourné est un nom décrivant la propriété et peut être affichée dans l’interface utilisateur de l’appelant.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetDisplayString(  
   DISPID  dispid,  
   BSTR*  pBstr  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dispid`  
 [in] Identificateur de dispatch de la propriété dont le nom complet est demandé.  
  
 `pBstr`  
 [out] Pointeur vers le `BSTR` contenant le nom complet de la propriété identifiée par `dispID`.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une liste valide `HRESULT`, généralement `S_OK`.  
  
## <a name="remarks"></a>Notes  
 La chaîne retournée n’est pas une valeur autorisée de la propriété. Il est simplement un affichage de la chaîne de la propriété.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface 1 IPerPropertyBrowsing2](../../winscript/reference/iperpropertybrowsing2-interface-1.md)