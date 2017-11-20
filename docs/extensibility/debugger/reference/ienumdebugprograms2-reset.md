---
title: IEnumDebugPrograms2::Reset | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugPrograms2::Reset
helpviewer_keywords: IEnumDebugPrograms2::Reset
ms.assetid: b289242b-24ea-4df3-a811-20b0c8a903d6
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9f8da5196f9a82d6b8f14c036441b9acbebbedf2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugprograms2reset"></a>IEnumDebugPrograms2::Reset
Réinitialise l’énumération au premier élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Reset(  
   void  
);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Une fois que cette méthode est appelée, l’appel suivant à la [suivant](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md) méthode retourne le premier élément de l’énumération.  
  
## <a name="see-also"></a>Voir aussi  
 [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)