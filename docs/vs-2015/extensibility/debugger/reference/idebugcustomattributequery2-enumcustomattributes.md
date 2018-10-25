---
title: IDebugCustomAttributeQuery2::EnumCustomAttributes | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
helpviewer_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
ms.assetid: 94bfce74-aa3d-45f0-8e04-5715faf85217
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fa53677865a3c22765589e8bacbdcf24df0d511e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49888813"
---
# <a name="idebugcustomattributequery2enumcustomattributes"></a>IDebugCustomAttributeQuery2::EnumCustomAttributes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtient un énumérateur pour tous les attributs personnalisés attachés à ce champ.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 [out] Retourne un [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) représentant la liste des attributs personnalisés de l’objet ; sinon, retourne une valeur null si aucun attribut personnalisé.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ou S_FALSE s’il en existe aucun attribut personnalisé sur ce champ. Sinon, retourne un code d’erreur ;  
  
## <a name="remarks"></a>Notes  
 Un champ peut avoir plusieurs attributs personnalisés.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)

