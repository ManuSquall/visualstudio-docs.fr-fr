---
title: IDebugProperty2::SetValueAsReference | Microsoft Docs
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
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: aa128e570c0b55af71f87946d7c25d668b987fcd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494953"
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugProperty2::SetValueAsReference](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugproperty2-setvalueasreference).  
  
Définit la valeur de cette propriété à la valeur de la référence donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT SetValueAsReference(  
   IDebugReference2** rgpArgs,  
   DWORD              dwArgCount,  
   IDebugReference2*  pValue,  
   DWORD              dwTimeout  
);  
```  
  
```csharp  
int SetValueAsReference(  
   IDebugReference2[] rgpArgs,  
   uint               dwArgCount,  
   IDebugReference2   pValue,  
   uint               dwTimeout  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `rgpArgs`  
 [in] Tableau d’arguments à passer à l’accesseur de propriété de code managé. Si la méthode setter de propriété ne prend pas d’arguments ou si cette [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objet ne fait pas référence à cet un accesseur Set de propriété, `rgpArgs` doit être une valeur null. Ce paramètre est généralement une valeur null.  
  
 `dwArgCount`  
 [in] Le nombre d’arguments dans le `rgpArgs` tableau.  
  
 `pValue`  
 [in] Une référence, sous la forme d’un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objet, à la valeur à utiliser pour définir cette propriété.  
  
 `dwTimeout`  
 [in] Combien de temps à suivre pour définir la valeur, en millisecondes. Une valeur typique est `INFINITE`. Cela affecte la durée pendant laquelle toute évaluation possible peut prendre.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne une erreur de code, généralement une des opérations suivantes :  
  
|Error|Description|  
|-----------|-----------------|  
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|Définition de la valeur à partir d’une référence n’est pas pris en charge.|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Impossible de définir la valeur que cette propriété fait référence à une méthode.|  
|`E_SETVALUE_VALUE_IS_READONLY`|La valeur est en lecture seule et ne peut pas être définie.|  
|`E_NOTIMPL`|La méthode n’est pas implémentée.|  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)

