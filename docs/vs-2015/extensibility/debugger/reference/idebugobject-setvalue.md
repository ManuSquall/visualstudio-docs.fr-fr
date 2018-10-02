---
title: IDebugObject::SetValue | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c47439c69ece059b12ff0d92efd438d73a366915
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504328"
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugObject::SetValue](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugobject-setvalue).  
  
Définit la valeur de l’objet à partir d’une série consécutive d’octets.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT SetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```csharp  
int SetValue(  
   byte[] pValue,   
   uint   nSize  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pValue`  
 [in] Un tableau d’octets représentant la nouvelle valeur.  
  
 `nSize`  
 [in] La taille de la valeur en octets.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Les valeurs du tableau sont copiées dans la collection [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objet, en remplaçant toute valeur existante. La taille de la nouvelle valeur peut être supérieure ou inférieure à la valeur existante. Cela `IDebugObject` ne peut pas être une référence null.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)

