---
title: 'Procédure pas à pas : débogage des erreurs de rendu dues à l’ombrage | Microsoft Docs'
description: Suivez une investigation qui détecte un bogue de nuanceur. Il illustre l’utilisation de Visual Studio Graphics Diagnostics, y compris l’historique des pixels Graphics et le débogueur HLSL.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 01875b05-cc7b-4add-afba-f2b776f86974
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 218b263d7e971a0d2bdaa72020bb7cb58c31e000
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387084"
---
# <a name="walkthrough-debugging-rendering-errors-due-to-shading"></a>Procédure pas à pas : débogage des erreurs de rendu dues à l’ombrage
Cette procédure pas à pas montre comment utiliser [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Graphics Diagnostics pour examiner un objet qui est mal coloré en raison d’un bogue de nuanceur.

 Cette procédure pas à pas montre comment effectuer les opérations suivantes :

- Examiner le document du journal de graphiques pour identifier les pixels qui indiquent le problème.

- Utiliser la fenêtre **Historique des pixels Graphics** pour examiner l’état des pixels plus en détail.

- Utiliser le **débogueur HLSL** pour examiner les nuanceurs de sommets et de pixels.

## <a name="scenario"></a>Scénario
 La coloration incorrecte des objets se produit le plus souvent quand un nuanceur de sommets passe des informations incorrectes ou incomplètes à un nuanceur de pixels.

 Dans ce scénario, vous avez récemment ajouté un objet à votre application. Vous avez également ajouté un nouveau vertex et des nuanceurs de pixels pour transformer l’objet et lui attribuer une apparence unique. Vous exécutez l’application pendant un test et vous constatez que l’objet est affiché dans une couleur noire unie. À l’aide de Graphics Diagnostics, vous capturez le problème dans un journal de graphisme pour déboguer l’application. Le problème ressemble à cette image dans l’application :

 ![Objet rendu avec des couleurs incorrectes.](media/gfx_diag_demo_render_error_shader_problem.png "gfx_diag_demo_render_error_shader_problem")

## <a name="investigation"></a>Investigation
 À l'aide des outils Graphics Diagnostics, vous pouvez charger le document du journal de graphisme pour examiner les frames capturés pendant le test.

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Pour examiner un frame dans un journal de graphisme

1. Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , chargez un journal de graphisme qui contient un frame qui affiche le modèle manquant. Une nouvelle fenêtre de document de journal de graphisme s’affiche dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . La partie supérieure de cette fenêtre contient la sortie de la cible de rendu du frame sélectionné. La partie inférieure contient la **Liste de frames**, qui affiche chaque frame capturé sous forme de miniature.

2. Dans la **liste de frames**, sélectionnez un frame dans lequel l’objet n’a pas l’apparence correcte. La cible de rendu est mise à jour pour refléter le frame sélectionné. Dans ce scénario, la fenêtre de document du journal de graphisme se présente comme suit :

    ![Document journal de graphisme dans Visual Studio.](media/gfx_diag_demo_render_error_shader_step_1.png "gfx_diag_demo_render_error_shader_step_1")

   Une fois que vous avez sélectionné un frame qui illustre le problème, vous pouvez utiliser la fenêtre **Historique des pixels Graphics** pour le diagnostiquer. La fenêtre **Historique des pixels Graphics** affiche les primitives ayant pu avoir un effet sur un pixel spécifique, leurs nuanceurs et les effets sur la cible de rendu, dans l’ordre chronologique.

#### <a name="to-examine-a-pixel"></a>Pour examiner un pixel

1. Ouvrez la fenêtre **Historique des pixels Graphics** . Dans la barre d’outils **Graphics Diagnostics** , choisissez **Historique des pixels**.

2. Sélectionnez le pixel à examiner. Dans la fenêtre de document du journal de graphiques, sélectionnez un des pixels sur l’objet colorié de manière incorrecte :

    ![La sélection d'un pixel affiche des informations à propos de son historique.](media/gfx_diag_demo_render_error_shader_step_2.png "gfx_diag_demo_render_error_shader_step_2")

    La fenêtre **Historique des pixels Graphics** est actualisée pour afficher le pixel sélectionné. Dans ce scénario, la fenêtre **Historique des pixels Graphics** se présente comme suit :

    ![La fenêtre d'historique affiche un événement DrawIndexed.](media/gfx_diag_demo_render_error_shader_step_3.png "gfx_diag_demo_render_error_shader_step_3")

    Notez que le résultat du nuanceur de pixels est le noir entièrement opaque (0, 0, 0, 1) et que la **fusion de sortie** a combiné ce nuanceur de pixels avec la couleur **précédente** du pixel de telle sorte que le **résultat** soit également un noir entièrement opaque.

   Après avoir examiné un pixel de couleur incorrecte et constaté que la sortie du nuanceur de pixels n’est pas la couleur attendue, vous pouvez utiliser le débogueur HLSL pour examiner le nuanceur de pixels et déterminer la raison du problème de couleur de l’objet. Le débogueur HLSL vous permet d’examiner l’état des variables HLSL pendant l’exécution, d’exécuter pas à pas le code HLSL et de définir des points d’arrêt pour vous aider à diagnostiquer le problème.

#### <a name="to-examine-the-pixel-shader"></a>Pour examiner le nuanceur de pixels

1. Démarrez le débogage du nuanceur de pixels. Dans la fenêtre **Historique des pixels Graphics** , sous la primitive de l’objet, à côté de **Nuanceur de pixels**, choisissez le bouton **Démarrer le débogage** .

2. Dans ce scénario, étant donné que le nuanceur de pixels passe seulement la couleur par le biais du nuanceur de sommets, il est clair que le nuanceur de pixels n’est pas la source du problème.

3. Placez le pointeur sur `input.color`. Notez que sa valeur est la couleur noire entièrement opaque (0, 0, 0, 1).

    ![Le membre « couleur » de « entrée » est noir.](media/gfx_diag_demo_render_error_shader_step_5.png "gfx_diag_demo_render_error_shader_step_5")

    Dans ce scénario, l'examen révèle que la couleur incorrecte est probablement due au fait que le nuanceur de sommets ne fournit pas les informations de couleur correctes nécessaires au bon fonctionnement du nuanceur de pixels.

   Après avoir déterminé que le nuanceur de sommets ne fournit probablement pas les informations appropriées au nuanceur de pixels, l'étape suivante consiste à examiner le nuanceur de sommets.

#### <a name="to-examine-the-vertex-shader"></a>Pour examiner le nuanceur de sommets

1. Démarrez le débogage du nuanceur de sommets. Dans la fenêtre **Historique des pixels Graphics** , sous la primitive de l’objet, à côté de **Nuanceur de sommets**, choisissez le bouton **Démarrer le débogage** .

2. Recherchez la structure de sortie du nuanceur de sommets, qui correspond à l’entrée du nuanceur de pixels. Dans ce scénario, cette structure s’appelle `output`. Examinez le code du nuanceur de sommets et notez que le membre `color` de la structure `output` a été défini explicitement sur la couleur noire entièrement opaque, peut-être en raison des efforts de débogage d'un utilisateur.

3. Vérifiez que le membre de couleur n'est jamais copié à partir de la structure d'entrée. Étant donné que la valeur `output.color` est définie sur la couleur noire entièrement opaque juste avant que la structure `output` ne soit retournée, il est préférable de vérifier que la valeur de `output` n’a pas été correctement initialisée sur une ligne précédente. Parcourez le code du nuanceur de sommets jusqu'à ce que vous atteigniez la ligne qui définit `output.color` sur Noir lorsque vous examinez la valeur de `output.color`. Notez que la valeur de `output.color` n'est pas initialisée tant qu'elle n'est pas définie sur Noir. Cela confirme que la ligne de code qui définit `output.color` sur Noir doit être modifiée, et non pas supprimée.

    ![La valeur « output.color » est noir.](media/gfx_diag_demo_render_error_shader_step_7.png "gfx_diag_demo_render_error_shader_step_7")

   Après avoir déterminé que le problème de rendu est lié au fait que le nuanceur de sommets ne fournit pas la couleur appropriée au nuanceur de pixels, vous pouvez utiliser ces informations pour résoudre le problème. Dans ce scénario, vous pouvez le résoudre en modifiant le code ci-après dans le nuanceur de sommets

```hlsl
output.color = float3(0.0f, 0.0f, 0.0f);
```

 to

```hlsl
output.color = input.color;
```

 Ce code passe seulement la couleur des sommets de l’objet sans la modifier, mais il est possible que des nuanceurs de sommets plus complexes modifient la couleur avant de la passer. Le code du nuanceur de sommets corrigé doit ressembler à ceci :

 ![Code du nuanceur de sommets corrigé.](media/gfx_diag_demo_render_error_shader_step_8.png "gfx_diag_demo_render_error_shader_step_8")

 Après avoir corrigé le code, vous devez le régénérer, puis réexécuter l’application pour constater que le problème d’affichage est résolu.

 ![Objet rendu avec des couleurs correctes.](media/gfx_diag_demo_render_error_shader_resolution.png "gfx_diag_demo_render_error_shader_resolution")
