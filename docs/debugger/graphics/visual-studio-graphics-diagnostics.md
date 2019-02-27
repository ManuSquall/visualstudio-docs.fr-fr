---
title: Diagnostics des graphiques | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cbc3edfabe041804a632b919eff4e565be9cc5e3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56703030"
---
# <a name="visual-studio-graphics-diagnostics"></a>Diagnostics des graphiques Visual Studio
Visual Studio*Graphics Diagnostics* est un ensemble d’outils pour l’enregistrement, puis en analysant les problèmes de rendu et de performances dans les applications Direct3D. Graphics Diagnostics peut être utilisé sur les applications qui s'exécutent localement sur votre PC Windows, dans un émulateur d'appareil Windows, ou sur un PC ou un appareil distant.

 Le flux de travail Graphics Diagnostics commence par capturer un enregistrement de la façon dont votre application utilise Direct3D (dynamiquement, durant son exécution) pour que les informations relatives au comportement puissent être analysées immédiatement, partagées ou enregistrées pour un usage différé. Sessions de capture peuvent être lancées et contrôlées manuellement à partir de Visual Studio ou avec l’outil de ligne de commande de capture **dxcap.exe**. Sessions de capture peuvent également lancer et contrôlées par programmation à l’aide de l’API de capture de Graphics Diagnostics.

 Une fois qu’une session de capture a été enregistrée, son contenu peut être lu par Visual Studio *Graphics Analyzer* à tout moment, en recréant les frames capturés à l’aide des ressources et des commandes de rendu utilisées par l’application. Ensuite, à l’aide des outils fournis dans la fenêtre Graphics Analyzer, un des frames capturés peuvent être analysé en détail. Ces outils permettent d'examiner un appel d'API, une ressource, un objet État du pipeline, une étape de canalisation Direct3D, ou même l'historique complet d'un pixel dans un frame capturé. L'utilisation conjointe de ces outils permet d'explorer un problème de rendu de façon intuitive, depuis son apparition dans un frame capturé jusqu'à sa cause racine dans le code source, les nuanceurs ou les ressources graphiques de l'application.

 Pour diagnostiquer les problèmes de performances, un frame capturé peut être analysé à l’aide de l’outil *Analyse des frames*. Cet outil explore les optimisations de performances potentielles en changeant automatiquement la manière dont l'application utilise Direct3D, et en vous fournissant des benchmarks de toutes les variations. Par le passé, vous avez peut-être été amené à effectuer et évaluer les modifications de ce genre manuellement, simplement pour trouver celles qui faisaient la différence. Avec l'outil Analyse des frames, il vous suffit d'apporter les modifications dont l'impact est garanti.

 Graphics Diagnostics contribue à rendre votre application graphique Direct3D plus esthétique et plus performante.

 Continuer à [vue d’ensemble](overview-of-visual-studio-graphics-diagnostics.md) pour en savoir plus sur ce que propose Visual Studio Graphics Diagnostics.

