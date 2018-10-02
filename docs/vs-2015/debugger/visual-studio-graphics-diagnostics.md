---
title: Visual Studio Graphics Diagnostics | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.graphics
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
caps.latest.revision: 42
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c708900a0eebb2f4de1515eeab2f788eb5345a03
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47495570"
---
# <a name="visual-studio-graphics-diagnostics"></a>Diagnostics des graphiques Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Visual Studio Graphics Diagnostics](https://docs.microsoft.com/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics).  
  
Visual Studio*Graphics Diagnostics* est un ensemble d’outils pour l’enregistrement, puis en analysant les problèmes de rendu et de performances dans les applications Direct3D. Graphics Diagnostics peut être utilisé sur les applications qui s’exécutent localement sur votre PC Windows, dans un émulateur d’appareil Windows, ou sur un PC ou un appareil distant.  
  
 Le flux de travail Graphics Diagnostics commence par capturer un enregistrement de la façon dont votre application utilise Direct3D (dynamiquement, durant son exécution) pour que les informations relatives au comportement puissent être analysées immédiatement, partagées ou enregistrées pour un usage différé. Sessions de capture peuvent être lancées et contrôlées manuellement à partir de Visual Studio ou avec l’outil de ligne de commande de capture **dxcap.exe**. Les sessions de capture peuvent également être lancées et contrôlées par programmation à l’aide des API de capture Graphics Diagnostics.  
  
 Une fois une session de capture a été enregistrée son contenu peut être lu par Visual Studio *Graphics Analyzer* à tout moment, recréant les frames capturés en utilisant les mêmes ressources exactes et de commandes de rendu de l’application utilisée. Ensuite, à l'aide des outils fournis dans la fenêtre Graphics Analyzer, les frames capturés peuvent être analysés en détail. Ces outils permettent d'examiner un appel d'API, une ressource, un objet État du pipeline, une étape de canalisation Direct3D, ou même l'historique complet d'un pixel dans un frame capturé. L’utilisation conjointe de ces outils permet d’explorer un problème de rendu de façon intuitive, depuis son apparition dans un frame capturé jusqu’à sa cause racine dans le code source, les nuanceurs ou les ressources graphiques de l’application.  
  
 Pour diagnostiquer les problèmes de performances, un frame capturé peut être analysé à l’aide du *analyse des frames* outil. Cet outil explore les optimisations de performances potentielles en changeant automatiquement la manière dont l'application utilise Direct3D, et en vous fournissant des benchmarks de toutes les variations. Par le passé, vous avez peut-être été amené à effectuer et évaluer les modifications de ce genre manuellement, simplement pour trouver celles qui faisaient la différence. Avec l'outil Analyse des frames, il vous suffit d'apporter les modifications dont l'impact est garanti.  
  
 Graphics Diagnostics contribue à rendre votre application graphique Direct3D plus esthétique et plus performante.  
  
 Continuer à [vue d’ensemble](../debugger/overview-of-visual-studio-graphics-diagnostics.md) pour en savoir plus sur ce que propose Visual Studio Graphics Diagnostics.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d’ensemble](../debugger/overview-of-visual-studio-graphics-diagnostics.md)  
 Présente le flux de travail et les outils de Graphics Diagnostics.  
  
 [Prise en main](../debugger/getting-started-with-visual-studio-graphics-diagnostics.md)  
 Dans cette section, vous apprendrez à installer Visual Studio Graphics Diagnostics, et à utiliser Graphics Diagnostics avec votre application Direct3D.  
  
 [Capture d’informations graphiques](../debugger/capturing-graphics-information.md)  
 Pour examiner un problème de rendu dans votre application à l’aide de Graphics Diagnostics, vous devez d’abord enregistrer des informations indiquant comment l’application utilise DirectX. Pendant la session d’enregistrement, que votre application s’exécute normalement, vous *capturer* (autrement dit, sélectionnez) les frames qui vous intéresse. Les captures contiennent des informations détaillées sur le rendu des frames. Vous pouvez enregistrer les informations capturées sous forme de document journal de graphisme pour l’examiner ultérieurement ou le partager avec d’autres membres de votre équipe.  
  
 [Utilisation du GPU](../debugger/gpu-usage.md)  
 Pour profiler votre application à l’aide de Graphics Diagnostics, utilisez l’outil Utilisation du GPU. Servez-vous de l'outil Utilisation du GPU conjointement avec d'autres outils de profilage, tels que l'outil Utilisation de l'UC, pour mettre en corrélation les activités de l'UC et du GPU éventuellement responsables des problèmes de performances de votre application.  
  
 [Document journal de graphisme](../debugger/graphics-log-document.md)  
 Pour démarrer l’examen d’un journal de graphisme enregistré, utilisez la fenêtre de document journal de graphisme pour sélectionner une image capturée, ou même un pixel spécifique, afin que vous puissiez examiner en détail le *événements* (autrement dit, les appels d’API DirectX) qui l’affectent .  
  
 [Analyse des frames](../debugger/graphics-frame-analysis.md)  
 Une fois le frame sélectionné, utilisez l’analyse des frames graphiques pour examiner et ajuster vos performances de rendu.  
  
 [Liste des événements](../debugger/graphics-event-list.md)  
 Une fois que vous avez sélectionné un frame, vous utilisez le **liste des événements Graphics** pour examiner les événements pour déterminer si elles sont liées au problème de rendu.  
  
 [État](../debugger/graphics-state.md)  
 La fenêtre État vous permet de comprendre l'état graphique actif au moment de l'événement actuel.  
  
 [Étapes de canalisation](../debugger/graphics-pipeline-stages.md)  
 Dans le **étapes de canalisation Graphics** fenêtre, vous examinez la façon dont l’événement sélectionné est traité par chaque étape du pipeline graphique afin que vous puissiez identifier où le problème de rendu s’affiche d’abord. L'examen des étapes de canalisation est particulièrement utile quand un objet ne s'affiche pas en raison d'une transformation incorrecte ou quand une des étapes génère une sortie qui ne correspond pas à ce qu'attend l'étape suivante.  
  
 [Pile des appels des événements](../debugger/graphics-event-call-stack.md)  
 Vous utilisez le **événements Graphics** pour examiner la pile des appels de l’événement sélectionné afin que vous pouvez accéder au code d’application qui est lié au problème de rendu.  
  
 [Historique des pixels](../debugger/graphics-pixel-history.md)  
 À l’aide de la **historique des pixels Graphics** fenêtre pour analyser la façon dont le pixel sélectionné est affecté par les événements qui l’ont influencé, vous pouvez identifier l’événement ou une combinaison d’événements qui provoquent certains types de problèmes de rendu. L'historique des pixels est particulièrement utile en cas de rendu incorrect d'un objet du fait d'une sortie du nuanceur de pixels incorrecte ou mal combinée avec le tampon de trame ou encore quand un objet ne s'affiche même pas si, par exemple, ses pixels ont été ignorés avant d'atteindre le tampon de trame.  
  
 [Table des objets](../debugger/graphics-object-table.md)  
 Vous utilisez le **Table des objets Graphics** pour examiner les propriétés et le contenu des objets Direct3D spécifiques et des ressources qui sont en vigueur pour l’événement sélectionné. La table des objets peut vous aider à déterminer le contexte du périphérique graphique actif au cours d’un événement et à examiner le contenu de ressources graphiques telles que les mémoires tampons constantes, les mémoires tampons de vertex et les textures.  
  
 [Débogueur HLSL](../debugger/hlsl-shader-debugger.md)  
 Pour examiner comment le code du nuanceur pour l’événement sélectionné et les graphiques de phase pipeline se comporte, vous utilisez le **débogueur HLSL** pour parcourir le code, examinez le contenu des variables et effectuer d’autres tâches de débogage classiques. Vous pouvez aussi utiliser le débogueur HLSL pour examiner le code de nuanceur de calcul, que les résultats subissent un traitement supplémentaire de la canalisation Graphics ou qu'ils soient seulement relus par votre application.  
  
 [Outil de capture en ligne de commande](../debugger/command-line-capture-tool.md)  
 Utilisez l'outil en ligne de commande de capture pour capturer et lire rapidement des informations graphiques sans passer par Visual Studio ou une capture par programmation. En particulier, vous pouvez utiliser l'outil en ligne de commande pour l'automatisation ou dans un environnement de test.  
  
 [Exemples](../debugger/graphics-diagnostics-examples.md)  
 Plusieurs exemples montrent comment utiliser conjointement les outils Graphics Diagnostics pour diagnostiquer différents types de problèmes de rendu.  
  
## <a name="related-sections"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md)|Présente la fonctionnalité de débogage de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|[Graphiques et jeux DirectX](http://go.microsoft.com/fwlink/?LinkId=256498)|Fournit des articles ayant trait aux technologies graphiques DirectX.|



