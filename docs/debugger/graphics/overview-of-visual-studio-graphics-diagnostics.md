---
title: Vue d’ensemble de Graphics Diagnostics | Microsoft Docs
description: Visual Studio Graphics Diagnostics est un ensemble d’outils permettant de journaliser l’activité Direct3D et d’analyser les journaux pour résoudre les problèmes de rendu et de performances.
ms.custom: SEO-VS-2020
ms.date: 02/09/2017
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 24b67b9585db973e6cbef3b1c28c6068e7c37034
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386187"
---
# <a name="overview-of-visual-studio-graphics-diagnostics"></a>Vue d'ensemble de Visual Studio Graphics Diagnostics
Visual Studio *Graphics Diagnostics* est un ensemble d’outils pour l’enregistrement, puis l’analyse des problèmes de rendu et de performances des applications Direct3D. Graphics Diagnostics peut être utilisé sur des applications qui s’exécutent localement sur votre PC Windows ou sur un PC ou un appareil distant.

## <a name="using-graphics-diagnostics-to-debug-rendering-problems"></a>Utilisation de Graphics Diagnostics pour déboguer les problèmes de rendu
 Le débogage des problèmes de rendu dans une application graphiquement riche n’est pas aussi simple que le démarrage d’un débogueur et l’exécution pas à pas du code. Dans chaque frame, des centaines de milliers de pixels uniques sont produits (chacun dépend d'un jeu complexe d'état, de données, de paramètres, et de code), il est possible que seuls quelques pixels présentent le problème que vous essayez de diagnostiquer. Pour compliquer encore plus les choses, le code qui génère chaque pixel est exécuté sur du matériel spécialisé qui traite des centaines de pixels en parallèle. Les outils et les techniques de débogage classiques (qui sont difficiles à exploiter même dans du code de thread léger) sont inefficaces face à autant de données.

 Les outils Graphics Diagnostics de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sont conçus pour vous aider à identifier les problèmes de rendu en commençant par les artefacts visuels qui indiquent le problème, puis en remontant à la source du problème en se concentrant uniquement sur le code de nuanceur associé, les étapes de canalisation, les appels de dessin, les ressources et l'état du périphérique dans le code source de l'application.

## <a name="directx-version-compatibility"></a>Compatibilité des versions DirectX
 Graphics Diagnostics prend en charge les applications qui utilisent Direct3D 10 ou une version ultérieure, et fournit une prise en charge limitée des applications qui utilisent Direct2D. Il ne prend pas en charge les applications qui utilisent des versions antérieures de Direct3D, DirectDraw ou d'autres API graphiques.

