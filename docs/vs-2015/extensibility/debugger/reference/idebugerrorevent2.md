---
title: IDebugErrorEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2
helpviewer_keywords:
- IDebugErrorEvent2 interface
ms.assetid: 275b6f38-b3d4-4cae-8491-491177f524fb
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 83170c72eeabaae2ac193e47ddc91e1ec1e54046
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695420"
---
# <a name="idebugerrorevent2"></a>IDebugErrorEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface spécifie un message d’erreur à signaler à l’utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugErrorEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le moteur DE débogage (DE) implémente cette interface pour signaler les erreurs en tant que messages explicites. L’interface [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface. Le SDM utilise [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) pour accéder à l' `IDebugEvent2` interface.  
  
## <a name="notes-for-callers"></a>Notes pour les appelants  
 Le DE crée et envoie cet objet d’événement pour signaler une erreur. L’événement est envoyé à l’aide de la fonction de rappel [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu’il est attaché au programme en cours de débogage.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre vtable  
 Cette interface implémente la méthode suivante :  
  
|Méthode|Description|  
|------------|-----------------|  
|`GetErrorMessage`|Retourne une erreur sous la forme d’une chaîne lisible par l’utilisateur.|  
  
## <a name="remarks"></a>Notes  
 Si le moteur de débogage rencontre une erreur, il peut utiliser cette interface pour signaler le message à l’utilisateur dans Visual Studio.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
