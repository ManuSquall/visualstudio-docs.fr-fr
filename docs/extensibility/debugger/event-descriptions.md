---
title: Descriptions des événements | Microsoft Docs
description: En savoir plus sur les types d’événements et les raisons de leur utilisation. Chaque type d’événement a un but spécifique.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ee2eedac924b3bbd58fac6980da9151a88da9196
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902642"
---
# <a name="event-descriptions"></a>Descriptions des événements
Chaque type d’événement a un but spécifique.

## <a name="events-and-the-reasons-for-their-use"></a>Événements et raisons de leur utilisation

|Événement|Description|
|-----------|-----------------|
|Activer les événements de document|Se produit lorsque le moteur DE débogage (DE) souhaite que l’IDE ouvre ou place un document au premier plan.|
|Événements d’erreur liés à un point d’arrêt ou point d’arrêt|Envoyé lorsqu’un point d’arrêt est lié ou lorsqu’un point d’arrêt ne peut pas être lié et qu’une erreur est retournée.|
|Événements indépendants des points d’arrêt|Se produit lorsqu’un point d’arrêt lié dissocie du code.|
|Peut arrêter des événements|Envoyé à l’IDE pour déterminer si l’utilisateur souhaite s’arrêter à un point spécifié dans le code.|
|Événements de point d’arrêt|Se produit lorsqu’un point d’arrêt de code ou de données est atteint.|
|Événements de texte de document|Se produit lorsque le texte d’un document est modifié. Ces événements ne sont pas envoyés par le biais de la `IDebugEventCallBack2::Event` méthode.|
|Événements de création de moteur|Envoyé lors de la création initiale d’un moteur.|
|Événements de point d’entrée|Envoyé lorsque le programme en cours de débogage a exécuté son code d’initialisation et a atteint son premier point d’entrée utilisateur.|
|Événements d’exception|Envoyé lorsqu’un programme en cours d’exécution a atteint une exception.|
|Événements de fin d’évaluation d’expression|Envoyé lorsque l’évaluation de l’expression asynchrone est terminée.|
|Rechercher des événements de symboles|Envoyé chaque fois que le DE doit demander à l’utilisateur de rechercher des symboles pour un module.|
|Événements de chargement complet|Envoyé uniquement lorsque la charge initiale du programme est terminée et que le premier code est sur le paragraphe de s’exécuter dans le programme.|
|Événements de message|Envoyé lorsque des messages sont envoyés aux utilisateurs.|
|Événements de chargement de module|Envoyé lorsqu’un nouveau module est chargé ou déchargé.|
|Événements de chaîne de sortie|Envoyé lorsque le programme écrit la sortie de débogage.|
|Créer et détruire des événements|Envoyé pour annoncer la création ou la destruction de processus, programmes, propriétés, sessions et threads afin que l’IDE de Visual Studio puisse effectuer le suivi de l’état des programmes en cours de débogage.|
|Événements de fin d’étape|Envoyé lorsqu’une étape est terminée.|
|Événements de changement de nom de thread|Envoyé lorsque l’utilisateur modifie le nom d’un thread.|
|Événements de changement de nom de programme|Envoyé lorsque l’utilisateur modifie le nom d’un programme.|

## <a name="see-also"></a>Voir aussi
- [Envoi des événements](../../extensibility/debugger/sending-events.md)
