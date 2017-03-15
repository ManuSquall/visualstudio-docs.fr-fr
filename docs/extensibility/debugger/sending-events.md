---
title: "L’envoi d’événements | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
caps.latest.revision: 7
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: edd4abfa31b309290bdb07fd98c104a279d98fc7
ms.lasthandoff: 02/22/2017

---
# <a name="sending-events"></a>L’envoi d’événements
Le mécanisme de communication entre le débogueur et le moteur de débogage (DE) est un modèle d’événement basé sur DCOM. Les événements sont envoyés en tant qu’objets COM, et chaque événement comporte des paramètres qui spécifient les éléments suivants :  
  
-   Le DE qui a appelé l’événement.  
  
-   Une description de ce qui est arrivé.  
  
-   Le processus de programme et informations sur le thread qui identifie le contexte où l’événement s’est produit. Le processus n’est pas envoyé pour les événements envoyés à partir d’un DE.  
  
-   Le type d’événement qui indique si l’événement est synchrone ou asynchrone.  
  
 Tous les événements de débogage sont envoyés à l’aide de la méthode [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Sources d’événements](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 Explique les deux sources d’événements : le moteur de débogage (DE) et la session de débogage manager (SDM).  
  
 [Types d’événements pris en charge](../../extensibility/debugger/supported-event-types.md)  
 Décrit les types d’événements actuellement prises en charge : synchrone et asynchrone.  
  
 [Descriptions des événements](../../extensibility/debugger/event-descriptions.md)  
 Définit les événements et les raisons de leur utilisation.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Création d’un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Décrit comment un DE fonctionne avec l’interpréteur ou le système d’exploitation pour fournir des services de débogage.
