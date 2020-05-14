---
title: Envoi d’événements (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5ec0d3aa29da562147b71b8efde49baf07d8ae0b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713042"
---
# <a name="send-events"></a>Envoyer des événements
Le mécanisme de communication entre le débbuggeur et le moteur de débogé (DE) est un modèle d’événement basé sur DCOM. Les événements sont envoyés sous forme d’objets COM, et chaque événement a des paramètres qui spécifient :

- Le DE qui a appelé l’événement.

- Une description de ce qui s’est passé.

- Les informations sur le processus, le programme et le fil qui identifient le contexte de l’endroit où l’événement s’est produit. Le processus n’est pas envoyé pour les événements envoyés à partir d’un DE.

- Le type d’événement qui indique si l’événement est synchrone ou asynchrone.

  Tous les événements de débog sont envoyés en utilisant la méthode [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="in-this-section"></a>Contenu de cette section
 [Sources d’événements](../../extensibility/debugger/event-sources-visual-studio-sdk.md) Explique les deux sources d’événements : le moteur de débogé (DE) et le gestionnaire de débogé de session (SDM).

 [Types d’événements soutenus](../../extensibility/debugger/supported-event-types.md) Discute des types d’événements actuellement pris en charge : asynchrones et synchrones.

 [Descriptions d’événements](../../extensibility/debugger/event-descriptions.md) Définit les événements et les raisons de leur utilisation.

## <a name="related-sections"></a>Sections connexes
 [Création d’un moteur de débogé personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md) Décrit comment un DE fonctionne avec l’interprète ou le système d’exploitation pour fournir des services de débogage.
