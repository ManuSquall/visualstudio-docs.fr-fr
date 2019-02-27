---
title: 'Procédure pas à pas : Objets manquants en raison Vertex Shader | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e42b54a0-8092-455c-945b-9ecafb129d93
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 14a7ffd3542fd9562488b3b442f1efe19f44a869
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56691746"
---
# <a name="walkthrough-missing-objects-due-to-vertex-shading"></a>Procédure pas à pas : objets manquants en raison de Vertex Shader
Cette procédure pas à pas montre comment utiliser les outils Graphics Diagnostics dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour examiner un objet qui est manquant à cause d’une erreur survenue à l’étape du nuanceur de sommets.

 Cette procédure pas à pas décrit les tâches suivantes :

-   Utilisation de la **liste des événements Graphics** pour rechercher les sources potentielles du problème.

-   Utilisation de la fenêtre **Étapes de canalisation Graphics** pour vérifier l’effet des appels de l’API Direct3D `DrawIndexed` .

-   Utilisation du **débogueur HLSL** pour examiner le nuanceur de sommets.

-   Utilisation de la **pile des appels des événements Graphics** pour trouver plus facilement la source d’une constante HLSL incorrecte.

## <a name="scenario"></a>Scénario
 Une des causes courantes observées quand un objet est manquant dans une application 3D est le nuanceur de sommets qui transforme les sommets de l’objet de manière incorrecte ou inattendue. C’est le cas, par exemple, si l’objet est réduit à une très petite échelle ou s’il est transformé pour s’afficher derrière la caméra, au lieu de devant.

 Dans ce scénario, quand l’application est exécutée pour être testée, l’arrière-plan est affiché comme prévu, mais l’un des objets ne s’affiche pas. À l’aide de Graphics Diagnostics, vous capturez le problème dans un journal de graphisme pour déboguer l’application. Le problème se présente ainsi dans l'application :

 ![L’objet n’est pas visible. ](media/gfx_diag_demo_missing_object_shader_problem.png "gfx_diag_demo_missing_object_shader_problem")

## <a name="investigation"></a>Examen
 À l’aide des outils Graphics Diagnostics, vous pouvez charger le fichier journal de graphisme pour examiner les frames capturés pendant le test.

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Pour examiner un frame dans un journal de graphiques

1. Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], chargez un journal de graphiques qui contient un frame présentant l’objet manquant. Un nouvel onglet de journal de graphisme s’affiche dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. La partie supérieure de cet onglet contient la sortie de la cible de rendu du frame sélectionné. La partie inférieure contient la **Liste de frames**, qui affiche chaque frame capturé sous forme de miniature.

2. Dans la **Liste de frames**, sélectionnez un frame qui montre que l’objet n’est pas affiché. La cible de rendu est mise à jour pour refléter le frame sélectionné. Dans ce scénario, l'onglet du journal de graphisme se présente comme suit :

    ![Document du journal des graphiques dans Visual Studio](media/gfx_diag_demo_missing_object_shader_step_1.png "gfx_diag_demo_missing_object_shader_step_1")

   Une fois que vous avez sélectionné un frame qui illustre le problème, vous pouvez commencer le diagnostic dans la fenêtre **Liste des événements Graphics**. La fenêtre **Liste des événements Graphics** contient chaque appel d’API Direct3D qui a été effectué pour afficher le frame actif, par exemple les appels API pour configurer l’état de l’appareil, créer et mettre à jour les mémoires tampons, et dessiner les objets qui apparaissent dans le frame. Plusieurs types d’appels sont intéressants, car il y a souvent (mais pas toujours) une modification correspondante dans la cible de rendu quand l’application fonctionne comme prévu. C’est le cas des appels de dessin, de distribution, de copie ou d’effacement, par exemple. Les appels de dessin sont particulièrement intéressants, car chacun d’eux représente la géométrie affichée par l’application (les appels de distribution permettent aussi cela).

   Comme vous savez que l’objet manquant n’est pas dessiné dans la cible de rendu (dans ce cas précis), mais que le reste de la scène est dessinée de la manière attendue, vous pouvez utiliser la fenêtre **Liste des événements Graphics** avec l’outil **Étapes de canalisation Graphics** pour identifier l’appel de dessin qui correspond à la géométrie de l’objet manquant. La fenêtre **Étapes de canalisation Graphics** affiche la géométrie qui a été envoyée à chaque appel de dessin, quel que soit son effet sur la cible de rendu. À mesure que vous parcourez les appels de dessin, les étapes de canalisation sont mises à jour pour afficher la géométrie qui est associée à l’appel, et la sortie de la cible de rendu est mise à jour pour afficher l’état de la cible de rendu à l’issue de l’appel.

#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>Pour rechercher l’appel de dessin correspondant à la géométrie manquante

