---
title: "Descriptions des &#233;v&#233;nements | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "débogage [Debugging SDK], événements"
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Descriptions des &#233;v&#233;nements
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Chaque type d'événement a un rôle spécifique.  
  
## Événements et les raisons de leur usage  
  
|Événement|Description|  
|---------------|-----------------|  
|Vérifiez les événements de document|La fonctionnalité générer lorsque le moteur \(DE\) de débogage souhaite l'IDE pour ouvrir et à un document au premier plan.|  
|Limite de point d'arrêt ou événement d'erreur de point d'arrêt|Envoyé lorsqu'un point d'arrêt est lié ou lorsqu'un point d'arrêt liaison impossible et une erreur est retournée.|  
|événements indépendants de point d'arrêt|La fonctionnalité générer lorsqu'un point d'arrêt lié annule la liaison de code.|  
|Peut arrêter des événements|Envoyé à l'IDE pour déterminer si l'utilisateur souhaite arrêter à un point spécifié dans le code.|  
|événements de point d'arrêt|La fonctionnalité générer lorsqu'un point d'arrêt de code ou de données est atteint.|  
|Événements de texte de document|La fonctionnalité générer lorsque le texte dans un document est modifié.  Ces événements ne sont pas envoyés par le biais de la méthode d' `IDebugEventCallBack2::Event` .|  
|le moteur créent des événements|Envoyé lorsqu'un moteur création.|  
|événements de point d'entrée|Envoyé lorsque le programme débogué a exécuté son code d'initialisation et a atteint son premier point d'entrée d'utilisateur.|  
|événements d'exception|Envoyé lorsqu'un programme en cours de exécution atteint une exception.|  
|Événements complets d'évaluation de l'expression|Envoyé lorsque l'évaluation de l'expression asynchrone est terminée.|  
|événements de symbole de recherche|Envoyé chaque fois que le De doit demander à l'utilisateur de rechercher des symboles d'un module.|  
|Événements complets de charge|Envoyées que lorsque le chargement initial est terminé et le premier code est sur le point d'exécution du programme.|  
|événements de message|Envoyé lorsque les messages sont envoyés aux utilisateurs.|  
|événements de chargement du module|Envoyé lorsqu'un module est chargé ou déchargé.|  
|Événements de chaîne|Envoyé lorsque la sortie de débogage de programme.|  
|Créez et détruisent des événements|Envoyé pour annoncer la création ou la destruction des processus, les programmes, les propriétés, les sessions et les threads afin que l'IDE de Visual Studio peut conserver l'état des programmes en cours.|  
|Événements complets d'étape|Envoyé lorsqu'une étape est terminée.|  
|événements de changement de nom de thread|Envoyé lorsque l'utilisateur modifie le nom d'un thread.|  
|Événements de modification du nom du programme|Envoyé lorsque l'utilisateur modifie le nom d'un programme.|  
  
## Voir aussi  
 [L'envoi d'événements](../../extensibility/debugger/sending-events.md)