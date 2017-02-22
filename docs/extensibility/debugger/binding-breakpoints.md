---
title: "Liaison des points d&#39;arr&#234;t | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "points d'arrêt, de liaison"
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Liaison des points d&#39;arr&#234;t
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Si l'utilisateur définit un point d'arrêt, peut\-être en appuyant sur F9, l'IDE formule la demande et invite la session de débogage à créer le point d'arrêt.  
  
## définir un point d'arrêt  
 Définir un point d'arrêt est un processus en deux étapes, car le code ou les données affectées par le point d'arrêt n'a pas pu être disponibles.  D'abord, le point d'arrêt doit être décrit l', puis, à mesure que le code ou les données deviennent disponibles, il doit être lié à ce code ou données, comme suit :  
  
1.  Le point d'arrêt est demandé des moteurs de débogage appropriés \(DEs\), puis le point d'arrêt est lié au code ou aux données lorsqu'elles devient disponible.  
  
2.  La requête de point d'arrêt est envoyée à la session de débogage, qui envoie au DES approprié.  Tout De qui choisit de traiter le point d'arrêt crée un correspondant en attente le point d'arrêt.  
  
3.  La session de débogage collecte les points d'arrêt en attente et les envoie au package de débogage \(le composant de débogage de Visual Studio\).  
  
4.  Le package de débogage invite la session de débogage à lier le point d'arrêt en attente au code ou aux données.  La session de débogage envoie la demande à tout le DES approprié.  
  
5.  Si le De peut lier le point d'arrêt, il envoie un événement lié de point d'arrêt dans la session de débogage.  Sinon, il envoie un événement d'erreur de point d'arrêt à la place.  
  
## En attente des points d'arrêt  
 Un point d'arrêt en attente peut être lié à plusieurs emplacements de code.  Par exemple, une ligne de code source pour le modèle c\+\+ peut être liée à chaque séquence de code générée du modèle.  La session de débogage peut utiliser un événement lié de point d'arrêt pour énumérer les contextes de code liés à un point d'arrêt lorsque l'événement a été envoyé.  Plus de contextes de code peuvent être liés ultérieurement, le De peut envoyer des événements liés de plusieurs points d'arrêt pour chaque demande de liaison.  Toutefois, un De doit renvoyer uniquement un événement d'erreur de point d'arrêt par demande de liaison.  
  
## Implémentation  
 Par programme, le package de débogage appelle le gestionnaire de débogage de session \(SDM\) et lui affecte une interface d' [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) qui encapsule une structure de [BP\_REQUEST\_INFO](../../extensibility/debugger/reference/bp-request-info.md) , qui décrit le point d'arrêt à définir.  Bien que les points d'arrêt puissent être de nombreux formulaires, ils correspondent finalement à un contexte de code ou de données.  
  
 Le SDM passe cet appel à chaque De approprié en appelant sa méthode d' [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) .  Si le De choisit de traiter le point d'arrêt, il crée et retourne une interface d' [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) .  Le SDM collecte ces interfaces et les repasser au package de débogage en tant qu'interface unique d' `IDebugPendingBreakpoint2` .  
  
 jusqu'à présent, aucun événement n'a été généré.  
  
 Les tentatives de package de débogage puis de lier le point d'arrêt en attente au code ou aux données en appelant [Lier](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md), qui est implémenté par le De.  
  
 Si le point d'arrêt est lié, le De envoie une interface d'événement d' [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) au package de débogage.  Le package de débogage utilise cette interface pour énumérer tous les contextes de code \(ou le contexte de données unique\) liés au point d'arrêt en appelant [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md), qui retourne une ou plusieurs interfaces d' [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) .  L'interface d' [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) retourne une interface d' [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) , et retourne d' [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) une union de [BP\_RESOLUTION\_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) contenant le contexte de code ou de données.  
  
 Si le De ne peut pas lier le point d'arrêt, il envoie une interface d'événement unique d' [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) au package de débogage.  Le package de débogage extrait le type d'erreur \(erreur ou de cet avertissement\) et le message d'information en appelant [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md), suivi d' [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) et d' [GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md).  Cela retourne une structure de [BP\_ERROR\_RESOLUTION\_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) qui contient le type d'erreur et le message.  
  
 Si un De traite un point d'arrêt mais liaison impossible, elle retourne une erreur de type `BPET_TYPE_ERROR`.  Le package de débogage répond en affichant une boîte de dialogue d'erreur, et l'IDE place un glyphe d'exclamation à l'intérieur de le glyphe de point d'arrêt à gauche de la ligne de code source.  
  
 Si un De traite un point d'arrêt, liaison impossible, mais un autre De peut lui lier, il retourne un avertissement.  L'IDE répond en plaçant un glyphe de question à l'intérieur de le glyphe de point d'arrêt à gauche de la ligne de code source.  
  
## Voir aussi  
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)