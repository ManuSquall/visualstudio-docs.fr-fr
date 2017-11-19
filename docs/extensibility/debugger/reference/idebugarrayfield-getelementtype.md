---
title: IDebugArrayField::GetElementType | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugArrayField::GetElementType
helpviewer_keywords: IDebugArrayField::GetElementType method
ms.assetid: c46bf625-0a48-4cbb-8f1f-286356f2c065
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a2286f201e358a190510fdff634b01f7ec9a64d9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugarrayfieldgetelementtype"></a>IDebugArrayField::GetElementType
Obtient le type d’élément dans le tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetElementType(   
   IDebugField** ppType  
);  
```  
  
```csharp  
int GetElementType(  
   out IDebugField ppType  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppType`  
 [out] Retourne un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objet qui décrit le type d’élément.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Le [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md) objet suppose que tous les éléments du tableau sont du même type.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)