### <a name="windows-10-and-direct3d-12"></a>Windows 10 et Direct3D 12
> [!NOTE]
> Visual Studio recommande PIX sur Windows pour les jeux DirectX 12. [Pix sur Windows](https://aka.ms/PIXonWindows) est un outil de réglage et de débogage des performances qui prend entièrement en charge DirectX 12. Pour [plus d’informations](visual-studio-graphics-diagnostics-directx-12.md) ou pour télécharger, cliquez [ici](https://aka.ms/downloadPIX).


 Windows 10 a introduit *Direct3D 12*, qui est sensiblement différent de Direct3D 10 et Direct3D 11. Ces différences permettent à DirectX d'être en phase avec le matériel graphique moderne et d'exploiter tout son potentiel. En outre, elles apportent également d'importants changements en matière d'API et octroient une plus grande responsabilité au programmeur qui doit gérer les problèmes de contention et de durée de vie des ressources. Malgré les différences, Graphics Diagnostics avec Direct3D 12 assure la parité des fonctionnalités avec Graphics Diagnostics avec Direct3D 11,2.

 Windows 10 assure également la prise en charge des versions précédentes de Direct3D, ainsi que des jeux et applications qui reposent sur ces dernières. Graphics Diagnostics dans Visual Studio prend toujours en charge Direct3D 10 et Direct3D 11 sur Windows 10.

### <a name="limited-direct2d-support"></a>Prise en charge limitée de Direct2D
 Étant donné que Direct2D est une API en mode utilisateur générée d’après Direct3D, vous pouvez utiliser Graphics Diagnostics pour déboguer les problèmes de rendu dans les applications qui utilisent Direct2D. Toutefois, étant donné que seuls les événements de Direct3D sous-jacents sont stockés à la place des événements de niveau supérieur de Direct2D, les événements de Direct2D n'apparaîtront pas dans la liste des événements graphiques. En outre, comme les relations entre les événements de Direct2D et les événements de Direct3D qui en résultent ne sont pas toujours claires, le fait d'utiliser Graphics Diagnostics pour déboguer les problèmes de rendu dans des applications qui utilisent Direct2D n'est pas simple. Vous pouvez toujours utiliser Graphics Diagnostics pour obtenir des informations sur les problèmes de bas niveau de rendu dans les applications qui utilisent Direct2D.

## <a name="graphics-diagnostics-features-in-visual-studio"></a>Fonctionnalités Graphics Diagnostics dans Visual Studio
 Graphics Diagnostics possède une interface dédiée, la fenêtre Graphics Analyzer, pour diagnostiquer les problèmes de rendu. Toutefois, il ajoute également certains outils à l’interface de Visual Studio.

### <a name="the-graphics-toolbar-visual-studio"></a>Barre d'outils Graphics (Visual Studio)
 La barre d'outils Graphics fournit un accès rapide aux commandes Graphics Diagnostics.

 Le bouton **Démarrer les diagnostics** exécute l’application dans Graphics Diagnostics. Quand une application s’exécute dans Graphics Diagnostics, le bouton **Capturer le frame rendu suivant** est activé.

### <a name="diagnostics-capture-interface"></a>Interface de capture de Diagnostics
 Quand vous exécutez votre application dans Graphics Diagnostics, Visual Studio affiche une interface de session de diagnostic que vous pouvez utiliser pour capturer des frames, et qui affiche également la charge actuelle de l’UC et du GPU. La charge de l'UC et du GPU s'affiche pour vous aider à identifier les frames que vous souhaitez peut-être capturer en raison de leurs caractéristiques de performances, plutôt que les erreurs de rendu.

 Toutefois, ce n'est pas le seul moyen de capturer des frames. Vous pouvez également capturer des frames à l'aide de l'interface de capture par programmation, ou à l'aide du programme de capture en ligne de commande, dxcap.exe.

 Pour plus d’informations, consultez [Capture d’informations Graphics](capturing-graphics-information.md).

### <a name="gpu-usage"></a>Utilisation du GPU
 Graphics Diagnostics peut également profiler les performances de votre application Direct3D. Comme le profilage des données est altéré par l'enregistrement des détails relatifs aux événements graphiques, cette opération est distincte de la capture de frame à examiner à l'aide de Graphics Analyzer.

 Pour plus d’informations, consultez [Utilisation du GPU](../../profiling/gpu-usage.md).

### <a name="directx-control-panel"></a>Panneau de configuration DirectX
 Le panneau de configuration DirectX est un composant DirectX que vous pouvez utiliser pour modifier la manière dont DirectX se comporte (par exemple, vous pouvez activer la version de débogage des composants d’exécution DirectX, sélectionner le type de messages de débogage qui sont stockés, et désactiver certaines fonctionnalités du matériel graphique utilisées pour émuler le matériel ayant des capacités moindres). Ce niveau de contrôle sur DirectX peut vous aider à déboguer et à tester votre application DirectX. Vous pouvez accéder au panneau de configuration DirectX à partir de Visual Studio.

#### <a name="to-open-the-directx-control-panel"></a>Pour ouvrir le panneau de configuration DirectX

- Dans la barre de menus, choisissez **Déboguer**, **Graphiques**, **Panneau de configuration DirectX**.

## <a name="graphics-analyzer"></a>Graphics Analyzer
 Visual Studio Graphics Analyzer est une interface dédiée pour l'examen des problèmes de rendu et de performances dans les frames que vous avez capturés. Dans Graphics Analyzer, vous trouverez plusieurs outils qui vous aideront à explorer et comprendre le comportement de rendu de votre application. Chaque outil expose des informations d'un genre distinct concernant le frame inspecté. Par ailleurs, les outils sont conçus pour être utilisés conjointement afin d'identifier intuitivement la source d'un problème de rendu, à partir du moment où il est apparu dans le tampon de trame.

 Cette illustration montre une disposition typique des outils dans Graphics Analyzer.

 ![Toutes les fenêtres du débogueur de graphiques](media/graphicsdebuggerwindows.png "GraphicsDebuggerWindows")

### <a name="the-graphics-toolbar-graphics-analyzer"></a>Barre d'outils Graphics (Graphics Analyzer)
 La barre d'outils Graphics fournit un accès rapide aux fenêtres d'outils Graphics Analyzer.

 ![Barre d’outils Graphics en mode de diagnostics des graphiques](media/vsg_toolbar.png "vsg_toolbar")

### <a name="graphics-log-document"></a>Document journal de graphisme
 Dans Graphics Analyzer, le document journal de graphisme est la fenêtre d'outil la plus importante. Cette fenêtre représente tous les frames capturés durant l’exécution de votre application dans Graphics Diagnostics. À ce stade, vous pouvez sélectionner un autre frame pour examiner ou choisir un pixel spécifique à analyser avec l'outil Historique des pixels. L'image de tampon de trame affichée dans ce document change pour refléter l'événement actuellement sélectionné, ce qui vous permet de voir la façon dont le tampon de trame est affecté au fil du temps.

 Le [document journal Graphics](graphics-log-document.md) est également le point d’entrée de l’outil Analyse des frames. Celui-ci vous aide à comprendre les performances d’un frame en changeant la façon dont certains aspects du rendu sont configurés et en fournissant des résultats de benchmark à comparer à l’original.

### <a name="event-list"></a>Liste des événements
 Les événements graphiques marquent chaque appel d'API Direct3D et chaque événement défini par l'utilisateur.

 La [liste d’événements](graphics-event-list.md) affiche tous les événements graphiques qui ont été enregistrés pendant le frame que vous examinez. Pour identifier plus facilement ce qui est important, vous pouvez visualiser la liste des événements hiérarchiquement, en fonction des dernières modifications d'état relatives à l'appel de dessin, ou sous forme de chronologie. En outre, les événements sont des événements à code de couleurs selon la file d'attente à laquelle ils appartiennent. Vous pouvez filtrer la liste pour inclure uniquement les événements qui vous intéressent.

 Quand vous sélectionnez un événement dans la liste, le reste des outils Graphics Analysis reflètent l'état du frame au moment de l'événement. De cette façon, vous pouvez voir l'effet d'un événement sur le GPU. Par exemple, vous pouvez voir l'effet immédiat d'un appel de dessin sur le tampon de trame, même s'il est masqué par d'autres appels de dessin. Certains événements ont également des liens hypertexte que vous pouvez suivre pour plus d'informations sur leurs paramètres ou les objets de ressource associés.

### <a name="pipeline-stages"></a>Étapes de canalisation
 Chaque appel de dessin dans votre application passe par la canalisation graphique fournie par Direct3D. À chaque étape de canalisation, la sortie de l'étape précédente est transformée par un petit programme appelé nuanceur. Elle est ensuite transmise à l'étape suivante, jusqu'à son rendu final à l'écran. De nombreuses erreurs de rendu se produisent à la frontière entre les étapes de canalisation quand le format de sortie est différent de ce qui est attendu à l'étape suivante, ou quand une étape produit simplement des résultats incorrects. Normalement, vous obtenez uniquement le résultat final visible sur votre écran. Vous ne pouvez pas distinguer facilement où l'erreur est survenue durant la canalisation.

 La fenêtre [étapes de canalisation](graphics-pipeline-stages.md) visualise le résultat de chaque étape indépendamment, ce qui vous permet de déterminer plus facilement l’étape dans laquelle un problème de rendu s’affiche pour la première fois. Une fois que vous avez identifié l'étape, vous pouvez démarrer le débogage de son nuanceur directement à partir de la fenêtre Étapes de canalisation.

### <a name="graphics-state"></a>État graphique
 Les opérations de rendu dépendent beaucoup de l'état de plusieurs objets. Des problèmes de rendu de toutes sortes sont provoqués par un état mal configuré.

 La fenêtre [État](graphics-state.md) collecte les informations d’état relatives à chaque appel de dessin au même emplacement pour en faciliter la localisation. En outre, elle met en surbrillance les modifications d’état qui se sont produites depuis l’appel de dessin précédent.

### <a name="pixel-history"></a>Historique des pixels
 Dans les scènes complexes, il n'est pas rare qu'un pixel soit ombré plusieurs fois dans un seul frame. La couleur précédente est parfois simplement remplacée, mais il arrive également que les couleurs soient combinées pour obtenir des effets tels que la transparence. Quand le résultat de la combinaison n'a pas l'apparence souhaitée, vous ne pouvez pas déterminer facilement si cela est dû au fait qu'une des couleurs est incorrecte, ou s'il s'agit d'un problème de combinaison. Parfois, un objet peut être absent, car sa contribution au pixel a été rejetée pour une raison quelconque.

 La fenêtre [historique des pixels](graphics-pixel-history.md) visualise l’historique complet des nuanceurs de chaque pixel dans le cadre, y compris les contributions rejetées. Pour les contributions qui n'ont pas été rejetées, elle affiche les résultats bruts du nuanceur et montre comment chaque nouvelle couleur a été combinée à la précédente. Avec ces informations, il est beaucoup plus facile de localiser la source des erreurs dans les pixels qui fusionnent les résultats du nuanceur, ou quand un objet rendu est manquant, car sa contribution au pixel a été rejetée de façon incorrecte.

### <a name="event-call-stack"></a>Pile des appels des événements
 Le code du nuanceur n'est pas la seule source des problèmes de rendu dans une application Direct3D. Parfois, le code source de votre application passe un paramètre incorrect ou ne configure pas correctement Direct3D. Il existe un type d’erreur que la fonctionnalité décrite précédemment, Historique des pixels, peut vous aider à identifier. Il s’agit de l’erreur liée à l’absence d’un objet rendu, en raison du rejet de tous ses pixels. Ce genre d'erreur se produit généralement quand vous avez configuré un paramètre de manière incorrecte, par exemple le paramètre qui contrôle la façon dont le test de profondeur est effectué. En principe, vous trouverez votre erreur quelque part dans la pile des appels de l'appel de dessin de l'objet manquant.

 La fenêtre [pile des appels d’événement](graphics-event-call-stack.md) affiche la pile des appels complète de chaque événement graphique dans la liste des événements, et vous permet même d’accéder au code source de votre application si des informations de débogage sont disponibles. Il s'agit d'un outil puissant qui vous permet de suivre une erreur depuis sa première apparition, dans le GPU, jusqu'à son origine dans le code source de votre application.

### <a name="object-table"></a>Table des objets
 Chaque frame rendu par votre application s'appuie probablement sur des centaines, voire des milliers d'objets de ressource. Cela peut inclure les mémoires tampons d’arrière-plan, les cibles de rendu, les textures, les mémoires tampons de vertex, les mémoires tampons d’index, les mémoires tampons générales, quasiment tout ce dont Direct3D se souvient en tant qu’objet.

 La [table](graphics-object-table.md) des objets affiche tous les objets qui existent au moment de l’événement graphique sélectionné dans la liste des événements. Dans la mesure où la plupart des objets d'une application classique sont des textures, la liste des événements est optimisée pour montrer rapidement les détails pertinents relatifs aux images. La colonne Type vous indique le type d'objet présent dans chaque ligne, alors que la colonne Format indique le sous-type ou la version de l'objet. D'autres informations sont également affichées. Certains objets possèdent également des liens hypertexte que vous pouvez suivre pour afficher l'objet avec une visionneuse plus spécialisée. C'est le cas, par exemple, pour les textures (vous pouvez afficher la texture en tant qu'image) ou les mémoires tampons (vous pouvez choisir la façon dont la visionneuse de mémoire tampon analyse et affiche les octets bruts de mémoire tampon en définissant le format de la mémoire tampon).

### <a name="frame-analysis"></a>Analyse des frames
 Le graphisme de votre application ne doit pas seulement être correct, il doit également être rapide. Cela doit aussi se vérifier sur les appareils moins puissants, tels que les ordinateurs portables avec des cartes graphiques intégrées ou les téléphones mobiles. Enfin, les graphiques doivent être esthétiquement parfaits.

 L’outil [Analyse des frames](graphics-frame-analysis.md) explore les optimisations de performances potentielles en changeant automatiquement la manière dont l’application utilise Direct3D, et en fournissant des résultats de benchmark à des fins de comparaison. Par exemple, l'analyse des frames peut activer le mappage MIP (ou MIP mapping) sur chaque texture, ce qui permet de révéler les textures susceptibles de tirer parti du mappage MIP mais pour lesquelles il n'est pas actuellement activé. Sur le matériel compatible, l’analyse des frames présente également des informations collectées à partir des compteurs de performances du GPU. Ce genre d’informations permet d’identifier les problèmes de performances au niveau du matériel, par exemple un nombre élevé de blocages de récupération de texture ou de pertes dans le cache.

 Toutefois, l’analyse des frames ne se réduit pas à une question de vitesse. Elle vise à atteindre les meilleures performances possibles avec un minimum de concessions sur la qualité visuelle. Parfois, un effet impressionnant sur un affichage de grande taille n'a pas le même impact sur le petit écran d'un téléphone, où un effet plus simple peut s'avérer tout aussi réussi sans épuiser la batterie. Les modifications automatiques et les benchmarks fournis par Graphics Analysis peuvent vous aider à trouver l’équilibre approprié pour votre application sur toute une gamme d’appareils.

## <a name="see-also"></a>Voir aussi
- [Outil en ligne de commande de capture](command-line-capture-tool.md)
- [Débogueur HLSL](hlsl-shader-debugger.md)
