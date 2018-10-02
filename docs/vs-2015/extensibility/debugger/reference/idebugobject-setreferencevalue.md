---
title: IDebugObject::SetReferenceValue | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 51770bf8b57877450917933af2f5382205aa60fd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516639"
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugObject::SetReferenceValue](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugobject-setreferencevalue).  
  
Définit la valeur de référence de cet objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 Cette méthode effectue cela [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) une référence à la valeur de l’objet indiqué dans l’objet le `pObject` paramètre, en supprimant toutes les références précédentes. Notez que ce `IDebugObject` objet doit être déjà d’un type référence.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)

