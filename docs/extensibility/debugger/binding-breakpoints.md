---
title: Points d’arrêt contraignants (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 680cff398a43d1ebe9ccf061ad42781500c7cf01
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739234"
---
# <a name="bind-breakpoints"></a>Bind points d’arrêt
Si l’utilisateur définit un point d’arrêt, peut-être en appuyant sur **F9**, l’IDE formule la demande et invite la session de débogé pour créer le point d’arrêt.

## <a name="set-a-breakpoint"></a>Définir un point d'arrêt
 La définition d’un point d’arrêt est un processus en deux étapes, car le code ou les données affectées par le point d’arrêt peuvent ne pas encore être disponibles. Tout d’abord, le point d’arrêt doit être décrit, puis, au fur et à mesure que le code ou les données deviennent disponibles, il doit être lié à ce code ou à ces données, comme suit :

1. Le point d’arrêt est demandé aux moteurs de débogé (DE) pertinents, puis le point d’arrêt est lié au code ou aux données dès qu’il devient disponible.

2. La demande de point d’arrêt est envoyée à la session de débog, qui l’envoie à tous les DE pertinents. Tout DE qui choisit de gérer le point d’arrêt crée un point d’arrêt correspondant en attente.

3. La session de débog recueille les points d’arrêt en attente et les renvoie à l’emballage de déboguer (le composant de débogage de Visual Studio).

4. Le paquet de débog invite la session de débog à lier le point d’arrêt en attente au code ou aux données. La session de débogé envoie cette demande à tous les DE pertinents.

5. Si le DE est capable de lier le point d’arrêt, il envoie un événement lié à un point d’arrêt de retour à la session de débogé. Si ce n’est pas le cas, il envoie un événement d’erreur de point de rupture à la place.

## <a name="pending-breakpoints"></a>Points d’arrêt en attente
 Un point d’arrêt en attente peut se lier à plusieurs emplacements de code. Par exemple, une ligne de code source pour un modèle CMD peut se lier à chaque séquence de code générée à partir du modèle. La session de débogé peut utiliser un événement lié au point d’arrêt pour énumérer les contextes de code liés à un point d’arrêt au moment de l’envoi de l’événement. Plus de contextes de code peuvent être liés plus tard, de sorte que le DE peut envoyer plusieurs événements liés point d’arrêt pour chaque demande de liaison. Toutefois, un DE ne devrait envoyer qu’un seul événement d’erreur de point de rupture par demande de liaison.

## <a name="implementation"></a>Implémentation
 Sur le plan programmatique, le paquet de débogé appelle le gestionnaire de déboque de session (SDM) et lui donne une interface [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) qui enveloppe une structure [BP_REQUEST_INFO,](../../extensibility/debugger/reference/bp-request-info.md) qui décrit le point d’arrêt à définir. Bien que les points d’arrêt puissent être de nombreuses formes, ils se résolvent en fin de compte à un code ou un contexte de données.

 Le SDM passe cet appel à chaque DE pertinent en appelant sa méthode [CreatePendingBreakpoint.](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) Si le DE choisit de gérer le point d’arrêt, il crée et renvoie une interface [IDebugPendingBreakpoint2.](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) Le SDM recueille ces interfaces et les transmet au paquet `IDebugPendingBreakpoint2` de débog comme une seule interface.

 Jusqu’à présent, aucun événement n’a été généré.

 Le paquet de débog tente alors de lier le point d’arrêt en attente au code ou aux données en appelant [Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md), qui est implémenté par le DE.

 Si le point d’arrêt est lié, le DE envoie une interface d’événement [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) au paquet de débogé. Le paquet de débogé utilise cette interface pour énumérer tous les contextes de code (ou le contexte de données unique) liés au point d’arrêt en appelant [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md), qui renvoie une ou plusieurs interfaces [IDebugBoundBreakpoint2.](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) [L’interface GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) renvoie une interface [IDebugBreakpointResolution2,](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) et [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) renvoie une [BP_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) syndicat contenant le code ou le contexte de données.

 Si le DE n’est pas en mesure de lier le point d’arrêt, il envoie une seule interface d’événement [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) au paquet de débogé. Le paquet de débog récupère le type d’erreur (erreur ou avertissement) et le message d’information en appelant [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md), suivi par [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) et [GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md). Cela renvoie une structure [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) qui contient le type d’erreur et le message.

 Si un DE gère un point d’arrêt mais ne `BPET_TYPE_ERROR`peut pas le lier, il renvoie une erreur de type . Le paquet de débaille répond en affichant une boîte de dialogue d’erreur, et l’IDE place un glyphe d’exclamation à l’intérieur du glyphe de point d’arrêt à gauche de la ligne de code source.

 Si un DE gère un point d’arrêt, ne peut pas le lier, mais un autre DE pourrait le lier, il retourne un avertissement. L’IDE répond en plaçant un glyphe de question à l’intérieur du glyphe de point d’arrêt à gauche de la ligne de code source.

## <a name="see-also"></a>Voir aussi
- [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)
