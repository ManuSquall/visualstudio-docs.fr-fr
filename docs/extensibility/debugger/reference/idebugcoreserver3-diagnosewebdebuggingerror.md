---
title: IDebugCoreServer3::DiagnoseWebDebuggingError | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
caps.latest.revision: 8
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
ms.openlocfilehash: 2c9ed64c1db1472e334333f3c2cb6d1bfb017c25
ms.contentlocale: fr-fr
ms.lasthandoff: 09/06/2017

---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
Tente de déterminer la raison pour laquelle un auto-attach a échoué.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DiagnoseWebDebuggingError(  
   LPCWSTR pszUrl  
);  
```  
  
```csharp  
int DiagnoseWebDebuggingError(  
   string pszUrl  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszUrl`  
 [in] Non utilisées actuellement ; doit toujours être défini sur une valeur null.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Autres codes de retour par défaut sont les suivants :  
  
|Code|Description|  
|----------|-----------------|  
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|Impossible de déterminer pourquoi le serveur distant a échoué démarrer le débogage.|  
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|Impossible de déboguer sur un serveur distant, probablement en raison d’autorisations insuffisantes ou parce que le verbe de débogage n’est pas activé.|  
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Le serveur web a été verrouillé et bloque le verbe DEBUG, ce qui est nécessaire pour activer le débogage.|  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
