---
title: IDebugMethodField::EnumArguments | Microsoft Docs
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
- IDebugMethodField::EnumArguments
helpviewer_keywords:
- IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2e016fde472874a902a80e4fe23f45a1cb3e5134
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49852035"
---
# <a name="idebugmethodfieldenumarguments"></a>IDebugMethodField::EnumArguments
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crée un énumérateur pour le type de chaque argument requis pour appeler la méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT EnumArguments(   
   IEnumDebugFields** ppParams  
);  
```  
  
```csharp  
int EnumArguments(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppParams`  
 [out] Retourne un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objet représentant la liste des types d’arguments. Retourne une valeur null s’il en existe aucun argument.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK, ou retourne S_FALSE s’il y a aucun argument. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Chaque élément est un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objet représentant les types de chaque paramètre. Appelez le [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) méthode pour récupérer des informations sur le type de chaque paramètre.  
  
 Si le nom du paramètre est nécessaire, ainsi que le type, puis appelez le [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)

