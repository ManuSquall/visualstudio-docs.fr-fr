---
title: IDebugMethodField::EnumParameters | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6eb2272aff9f02e4de85c5420bd687b059c0e839
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55035439"
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
Crée un énumérateur pour les paramètres de la méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumParameters(   
   IEnumDebugFields** ppParams  
);  
```  
  
```csharp  
int EnumParameters(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppParams`  
 [out] Retourne un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant la liste des paramètres à la méthode de l’objet ; sinon, retourne une valeur null si aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK, ou retourne S_FALSE s’il n’existe aucun paramètre. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Chaque élément est un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objet représentant les différents types de paramètres. Appelez le [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) méthode sur chaque objet pour déterminer exactement quel type de paramètre de l’objet représente.  
  
 Un paramètre inclut son nom de la variable et son type. Le premier paramètre à une méthode de classe est généralement le pointeur « this ».  
  
 Si seuls les types des paramètres est nécessaire, appelez le [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)