---
title: IDebugMethodField::EnumAllLocals | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumAllLocals
helpviewer_keywords:
- IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2f0f89c3fee45d6d56b845753958d697e41ab11f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68190887"
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crée un énumérateur pour toutes les variables locales de la méthode, y compris celles générées en interne par un compilateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 [in] Un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objet représentant une adresse de débogage au sein de la méthode, qui pointe vers une étendue particulière ou d’un contexte.  
  
 `ppLocals`  
 [out] Retourne un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) de l’objet qui représente la liste de toutes les variables locales dans la portée spécifiée ; sinon, retourne une valeur null n’indiquant aucuns variables locales.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK, ou retourne S_FALSE s’il n’y a aucuns variables locales. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Uniquement les variables définies dans le bloc qui contient l’adresse de débogage donné sont énumérés. Cette méthode inclut les variables locales générées par le compilateur. Si tout ce qui est nécessaire sont les variables locales définies explicitement dans la source, l’appel de la [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) (méthode).  
  
 Une méthode peut contenir plusieurs contextes d’étendue ou de blocs.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)
