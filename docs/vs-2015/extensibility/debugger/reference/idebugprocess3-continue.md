---
title: 'IDebugProcess3 :: continuer | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 92a36bb7e89d8afaa6d76f7d7b3772bd1714ffa7
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86386236"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Poursuit l’exécution de ce processus à partir d’un état arrêté. Tout état d’exécution précédent (par exemple, une étape) est préservé et le processus recommence à s’exécuter.  
  
> [!NOTE]
> Cette méthode doit être utilisée à la place de [continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Continue(  
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Continue(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pThread`  
 dans Objet [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) qui représente le thread à continuer.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK` ; sinon, retourne le code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est appelée sur ce processus, quel que soit le nombre de processus en cours de débogage, ou le processus qui a généré l’événement d’arrêt. L’implémentation doit conserver l’état d’exécution précédent (par exemple, une étape) et continuer l’exécution comme si elle n’avait jamais été arrêtée avant la fin de son exécution. Autrement dit, si un thread de ce processus effectue une opération de pas à pas et s’est arrêté parce qu’un autre processus s’est arrêté, puis `Continue` a été appelé, le thread spécifié doit terminer l’opération de pas à pas d’origine.  
  
 **Avertissement** N’envoyez pas d’événement d’arrêt ou d’événement immédiat (synchrone) à un [événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) lors de la gestion de cet appel ; dans le cas contraire, le débogueur peut cesser de répondre.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
