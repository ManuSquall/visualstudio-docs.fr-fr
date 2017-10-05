---
title: IDebugBoundBreakpoint2::SetCondition | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugBoundBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugBoundBreakpoint2::SetCondition method
ms.assetid: 5d366876-efed-43d0-8ea1-dfdb009cbfac
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
ms.openlocfilehash: 2b4e7fa667bfd5c0956233588210bc87e55d02bd
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="idebugboundbreakpoint2setcondition"></a>IDebugBoundBreakpoint2::SetCondition
Définit ou modifie la condition associée à ce point d’arrêt lié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetCondition(   
   BP_CONDITION bpCondition  
);  
```  
  
```csharp  
int SetCondition(   
   enum_BP_CONDITION bpCondition  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `bpCondition`  
 [in] Une valeur à partir de la [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) énumération qui décrit la condition.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Retourne `E_BP_DELETED` si l’état de l’objet de point d’arrêt lié est défini `BPS_DELETED` (dans le cadre de la [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) énumération).  
  
## <a name="remarks"></a>Remarques  
 Toute condition qui a été précédemment associée à ce point d’arrêt est perdue.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
