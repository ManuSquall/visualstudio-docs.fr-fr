---
title: IDebugFunctionPosition2::GetOffset | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugFunctionPosition2::GetOffset
helpviewer_keywords:
- IDebugFunctionPosition2::GetOffset
ms.assetid: 60943782-aec7-4be2-b222-1984ed53a543
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 6ac867e80102332e988c89204721322132584ec6
ms.lasthandoff: 02/22/2017

---
# <a name="idebugfunctionposition2getoffset"></a>IDebugFunctionPosition2::GetOffset
Récupère la position de la fonction dans le document source.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetOffset(   
   TEXT_POSITION* pPosition  
);  
```  
  
```c#  
int GetOffset(  
   TEXT_POSITION[] pPosition  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pPosition`  
 [dans, out] A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) structure est remplie avec la position de la fonction dans un document.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
