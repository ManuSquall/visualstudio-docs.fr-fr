---
title: Graphics Diagnostics Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ca0a1613f46f8542a3ede4ce2053b3584824590e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75847825"
---
# <a name="visual-studio-graphics-diagnostics"></a>Diagnostics des graphiques Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio*Graphics Diagnostics* est un ensemble d’outils pour l’enregistrement, puis l’analyse des problèmes de rendu et de performances dans les applications Direct3D. Graphics Diagnostics peut être utilisé sur les applications qui s'exécutent localement sur votre PC Windows, dans un émulateur d'appareil Windows, ou sur un PC ou un appareil distant.  
  
 Le flux de travail Graphics Diagnostics commence par capturer un enregistrement de la façon dont votre application utilise Direct3D (dynamiquement, durant son exécution) pour que les informations relatives au comportement puissent être analysées immédiatement, partagées ou enregistrées pour un usage différé. Les sessions de capture peuvent être lancées et contrôlées manuellement à partir de Visual Studio ou à l’aide de l’outil de capture de ligne de commande **dxcap.exe**. Les sessions de capture peuvent également être initialisées et contrôlées par programme à l’aide des API de capture Graphics Diagnostics.  
  
 Une fois qu’une session de capture a été enregistrée, son contenu peut être lu par Visual Studio *Graphics Analyzer* à tout moment, en recréant les frames capturés à l’aide des ressources et des commandes de rendu utilisées par l’application. Ensuite, à l’aide des outils fournis dans la fenêtre Graphics Analyzer, tous les frames capturés peuvent être analysés en détail. Ces outils permettent d'examiner un appel d'API, une ressource, un objet État du pipeline, une étape de canalisation Direct3D, ou même l'historique complet d'un pixel dans un frame capturé. L'utilisation conjointe de ces outils permet d'explorer un problème de rendu de façon intuitive, depuis son apparition dans un frame capturé jusqu'à sa cause racine dans le code source, les nuanceurs ou les ressources graphiques de l'application.  
  
 Pour diagnostiquer les problèmes de performances, un frame capturé peut être analysé à l’aide de l’outil *Analyse des frames*. Cet outil explore les optimisations de performances potentielles en changeant automatiquement la manière dont l'application utilise Direct3D, et en vous fournissant des benchmarks de toutes les variations. Par le passé, vous avez peut-être été amené à effectuer et évaluer les modifications de ce genre manuellement, simplement pour trouver celles qui faisaient la différence. Avec l'outil Analyse des frames, il vous suffit d'apporter les modifications dont l'impact est garanti.  
  
 Graphics Diagnostics contribue à rendre votre application graphique Direct3D plus esthétique et plus performante.  
  
 Passez à la [vue d’ensemble](../debugger/overview-of-visual-studio-graphics-diagnostics.md) pour en savoir plus sur les offres Visual Studio Graphics Diagnostics.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d'ensemble](../debugger/overview-of-visual-studio-graphics-diagnostics.md)  
 Présente le flux de travail et les outils de Graphics Diagnostics.  
  
 [Prise en main](../debugger/getting-started-with-visual-studio-graphics-diagnostics.md)  
 Dans cette section, vous apprendrez à installer Visual Studio Graphics Diagnostics, et à utiliser Graphics Diagnostics avec votre application Direct3D.  
  
 [Capture d'informations graphiques](../debugger/capturing-graphics-information.md)  
 Pour examiner un problème de rendu dans votre application à l'aide de Graphics Diagnostics, vous devez d'abord enregistrer des informations indiquant comment l'application utilise DirectX. Au cours de la session d’enregistrement, pendant l’exécution normale de l’application, vous *capturez* (ou sélectionnez) les frames qui vous intéressent. Les captures contiennent des informations détaillées sur le rendu des frames. Vous pouvez enregistrer les informations capturées sous forme de document journal de graphisme pour l’examiner ultérieurement ou le partager avec d’autres membres de votre équipe.  
  
 [Utilisation du GPU](../debugger/gpu-usage.md)  
 Pour profiler votre application à l’aide de Graphics Diagnostics, utilisez l’outil Utilisation du GPU. Servez-vous de l'outil Utilisation du GPU conjointement avec d'autres outils de profilage, tels que l'outil Utilisation de l'UC, pour mettre en corrélation les activités de l'UC et du GPU éventuellement responsables des problèmes de performances de votre application.  
  
 [Document de journal Graphics](../debugger/graphics-log-document.md)  
 Pour débuter l’examen d’un journal de graphisme enregistré, vous devez utiliser la fenêtre du document journal Graphics pour sélectionner un frame capturé (voire un pixel spécifique) et ainsi examiner en détail les *événements* (c’est-à-dire, les appels d’API DirectX) qui l’affectent.  
  
 [Analyse des frames](../debugger/graphics-frame-analysis.md)  
 Une fois le frame sélectionné, utilisez l'analyse des frames graphiques pour examiner et ajuster vos performances de rendu.  
  
 [Liste des événements](../debugger/graphics-event-list.md)  
 Après avoir sélectionné un frame, utilisez la **Liste des événements Graphics** pour examiner les événements associés et déterminer s’ils sont liés au problème de rendu.  
  
 [State](../debugger/graphics-state.md)  
 La fenêtre État vous permet de comprendre l'état graphique actif au moment de l'événement actuel.  
  
 [Étapes d’un pipeline](../debugger/graphics-pipeline-stages.md)  
 Dans la fenêtre **Étapes de canalisation Graphics**, cherchez à déterminer comment l’événement sélectionné est traité par chaque étape de canalisation Graphics pour voir à quel moment le problème de rendu s’est manifesté. L'examen des étapes de canalisation est particulièrement utile quand un objet ne s'affiche pas en raison d'une transformation incorrecte ou quand une des étapes génère une sortie qui ne correspond pas à ce qu'attend l'étape suivante.  
  
 [Pile des appels des événements](../debugger/graphics-event-call-stack.md)  
 Utilisez la **Pile des appels des événements Graphics** pour examiner la pile des appels de l’événement sélectionné et accéder au code d’application lié au problème de rendu.  
  
 [Historique des pixels](../debugger/graphics-pixel-history.md)  
 En utilisant la fenêtre **Historique des pixels Graphics** pour déterminer dans quelle mesure le pixel sélectionné est affecté par les événements qui l’ont influencé, vous pouvez identifier l’événement ou la combinaison d’événements qui provoquent certains types de problèmes de rendu. L'historique des pixels est particulièrement utile en cas de rendu incorrect d'un objet du fait d'une sortie du nuanceur de pixels incorrecte ou mal combinée avec le tampon de trame ou encore quand un objet ne s'affiche même pas si, par exemple, ses pixels ont été ignorés avant d'atteindre le tampon de trame.  
  
 [Table des objets](../debugger/graphics-object-table.md)  
 Utilisez la **Table des objets Graphics** pour examiner les propriétés et le contenu d’objets et de ressources Direct3D spécifiques qui sont utilisés dans le cadre de l’événement sélectionné. La table des objets peut vous aider à déterminer le contexte du périphérique graphique actif au cours d’un événement et à examiner le contenu de ressources graphiques telles que les mémoires tampons constantes, les mémoires tampons de vertex et les textures.  
  
 [Débogueur HLSL](../debugger/hlsl-shader-debugger.md)  
 Pour examiner le comportement du code de nuanceur pour l’événement et l’étape de canalisation Graphics sélectionnés, utilisez le **Débogueur HLSL** pour parcourir le code, examiner le contenu des variables et effectuer d’autres tâches classiques de débogage. Vous pouvez aussi utiliser le débogueur HLSL pour examiner le code de nuanceur de calcul, que les résultats subissent un traitement supplémentaire de la canalisation Graphics ou qu'ils soient seulement relus par votre application.  
  
 [Outil en ligne de commande de capture](../debugger/command-line-capture-tool.md)  
 Utilisez l'outil en ligne de commande de capture pour capturer et lire rapidement des informations graphiques sans passer par Visual Studio ou une capture par programmation. En particulier, vous pouvez utiliser l'outil en ligne de commande pour l'automatisation ou dans un environnement de test.  
  
 [Exemples](../debugger/graphics-diagnostics-examples.md)  
 Plusieurs exemples montrent comment utiliser conjointement les outils Graphics Diagnostics pour diagnostiquer différents types de problèmes de rendu.  
  
## <a name="related-sections"></a>Sections connexes  
  
|Intitulé|Description|  
|-----------|-----------------|  
|[Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md)|Présente la fonctionnalité de débogage de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|[Graphiques et jeux DirectX](https://msdn.microsoft.com/library/ee663274(v=vs.85).aspx)|Fournit des articles ayant trait aux technologies graphiques DirectX.|
