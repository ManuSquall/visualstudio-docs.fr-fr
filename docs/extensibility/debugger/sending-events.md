---
title: "Envoi d’événements | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bf4c3b0f494a5825820b8f794ccaf5dc727786e3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
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