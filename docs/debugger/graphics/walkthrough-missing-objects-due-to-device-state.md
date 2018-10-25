---
title: 'Procédure pas à pas : Objets manquants en raison état de l’appareil | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1b0d2bbd-0729-4aa5-8308-70c5bf1468c5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8d1e31063bf5cf24fa5b19b1446b4c41f2dd7bd2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49869764"
---
# <a name="walkthrough-missing-objects-due-to-device-state"></a>Procédure pas à pas : objets manquants en raison de l'état du périphérique
Cette procédure pas à pas montre comment utiliser Graphics Diagnostics dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour examiner un objet qui est manquant à cause de la configuration incorrecte de l’état de l’appareil.  
  
 Cette procédure pas à pas montre comment effectuer les opérations suivantes :  
  
-   Utiliser la fenêtre **Liste des événements Graphics** pour rechercher les sources potentielles du problème.  
  
-   Utiliser la fenêtre **Étapes de canalisation Graphics** pour vérifier l’effet des appels de l’API Direct3D `DrawIndexed` .  
  
-   Utiliser la fenêtre **Historique des pixels Graphics** pour identifier le problème de façon plus précise.  
  
-   Examiner l’état de l’appareil pour déceler les problèmes potentiels ou les configurations incorrectes.  
  
## <a name="scenario"></a>Scénario  
 L’une des raisons pour lesquelles les objets ne s’affichent parfois pas à l’endroit prévu dans une application 3D est une configuration incorrecte de l’appareil graphique qui entraîne l’exclusion des objets du rendu. Cela se produit, par exemple, quand l’ordre d’enroulement provoque à tort la suppression des triangles ou quand la fonction de test Depth Test donne lieu au rejet de tous les pixels de l’objet.  
  
 Dans le scénario qui est décrit dans cette procédure pas à pas, vous venez d’atteindre la première étape importante du développement de votre application 3D. Vous êtes prêt à tester l’application pour la première fois. Toutefois, quand vous exécutez l’application, vous constatez que seule l’interface utilisateur s’affiche. À l’aide de Graphics Diagnostics, vous capturez le problème dans un fichier journal de graphisme pour déboguer l’application. Le problème se présente ainsi dans l'application :  
  
 ![L’application avant la résolution du problème](media/vsg_walkthru1_firstview.png "vsg_walkthru1_firstview")  
  
 Pour plus d’informations sur la capture des problèmes de graphisme dans un journal de graphisme, consultez [Capturing Graphics Information](capturing-graphics-information.md).  
  
## <a name="investigation"></a>Examen  
 À l’aide des outils Graphics Diagnostics, vous pouvez charger le fichier journal de graphisme pour examiner les frames capturés pendant le test.  
  
#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Pour examiner un frame dans un journal de graphiques  
  
1. Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], chargez un journal de graphisme qui contient un frame présentant le modèle manquant. Un nouvel onglet Graphics Diagnostics s’affiche dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. La partie supérieure de cet onglet contient la sortie de la cible de rendu du frame sélectionné. La partie inférieure contient la **Liste de frames**, qui affiche chaque frame capturé sous forme de miniature.  
  
2. Dans **Liste de frames**, sélectionnez un frame qui montre que le modèle n’est pas affiché. La cible de rendu est mise à jour pour refléter le frame sélectionné. Dans ce scénario, l'onglet du journal de graphisme se présente comme suit :  
  
    ![Le .vsglog framebuffer preview et le cadre de la liste d’onglets](media/vsg_walkthru1_experiment.png "vsg_walkthru1_experiment")  
  
   Une fois que vous avez sélectionné un frame qui illustre le problème, vous pouvez utiliser la **Liste des événements Graphics** pour le diagnostiquer. La fenêtre **Liste des événements Graphics** contient chaque appel d’API Direct3D qui a été effectué pour afficher le frame actif, par exemple les appels API pour configurer l’état de l’appareil, créer et mettre à jour les mémoires tampons, et dessiner les objets qui apparaissent dans le frame. Plusieurs types d’appels sont intéressants, car il y a souvent (mais pas toujours) une modification correspondante dans la cible de rendu quand l’application fonctionne comme prévu. C’est le cas des appels de dessin, de distribution, de copie ou d’effacement, par exemple. Les appels de dessin sont particulièrement intéressants, car chacun d’eux représente la géométrie affichée par l’application (les appels de distribution permettent aussi cela).  
  
#### <a name="to-ensure-that-draw-calls-are-being-made"></a>Pour vérifier que les appels de dessin sont effectués  
  
