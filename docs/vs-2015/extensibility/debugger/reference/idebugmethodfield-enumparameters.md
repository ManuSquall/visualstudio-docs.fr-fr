---
title: 'IDebugMethodField :: EnumParameters | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8ebdd604ba97fda8751cf037e7494b59e7bb77ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162597"
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crée un énumérateur pour les paramètres de la méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 à Retourne un objet [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant la liste des paramètres de la méthode. Sinon, retourne une valeur null s’il n’y a aucun paramètre.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne S_OK ou retourne S_FALSE s’il n’y a aucun paramètre. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Chaque élément est un objet [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) représentant différents types de paramètres. Appelez la méthode [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) sur chaque objet pour déterminer exactement le type de paramètre représenté par l’objet.  
  
 Un paramètre comprend à la fois son nom de variable et son type. Le premier paramètre d’une méthode de classe est généralement le pointeur « this ».  
  
 Si seuls les types des paramètres sont nécessaires, appelez la méthode [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)
