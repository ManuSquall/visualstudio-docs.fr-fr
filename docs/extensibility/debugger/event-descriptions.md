---
title: Description de l’événement | Documents Microsoft
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
ms.openlocfilehash: 600d9576d72dbd36b5ff7c2a0d9f0333f72dfafa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="event-descriptions"></a>Descriptions des événements
Chaque type d’événement a un objectif spécifique.  
  
## <a name="events-and-the-reasons-for-their-use"></a>Les événements et les raisons de leur utilisation  
  
|événement|Description|  
|-----------|-----------------|  
|Activer les événements de document|Se produit lorsque le moteur de débogage (DE) souhaite que l’IDE pour ouvrir ou de mettre un document au premier plan.|  
|Point d’arrêt lié ou des événements d’erreur de point d’arrêt|Envoyé lorsqu’un point d’arrêt est lié ou un point d’arrêt ne peut pas créer une liaison et une erreur est retournée.|  
|Événements de point d’arrêt indépendant|Se produit lorsqu’un point d’arrêt lié annule la liaison à partir du code.|  
|Peut arrêter d’événements|Envoyé à l’IDE pour déterminer si l’utilisateur souhaite de s’arrêter à un point spécifié dans le code.|  
|Événements de point d’arrêt|Se produit lorsqu’un point d’arrêt de code ou de données est atteint.|  
|Événements de document texte|Se produit lorsque le texte dans un document est modifié. Ces événements ne sont pas envoyées à travers le `IDebugEventCallBack2::Event` (méthode).|  
|Moteur de créer des événements|Envoyé lors de la création d’un moteur.|  
|Événements de point d’entrée|Envoyé lorsque le programme débogué exécuter son code d’initialisation et a atteint son premier point d’entrée utilisateur.|  
|Événements d’exception|Envoyé lorsque l’exécution d’un programme rencontre une exception.|  
|Événements de complète d’évaluation d’expression|Envoyé lorsque l’évaluation d’expression asynchrone est terminée.|  
|Rechercher des événements de symbole|Envoyé lorsque le DE doit demander à l’utilisateur de rechercher des symboles pour un module.|  
|Événements de chargement complets|Envoyé uniquement lorsque le chargement du programme initiale est terminé et que le premier code est prêt à être exécuté dans le programme.|  
|Événements de message|Envoyé lorsque des messages sont envoyés aux utilisateurs.|  
|Événements de chargement de module|Envoyé lorsqu’un nouveau module est chargé ou déchargé.|  
|Événements de sortie de chaîne|Envoyé lorsque le programme écrit la sortie de débogage.|  
|Création et la destruction des événements|Envoyé à l’aide de la création ou la destruction de processus, les programmes, les propriétés, les sessions et les threads afin de l’IDE Visual Studio peut assurer le suivi de l’état des programmes en cours de débogage.|  
|Étape des événements terminées|Envoyé lorsqu’une étape est terminée.|  
|Événements de changement de nom de thread|Envoyé lorsque l’utilisateur modifie le nom d’un thread.|  
|Événements de changement de nom de programme|Envoyé lorsque l’utilisateur modifie le nom d’un programme.|  
  
## <a name="see-also"></a>Voir aussi  
 [Envoi d’événements](../../extensibility/debugger/sending-events.md)