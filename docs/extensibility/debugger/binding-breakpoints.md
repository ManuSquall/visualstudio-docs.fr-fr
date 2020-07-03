---
title: Liaison de points d’arrêt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e839b6e0e7967c4802bee5617da3334c5d4033c5
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903225"
---
# <a name="bind-breakpoints"></a>Lier des points d’arrêt
Si l’utilisateur définit un point d’arrêt, par exemple en appuyant sur **F9**, l’IDE formule la demande et invite la session de débogage à créer le point d’arrêt.

## <a name="set-a-breakpoint"></a>Définir un point d'arrêt
 La définition d’un point d’arrêt est un processus en deux étapes, car le code ou les données affectées par le point d’arrêt ne sont peut-être pas encore disponibles. Tout d’abord, le point d’arrêt doit être décrit, puis, à mesure que le code ou les données deviennent disponibles, il doit être lié à ce code ou à ces données, comme suit :

1. Le point d’arrêt est demandé à partir des moteurs de débogage appropriés (DEs), puis le point d’arrêt est lié au code ou aux données dès qu’il est disponible.

2. La demande de point d’arrêt est envoyée à la session de débogage, qui l’envoie à tous les. Tout qui choisit de gérer le point d’arrêt crée un point d’arrêt en attente correspondant.

3. La session de débogage collecte les points d’arrêt en attente et les renvoie au package de débogage (le composant de débogage de Visual Studio).

4. Le package de débogage invite la session de débogage à lier le point d’arrêt en attente au code ou aux données. La session de débogage envoie cette demande à tous les DEs.

5. Si le DE est en mesure de lier le point d’arrêt, il renvoie un événement lié à un point d’arrêt à la session de débogage. Si ce n’est pas le cas, il envoie un événement d’erreur de point d’arrêt à la place.

## <a name="pending-breakpoints"></a>Points d’arrêt en attente
 Un point d’arrêt en attente peut être lié à plusieurs emplacements de code. Par exemple, une ligne de code source pour un modèle C++ peut être liée à chaque séquence de code générée à partir du modèle. La session de débogage peut utiliser un événement lié à un point d’arrêt pour énumérer les contextes de code liés à un point d’arrêt au moment où l’événement a été envoyé. D’autres contextes DE code peuvent être liés plus tard, si bien que peut envoyer plusieurs événements liés à un point d’arrêt pour chaque demande de liaison. Toutefois, un ne doit envoyer qu’un seul événement d’erreur DE point d’arrêt par demande de liaison.

## <a name="implementation"></a>Implémentation
 Par programme, le package de débogage appelle le gestionnaire de débogage de session (SDM) et lui donne une interface [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) qui encapsule une structure [BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md) , qui décrit le point d’arrêt à définir. Bien que les points d’arrêt puissent être de nombreuses formes, ils sont finalement résolus en un code ou un contexte de données.

 Le SDM passe cet appel à chaque correspondant DE en appelant sa méthode [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) . Si le DE choisit de gérer le point d’arrêt, il crée et retourne une interface [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) . Le SDM collecte ces interfaces et les transmet au package de débogage sous la forme d’une `IDebugPendingBreakpoint2` interface unique.

 Jusqu’à présent, aucun événement n’a été généré.

 Le package de débogage tente alors de lier le point d’arrêt en attente au code ou aux données en appelant [Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md), qui est implémenté par le.

 Si le point d’arrêt est lié, le DE envoie une interface d’événement [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) au package de débogage. Le package de débogage utilise cette interface pour énumérer tous les contextes de code (ou le contexte de données unique) liés au point d’arrêt en appelant [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md), qui retourne une ou plusieurs interfaces [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) . L’interface [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) retourne une interface [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) , et [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) retourne une [BP_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) Union contenant le code ou le contexte de données.

 Si le DE n’est pas en mesure de lier le point d’arrêt, il envoie une interface d’événement [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) unique au package de débogage. Le package de débogage récupère le type d’erreur (erreur ou avertissement) et le message d’information en appelant [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md), suivi de [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) et [GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md). Cela retourne une structure [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) qui contient le type et le message d’erreur.

 Si un DE gère un point d’arrêt, mais ne peut pas le lier, il retourne une erreur de type `BPET_TYPE_ERROR` . Le package de débogage répond en affichant une boîte de dialogue d’erreur et l’IDE place un glyphe d’exclamation à l’intérieur du glyphe de point d’arrêt à gauche de la ligne de code source.

 Si un DE gère un point d’arrêt, ne peut pas le lier, mais un autre peut le lier, il renvoie un avertissement. L’IDE répond en plaçant un glyphe de question à l’intérieur du glyphe de point d’arrêt à gauche de la ligne de code source.

## <a name="see-also"></a>Voir aussi
- [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)