1. Ouvrez la fenêtre **Liste des événements Graphics** . Dans la barre d’outils **Graphics Diagnostics** , choisissez **Liste des événements**.

2. Ouvrez la fenêtre **Étapes de canalisation Graphics** . Dans la barre d’outils **Graphics Diagnostics** , choisissez **Étapes de canalisation**.

3. À mesure que vous parcourez chaque appel de dessin dans la fenêtre **Liste des événements Graphics** , recherchez l’objet manquant dans la fenêtre **Étapes de canalisation Graphics** . Pour rendre la tâche plus simple, entrez “Draw” dans la zone **Rechercher** , en haut à droite de la fenêtre **Liste des événements Graphics** . Cela permet de filtrer la liste pour retenir uniquement les événements qui contiennent « Draw » dans leur titre.

    Dans la fenêtre **Étapes de canalisation Graphics** , l’étape **Assembleur d’entrée** montre la géométrie de l’objet avant sa transformation tandis que l’étape **Nuanceur de sommets** montre le même objet après sa transformation. Dans ce scénario, vous avez trouvé l’objet manquant quand il s’affiche à l’étape **Assembleur d’entrée** , mais pas à l’étape **Nuanceur de sommets** .

   > [!NOTE]
   >  Si d’autres étapes de géométrie (par exemple, Nuanceur de coque, Nuanceur de domaine ou Nuanceur de géométrie) traitent l’objet, elles peuvent être la cause du problème. En règle générale, le problème est lié à la première étape durant laquelle le résultat n’est pas affiché ou est affiché de manière inattendue.

4. Arrêtez quand vous atteignez l’appel de dessin qui correspond à l’objet manquant. Dans ce scénario, la fenêtre **Étapes de canalisation Graphics** indique que la géométrie a été émise vers le GPU (indiqué par la présence de l’aperçu Assembleur d’entrée), mais elle n’apparaît pas dans la cible de rendu à cause d’une erreur survenue à l’étape du nuanceur de sommets (indiquée par l’aperçu Nuanceur de sommets) :

    ![Un événement DrawIndexed et son effet sur le pipeline](media/gfx_diag_demo_missing_object_shader_step_2.png "gfx_diag_demo_missing_object_shader_step_2")

   Une fois que vous avez constaté que l’application a effectué un appel de dessin pour la géométrie de l’objet manquant et que vous avez découvert que le problème se produit à l’étape du nuanceur de sommets, vous pouvez utiliser le débogueur HLSL pour examiner le nuanceur de sommets et comprendre ce qui s’est passé avec la géométrie de l’objet. Le débogueur HLSL vous permet d’examiner l’état des variables HLSL pendant l’exécution, d’exécuter pas à pas le code HLSL et de définir des points d’arrêt pour vous aider à diagnostiquer le problème.

#### <a name="to-examine-the-vertex-shader"></a>Pour examiner le nuanceur de sommets

1. Démarrez le débogage du nuanceur de sommets. Dans la fenêtre **Étapes de canalisation Graphics** , sous l’étape **Nuanceur de sommets** , choisissez le bouton **Démarrer le débogage** .

2. Vous avez constaté que l’étape **Assembleur d’entrée** fournit des données correctes au nuanceur de sommets et que l’étape **Nuanceur de sommets** ne produit aucune sortie. Vous souhaitez donc examiner la structure de la sortie du nuanceur de sommets, `output`. Vous exécutez le code HLSL pas à pas pour déterminer plus en détail à quels moments `output` est modifié.

3. La première modification apportée à `output` est l’écriture du membre `worldPos` .

    ![La valeur « Output.worldpos » semble raisonnable](media/gfx_diag_demo_missing_object_shader_step_4.png "gfx_diag_demo_missing_object_shader_step_4")

    Comme sa valeur vous semble correcte, vous continuez l’exécution du code pas à pas jusqu’à la ligne suivante qui modifie `output`.

4. La modification suivante apportée à `output` est l’écriture du membre `pos` .

    ![La valeur de « output.pos » a été remis à zéro](media/gfx_diag_demo_missing_object_shader_step_5.png "gfx_diag_demo_missing_object_shader_step_5")

    Cette fois, la valeur du membre `pos` , composée uniquement de zéros, vous semble douteuse. Vous voulez alors essayer de comprendre pourquoi `output.pos` a cette valeur composée de zéros.

