---
title: Visual Studio Graphics Diagnostics | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1974480a2abefaaa38c05f4b1e4588eaddfd480e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="visual-studio-graphics-diagnostics"></a>Diagnostics des graphiques Visual Studio
Visual Studio*Graphics Diagnostics* est un ensemble d’outils pour l’enregistrement, puis en analysant les problèmes de rendu et de performances dans les applications Direct3D. Graphics Diagnostics peut être utilisé sur les applications qui s’exécutent localement sur votre PC Windows, dans un émulateur d’appareil Windows, ou sur un PC ou un appareil distant.  
  
 Le flux de travail Graphics Diagnostics commence par capturer un enregistrement de la façon dont votre application utilise Direct3D (dynamiquement, durant son exécution) pour que les informations relatives au comportement puissent être analysées immédiatement, partagées ou enregistrées pour un usage différé. Sessions de capture peuvent être lancées et contrôlées manuellement à partir de Visual Studio ou avec l’outil de ligne de commande de capture **dxcap.exe**. Les sessions de capture peuvent également être lancées et contrôlées par programmation à l’aide des API de capture Graphics Diagnostics.  
  
 Après une session de capture a été enregistrée son contenu peut être lu par Visual Studio *Graphics Analyzer* à tout moment, en recréant les frames capturés en utilisant les mêmes ressources exacts et de commandes de rendu de l’application utilisée. Ensuite, à l'aide des outils fournis dans la fenêtre Graphics Analyzer, les frames capturés peuvent être analysés en détail. Ces outils permettent d'examiner un appel d'API, une ressource, un objet État du pipeline, une étape de canalisation Direct3D, ou même l'historique complet d'un pixel dans un frame capturé. L’utilisation conjointe de ces outils permet d’explorer un problème de rendu de façon intuitive, depuis son apparition dans un frame capturé jusqu’à sa cause racine dans le code source, les nuanceurs ou les ressources graphiques de l’application.  
  
 Pour diagnostiquer des problèmes de performances, un frame capturé peut être analysé à l’aide de la *analyse des frames* outil. Cet outil explore les optimisations de performances potentielles en changeant automatiquement la manière dont l'application utilise Direct3D, et en vous fournissant des benchmarks de toutes les variations. Par le passé, vous avez peut-être été amené à effectuer et évaluer les modifications de ce genre manuellement, simplement pour trouver celles qui faisaient la différence. Avec l'outil Analyse des frames, il vous suffit d'apporter les modifications dont l'impact est garanti.  
  
 Graphics Diagnostics contribue à rendre votre application graphique Direct3D plus esthétique et plus performante.  
  
 Continuer à [vue d’ensemble](overview-of-visual-studio-graphics-diagnostics.md) pour en savoir plus sur ce que propose Visual Studio Graphics Diagnostics.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d’ensemble](overview-of-visual-studio-graphics-diagnostics.md)  
 Présente le flux de travail et les outils de Graphics Diagnostics.  
  
 [Prise en main](getting-started-with-visual-studio-graphics-diagnostics.md)  
 Dans cette section, vous apprendrez à installer Visual Studio Graphics Diagnostics, et à utiliser Graphics Diagnostics avec votre application Direct3D.  
  
 [Capturing Graphics Information](capturing-graphics-information.md)  
 Pour examiner un problème de rendu dans votre application à l’aide de Graphics Diagnostics, vous devez d’abord enregistrer des informations indiquant comment l’application utilise DirectX. Au cours de la session d’enregistrement, en tant que votre application s’exécute normalement, vous *capture* (autrement dit, sélectionnez) les frames qui vous intéressent. Les captures contiennent des informations détaillées sur le rendu des frames. Vous pouvez enregistrer les informations capturées sous forme de document journal de graphisme pour l’examiner ultérieurement ou le partager avec d’autres membres de votre équipe.  
  
 [Utilisation du GPU](gpu-usage.md)  
 Pour profiler votre application à l’aide de Graphics Diagnostics, utilisez l’outil Utilisation du GPU. Servez-vous de l'outil Utilisation du GPU conjointement avec d'autres outils de profilage, tels que l'outil Utilisation de l'UC, pour mettre en corrélation les activités de l'UC et du GPU éventuellement responsables des problèmes de performances de votre application.  
  
 [Document journal de graphisme](graphics-log-document.md)  
 Pour démarrer l’examen d’un journal de graphisme enregistré, vous utilisez la fenêtre de document journal de graphisme pour sélectionner un frame capturé, voire un pixel spécifique, afin que vous pouvez examiner en détail le *événements* (autrement dit, les appels d’API DirectX) qui l’affectent .  
  
 [Analyse des frames](graphics-frame-analysis.md)  
 Une fois le frame sélectionné, utilisez l’analyse des frames graphiques pour examiner et ajuster vos performances de rendu.  
  
 [Liste des événements](graphics-event-list.md)  
 Après avoir sélectionné un frame, vous utilisez la **liste des événements Graphics** pour examiner les événements pour déterminer si elles sont liées au problème de rendu.  
  
 [État](graphics-state.md)  
 La fenêtre État vous permet de comprendre l'état graphique actif au moment de l'événement actuel.  
  
 [Étapes de canalisation](graphics-pipeline-stages.md)  
 Dans le **étapes de canalisation Graphics** fenêtre, vous étudiez la manière dont l’événement sélectionné est traité par chaque étape du pipeline graphique afin que vous puissiez identifier où le problème de rendu s’affiche d’abord. L'examen des étapes de canalisation est particulièrement utile quand un objet ne s'affiche pas en raison d'une transformation incorrecte ou quand une des étapes génère une sortie qui ne correspond pas à ce qu'attend l'étape suivante.  
  
 [Pile des appels des événements](graphics-event-call-stack.md)  
 Vous utilisez la **événements Graphics** pour examiner la pile des appels de l’événement actuellement sélectionné afin que vous pouvez accéder au code d’application qui est lié au problème de rendu.  
  
 [Historique des pixels](graphics-pixel-history.md)  
 À l’aide de la **historique des pixels Graphics** fenêtre pour analyser la façon dont le pixel sélectionné est affecté par les événements qui ont influencé, vous pouvez identifier l’événement ou la combinaison d’événements qui provoquent certains types de problèmes de rendu. L'historique des pixels est particulièrement utile en cas de rendu incorrect d'un objet du fait d'une sortie du nuanceur de pixels incorrecte ou mal combinée avec le tampon de trame ou encore quand un objet ne s'affiche même pas si, par exemple, ses pixels ont été ignorés avant d'atteindre le tampon de trame.  
  
 [Table des objets](graphics-object-table.md)  
 Vous utilisez la **Table des objets Graphics** pour examiner les propriétés et le contenu des objets Direct3D spécifiques et des ressources qui sont en vigueur pour l’événement sélectionné. La table des objets peut vous aider à déterminer le contexte du périphérique graphique actif au cours d’un événement et à examiner le contenu de ressources graphiques telles que les mémoires tampons constantes, les mémoires tampons de vertex et les textures.  
  
 [Débogueur HLSL](hlsl-shader-debugger.md)  
 Pour examiner le code du nuanceur pour l’événement sélectionné et les graphiques l’étape de canalisation, vous utilisez la **débogueur HLSL** pour parcourir le code, examiner le contenu des variables et effectuer d’autres tâches classiques de débogage. Vous pouvez aussi utiliser le débogueur HLSL pour examiner le code de nuanceur de calcul, que les résultats subissent un traitement supplémentaire de la canalisation Graphics ou qu'ils soient seulement relus par votre application.  
  
 [Outil de capture en ligne de commande](command-line-capture-tool.md)  
 Utilisez l'outil en ligne de commande de capture pour capturer et lire rapidement des informations graphiques sans passer par Visual Studio ou une capture par programmation. En particulier, vous pouvez utiliser l'outil en ligne de commande pour l'automatisation ou dans un environnement de test.  
  
 [Exemples](graphics-diagnostics-examples.md)  
 Plusieurs exemples montrent comment utiliser conjointement les outils Graphics Diagnostics pour diagnostiquer différents types de problèmes de rendu.  
  
## <a name="related-sections"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Visite guidée des fonctionnalités du débogueur](../debugging-in-visual-studio.md)|Présente la fonctionnalité de débogage de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].|  
|[Graphiques et jeux DirectX](http://go.microsoft.com/fwlink/?LinkId=256498)|Fournit des articles ayant trait aux technologies graphiques DirectX.|