1. Ouvrez la fenêtre **Liste des événements Graphics** . Dans la barre d’outils **Graphics Diagnostics** , choisissez **Liste des événements**.  
  
2. Dans la fenêtre **Liste des événements Graphics** , recherchez les appels de dessin. Pour rendre la tâche plus simple, entrez “Draw” dans la zone **Rechercher** , en haut à droite de la fenêtre **Liste des événements Graphics** . Cela permet de filtrer la liste pour retenir uniquement les événements qui contiennent « Draw » dans leur titre. Dans ce scénario, vous découvrez que plusieurs appels de dessin ont été effectués :  
  
    ![Liste des événements Graphics affichant les événements capturés](media/vsg_walkthru1_.png "vsg_walkthru1_")  
  
   Après avoir constaté que les appels de dessin sont bien effectués, vous pouvez déterminer celui qui correspond à la géométrie manquante. Vous savez que la géométrie manquante n’est pas dessinée dans la cible de rendu (dans ce cas précis). Vous pouvez donc utiliser la fenêtre **Étapes de canalisation Graphics** pour déterminer quel appel de dessin correspond à la géométrie manquante. La fenêtre **Étapes de canalisation Graphics** affiche la géométrie qui a été envoyée à chaque appel de dessin, quel que soit son effet sur la cible de rendu. À mesure que vous parcourez les appels de dessin, les étapes de canalisation sont mises à jour pour afficher la géométrie qui est associée à l’appel, et la sortie de la cible de rendu est mise à jour pour afficher l’état de la cible de rendu à l’issue de l’appel.  
  
#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>Pour rechercher l’appel de dessin correspondant à la géométrie manquante  
  
1. Ouvrez la fenêtre **Étapes de canalisation Graphics** . Dans la barre d’outils **Graphics Diagnostics** , choisissez **Étapes de canalisation**.  
  
2. Parcourez chaque appel de dessin tout en recherchant le modèle manquant dans la fenêtre **Étapes de canalisation Graphics** . L’étape **Assembleur d’entrée** affiche les données de modèle brutes. L’étape **Nuanceur de sommets** affiche les données de modèle transformées. L’étape **Nuanceur de pixels** affiche la sortie du nuanceur de pixels. L’étape **Fusion de sortie** affiche la cible de rendu fusionnée de cet appel de dessin et de tous les appels de dessin précédents.  
  
3. Arrêtez quand vous avez atteint l’appel de dessin qui correspond au modèle manquant. Dans ce scénario, la fenêtre **Étapes de canalisation Graphics** indique que la géométrie a été affichée, mais pas dans la cible de rendu :  
  
    ![Visionneuse de pipeline affichant l’objet manquant](media/vsg_walkthru1_pipeline.png "vsg_walkthru1_pipeline")  
  
   Vous avez vérifié que l’application a bien affiché la géométrie manquante et vous avez trouvé l’appel de dessin correspondant. Vous pouvez maintenant sélectionner une partie de la sortie de la cible de rendu qui doit afficher la géométrie manquante, puis utiliser la fenêtre **Historique des pixels Graphics** pour déterminer la raison pour laquelle les pixels ont été exclus. L’historique des pixels contient une liste de chaque appel de dessin qui peut avoir eu un effet sur un pixel donné. Dans la fenêtre **Historique des pixels Graphics** , chaque appel de dessin est identifié par un nombre qui est également affiché dans la fenêtre **Liste des événements Graphics** . Cela vous permet de vérifier que le pixel doit afficher la géométrie manquante et de savoir pourquoi le pixel a été exclu.  
  
#### <a name="to-determine-why-the-pixel-was-excluded"></a>Pour déterminer pourquoi le pixel a été exclu  
  
1. Ouvrez la fenêtre **Historique des pixels Graphics** . Dans la barre d’outils **Graphics Diagnostics** , choisissez **Historique des pixels**.  
  
2. En vous basant sur le **Nuanceur de pixels** , sélectionnez un pixel dans la sortie de la mémoire de l’image qui doit contenir une partie de la géométrie manquante. Dans ce scénario, la sortie du nuanceur de pixels doit couvrir la majorité de la cible de rendu. Après la sélection d’un pixel, la fenêtre **Historique des pixels Graphics** ressemble à ceci :  
  
    ![Appels de dessin de fenêtre d’historique des pixels affichant connexes](media/vsg_walkthru1_hist1.png "vsg_walkthru1_hist1")  
  