5. Vous remarquez que `output.pos` prend sa valeur d’une variable nommée `temp`. Sur la ligne précédente, vous constatez que la valeur de `temp` est le résultat de la multiplication de sa valeur précédente par une constante nommée `projection`. Vous supposez que la valeur douteuse de `temp`est le résultat de cette multiplication. Quand vous placez le pointeur sur `projection`, vous voyez que sa valeur n’est composée que de zéros, elle aussi.

    ![La matrice de projection contient une transformation incorrecte](media/gfx_diag_demo_missing_object_shader_step_6.png "gfx_diag_demo_missing_object_shader_step_6")

    Dans ce scénario, l’examen révèle que la valeur douteuse de `temp`est probablement le résultat de la multiplication par `projection`. De plus, comme `projection` est une constante censée contenir une matrice de projection, vous savez qu’elle ne doit pas contenir que des zéros.

   Après avoir déterminé que la constante HLSL `projection`, passée au nuanceur par votre application, est la source probable du problème, vous devez maintenant rechercher à quel endroit, dans le code source de votre application, la mémoire tampon constante est remplie. Vous pouvez faire cette recherche dans la fenêtre **Liste des événements Graphics** .

#### <a name="to-find-where-the-constant-is-set-in-your-apps-source-code"></a>Pour rechercher où la constante est définie dans le code source de votre application

1. Ouvrez la fenêtre **Pile des appels des événements Graphics** . Dans la barre d’outils **Graphics Diagnostics** , choisissez **Pile des appels des événements Graphics**.

2. Remontez la pile des appels dans le code source de votre application. Dans la fenêtre **Pile des appels des événements Graphics** , choisissez le premier appel en haut pour voir si la mémoire tampon constante est remplie à cet endroit. Si ce n’est pas le cas, continuez de remonter la pile des appels jusqu’à ce que vous trouviez l’endroit où elle est remplie. Dans ce scénario, vous découvrez que la mémoire tampon constante est remplie, via l’API Direct3D `UpdateSubresource` , plus haut dans la pile des appels dans une fonction nommée `MarbleMaze::Render`, et que sa valeur provient d’un objet mémoire tampon constante nommé `m_marbleConstantBufferData`:

    ![Le code qui définit la mémoire tampon constante de l’objet](media/gfx_diag_demo_missing_object_shader_step_7.png "gfx_diag_demo_missing_object_shader_step_7")

   > [!TIP]
   >  Si vous déboguez simultanément votre application, vous pouvez définir un point d’arrêt à cet emplacement, qui sera atteint lorsque le frame suivant sera affiché. En examinant ensuite les membres de `m_marbleConstantBufferData` , vous constatez que le membre `projection` a une valeur composée uniquement de zéros quand la mémoire tampon constante est remplie.

   Vous avez trouvé l’endroit où la mémoire tampon constante est remplie et découvert que ses valeurs proviennent de la variable `m_marbleConstantBufferData`. Vous devez maintenant trouver l’endroit où le membre `m_marbleConstantBufferData.projection` a une valeur composée de zéros. Vous pouvez utiliser **Rechercher toutes les références** pour rechercher rapidement le code qui modifie la valeur de `m_marbleConstantBufferData.projection`.

#### <a name="to-find-where-the-projection-member-is-set-in-your-apps-source-code"></a>Pour rechercher où le membre projection est défini dans le code source de votre application

1. Recherchez les références à `m_marbleConstantBufferData.projection`. Ouvrez le menu contextuel de la variable `m_marbleConstantBufferData`, puis choisissez **Rechercher toutes les références**.

2. Pour accéder à la ligne dans le code source de votre application où le membre `projection` est modifié, sélectionnez cette ligne dans la fenêtre **Résultats de la recherche de symbole** . Comme le premier résultat qui modifie le membre projection ne peut pas être la cause du problème, vous allez devoir examiner plusieurs parties du code source de votre application.

   Après avoir trouvé où `m_marbleConstantBufferData.projection` est défini, vous pouvez examiner le code source environnant pour déterminer l’origine de la valeur incorrecte. Dans ce scénario, vous constatez que la valeur de `m_marbleConstantBufferData.projection` est définie sur une variable locale nommée `projection` avant son initialisation sur une valeur fournie par le code `m_camera->GetProjection(&projection);` sur la ligne suivante.

   ![La projection marble est définie avant l’initialisation](media/gfx_diag_demo_missing_object_shader_step_9.png "gfx_diag_demo_missing_object_shader_step_9")

   Pour résoudre le problème, déplacez la ligne de code qui définit la valeur de `m_marbleConstantBufferData.projection` après la ligne qui initialise la valeur de la variable locale `projection`.

   ![Le C corrigé&#43; &#43; code source](media/gfx_diag_demo_missing_object_shader_step_10.png "gfx_diag_demo_missing_object_shader_step_10")

   Après avoir corrigé le code, vous pouvez le régénérer, puis réexécuter l’application pour vérifier que le problème d’affichage est résolu :

   ![L’objet est désormais affiché. ](media/gfx_diag_demo_missing_object_shader_resolution.png "gfx_diag_demo_missing_object_shader_resolution")