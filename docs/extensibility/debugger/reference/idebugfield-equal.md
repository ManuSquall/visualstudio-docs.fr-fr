---
title: IDebugField::Equal | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugField::Equal
helpviewer_keywords: IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 30ef8524fbc5d6451bcc302079f769fd05c66185
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
Cette méthode compare ce champ avec le champ spécifié pour l’égalité.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Equal(   
   IDebugField* pField  
);  
```  
  
```csharp  
int Equal(  
   IDebugField pField  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pField`  
 [in] Le champ à comparer à celui-ci.  
  
## <a name="return-value"></a>Valeur de retour  
 Si les champs sont les mêmes, retourne `S_OK`. Si les champs sont différents, retourne `S_FALSE.` dans le cas contraire, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)