---
title: IDebugCustomAttributeQuery2::EnumCustomAttributes | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCustomAttributeQuery2::EnumCustomAttributes
helpviewer_keywords: IDebugCustomAttributeQuery2::EnumCustomAttributes
ms.assetid: 94bfce74-aa3d-45f0-8e04-5715faf85217
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 47b643c8f08de60bb873f3daf69ee93e0816d31f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcustomattributequery2enumcustomattributes"></a>IDebugCustomAttributeQuery2::EnumCustomAttributes
Obtient un énumérateur pour tous les attributs personnalisés attachés à ce champ.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumCustomAttributes(   
   IEnumDebugCustomAttributes** ppEnum  
);  
```  
  
```csharp  
int EnumCustomAttributes(  
   out IEnumDebugCustomAttributes ppEnum  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppEnum`  
 [out] Retourne un [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) l’objet représentant la liste des attributs personnalisés ; sinon, retourne une valeur null s’il en existe pas d’attributs personnalisés.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ou S_FALSE si il n’y pas d’attributs personnalisés sur ce champ. Sinon, retourne un code d’erreur ;  
  
## <a name="remarks"></a>Remarques  
 Un champ peut avoir plusieurs attributs personnalisés.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)