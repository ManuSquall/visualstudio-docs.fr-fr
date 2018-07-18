---
title: IDebugField::GetType | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugField::GetType
helpviewer_keywords:
- IDebugField::GetType method
ms.assetid: b3cdec9f-ef7b-44d0-a775-d17ef7eae968
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ad684837fcda28fbe45874e5a5573f4581a9217f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31118802"
---
# <a name="idebugfieldgettype"></a>IDebugField::GetType
Cette méthode obtient le type du champ.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetType(   
   IDebugField** ppType  
);  
```  
  
```csharp  
int GetType(  
   out IDebugField ppType  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppType`  
 [out] Retourne le type de champ en tant qu’un autre [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objet.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)