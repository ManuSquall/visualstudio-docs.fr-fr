---
title: Envoi d’événements | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9bbe7946b866cd751be1f0dac2dba5b8dea57e04
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sending-events"></a>Envoi d’événements
Le mécanisme de communication entre le débogueur et le moteur de débogage (DE) est un modèle d’événement en fonction de DCOM. Les événements sont envoyés en tant qu’objets COM, et chaque événement avec des paramètres qui spécifient les éléments suivants :  
  
-   Le DE qui a appelé l’événement.  
  
-   Description de ce qui est arrivé.  
  
-   Le processus de programme et informations sur le thread qui identifiant le contexte d’où l’événement s’est produite. Le processus n’est pas envoyé pour les événements envoyés à partir d’un DE.  
  
-   Le type d’événement qui indique si l’événement est synchrone ou asynchrone.  
  
 Tous les événements de débogage sont envoyés à l’aide de la méthode [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Sources d’événements](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 Explique les deux sources d’événements : le moteur de débogage (DE) et la session de débogage responsable de la.  
  
 [Types d’événements pris en charge](../../extensibility/debugger/supported-event-types.md)  
 Décrit les types d’événements pris en charge actuellement : synchrone et asynchrone.  
  
 [Descriptions des événements](../../extensibility/debugger/event-descriptions.md)  
 Définit les événements et les raisons de leur utilisation.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Création d’un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Décrit le fonctionne d’un DE avec l’interpréteur ou le système d’exploitation pour fournir des services de débogage.