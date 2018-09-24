---
title: Descriptions d’événement | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: afcad096b9f2991939b1378e44524c9cd83a9baf
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231032"
---
# <a name="event-descriptions"></a>Descriptions des événements
Chaque type d’événement a un objectif spécifique.  
  
## <a name="events-and-the-reasons-for-their-use"></a>Événements et les raisons de leur utilisation  
  
|Événement|Description|  
|-----------|-----------------|  
|Activer les événements de document|Se produit lorsque le moteur de débogage (dé) veut l’IDE pour ouvrir ou de mettre un document au premier plan.|  
|Point d’arrêt lié ou des événements d’erreur de point d’arrêt|Envoyé lorsqu’un point d’arrêt est lié ou un point d’arrêt ne peut pas lier et une erreur est retournée.|  
|Événements de point d’arrêt indépendant|Se produit lorsqu’un point d’arrêt lié annule la liaison à partir du code.|  
|Peut arrêter les événements|Envoyé à l’IDE pour déterminer si l’utilisateur souhaite arrêter à un point spécifié dans le code.|  
|Événements de point d’arrêt|Se produit lorsqu’un point d’arrêt du code ou des données est atteint.|  
|Événements de texte de document|Se produit lorsque le texte dans un document est modifié. Ces événements ne sont pas envoyés via le `IDebugEventCallBack2::Event` (méthode).|  
|Moteur de créer des événements|Envoyé lorsque vous créez un moteur.|  
|Événements de point d’entrée|Envoyé lorsque le programme en cours de débogage a exécuté son code d’initialisation et atteint son premier point d’entrée utilisateur.|  
|Événements d’exception|Envoyé lorsqu’un programme en cours d’exécution atteint une exception.|  
|Événements de fin expression d’évaluation|Envoyé lorsque l’évaluation de l’expression asynchrone est terminée.|  
|Rechercher des événements de symbole|Envoyé chaque fois que vous le DE demander à l’utilisateur à rechercher des symboles pour un module.|  
|Événements de fin de charge|Envoyé uniquement lorsque la charge initiale du programme est terminée et que le premier code est prêt à être exécuté dans le programme.|  
|Événements de message|Envoyé lorsque des messages sont envoyés aux utilisateurs.|  
|Événements de chargement de module|Envoyé lorsqu’un nouveau module est chargé ou déchargé.|  
|Événements de chaîne de sortie|Envoyé lorsque le programme écrit la sortie de débogage.|  
|Créer et détruire des événements|Envoyé d’annoncer la création ou la destruction des processus, des programmes, des propriétés, des sessions et des threads afin de l’IDE Visual Studio peut effectuer le suivi de l’état des programmes en cours de débogage.|  
|Événements de fin d’étape|Envoyé lorsqu’une étape est terminée.|  
|Événements de changement de nom de thread|Envoyé lorsque l’utilisateur modifie le nom d’un thread.|  
|Événements de changement de nom de programme|Envoyé lorsque l’utilisateur modifie le nom d’un programme.|  
  
## <a name="see-also"></a>Voir aussi  
 [Envoi d’événements](../../extensibility/debugger/sending-events.md)