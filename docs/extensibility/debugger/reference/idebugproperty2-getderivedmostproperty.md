---
title: IDebugProperty2::GetDerivedMostProperty | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty2::GetDerivedMostProperty
helpviewer_keywords: IDebugProperty2::GetDerivedMostProperty
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3ac691b8e1c2d28477eb8c07f760eae8909a9633
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugproperty2getderivedmostproperty"></a>IDebugProperty2::GetDerivedMostProperty
Obtient la propriété plus dérivé d’une propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetDerivedMostProperty (   
   IDebugProperty2** ppDerivedMost  
);  
```  
  
```csharp  
int GetDerivedMostProperty (   
   out IDebugProperty2 ppDerivedMost  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppDerivedMost`  
 [out] Retourne un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objet qui représente la propriété la plus dérivée.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon retourne le code d’erreur. Retourne `S_GETDERIVEDMOST_NO_DERIVED_MOST` s’il n’existe aucune propriété plus dérivé à récupérer.  
  
## <a name="remarks"></a>Remarques  
 Par exemple, si cette propriété décrit un objet qui implémente `ClassRoot` mais qui est réellement une instanciation de `ClassDerived` qui est dérivée de `ClassRoot`, cette méthode retourne un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objet décrivant la `ClassDerived` objet.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)