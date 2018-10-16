---
title: IDebugObject::GetManagedDebugObject | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b1dde6683173931fa261e4f0793413bcf5bc42e5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49198560"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crée une copie de l’objet managé dans l’espace d’adressage du moteur de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetManagedDebugObject(   
   IDebugManagedObject** ppObject  
);  
```  
  
```csharp  
int GetManagedDebugObject(  
   out IDebugManagedObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppObject`  
 [out] Retourne un [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) objet représentant l’objet managé qui vient d’être créé.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur. Retourne E_FAIL si ce [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) ne représente pas une instance de classe de valeur managé.  
  
## <a name="remarks"></a>Notes  
 Cela [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objet doit représenter une instance de classe de valeur managé, comme un `System.Decimal` instance. En faisant une copie locale, la surcharge de l’appel [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) est éliminé.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)

