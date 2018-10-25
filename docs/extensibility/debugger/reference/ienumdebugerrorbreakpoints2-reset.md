---
title: IEnumDebugErrorBreakpoints2::Reset | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugErrorBreakpoints2::Reset
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2::Reset
ms.assetid: d5b04bba-a8b9-4141-94fb-250c77f0534c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 97d010a6ce699085693040e18824cbecf20d9e06
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49880089"
---
# <a name="ienumdebugerrorbreakpoints2reset"></a>IEnumDebugErrorBreakpoints2::Reset
Réinitialise l’énumération au premier élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Reset(  
   void  
);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Une fois que cette méthode est appelée, l’appel suivant à la [suivant](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md) méthode retourne le premier élément de l’énumération.  
  
## <a name="see-also"></a>Voir aussi  
 [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)