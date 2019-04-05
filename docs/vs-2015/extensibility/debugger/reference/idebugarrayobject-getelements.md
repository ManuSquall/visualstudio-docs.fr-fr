---
title: IDebugArrayObject::GetElements | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cad81d76e2fcec01fa50a37fa6ab6cb49cfc79be
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "58947923"
---
# <a name="idebugarrayobjectgetelements"></a>IDebugArrayObject::GetElements
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtient un énumérateur de tous les éléments du tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 Comme alternative, utilisez la [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) et [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) méthodes pour itérer les éléments.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
