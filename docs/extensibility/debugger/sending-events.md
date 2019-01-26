---
title: Envoi d’événements | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 397c5edfb76d2a4277db0e805daf4a55bd9608dc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54995819"
---
# <a name="send-events"></a>Envoyer des événements
Le mécanisme de communication entre le débogueur et le moteur de débogage (dé) est un modèle d’événement basé sur DCOM. Les événements sont envoyés en tant qu’objets COM, et chaque événement possède des paramètres qui spécifient :  
  
- Le DE qui a appelé l’événement.  
  
- Une description de ce qui est arrivé.  
  
- Le processus de programme et informations sur le thread qui identifie le contexte d’où l’événement s’est produite. Le processus n’est pas envoyé pour les événements envoyés à partir d’un DE.  
  
- Le type d’événement qui indique si l’événement est synchrone ou asynchrone.  
  
  Tous les événements de débogage sont envoyées à l’aide de la méthode [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Sources d’événements](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 Explique les deux sources d’événements : le moteur de débogage (dé) et la session de débogage manager (SDM).  
  
 [Types d’événements pris en charge](../../extensibility/debugger/supported-event-types.md)  
 Décrit les types d’événements actuellement prises en charge : synchrones et asynchrones.  
  
 [Descriptions des événements](../../extensibility/debugger/event-descriptions.md)  
 Définit les événements et les raisons de leur utilisation.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Création d’un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Décrit le fonctionne d’un DE avec le système d’exploitation ou un interpréteur pour fournir des services de débogage.