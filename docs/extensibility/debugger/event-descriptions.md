---
title: Descriptions de l’événement Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3c2582717fd4da3b833da90a951f9b8f72a59f71
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738785"
---
# <a name="event-descriptions"></a>Descriptions d’événements
Chaque type d’événement a un but spécifique.

## <a name="events-and-the-reasons-for-their-use"></a>Événements et les raisons de leur utilisation

|Événement|Description|
|-----------|-----------------|
|Activer les événements documentaires|Se produire lorsque le moteur de débogé (DE) veut que l’IDE s’ouvre ou apporte un document au premier plan.|
|Événements d’erreur liés au point de rupture ou de point de rupture|Envoyé lorsqu’un point d’arrêt est lié ou lorsqu’un point d’arrêt ne peut pas se lier et qu’une erreur est retournée.|
|Événements non liés de point de rupture|Se produire lorsqu’un point d’arrêt lié se détache du code.|
|Peut arrêter les événements|Envoyé à l’IDE pour déterminer si l’utilisateur souhaite s’arrêter à un point précis dans le code.|
|Événements breakpoint|Se produire lorsqu’un code ou un point d’arrêt de données est touché.|
|Événements texte documentaire|Se produire lorsque le texte d’un document est modifié. Ces événements ne sont `IDebugEventCallBack2::Event` pas envoyés par la méthode.|
|Le moteur crée des événements|Envoyé lorsqu’un moteur est créé pour la première fois.|
|Événements de point d’entrée|Envoyé lorsque le programme étant déboché a exécuté son code d’initialisation et atteint son premier point d’entrée utilisateur.|
|Événements d’exception|Envoyé quand un programme en cours d’exécution atteint une exception.|
|Évaluation de l’expression des événements complets|Envoyé lorsque l’évaluation d’expression asynchrone est terminée.|
|Trouver des événements Symbol|Envoyé chaque fois que le DE a besoin de demander à l’utilisateur de trouver des symboles pour un module.|
|Charger des événements complets|Envoyé seulement lorsque la charge initiale du programme est terminée et que le premier code est sur le point de s’exécuter dans le programme.|
|Événements de messages|Envoyé lorsque des messages sont envoyés aux utilisateurs.|
|Événements de chargement de module|Envoyé lorsqu’un nouveau module est chargé ou déchargé.|
|Événements de chaîne de sortie|Envoyé lorsque le programme écrit la sortie de déboiffé.|
|Créer et détruire des événements|Envoyé pour annoncer la création ou la destruction de processus, programmes, propriétés, sessions et fils afin que le Visual Studio IDE puisse garder une trace de l’état des programmes en cours de déboisation.|
|Étape des événements complets|Envoyé quand une étape est terminée.|
|Événements de changement de nom de fil|Envoyé lorsque l’utilisateur change le nom d’un thread.|
|Événements de changement de nom du programme|Envoyé lorsque l’utilisateur change le nom d’un programme.|

## <a name="see-also"></a>Voir aussi
- [Envoi des événements](../../extensibility/debugger/sending-events.md)
