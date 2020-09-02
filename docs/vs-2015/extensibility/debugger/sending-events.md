---
title: Envoi d’événements | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 98247b894d2db628d508713875ba0ea7d0642729
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204743"
---
# <a name="sending-events"></a>Envoi d’événements
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le mécanisme de communication entre le débogueur et le moteur de débogage (DE) est un modèle d’événement basé sur DCOM. Les événements sont envoyés en tant qu’objets COM, et chaque événement possède des paramètres qui spécifient les éléments suivants :  
  
- DE qui a appelé l’événement.  
  
- Description de ce qui s’est passé.  
  
- Informations sur le processus, le programme et le thread qui identifient le contexte dans lequel l’événement s’est produit. Le processus n’est pas envoyé pour les événements envoyés à partir d’un.  
  
- Type d’événement qui indique si l’événement est synchrone ou asynchrone.  
  
  Tous les événements de débogage sont envoyés à l’aide de la méthode [IDebugEventCallback2 :: Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Sources d’événement](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 Explique les deux sources d’événements : le moteur de débogage (DE) et le gestionnaire de débogage de session (SDM).  
  
 [Types d’événements pris en charge](../../extensibility/debugger/supported-event-types.md)  
 Décrit les types d’événements actuellement pris en charge : asynchrone et synchrone.  
  
 [Descriptions des événements](../../extensibility/debugger/event-descriptions.md)  
 Définit les événements et les raisons de leur utilisation.  
  
## <a name="related-sections"></a>Sections connexes  
 [Création d’un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Décrit comment un DE fonctionne avec l’interpréteur ou le système d’exploitation pour fournir des services de débogage.