## <a name="in-this-section"></a>Dans cette section
 [Vue d’ensemble](overview-of-visual-studio-graphics-diagnostics.md) présente le flux de travail Graphics Diagnostics et des outils.

 [Mise en route](getting-started-with-visual-studio-graphics-diagnostics.md) dans cette section, vous allez apprendre à installer Visual Studio Graphics Diagnostics et comment commencer à utiliser Graphics Diagnostics avec votre application Direct3D.

 [Capture d’informations graphiques](capturing-graphics-information.md) pour utiliser Graphics Diagnostics pour examiner un problème de rendu dans votre application, vous devez d’abord enregistrez des informations sur la façon dont l’application utilise DirectX. Au cours de la session d’enregistrement, pendant l’exécution normale de l’application, vous *capturez* (ou sélectionnez) les frames qui vous intéressent. Les captures contiennent des informations détaillées sur le rendu des frames. Vous pouvez enregistrer les informations capturées sous forme de document journal de graphisme pour l’examiner ultérieurement ou le partager avec d’autres membres de votre équipe.

 [Utilisation du GPU](gpu-usage.md) pour utiliser Graphics Diagnostics pour profiler votre application, utilisez l’outil utilisation du GPU. Servez-vous de l'outil Utilisation du GPU conjointement avec d'autres outils de profilage, tels que l'outil Utilisation de l'UC, pour mettre en corrélation les activités de l'UC et du GPU éventuellement responsables des problèmes de performances de votre application.

 [Document journal de graphisme](graphics-log-document.md) pour démarrer l’examen d’un journal de graphisme enregistré, utilisez la fenêtre de document journal de graphisme pour sélectionner un frame capturé, voire un pixel spécifique, afin que vous puissiez examiner en détail le *événements* (qui est, les appels d’API de DirectX) qui l’affectent.

 [Analyse des frames](graphics-frame-analysis.md) après avoir sélectionné un frame, vous utilisez l’analyse des frames graphiques pour examiner et ajuster vos performances de rendu.

 [Liste des événements](graphics-event-list.md) une fois que vous avez sélectionné un frame, vous utilisez le **liste des événements Graphics** pour examiner les événements pour déterminer si elles sont liées au problème de rendu.

 [État](graphics-state.md) fenêtre de l’état vous permet de comprendre l’état graphique qui est active au moment de l’événement actuel.

 [Canalisation](graphics-pipeline-stages.md) dans le **étapes de canalisation Graphics** fenêtre, vous examinez la façon dont l’événement sélectionné est traité par chaque étape du pipeline graphique afin que vous puissiez identifier où le problème de rendu premier s’affiche. L'examen des étapes de canalisation est particulièrement utile quand un objet ne s'affiche pas en raison d'une transformation incorrecte ou quand une des étapes génère une sortie qui ne correspond pas à ce qu'attend l'étape suivante.

 [Pile des appels des événements](graphics-event-call-stack.md) vous utiliser le **événements Graphics** pour examiner la pile des appels de l’événement sélectionné afin que vous pouvez accéder au code d’application qui est lié au problème de rendu.

 [Historique des pixels](graphics-pixel-history.md) à l’aide de la **historique des pixels Graphics** fenêtre pour analyser la façon dont le pixel sélectionné est affecté par les événements qui l’ont influencé, vous pouvez identifier l’événement ou une combinaison d’événements qui provoquent certains types de problèmes de rendu. L'historique des pixels est particulièrement utile en cas de rendu incorrect d'un objet du fait d'une sortie du nuanceur de pixels incorrecte ou mal combinée avec le tampon de trame ou encore quand un objet ne s'affiche même pas si, par exemple, ses pixels ont été ignorés avant d'atteindre le tampon de trame.

 [Objet Table](graphics-object-table.md) vous utiliser le **Table des objets Graphics** pour examiner les propriétés et le contenu des objets Direct3D spécifiques et des ressources qui sont en vigueur pour l’événement sélectionné. La table des objets peut vous aider à déterminer le contexte du périphérique graphique actif au cours d’un événement et à examiner le contenu de ressources graphiques telles que les mémoires tampons constantes, les mémoires tampons de vertex et les textures.

 [Débogueur HLSL](hlsl-shader-debugger.md) pour examiner comment le code du nuanceur pour l’événement sélectionné et les graphiques de phase pipeline se comporte, vous utilisez le **débogueur HLSL** pour parcourir le code, examinez le contenu des variables et effectuer d’autres tâches classiques de débogage. Vous pouvez aussi utiliser le débogueur HLSL pour examiner le code de nuanceur de calcul, que les résultats subissent un traitement supplémentaire de la canalisation Graphics ou qu'ils soient seulement relus par votre application.

 [L’outil de ligne de commande de Capture](command-line-capture-tool.md) utiliser l’outil de ligne de commande de capture pour capturer et lire les informations graphiques sans utiliser Visual Studio ou capture par programmation rapidement. En particulier, vous pouvez utiliser l'outil en ligne de commande pour l'automatisation ou dans un environnement de test.

 [Exemples](graphics-diagnostics-examples.md) plusieurs exemples montrent comment utiliser conjointement les outils Graphics Diagnostics pour diagnostiquer différents types de problèmes de rendu.

## <a name="related-sections"></a>Rubriques connexes

| Titre | Description |
| - | - |
| [Visite guidée des fonctionnalités du débogueur](/visualstudio/debugger/debugger-feature-tour) | Présente la fonctionnalité de débogage de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. |
| [Graphiques et jeux DirectX](http://go.microsoft.com/fwlink/?LinkId=256498) | Fournit des articles ayant trait aux technologies graphiques DirectX. |
