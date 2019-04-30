---
title: IDispatchEx::GetNameSpaceParent | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetNameSpaceParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetNameSpaceParent method
ms.assetid: 0b077d39-2fd6-4390-8cd5-128d9b8dc90c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1abe2a880e12d6a4a3c1dfda32d30722525858f5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000825"
---
# <a name="idispatchexgetnamespaceparent"></a>IDispatchEx::GetNameSpaceParent
Récupère l’interface pour le parent de l’espace de noms d’un objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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