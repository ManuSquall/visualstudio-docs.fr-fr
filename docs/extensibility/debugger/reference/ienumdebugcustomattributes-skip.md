---
title: IEnumDebugCustomAttributes::Skip | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumCustomAttributes::Skip
helpviewer_keywords: IEnumDebugCustomAttributes::Skip
ms.assetid: 54c72e23-cd4c-4746-935c-abea8057dd1b
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 90f4f369f1d896a03b18816a061def1b056757ed
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugcustomattributesskip"></a>IEnumDebugCustomAttributes::Skip
Ignore un nombre spécifié d’attributs personnalisés dans une séquence d’énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
```csharp  
int Skip(  
   uint celt  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `celt`  
 [in] Nombre d’éléments à ignorer.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si `celt` est supérieur au nombre d’éléments restants ; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Si `celt` spécifie une valeur supérieure au nombre d’éléments restants, l’énumération est définie à la fin et `S_FALSE` est retourné.  
  
## <a name="see-also"></a>Voir aussi  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)