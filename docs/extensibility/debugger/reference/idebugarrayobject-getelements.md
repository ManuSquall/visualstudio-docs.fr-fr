---
title: IDebugArrayObject::GetElements | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugArrayObject::GetElements
helpviewer_keywords: IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 744570bac67648b26467867931be2fb3f24a98ef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugarrayobjectgetelements"></a>IDebugArrayObject::GetElements
Obtient un énumérateur de tous les éléments du tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetElements(   
   IEnumDebugObjects** ppEnum  
);  
```  
  
```csharp  
int GetElements(  
   out IEnumDebugObjects ppEnum  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppEnum`  
 [out] Retourne un [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md) objet qui permet l’énumération sur tous les éléments.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 En guise d’alternative, utilisez la [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) et [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) méthodes pour boucler dans les éléments.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)