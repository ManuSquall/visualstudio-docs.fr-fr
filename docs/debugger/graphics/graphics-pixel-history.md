---
title: Historique des pixels Graphics | Microsoft Docs
description: Résoudre les problèmes de rendu en regardant l’historique d’un pixel spécifique. L’historique des pixels Graphics affiche les effets des événements Direct3D.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.pixelhistory
ms.assetid: 0a2cbde5-1ad9-487e-857c-a3664158c268
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 977d97bad864c27c164b6a7da0b14ad1a08128e3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888626"
---
# <a name="graphics-pixel-history"></a>Historique des pixels Graphics
La fenêtre Historique des pixels Graphics dans Visual Studio Graphics Analyzer vous aide à comprendre comment un pixel spécifique est affecté par les événements Direct3D qui se produisent dans un frame de votre jeu ou application.

 Voici la fenêtre Historique des pixels :

 ![Pixel avec trois événements Direct3D dans son historique.](media/gfx_diag_demo_pixel_history_orientation.png "gfx_diag_demo_pixel_history_orientation")

## <a name="understanding-the-pixel-history-window"></a>Présentation de la fenêtre Historique des pixels
 À l'aide de l'Historique des pixels, vous pouvez analyser la façon dont un pixel spécifique de la cible de rendu est affecté par des événements Direct3D dans un frame. Vous pouvez identifier un problème de rendu d'un événement Direct3D spécifique, même quand d'autres évènements (ou d'autres primitives du même événement) continuent à changer la valeur de la couleur finale du pixel. Par exemple, un pixel peut être rendu de manière incorrecte et être ensuite masqué par un autre pixel, semi-transparent, ce qui entraîne un mélange de leurs couleurs dans le framebuffer. Ce genre de problème peut être difficile à diagnostiquer si vous n'avez que le contenu final de la cible de rendu comme repère.

 La fenêtre Historique des pixels affiche l'historique complet d'un pixel dans le frame sélectionné. La zone **Tampon de trame final** en haut de la fenêtre affiche la couleur écrite dans le framebuffer à la fin du frame, ainsi que des informations supplémentaires sur le pixel, par exemple son frame d’origine et ses coordonnées d’écran. Cette zone contient également la case à cocher **Restituer Alpha**. Quand cette case est cochée, la couleur de la zone **Tampon de trame final** et les valeurs de couleur intermédiaires sont affichées en transparence sur un modèle de damier. Si la case n'est pas cochée, le canal alpha des valeurs de couleur est ignoré.

 La partie inférieure de la fenêtre affiche les événements qui ont pu affecter la couleur du pixel, ainsi que les pseudo-événements **Initial** et **Final** qui représentent les valeurs de couleur initiale et finale du pixel dans le framebuffer. La valeur de couleur initiale est déterminée par le premier événement qui a changé la couleur du pixel (en règle générale un événement `Clear`). Un pixel a toujours ces deux pseudo-événements dans son historique, même quand aucun autre événement ne l'a affecté. Quand d’autres événements ont eu l’occasion d’affecter le pixel, ils sont affichés entre les événements **Initial** et **Final**. Vous pouvez développer les événements pour afficher leurs détails. Pour les événements simples comme ceux qui effacent une cible de rendu, l'effet de l'événement correspond juste à une valeur de couleur. Les événements plus complexes tels que les appels de dessin génèrent une ou plusieurs primitives qui peuvent contribuer à la couleur du pixel.

 Les primitives dessinées par l'événement sont identifiées par leur type et leur index, ainsi que par le nombre total de primitives de l'objet. Par exemple, un identificateur comme **Triangle (1456) sur (6214)** signifie que la primitive correspond au 1456e triangle d’un objet composé de 6214 triangles. À gauche de chaque identificateur de primitive se trouve une icône qui résume l'effet de la primitive sur le pixel. Les primitives qui affectent la couleur du pixel sont représentées par un rectangle arrondi rempli à l'aide de la couleur résultante. Les primitives qui n'ont pas d'effet sur la couleur du pixel sont représentées par des icônes qui indiquent la raison pour laquelle le pixel a été exclu. Ces icônes sont décrites dans la section [Exclusion de primitive](#exclusion) plus loin dans cet article.

 Vous pouvez développer chaque primitive pour examiner la façon dont la sortie du nuanceur de pixels a été fusionnée avec la couleur de pixel existante pour produire la couleur résultante. À ce stade, vous pouvez également examiner ou déboguer le code du nuanceur de pixels associé à la primitive. En outre, vous pouvez développer davantage le nœud du nuanceur de sommets pour examiner l'entrée du nuanceur de sommets.

### <a name="primitive-exclusion"></a><a name="exclusion"></a> Exclusion de primitive
 Si une primitive ne peut pas affecter la couleur d'un pixel, l'exclusion peut se produire pour diverses raisons. Chaque raison est représentée par une icône décrite dans ce tableau :

|Icône|Raison de l'exclusion|
|----------|--------------------------|
|![Icône d'échec au test de profondeur.](media/vsg_hist_icon_failed_depth.png "vsg_hist_icon_failed_depth")|Le pixel a été exclu parce qu'il n'a pas réussi le test Depth Test.|
|![Icône d'échec au test Scissor.](media/vsg_hist_icon_failed_scissor.png "vsg_hist_icon_failed_scissor")|Le pixel a été exclu parce qu'il n'a pas réussi le test Scissor Test.|
|![Icône d'échec au test Stencil.](media/vsg_hist_icon_failed_stencil.png "vsg_hist_icon_failed_stencil")|Le pixel a été exclu parce qu'il n'a pas réussi le test Stencil Test.|

### <a name="draw-call-exclusion"></a>Exclusion d'appel de dessin
 Si aucune des primitives d’un appel de dessin ne peut affecter la cible de rendu, car elles ne réussissent pas un test, l’appel de dessin ne peut pas être développé et une icône correspondant à la raison de l’exclusion s’affiche juste à côté. Les raisons de l'exclusion d'un appel de dessin ressemblent aux raisons de l'exclusion d'une primitive. En outre, leurs icônes sont similaires.

### <a name="viewing-and-debugging-shader-code"></a>Affichage et débogage du code du nuanceur
 Vous pouvez examiner et déboguer le code des nuanceurs de sommets, de coques, de domaines, de géométries et de pixels à l'aide des contrôles situés sous la primitive associée au nuanceur.

##### <a name="to-view-a-shaders-source-code"></a>Pour afficher le code source d'un nuanceur

1. Dans la fenêtre **Historique des pixels Graphics**, localisez l’appel de dessin qui correspond au nuanceur que vous souhaitez examiner, puis développez-le.

2. Sous l’appel de dessin que vous venez de développer, sélectionnez une primitive qui illustre le problème qui vous intéresse, puis développez-la.

3. Sous la primitive qui vous intéresse, suivez le lien du titre du nuanceur. Par exemple, suivez le lien **Nuanceur de sommets obj:30** pour afficher le code source du nuanceur de sommets.

    > [!TIP]
    > Le numéro d’objet, **obj:30**, identifie ce nuanceur dans toute l’interface Graphics Analyzer, par exemple dans la table des objets et la fenêtre Étapes de canalisation.

##### <a name="to-debug-a-shader"></a>Pour déboguer un nuanceur

1. Dans la fenêtre **Historique des pixels Graphics**, localisez l’appel de dessin qui correspond au nuanceur que vous souhaitez examiner, puis développez-le.

2. Sous l'appel de dessin que vous venez de développer, sélectionnez ensuite une primitive qui illustre le problème qui vous intéresse, puis développez-la.

3. Sous la primitive qui vous intéresse, choisissez **Démarrer le débogage**. La valeur par défaut de ce point d'entrée dans le débogueur HLSL correspond au premier appel du nuanceur pour la primitive correspondante, c'est-à-dire le premier pixel ou sommet traité par le nuanceur. Il existe un seul pixel associé à la primitive, mais il existe plusieurs appels de nuanceur de sommets pour les lignes et les triangles.

     Si vous souhaitez déboguer l’appel de nuanceur de sommets pour un sommet spécifique, développez le lien de titre VertexShader, recherchez le sommet qui vous intéresse, puis choisissez **Démarrer le débogage** à côté.

### <a name="links-to-graphics-objects"></a>Liens vers les objets graphiques
 Pour comprendre les événements graphiques de l'historique des pixels, vous pouvez avoir besoin d'informations sur l'état de l'appareil au moment de l'événement ou sur les objets Direct3D référencés par l'événement. Pour chaque événement de l’historique des pixels, l’**Historique des pixels Graphics** fournit des liens vers l’état de l’appareil actuel et les objets connexes.

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : objets manquants en raison de l’état de l’appareil](walkthrough-missing-objects-due-to-device-state.md)
- [Procédure pas à pas : débogage des erreurs de rendu dues à l’ombrage](walkthrough-debugging-rendering-errors-due-to-shading.md)