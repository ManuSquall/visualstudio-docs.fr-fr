---
title: IDebugModule3::LoadSymbols | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 00b357a7c122de2788875632b770c4346963d975
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="idebugmodule3loadsymbols"></a>IDebugModule3::LoadSymbols
Charge les symboles du module actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT LoadSymbols(  
   void  
);  
```  
  
```csharp  
int LoadSymbols();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Si la méthode réussit, elle retourne `S_OK`. En cas d’échec, il retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Cette méthode charge les symboles à partir du chemin de recherche actuel (qui peut être modifié en appelant le [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md) méthode).  
  
 Cette méthode est préférée sur la [ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
