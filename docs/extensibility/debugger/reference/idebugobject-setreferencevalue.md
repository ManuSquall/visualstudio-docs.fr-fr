---
title: IDebugObject::SetReferenceValue | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject::SetReferenceValue
helpviewer_keywords: IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8045ef99ae500dac5baf2371d84c0503630dcc68
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
Définit la valeur de référence de cet objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetReferenceValue(   
   IDebugObject* pObject  
);  
```  
  
```csharp  
int SetReferenceValue(  
   [In] IDebugObject pObject  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pObject`  
 [in] Un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objet représentant la nouvelle valeur de référence.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode convertit cette [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) une référence à la valeur de l’objet donné dans l’objet du `pObject` paramètre, jeter toutes les références précédentes. Notez que cette `IDebugObject` objet doit déjà être un type référence.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)