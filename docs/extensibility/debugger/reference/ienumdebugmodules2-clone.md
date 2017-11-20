---
title: IEnumDebugModules2::Clone | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugModules2::Clone
helpviewer_keywords: IEnumDebugModules2::Clone
ms.assetid: fd6d3abc-20d9-4f6f-9c8e-5bd29f68d47d
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cbeb94a2cbdfbbe04893ed491287057639d3949d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugmodules2clone"></a>IEnumDebugModules2::Clone
Retourne une copie de l’énumération actuelle comme un objet distinct.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Clone(  
   IEnumDebugModules2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugModules2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppEnum`  
 [out] Retourne une copie de cette énumération comme un objet distinct.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 La copie de l’énumération a le même état que l’original au moment de que cette méthode est appelée. Toutefois, les États de la copie et l’original sont distincts et peuvent être modifiées individuellement.  
  
## <a name="see-also"></a>Voir aussi  
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)