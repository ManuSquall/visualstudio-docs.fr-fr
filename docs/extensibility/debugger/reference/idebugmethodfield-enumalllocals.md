---
title: IDebugMethodField::EnumAllLocals | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMethodField::EnumAllLocals
helpviewer_keywords:
- IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2c8208b0d803dc5cbf6333f15cbda5b0f34bbd16
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
Crée un énumérateur pour toutes les variables locales de la méthode, y compris celles générées de manière interne par un compilateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumAllLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```csharp  
int EnumAllLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pAddress`  
 [in] Un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objet représentant une adresse de débogage dans la méthode, en pointant sur une étendue particulière ou d’un contexte.  
  
 `ppLocals`  
 [out] Retourne un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) de l’objet qui représente la liste de toutes les variables locales dans la portée spécifiée ; sinon, retourne une valeur null n’indiquant aucuns variables locales.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ou retourne S_FALSE, s’il n’y a aucuns variables locales. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Uniquement les variables définies dans le bloc qui contient l’adresse de débogage donné sont énumérées. Cette méthode inclut toutes les variables locales générées par le compilateur. Si tout ce qui est nécessaire sont les variables locales définies explicitement dans la source, l’appel de la [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) (méthode).  
  
 Une méthode peut contenir plusieurs contextes ou des blocs de portée.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)