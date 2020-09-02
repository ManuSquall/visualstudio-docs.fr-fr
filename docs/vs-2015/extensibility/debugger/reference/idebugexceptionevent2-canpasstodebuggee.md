---
title: 'IDebugExceptionEvent2 :: CanPassToDebuggee | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 383287a027a75adfb4c58020675e08a46198eacf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163811"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Détermine si le moteur de débogage (DE) prend en charge l’option de passage de cette exception au programme en cours de débogage au moment de la reprise de l’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT CanPassToDebuggee(  
   void  
);  
```  
  
```csharp  
int CanPassToDebuggee();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une ou l’autre `S_OK` (l’exception peut être passée au programme) ou `S_FALSE` (l’exception ne peut pas être transmise sur).  
  
## <a name="remarks"></a>Notes  
 L’option DE doit avoir une action par défaut pour passer à l’élément débogué. L’IDE peut recevoir l’événement [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) et appeler la méthode [continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) sans appeler la `CanPassToDebuggee` méthode. Par conséquent, le paramètre DE doit avoir un cas par défaut pour le passage de l’exception sur ou non.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [Continuer](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
