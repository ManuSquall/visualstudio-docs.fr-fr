---
title: 'IDispatchEx :: GetNameSpaceParent | Microsoft Docs'
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
ms.openlocfilehash: d2f47fab9831441e72a4ef3d4332a41c08e6a108
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574082"
---
# <a name="idispatchexgetnamespaceparent"></a>IDispatchEx::GetNameSpaceParent
Récupère l’interface pour le parent d’espace de noms d’un objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetNameSpaceParent(  
   IUnknown **ppunk  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppunk`  
 Adresse d’un pointeur d’interface `IUnknown` qui reçoit l’interface du parent de l’espace de noms.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite ou un code d’erreur défini par OLE dans le cas contraire.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDispatchEx](../../winscript/reference/idispatchex-interface.md)