---
title: Pile des appels événement Graphics | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.callstack
ms.assetid: 8a30168d-8b39-4de1-b094-c7356ba101a3
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8344050d26286263e0c33974b976e4ae25ff18de
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58951530"
---
# <a name="graphics-event-call-stack"></a>Pile des appels des événements Graphics
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La pile des appels des événements Graphics dans Visual Studio Graphics Analyzer vous permet de mapper la relation entre les événements graphiques problématiques et le code source de votre application.  
  
 Voici la fenêtre Pile des appels des événements :  
  
 ![Pile des appels précédents un événement DrawIndexed. ](../debugger/media/gfx-diag-demo-graphics-event-call-stack-orientation.png "gfx_diag_demo_graphics_event_call_stack_orientation")  
  
## <a name="understanding-the-graphics-event-call-stack"></a>Présentation de la pile des appels des événements Graphics  
 Vous pouvez utiliser la fenêtre Pile des appels des événements pour comprendre le flux d'exécution qui a conduit à un événement Direct3D particulier. Elle ressemble à la fenêtre de pile des appels de Visual Studio. Toutefois, au lieu d'afficher la pile des appels du thread actif dans une application en cours d'exécution, elle affiche la pile des appels telle qu'elle existait quand l'événement Direct3D sélectionné s'est produit. À partir de la pile des appels des événements, vous pouvez accéder au site d'appel de l'événement Direct3D sélectionné pour inspecter le code environnant.  
  
 En ayant recours à la pile des appels des événements pour identifier le chemin de code d'où provient un événement lié à un problème, vous pouvez utiliser vos connaissances de la base de code pour en déduire les sources potentielles du problème. Par ailleurs, vous pouvez ajouter des points d'arrêt dans le code source de votre application pour pouvoir utiliser les techniques traditionnelles de débogage et comprendre comment l'état de l'application ou les paramètres d'événement sont à l'origine du problème. Cette analyse peut vous aider à trouver les problèmes du code source qui se manifestent uniquement sous forme de problèmes de rendu.  
  
### <a name="graphics-event-call-stack-information"></a>Informations de la Pile des appels des événements Graphics  
 La pile des appels des événements ne prend pas en charge les événements antérieurs aux frames ou définis par l'utilisateur. La Pile des appels des événements Graphics s'affiche sous forme de tableau.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Name**|Symbole qui identifie de manière unique la fonction qui contient le site d'appel. Le symbole de débogage de la fonction est affiché quand il est disponible. Par ailleurs, le décalage de fonction est affiché.|  
|**Fichier**|Nom de fichier du fichier de code source ou du fichier bibliothèque qui contient le site d'appel.|  
|**Emplacement**|Numéro de ligne du site d'appel.|  
  
### <a name="links-to-graphics-objects"></a>Liens vers les objets graphiques  
 Pour comprendre l'événement graphique sélectionné, vous aurez peut-être besoin d'informations sur les objets Direct3D auxquels il est associé. La fenêtre **Pile des appels des événements Graphics** fournit des liens vers ces informations.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : objets manquants en raison de Vertex Shader](../debugger/walkthrough-missing-objects-due-to-vertex-shading.md)
