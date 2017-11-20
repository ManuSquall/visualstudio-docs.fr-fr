---
title: "Procédure pas à pas : Objets manquants en raison Pipeline mal configuré | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed8ac02d-b38f-4055-82fb-67757c2ccbb9
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0b262bea021413d1108050d4becfdbb8f8d7ae31
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-missing-objects-due-to-misconfigured-pipeline"></a>Procédure pas à pas : objets manquants en raison d'un pipeline mal configuré
Cette procédure pas à pas montre comment utiliser les outils Graphics Diagnostics de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour examiner un objet qui est manquant, car un nuanceur de pixels n’a pas été défini.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Utilisation de la **liste des événements Graphics** pour rechercher les sources potentielles du problème.  
  
-   Utilisation de la fenêtre **Étapes de canalisation Graphics** pour examiner l’effet de l’appel de l’API Direct3D `DrawIndexed` .  
  
-   Inspection du contexte de périphérique pour confirmer qu’aucune étape de nuanceur n’a été définie.  
  
-   Utilisation de la fenêtre **Étapes de canalisation Graphics** avec la **Pile des appels des événements Graphics** pour aider à trouver la source du nuanceur de pixels non défini.  
  
## <a name="scenario"></a>Scénario  
 Quand un objet est manquant dans une application 3D, c’est parfois dû au fait que l’une des étapes du nuanceur n’est pas définie avant le rendu de l’objet. Dans les applications qui ont des besoins de rendu simples, la source de cette erreur se situe généralement quelque part dans la pile des appels de dessin de l’objet. Toutefois, en guise d’optimisation, certaines applications rassemblent des objets qui ont des programmes nuanceurs, des textures ou d’autres données en commun pour minimiser la surcharge liée au changement d’état. Dans ces applications, la source de l’erreur peut être dissimulée au fond du système de traitement par lot, plutôt que située dans la pile des appels de l’appel de dessin. Comme le scénario de cette procédure pas à pas illustre une application ayant des besoins de rendu simples, la source de l’erreur se trouve dans la pile des appels.  
  
 Dans ce scénario, quand l’application est exécutée pour être testée, l’arrière-plan est affiché comme prévu, mais l’un des objets ne s’affiche pas. À l’aide de Graphics Diagnostics, vous capturez le problème dans un journal de graphisme pour déboguer l’application. Le problème se présente ainsi dans l'application :  
  
 ![L’objet ne peut pas être visualisé](media/gfx_diag_demo_misconfigured_pipeline_problem.png "gfx_diag_demo_misconfigured_pipeline_problem")  
  
## <a name="investigation"></a>Examen  
 À l'aide des outils Graphics Diagnostics, vous pouvez charger le document du journal de graphisme pour examiner les frames capturés pendant le test.  
  
#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Pour examiner un frame dans un journal de graphisme  
  
1.  Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], chargez un document de journal de graphisme qui contient un frame qui montre l’objet manquant. Un nouvel onglet de journal de graphisme s’affiche dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. La partie supérieure de cet onglet contient la sortie de la cible de rendu du frame sélectionné. La partie inférieure contient la **Liste de frames**, qui affiche chaque frame capturé sous forme de miniature.  
  
2.  Dans la **Liste de frames**, sélectionnez un frame qui montre que l’objet n’est pas affiché. La cible de rendu est mise à jour pour refléter le frame sélectionné. Dans ce scénario, l'onglet du journal de graphisme se présente comme suit :  
  
     ![Document du journal des graphiques dans Visual Studio](media/gfx_diag_demo_misconfigured_pipeline_step_1.png "gfx_diag_demo_misconfigured_pipeline_step_1")  
  
 Une fois que vous avez sélectionné un frame qui illustre le problème, vous pouvez commencer le diagnostic à l’aide de la **Liste des événements Graphics**. La **Liste des événements Graphics** contient chaque appel d’API Direct3D qui a été effectué pour afficher le frame actif, par exemple pour configurer l’état du périphérique, créer et mettre à jour les mémoires tampons, et dessiner des objets qui apparaissent dans le frame. Plusieurs types d’appels (par exemple les appels de dessin, de distribution, de copie ou d’effacement) sont intéressants, car il y a souvent (mais pas toujours) une modification correspondante de la cible de rendu quand l’application fonctionne comme prévu. Les appels de dessin sont particulièrement intéressants, car chacun d’eux représente la géométrie affichée par l’application.  
  
 Comme vous savez que la cible de rendu ne contient pas l’objet manquant, mais qu’il semble également ne pas y avoir d’autre erreur, vous pouvez utiliser la **Liste des événements Graphics** avec l’outil **Étapes de canalisation Graphics** pour identifier l’appel de dessin qui correspond à la géométrie de l’objet manquant. La fenêtre **Étapes de canalisation Graphics** affiche la géométrie qui a été envoyée à chaque appel de dessin, quel que soit son effet sur la cible de rendu. À mesure que vous parcourez les appels de dessin, les étapes de canalisation sont mises à jour pour afficher la géométrie qui est associée à chaque appel quand il transite par chaque étape activé, et la sortie de cible de rendu est mise à jour pour afficher l’état de la cible de rendu une fois l’appel terminé.  
  
