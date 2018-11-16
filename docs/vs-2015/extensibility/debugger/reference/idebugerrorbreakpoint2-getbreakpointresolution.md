---
title: IDebugErrorBreakpoint2::GetBreakpointResolution | Microsoft Docs
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
- IDebugErrorBreakpoint2::GetBreakpointResolution
helpviewer_keywords:
- IDebugErrorBreakpoint2::GetBreakpointResolution
ms.assetid: 1c2324ed-2a11-4e63-8f3a-f420c7a4018b
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 07212e54c0e176ef974ec2d92f3406e683baec53
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51780436"
---
# <a name="idebugerrorbreakpoint2getbreakpointresolution"></a>IDebugErrorBreakpoint2::GetBreakpointResolution
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtient la résolution d’erreur de point d’arrêt qui décrit l’erreur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetBreakpointResolution(   
   IDebugErrorBreakpointResolution2** ppErrorResolution  
);  
```  
  
```csharp  
int GetBreakpointResolution(   
   out IDebugErrorBreakpointResolution2 ppErrorResolution  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppErrorResolution`  
 [out] Retourne un [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md) objet qui décrit l’erreur.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)   
 [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)

