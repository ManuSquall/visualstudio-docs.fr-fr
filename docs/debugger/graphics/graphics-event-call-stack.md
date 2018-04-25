---
title: Pile des appels des événements Graphics | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.callstack
ms.assetid: 8a30168d-8b39-4de1-b094-c7356ba101a3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 879189fe71a4bf9dc0b7c56afe81d85d4316b6a4
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="graphics-event-call-stack"></a>Pile des appels des événements Graphics
La pile des appels des événements Graphics dans Visual Studio Graphics Analyzer vous permet de mapper la relation entre les événements graphiques problématiques et le code source de votre application.  
  
 Voici la fenêtre Pile des appels des événements :  
  
 ![Pile des appels précédents un événement DrawIndexed. ] (media/gfx_diag_demo_graphics_event_call_stack_orientation.png "gfx_diag_demo_graphics_event_call_stack_orientation")  
  
## <a name="understanding-the-graphics-event-call-stack"></a>Présentation de la pile des appels des événements Graphics  
 Vous pouvez utiliser la fenêtre Pile des appels des événements pour comprendre le flux d'exécution qui a conduit à un événement Direct3D particulier. Il ressemble à la fenêtre Pile des appels Visual Studio, mais au lieu d’afficher la pile des appels du thread actuel dans une application en cours d’exécution, il affiche la pile des appels telle qu’elle existait lors de l’événement Direct3D sélectionné s’est produite. À partir de la pile des appels des événements, vous pouvez accéder au site d'appel de l'événement Direct3D sélectionné pour inspecter le code environnant.  
  
 En ayant recours à la pile des appels des événements pour identifier le chemin de code d'où provient un événement lié à un problème, vous pouvez utiliser vos connaissances de la base de code pour en déduire les sources potentielles du problème. Par ailleurs, vous pouvez ajouter des points d'arrêt dans le code source de votre application pour pouvoir utiliser les techniques traditionnelles de débogage et comprendre comment l'état de l'application ou les paramètres d'événement sont à l'origine du problème. Cette analyse peut vous aider à trouver les problèmes du code source qui se manifestent uniquement sous forme de problèmes de rendu.  
  
### <a name="graphics-event-call-stack-information"></a>Informations de la Pile des appels des événements Graphics  
 La pile des appels des événements ne prend pas en charge les événements antérieurs aux frames ou définis par l'utilisateur. La Pile des appels des événements Graphics s'affiche sous forme de tableau.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Name**|Symbole qui identifie de manière unique la fonction qui contient le site d'appel. Le symbole de débogage de la fonction est affiché quand il est disponible. Par ailleurs, le décalage de fonction est affiché.|  
|**Fichier**|Nom de fichier du fichier de code source ou du fichier bibliothèque qui contient le site d'appel.|  
|**Emplacement**|Numéro de ligne du site d'appel.|  
  
### <a name="links-to-graphics-objects"></a>Liens vers les objets graphiques  
 Pour comprendre l'événement graphique sélectionné, vous aurez peut-être besoin d'informations sur les objets Direct3D auxquels il est associé. Le **événements Graphics** fenêtre fournit des liens vers ces informations.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : objets manquants en raison de l’ombrage de vertex](walkthrough-missing-objects-due-to-vertex-shading.md)