#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>Pour rechercher l’appel de dessin correspondant à la géométrie manquante  
  
1.  Ouvrez la fenêtre **Liste des événements Graphics** . Dans la barre d’outils **Graphics Diagnostics** , choisissez **Liste des événements**.  
  
2.  Ouvrez la fenêtre **Étapes de canalisation Graphics** . Dans la barre d’outils **Graphics Diagnostics** , choisissez **Étapes de canalisation**.  
  
3.  À mesure que vous parcourez chaque appel de dessin dans la fenêtre **Liste des événements Graphics** , recherchez l’objet manquant dans la fenêtre **Étapes de canalisation Graphics** . Pour rendre la tâche plus simple, entrez “Draw” dans la zone **Rechercher** , en haut à droite de la fenêtre **Liste des événements Graphics** . Cela permet de filtrer la liste pour retenir uniquement les événements qui contiennent « Draw » dans leur titre.  
  
     Dans la fenêtre **Étapes de canalisation Graphics** , l’étape **Assembleur d’entrée** montre la géométrie de l’objet avant sa transformation tandis que l’étape **Nuanceur de sommets** montre le même objet après sa transformation. Dans ce scénario, notez que la fenêtre **Étapes de canalisation Graphics** montre les étapes **Assembleur d’entrée** et  **Nuanceur de sommets** , mais pas l’étape **Nuanceur de pixels** pour l’un des appels de dessin.  
  
    > [!NOTE]
    >  Si d’autres étapes de canalisation (par exemple Nuanceur de coque, Nuanceur de domaine ou Nuanceur de géométrie) traitent l’objet, elles peuvent être la cause du problème. En règle générale, le problème est lié à la première étape durant laquelle le résultat n’est pas affiché ou est affiché de manière inattendue.  
  
4.  Arrêtez quand vous atteignez l’appel de dessin qui correspond à l’objet manquant. Dans ce scénario, la fenêtre **Étapes de canalisation Graphics** indique que la géométrie a été émise vers le GPU (indiqué par la présence de l’étape **Assembleur d’entrée** ) et transformée (indiqué par l’étape **Nuanceur de sommets** ), mais elle n’apparaît pas dans la cible de rendu, car il ne semble pas y avoir de nuanceur de pixels actif (indiqué par l’absence de l’étape **Nuanceur de pixels** ). Dans ce scénario, vous pouvez même voir la silhouette de l'objet manquant à l’étape **Fusion de sortie** :  
  
     ![Événement DrawIndexed et son effet sur le pipeline](media/gfx_diag_demo_misconfigured_pipeline_step_2.png "gfx_diag_demo_misconfigured_pipeline_step_2")  
  
 Une fois que vous avez confirmé que l’application avait émis un appel de dessin pour la géométrie de l’objet manquant et que vous avez découvert que l’étape de nuanceur de pixels était inactive, vous pouvez examiner l’état du périphérique pour confirmer vos constatations. Vous pouvez utiliser la **Table des objets Graphics** pour examiner le contexte de périphérique et d’autres données d’objets Direct3D.  
  
#### <a name="to-examine-device-context"></a>Pour examiner le contexte de périphérique  
  
1.  Ouvrez le **Contexte de périphérique d3d11**. Dans le **étapes de canalisation Graphics** fenêtre, choisissez le **ID3D11DeviceContext** lien qui fait partie de la `DrawIndexed` appel qui s’affiche en haut de la fenêtre.  
  
