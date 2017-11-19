---
title: IDebugCustomAttribute::GetName | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCustomAttribute::GetName
helpviewer_keywords: IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 165362ab03685a3acca457e4095778b9dcb182e8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
Obtient le nom de l’attribut personnalisé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetName(   
   BSTR* bstrName  
);  
```  
  
```csharp  
int GetName(  
   out string bstrName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `bstrName`  
 [out] Retourne une chaîne contenant le nom de l’attribut personnalisé.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Nommé retourné par cette méthode correspond au nom de la classe utilisée pour déclarer l’attribut. Cela peut correspondent pas exactement au nom de la classe de l’attribut personnalisé comme c# permet le suffixe « Attribute » à supprimer à partir d’un nom d’attribut personnalisé lorsqu’elle est utilisée dans une déclaration.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)