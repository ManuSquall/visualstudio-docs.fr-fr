---
title: IDebugArrayObject::GetElement | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugArrayObject::GetElement
helpviewer_keywords: IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 451c758ef067bfd162e5451a629983ef2130a1d9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugarrayobjectgetelement"></a>IDebugArrayObject::GetElement
Obtient un élément du tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetElement(   
   DWORD          dwIndex,  
   IDebugObject** ppElement  
);  
```  
  
```csharp  
int GetElement(  
   [In] uint dwIndex,   
   out IDebugObject ppElement  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwIndex`  
 [in] L’index de l’élément.  
  
 `ppElement`  
 [out] Retourne un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interface qui représente l’élément.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Cette méthode voit tous les éléments d’un objet tableau comme un tableau unidimensionnel, même si l’objet de tableau est multidimensionnel. Par exemple, étant donné le tableau `myarray[3][2][6]` et un `dwIndex` paramètre 20, cette méthode retourne l’élément à partir de `myarray[1][1][2]`et un `dwIndex` paramètre 21 renvoie l’élément à partir de `myarray[1][1][3]`. Utilisez le [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) méthode pour déterminer le nombre total d’éléments dans le tableau.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)