2.  Examinez l’état du périphérique affiché sous l’onglet **Contexte de périphérique d3d11** pour vérifier qu’aucun nuanceur de pixels n’était actif pendant l’appel de dessin. Dans ce scénario, les **Informations générales sur le nuanceur**(affichées sous **État du nuanceur de pixels**) indiquent que le nuanceur est **NULL**:  
  
     ![Le contexte de périphérique D3D 11 affiche l’état de nuanceur de pixels](media/gfx_diag_demo_misconfigured_pipeline_step_4.png "gfx_diag_demo_misconfigured_pipeline_step_4")  
  
 Une fois que vous avez confirmé que le nuanceur de pixels avait été défini sur la valeur null par votre application, l’étape suivante consiste à trouver l’emplacement, dans le code source de votre application, où le nuanceur est défini. Vous pouvez utiliser la **Liste des événements Graphics** avec la **Pile des appels des événements Graphics** pour rechercher cet emplacement.  
  
#### <a name="to-find-where-the-pixel-shader-is-set-in-your-apps-source-code"></a>Pour trouver où le nuanceur de pixels est défini dans le code source de votre application  
  
1.  Recherchez l’appel `PSSetShader` qui correspond à l’objet manquant. Dans la fenêtre **Liste des événements Graphics** , entrez “Draw;PSSetShader” dans la zone **Rechercher** , en haut à droite de la fenêtre **Liste des événements Graphics** . Cette opération permet de filtrer la liste pour retenir uniquement les événements “PSSetShader” et les événements dont le titre contient “Draw”. Choisissez le premier appel `PSSetShader` qui apparaît avant l’appel de dessin de l’objet manquant.  
  
    > [!NOTE]
    >  `PSSetShader` n’apparaît pas dans la fenêtre **Liste des événements Graphics** s’il n’a pas été défini durant ce frame. En général, cela se produit uniquement si le nuanceur de pixels est utilisé pour tous les objets, ou si l’appel `PSSetShader` a été ignoré par inadvertance pendant ce frame. Dans les deux cas, nous vous recommandons de rechercher les appels `PSSetShader` dans le code source de l’application et d’appliquer des techniques de débogage classiques pour examiner le comportement de ces appels.  
  
2.  Ouvrez la fenêtre **Pile des appels des événements Graphics** . Dans la barre d’outils **Graphics Diagnostics** , choisissez **Pile des appels des événements Graphics**.  
  
3.  Utilisez la pile des appels pour rechercher l’appel `PSSetShader` dans le code source de votre application. Dans la fenêtre **Pile des appels des événements Graphics** , choisissez l’appel supérieur et examinez la valeur définie pour le nuanceur de pixels. Le nuanceur de pixels peut être directement défini comme null, ou la valeur null peut être due à un argument qui a été transmis à la fonction ou autre état. S’il n’est pas défini directement, vous pourrez peut-être trouver la source de la valeur null vers le haut de la pile des appels. Dans ce scénario, vous découvrez que le nuanceur de pixels prend directement la valeur `nullptr` dans la fonction supérieure, qui se nomme `CubeRenderer::Render`:  
  
     ![Le code qui n’initialise pas le nuanceur de pixels](media/gfx_diag_demo_misconfigured_pipeline_step_5.png "gfx_diag_demo_misconfigured_pipeline_step_5")  
  
    > [!NOTE]
    >  Si vous ne trouvez pas la source de la valeur null en examinant simplement la pile des appels, nous vous recommandons de définir un point d’arrêt conditionnel sur l’appel `PSSetShader` pour que l’exécution du programme s’arrête quand le nuanceur de pixels prend la valeur null. Ensuite, redémarrez l’application en mode débogage et appliquez des techniques de débogage traditionnelles pour rechercher la source de la valeur null.  
  
 Pour résoudre le problème, affectez le nuanceur de pixels approprié à l’aide du premier paramètre de l’appel d’API `ID3D11DeviceContext::PSSetShader` .  
  
 ![La correction C &#43; &#43; le code source](media/gfx_diag_demo_misconfigured_pipeline_step_6.png "gfx_diag_demo_misconfigured_pipeline_step_6")  
  
 Après avoir corrigé le code, vous pouvez le régénérer et réexécuter l’application pour vérifier que le problème d’affichage est résolu :  
  
 ![L’objet est maintenant affiché](media/gfx_diag_demo_misconfigured_pipeline_resolution.jpg "gfx_diag_demo_misconfigured_pipeline_resolution")