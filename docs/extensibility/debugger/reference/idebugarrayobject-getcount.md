---
title: IDebugArrayObject::GetCount | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugArrayObject::GetCount
helpviewer_keywords: IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7c7a860dd1039f5b2e5a2049674ba78a91af7741
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugarrayobjectgetcount"></a>IDebugArrayObject::GetCount
Obtient le nombre d’éléments dans le tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[C++]  
HRESULT GetCount(   
   DWORD* pdwElements  
);  
```  
  
```  
[C#]  
int GetCount(  
   out uint pdwElements  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pdwElements`  
 [out] Retourne le nombre.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Cette méthode voit tous les éléments d’un objet tableau comme un tableau unidimensionnel, même si l’objet de tableau est multidimensionnel. Par exemple, étant donné le tableau `myarray[3][2][6]`, cette méthode retourne 36 dans le `pdwElements` paramètre. Utilisez le [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) méthode pour récupérer l’un des éléments individuels à la fois.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)