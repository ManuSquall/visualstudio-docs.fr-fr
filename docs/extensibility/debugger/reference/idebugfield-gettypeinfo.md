---
title: IDebugField::GetTypeInfo | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugField::GetTypeInfo
helpviewer_keywords: IDebugField::GetTypeInfo method
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 11b04ce148fbfe8129f62c21da0a0b015ed6e8f3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugfieldgettypeinfo"></a>IDebugField::GetTypeInfo
Cette méthode obtient indépendante du type d’informations sur le symbole ou d’un type.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetTypeInfo(   
   TYPE_INFO* pTypeInfo  
);  
```  
  
```csharp  
int GetTypeInfo(  
   TYPE_INFO[] pTypeInfo  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pTypeInfo`  
 [out] Retourne de type d’informations dans le [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) structure.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Les informations de type indépendant inclut, par exemple, le domaine d’application, le module et la classe qui contient le symbole.  
  
## <a name="see-also"></a>Voir aussi  
 [GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)