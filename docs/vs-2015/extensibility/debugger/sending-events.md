---
title: Envoi d’événements | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9109ef312fb16b4b370a9a8428f3ffb202b272ff
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862864"
---
# <a name="sending-events"></a>Envoi d’événements
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le mécanisme de communication entre le débogueur et le moteur de débogage (dé) est un modèle d’événement basé sur DCOM. Les événements sont envoyés en tant qu’objets COM, et chaque événement possède des paramètres qui spécifient les éléments suivants :  
  
- Le DE qui a appelé l’événement.  
  
- Une description de ce qui est arrivé.  
  
- Le processus de programme et informations sur le thread qui identifie le contexte d’où l’événement s’est produite. Le processus n’est pas envoyé pour les événements envoyés à partir d’un DE.  
  
- Le type d’événement qui indique si l’événement est synchrone ou asynchrone.  
  
  Tous les événements de débogage sont envoyées à l’aide de la méthode [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Sources d’événement](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 Explique les deux sources d’événements : le moteur de débogage (dé) et la session de débogage manager (SDM).  
  
 [Types d’événements pris en charge](../../extensibility/debugger/supported-event-types.md)  
 Décrit les types d’événements actuellement prises en charge : synchrones et asynchrones.  
  
 [Descriptions des événements](../../extensibility/debugger/event-descriptions.md)  
 Définit les événements et les raisons de leur utilisation.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Création d’un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Décrit le fonctionne d’un DE avec le système d’exploitation ou un interpréteur pour fournir des services de débogage.

