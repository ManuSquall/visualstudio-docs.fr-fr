---
title: Graphics Diagnostics | Microsoft Docs
description: Visual Studio Graphics Diagnostics est un ensemble d’outils pour la journalisation et l’analyse de l’activité Direct3D. Utilisez-les pour résoudre les problèmes de rendu et de performances.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b6b769131831a0f1f94aa4fcc8e94a9a88bf9890
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386122"
---
# <a name="visual-studio-graphics-diagnostics"></a>Diagnostics des graphiques Visual Studio
>[!NOTE]
> Visual Studio recommande PIX sur Windows pour les jeux DirectX 12. [Pix sur Windows](https://aka.ms/PIXonWindows) est un outil de réglage et de débogage des performances qui prend entièrement en charge DirectX 12. Pour [plus d’informations](visual-studio-graphics-diagnostics-directx-12.md) ou pour télécharger, cliquez [ici](https://aka.ms/downloadPIX).

Visual Studio *Graphics Diagnostics* est un ensemble d’outils pour l’enregistrement, puis l’analyse des problèmes de rendu et de performances des applications Direct3D. Graphics Diagnostics peut être utilisé sur les applications qui s'exécutent localement sur votre PC Windows, dans un émulateur d'appareil Windows, ou sur un PC ou un appareil distant.

 Le flux de travail Graphics Diagnostics commence par capturer un enregistrement de la façon dont votre application utilise Direct3D (dynamiquement, durant son exécution) pour que les informations relatives au comportement puissent être analysées immédiatement, partagées ou enregistrées pour un usage différé. Les sessions de capture peuvent être lancées et contrôlées manuellement à partir de Visual Studio ou à l’aide de l’outil de capture de ligne de commande **dxcap.exe**. Les sessions de capture peuvent également être initialisées et contrôlées par programme à l’aide des API de capture Graphics Diagnostics.

 Une fois qu’une session de capture a été enregistrée, son contenu peut être lu par Visual Studio *Graphics Analyzer* à tout moment, en recréant les frames capturés à l’aide des ressources et des commandes de rendu utilisées par l’application. Ensuite, à l’aide des outils fournis dans la fenêtre Graphics Analyzer, tous les frames capturés peuvent être analysés en détail. Ces outils permettent d'examiner un appel d'API, une ressource, un objet État du pipeline, une étape de canalisation Direct3D, ou même l'historique complet d'un pixel dans un frame capturé. L'utilisation conjointe de ces outils permet d'explorer un problème de rendu de façon intuitive, depuis son apparition dans un frame capturé jusqu'à sa cause racine dans le code source, les nuanceurs ou les ressources graphiques de l'application.

 Pour diagnostiquer les problèmes de performances, un frame capturé peut être analysé à l’aide de l’outil *Analyse des frames*. Cet outil explore les optimisations de performances potentielles en changeant automatiquement la manière dont l'application utilise Direct3D, et en vous fournissant des benchmarks de toutes les variations. Par le passé, vous avez peut-être été amené à effectuer et évaluer les modifications de ce genre manuellement, simplement pour trouver celles qui faisaient la différence. Avec l'outil Analyse des frames, il vous suffit d'apporter les modifications dont l'impact est garanti.

 Graphics Diagnostics contribue à rendre votre application graphique Direct3D plus esthétique et plus performante.

 Passez à la [vue d’ensemble](overview-of-visual-studio-graphics-diagnostics.md) pour en savoir plus sur les offres Visual Studio Graphics Diagnostics.

## <a name="in-this-section"></a>Dans cette section
 [Vue d’ensemble](overview-of-visual-studio-graphics-diagnostics.md) Présente le flux de travail et les outils Graphics Diagnostics.

 [Prise en main](getting-started-with-visual-studio-graphics-diagnostics.md) Dans cette section, vous allez apprendre à installer Visual Studio Graphics Diagnostics et à commencer à utiliser Graphics Diagnostics avec votre application Direct3D.

 [Capture d’informations graphiques](capturing-graphics-information.md) Pour utiliser Graphics Diagnostics pour examiner un problème de rendu dans votre application, vous devez d’abord enregistrer des informations sur la façon dont l’application utilise DirectX. Au cours de la session d’enregistrement, pendant l’exécution normale de l’application, vous *capturez* (ou sélectionnez) les frames qui vous intéressent. Les captures contiennent des informations détaillées sur le rendu des frames. Vous pouvez enregistrer les informations capturées sous forme de document journal de graphisme pour l’examiner ultérieurement ou le partager avec d’autres membres de votre équipe.

 [Utilisation du GPU](../../profiling/gpu-usage.md) Pour utiliser Graphics Diagnostics pour profiler votre application, utilisez l’outil utilisation du GPU. Servez-vous de l'outil Utilisation du GPU conjointement avec d'autres outils de profilage, tels que l'outil Utilisation de l'UC, pour mettre en corrélation les activités de l'UC et du GPU éventuellement responsables des problèmes de performances de votre application.

 [Document journal de graphisme](graphics-log-document.md) Pour démarrer l’examen d’un journal de graphisme enregistré, vous utilisez la fenêtre de document du journal de graphisme pour sélectionner un frame capturé (voire un pixel spécifique) afin de pouvoir examiner en détail les *événements* (autrement dit, les appels de l’API DirectX) qui l’affectent.

 [Analyse des frames](graphics-frame-analysis.md) Après avoir sélectionné un frame, vous utilisez analyse des frames graphiques pour examiner et ajuster vos performances de rendu.

 [Liste des événements](graphics-event-list.md) Après avoir sélectionné un frame, utilisez la **liste des événements Graphics** pour examiner ses événements et déterminer s’ils sont liés au problème de rendu.

 [État](graphics-state.md) La fenêtre État vous aide à comprendre l’état des graphismes qui est actif au moment de l’événement actuel.

 [Étapes de pipeline](graphics-pipeline-stages.md) Dans la fenêtre **étapes de canalisation Graphics** , vous examinez comment l’événement actuellement sélectionné est traité par chaque étape du pipeline Graphics afin que vous puissiez identifier l’endroit où le problème de rendu s’affiche pour la première fois. L'examen des étapes de canalisation est particulièrement utile quand un objet ne s'affiche pas en raison d'une transformation incorrecte ou quand une des étapes génère une sortie qui ne correspond pas à ce qu'attend l'étape suivante.

 [Pile des appels d’événements](graphics-event-call-stack.md) Vous utilisez la **pile des appels des événements Graphics** pour examiner la pile des appels de l’événement actuellement sélectionné afin de pouvoir accéder au code de l’application lié au problème de rendu.

 [Historique des pixels](graphics-pixel-history.md) En utilisant la fenêtre **historique des pixels Graphics** pour analyser la manière dont le pixel actuellement sélectionné est affecté par les événements qui l’ont influencé, vous pouvez identifier l’événement ou la combinaison d’événements qui provoquent certains types de problèmes de rendu. L'historique des pixels est particulièrement utile en cas de rendu incorrect d'un objet du fait d'une sortie du nuanceur de pixels incorrecte ou mal combinée avec le tampon de trame ou encore quand un objet ne s'affiche même pas si, par exemple, ses pixels ont été ignorés avant d'atteindre le tampon de trame.

 [Table des objets](graphics-object-table.md) Vous utilisez la **table des objets Graphics** pour examiner les propriétés et le contenu d’objets et de ressources Direct3D spécifiques qui sont en vigueur pour l’événement actuellement sélectionné. La table des objets peut vous aider à déterminer le contexte du périphérique graphique actif au cours d’un événement et à examiner le contenu de ressources graphiques telles que les mémoires tampons constantes, les mémoires tampons de vertex et les textures.

 [Débogueur HLSL](hlsl-shader-debugger.md) Pour examiner le comportement du code du nuanceur pour l’événement et l’étape de pipeline graphique actuellement sélectionnés, utilisez le **débogueur HLSL** pour parcourir le code, examiner le contenu des variables et effectuer d’autres tâches de débogage classiques. Vous pouvez aussi utiliser le débogueur HLSL pour examiner le code de nuanceur de calcul, que les résultats subissent un traitement supplémentaire de la canalisation Graphics ou qu'ils soient seulement relus par votre application.

 [Outil de capture en ligne de commande](command-line-capture-tool.md) Utilisez l’outil de capture en ligne de commande pour capturer et lire rapidement des informations graphiques sans utiliser Visual Studio ou la capture par programmation. En particulier, vous pouvez utiliser l'outil en ligne de commande pour l'automatisation ou dans un environnement de test.

 [Exemples](graphics-diagnostics-examples.md) Plusieurs exemples montrent comment utiliser les outils de Graphics Diagnostics ensemble pour diagnostiquer différents types de problèmes de rendu.

## <a name="related-sections"></a>Sections connexes

| Intitulé | Description |
| - | - |
| [Visite guidée des fonctionnalités du débogueur](../debugger-feature-tour.md) | Présente la fonctionnalité de débogage de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. |
| [Graphiques et jeux DirectX](/windows/win32/directx) | Fournit des articles ayant trait aux technologies graphiques DirectX. |
| [Prise en charge de DirectX 12 dans Visual Studio](visual-studio-graphics-diagnostics-directx-12.md) | En savoir plus sur la prise en charge de DirectX 12 dans Visual Studio |
