---
title: IDispatchEx::GetNameSpaceParent | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDispatchEx.GetNameSpaceParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetNameSpaceParent method
ms.assetid: 0b077d39-2fd6-4390-8cd5-128d9b8dc90c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12168ddb5f65c62e81a8f724cacf8b3fd4a1b3a9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexgetnamespaceparent"></a>IDispatchEx::GetNameSpaceParent
Récupère l’interface pour le parent de l’espace de noms d’un objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetNameSpaceParent(  
   IUnknown **ppunk  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppunk`  
 Adresse d’un `IUnknown` pointeur d’interface qui reçoit l’interface de l’espace de noms parent.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite ou sinon un code d’erreur défini par OLE.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDispatchEx](../../winscript/reference/idispatchex-interface.md)