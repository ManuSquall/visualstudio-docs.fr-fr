---
title: IDebugProperty2::GetParent | Microsoft Docs
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
- IDebugProperty2::GetParent
helpviewer_keywords:
- IDebugProperty2::GetParent
ms.assetid: 58780469-fe25-4d84-9187-67940ca0767f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 131bda7f00ef708eb4554a73dc8389f39d3f2e47
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508513"
---
# <a name="idebugproperty2getparent"></a>IDebugProperty2::GetParent
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugProperty2::GetParent](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugproperty2-getparent).  
  
Obtient la propriété parent d’une propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetParent (   
   IDebugProperty2** ppParent  
);  
```  
  
```csharp  
int GetParent (   
   out IDebugProperty2 ppParent  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppParent`  
 [out] Retourne un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objet qui représente le parent de la propriété.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon retourne le code d’erreur. Retourne `S_GETPARENT_NO_PARENT` s’il n’existe aucun parent.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)

