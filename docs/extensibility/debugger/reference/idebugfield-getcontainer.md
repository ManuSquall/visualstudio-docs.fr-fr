---
title: IDebugField::GetContainer | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugField::GetContainer
helpviewer_keywords: IDebugField::GetContainer method
ms.assetid: 6d6c8213-6181-4adf-9584-3e4cac163dd8
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0049ebeb51d385850105d65d5db624829005d7d7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugfieldgetcontainer"></a>IDebugField::GetContainer
Cette méthode obtient le conteneur d’un champ.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetContainer(   
   IDebugContainerField** ppContainerField  
);  
```  
  
```csharp  
int GetContainer(  
   out IDebugContainerField ppContainerField  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppContainerField`  
 [out] Retourne le conteneur, tel que représenté par la [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interface.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Si ce champ n’est pas un conteneur, retourné `ppContainerField` correspond à une valeur null.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)