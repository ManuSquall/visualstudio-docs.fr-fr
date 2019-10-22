---
title: 'IPerPropertyBrowsing2 :: GetDisplayString | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: bc702ad15d1aba04bf991c04b585728afde4fb41
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571452"
---
# <a name="iperpropertybrowsing2getdisplaystring"></a>IPerPropertyBrowsing2::GetDisplayString
Obtient une chaîne pour afficher les types qui ne sont pas visibles par nature, le texte retourné est un nom qui décrit la propriété et peut être affiché dans l’interface utilisateur de l’appelant.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetDisplayString(  
   DISPID  dispid,  
   BSTR*  pBstr  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dispid`  
 dans Identificateur de dispatch de la propriété dont le nom d’affichage est demandé.  
  
 `pBstr`  
 à Pointeur vers le `BSTR` contenant le nom complet de la propriété identifiée par `dispID`.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un `HRESULT` valide, généralement `S_OK`.  
  
## <a name="remarks"></a>Notes  
 La chaîne retournée n’est pas une valeur autorisée pour la propriété. Il s’agit simplement d’un affichage de chaîne de la propriété.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface 1 IPerPropertyBrowsing2](../../winscript/reference/iperpropertybrowsing2-interface-1.md)