---
title: Pile des appels des événements Graphics | Microsoft Docs
description: Passez en revue la pile des appels des événements Graphics dans Visual Studio Graphics Analyzer pour mapper la relation entre les événements graphiques problématiques et le code source de votre application.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.callstack
ms.assetid: 8a30168d-8b39-4de1-b094-c7356ba101a3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85712f2b8971b2b5284dab89d90eecec9010e9b4
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727748"
---
# <a name="graphics-event-call-stack"></a>Pile des appels des événements Graphics
La pile des appels des événements Graphics dans Visual Studio Graphics Analyzer vous permet de mapper la relation entre les événements graphiques problématiques et le code source de votre application.

 Voici la fenêtre Pile des appels des événements :

 ![La pile des appels précédant un événement DrawIndexed.](media/gfx_diag_demo_graphics_event_call_stack_orientation.png "gfx_diag_demo_graphics_event_call_stack_orientation")

## <a name="understanding-the-graphics-event-call-stack"></a>Présentation de la pile des appels des événements Graphics
 Vous pouvez utiliser la fenêtre Pile des appels des événements pour comprendre le flux d'exécution qui a conduit à un événement Direct3D particulier. Elle ressemble à la fenêtre de pile des appels de Visual Studio. Toutefois, au lieu d’afficher la pile des appels du thread actif dans une application en cours d’exécution, elle affiche la pile des appels telle qu’elle existait quand l’événement Direct3D sélectionné s’est produit. À partir de la pile des appels des événements, vous pouvez accéder au site d'appel de l'événement Direct3D sélectionné pour inspecter le code environnant.

 En ayant recours à la pile des appels des événements pour identifier le chemin de code d'où provient un événement lié à un problème, vous pouvez utiliser vos connaissances de la base de code pour en déduire les sources potentielles du problème. Par ailleurs, vous pouvez ajouter des points d'arrêt dans le code source de votre application pour pouvoir utiliser les techniques traditionnelles de débogage et comprendre comment l'état de l'application ou les paramètres d'événement sont à l'origine du problème. Cette analyse peut vous aider à trouver les problèmes du code source qui se manifestent uniquement sous forme de problèmes de rendu.

### <a name="graphics-event-call-stack-information"></a>Informations de la Pile des appels des événements Graphics
 La pile des appels des événements ne prend pas en charge les événements antérieurs aux frames ou définis par l'utilisateur. La Pile des appels des événements Graphics s'affiche sous forme de tableau.

|Colonne|Description|
|------------|-----------------|
|**Nom**|Symbole qui identifie de manière unique la fonction qui contient le site d'appel. Le symbole de débogage de la fonction est affiché quand il est disponible. Par ailleurs, le décalage de fonction est affiché.|
|**File**|Nom de fichier du fichier de code source ou du fichier bibliothèque qui contient le site d'appel.|
|**Lieu**|Numéro de ligne du site d'appel.|

### <a name="links-to-graphics-objects"></a>Liens vers les objets graphiques
 Pour comprendre l'événement graphique sélectionné, vous aurez peut-être besoin d'informations sur les objets Direct3D auxquels il est associé. La fenêtre **Pile des appels des événements Graphics** fournit des liens vers ces informations.

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : objets manquants en raison de Vertex Shader](walkthrough-missing-objects-due-to-vertex-shading.md)