3. Vérifiez que le pixel sélectionné dans la cible de rendu contient une partie de la géométrie en mettant en correspondance le numéro de l’appel de dessin examiné (dans la fenêtre **Liste des événements Graphics** ) avec l’un des appels de dessin figurant dans la fenêtre **Historique des pixels Graphics** . Si aucun des appels de la fenêtre **Historique des pixels Graphics** ne correspond à l’appel de dessin que vous examinez, répétez ces étapes (sauf l’étape 1) jusqu’à ce que vous trouviez une correspondance. Dans ce scénario, l’appel de dessin correspondant se présente comme suit :  
  
    ![Fenêtre d’historique des pixels affichant les informations relatives au fragment](media/vsg_walkthru1_hist2.png "vsg_walkthru1_hist2")  
  
4. Quand vous trouvez une correspondance, développez l’appel de dessin correspondant dans la fenêtre **Historique des pixels Graphics** et vérifiez que le pixel a été exclu. Chaque appel de dessin affiché dans la fenêtre **Historique des pixels Graphics** correspond à une ou plusieurs primitives géométriques (points, lignes ou triangles) entrées en intersection avec ce pixel du fait de la géométrie de l’objet correspondant. Chacune de ces intersections peut contribuer à définir la couleur finale du pixel. Une primitive qui est exclue parce qu’elle n’a pas réussi le test Depth Test est représentée par une icône illustrant une lettre Z sur une flèche descendante de gauche à droite.  
  
5. Développez une primitive exclue pour examiner plus en détail l’état qui a causé son exclusion. Dans le groupe **Fusion de sortie** , placez le pointeur sur **Résultat**. Une info-bulle indique la raison pour laquelle la primitive a été exclue. Dans ce scénario, l’examen révèle que la primitive a été exclue parce qu’elle n’a pas réussi le test Depth Test et qu’elle n’a donc pas contribué à définir la couleur finale du pixel.  
  
   Vous avez déterminé que la géométrie ne s’est pas affichée en raison de l’échec de ses primitives au test Depth Test. Vous pouvez donc supposer que ce problème est lié à une configuration incorrecte de l’état de l’appareil. Vous pouvez examiner l’état de l’appareil et d’autres données d’objet Direct3D dans la fenêtre **Table des objets Graphics**.  
  
#### <a name="to-examine-device-state"></a>Pour examiner l’état de l’appareil  
  
1. Ouvrez la fenêtre **Table des objets Graphics** . Dans la barre d’outils **Graphics Diagnostics** , choisissez **Table des objets**.  
  
2. Recherchez l’objet **Périphérique D3D10** dans **Table des objets Graphics**, puis ouvrez l’objet **Périphérique D3D10** . Un nouvel onglet **Périphérique D3D10** s’ouvre dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Pour simplifier cette opération, vous pouvez trier la **Table des objets Graphics** par **Type**:  
  
    ![Table des objets Graphics et état de périphérique associé](media/vsg_walkthru1_objtable.png "vsg_walkthru1_objtable")  
  
3. Examinez l’état de l’appareil affiché dans l’onglet **Périphérique D3D10** pour y découvrir les problèmes potentiels. Comme vous avez déterminé que la géométrie ne s’est pas affichée en raison de l’échec de ses primitives au test Depth Test, vous pouvez vous concentrer sur l’état de l’appareil, tel que le stencil de profondeur, qui affecte ce test Depth Test. Dans ce scénario, la **description du stencil de profondeur** (sous **État de la fusion de sortie**) présente une valeur inhabituelle pour le membre **fonction de profondeur** , `D3D10_COMPARISON_GREATER`:  
  
    ![Fenêtre de périphérique D3D10 affichant les informations du stencil de profondeur](media/vsg_walkthru1_devicestate.png "vsg_walkthru1_devicestate")  
  
   Après avoir déterminé que le problème de rendu est lié à une fonction de profondeur mal configurée, vous pouvez utiliser cette information ainsi que votre connaissance du code pour identifier l’emplacement où la fonction de profondeur a été mal définie, et résoudre le problème. Si vous êtes peu familiarisé avec le code, vous pouvez identifier le problème à l’aide des indices que vous avez rassemblés lors du débogage. Par exemple, en reprenant la **description du stencil de profondeur** de ce scénario, vous pouvez rechercher le code pour les mots tels que « profondeur » ou « supérieure ». Après avoir corrigé le code, vous devez le régénérer, puis réexécuter l’application pour vérifier que le problème d’affichage est résolu :  
  
   ![Application une fois le problème est résolu](media/vsg_walkthru1_finalview.png "vsg_walkthru1_finalview")