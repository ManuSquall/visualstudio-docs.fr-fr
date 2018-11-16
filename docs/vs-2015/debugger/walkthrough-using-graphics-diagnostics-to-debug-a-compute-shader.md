---
title: 'Procédure pas à pas : Utilisation de Graphics Diagnostics pour déboguer un nuanceur de calcul | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 69287456-644b-4aff-bd03-b1bbb2abb82a
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55f0b9de879011110d8df46c0e4d738265b0fa34
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51730642"
---
# <a name="walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader"></a>Procédure pas à pas : utilisation de Graphics Diagnostics pour déboguer un Shader de calcul
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette procédure pas à pas montre comment utiliser les outils Visual Studio Graphics Diagnostics pour examiner un nuanceur de calcul qui génère des résultats incorrects.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Utilisation de la **liste des événements Graphics** pour rechercher les sources potentielles du problème.  
  
-   À l’aide de la **événements Graphics** pour déterminer le calcul nuanceur est exécuté par un DirectCompute `Dispatch` événement.  
  
-   À l’aide de la **étapes de canalisation Graphics** fenêtre et du débogueur HLSL pour examiner le nuanceur de calcul qui est la source du problème.  
  
## <a name="scenario"></a>Scénario  
 Dans ce scénario, vous avez écrit une simulation relative à la dynamique des fluides, qui utilise DirectCompute pour effectuer les calculs les plus poussés de la mise à jour de la simulation. Quand l'application est exécutée, le rendu du jeu de données et de l'interface utilisateur semble correct. Toutefois, la simulation ne se comporte pas comme prévu. À l'aide de Graphics Diagnostics, vous pouvez capturer le problème dans un journal de graphisme pour déboguer l'application. Le problème se présente ainsi dans l'application :  
  
 ![Le fluide simulé est défaillant. ](../debugger/media/gfx-diag-demo-compute-shader-fluid-problem.png "gfx_diag_demo_compute_shader_fluid_problem")  
  
 Pour plus d’informations sur la capture des problèmes de graphisme dans un journal de graphisme, consultez [Capturing Graphics Information](../debugger/capturing-graphics-information.md).  
  
## <a name="investigation"></a>Examen  
 Vous pouvez utiliser les outils Graphics Diagnostics pour charger le fichier journal de graphisme et inspecter les frames capturés.  
  
#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Pour examiner un frame dans un journal de graphiques  
  
1. Dans Visual Studio, chargez un journal de graphisme qui contient un frame exposant les résultats de simulation incorrects. Un nouvel onglet Graphics Diagnostics s'affiche dans Visual Studio. La partie supérieure de cet onglet contient la sortie de la cible de rendu du frame sélectionné. Dans la partie inférieure est la **liste de frames**, qui affiche une miniature de chaque frame capturé.  
  
2. Dans le **liste de frames**, sélectionnez un frame qui illustre le comportement de simulation incorrect. Bien que l'erreur semble se situer dans le code de simulation et non dans le code de rendu, vous devez choisir un frame, car les événements DirectCompute sont capturés frame par frame, avec les événements Direct3D. Dans ce scénario, l'onglet du journal de graphisme se présente comme suit :  
  
    ![Document du journal des graphiques dans Visual Studio. ](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-1.png "gfx_diag_demo_compute_shader_fluid_step_1")  
  
   Une fois que vous avez sélectionné un frame qui illustre le problème, vous pouvez utiliser la **Liste des événements Graphics** pour le diagnostiquer. Le **liste des événements Graphics** contient un événement pour chaque appel de DirectCompute et l’appel d’API de Direct3D qui a été effectuée durant le frame actif, par exemple, appels d’API pour exécuter un calcul sur le GPU, ou pour afficher le jeu de données ou l’interface utilisateur. Dans le cas présent, nous sommes intéressés par les événements `Dispatch` qui représentent certaines parties de la simulation exécutées sur le GPU.  
  
#### <a name="to-find-the-dispatch-event-for-the-simulation-update"></a>Pour rechercher l'événement Dispatch pour la mise à jour de la simulation  
  
1. Sur le **Graphics Diagnostics** barre d’outils, choisissez **liste des événements** pour ouvrir le **liste des événements Graphics** fenêtre.  
  
2. Inspecter le **liste des événements Graphics** pour l’événement de dessin qui restitue le jeu de données. Pour faciliter cette opération, entrez `Draw` dans le **recherche** zone dans le coin supérieur droit de la **liste des événements Graphics** fenêtre. Cela permet de filtrer la liste pour retenir uniquement les événements qui contiennent « Draw » dans leur titre. Dans ce scénario, vous découvrez que les événements de dessin suivants se sont produits :  
  
    ![La liste des événements &#40;EL&#41; montre les événements de dessin. ](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-2.png "gfx_diag_demo_compute_shader_fluid_step_2")  
  
3. Parcourez chaque événement de dessin pendant que vous regardez la cible de rendu sous l'onglet du document journal de graphisme.  
  
4. Arrêtez-vous quand la cible de rendu affiche pour la première fois le jeu de données. Dans ce scénario, le jeu de données est rendu dans le premier événement de dessin. L'erreur de la simulation s'affiche :  
  
    ![Cet événement draw restitue le jeu de données de simulation. ](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-3.png "gfx_diag_demo_compute_shader_fluid_step_3")  
  
5. Observons à présent le **liste des événements Graphics** pour le `Dispatch` événement qui met à jour la simulation. Comme il est probable que la simulation est mise à jour avant son rendu, vous pouvez vous concentrer tout d'abord sur les événements `Dispatch` qui se produisent avant l'événement de dessin de rendu des résultats. Pour simplifier ce processus, modifiez la **recherche** boîte lire `Draw;Dispatch;CSSetShader(`. Cela permet de filtrer la liste pour qu'elle contienne également les événements `Dispatch` et `CSSetShader`, en plus des événements de dessin. Dans ce scénario, vous découvrez que plusieurs événements `Dispatch` se sont produits avant l'événement de dessin :  
  
    ![Affiche les événements de dessin, Dispatch et CSSetShader](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-4.png "gfx_diag_demo_compute_shader_fluid_step_4")  
  
   Une fois que vous avez isolé une partie des nombreux événements `Dispatch` qui peuvent correspondre au problème, vous pouvez les examiner plus en détail.  
  
#### <a name="to-determine-which-compute-shader-a-dispatch-call-executes"></a>Pour identifier le nuanceur de calcul exécuté par un appel de Dispatch  
  
1. Sur le **Graphics Diagnostics** barre d’outils, choisissez **pile des appels des événements** pour ouvrir le **événements Graphics** fenêtre.  
  
2. À partir de l'événement de dessin qui restitue les résultats de la simulation, naviguez vers l'arrière de chaque événement `CSSetShader` précédent. Ensuite, dans le **événements Graphics** fenêtre, choisissez la fonction de plus haut pour accéder au site d’appel. Sur le site d’appel, vous pouvez utiliser le premier paramètre de la [CSSetShader](http://msdn.microsoft.com/library/ff476402.aspx) fonction d’appel pour déterminer lequel nuanceur de calcul exécuté par le prochain `Dispatch` événement.  
  
   Dans ce scénario, il existe trois paires d'événements `CSSetShader` et `Dispatch` dans chaque frame. Si vous revenez en arrière, la troisième paire représente l'étape d'intégration (où les particules fluides sont effectivement déplacées), la deuxième paire représente l'étape de calcul des forces (où les forces qui affectent chaque particule sont calculées), et la première paire représente l'étape de calcul de la densité.  
  
#### <a name="to-debug-the-compute-shader"></a>Pour déboguer le nuanceur de calcul  
  
1. Sur le **Graphics Diagnostics** barre d’outils, choisissez **canalisation** pour ouvrir le **étapes de canalisation Graphics** fenêtre.  
  
2. Sélectionnez le troisième `Dispatch` événements (celui qui précède immédiatement l’événement de dessin), puis, dans le **étapes de canalisation Graphics** fenêtre, sous le **nuanceur de calcul** à l’étape, choisissez  **Démarrer le débogage**.  
  
    ![Sélection du troisième événement Dispatch dans l’EL](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-6.png "gfx_diag_demo_compute_shader_fluid_step_6")  
  
    Le débogueur HLSL démarre au niveau du nuanceur qui exécute l'étape d'intégration.  
  
3. Examinez le code source du nuanceur de calcul à l'étape d'intégration pour rechercher la source de l'erreur. Quand vous utilisez Graphics Diagnostics pour déboguer du code de nuanceur de calcul HLSL, vous pouvez effectuer un pas à pas détaillé dans le code, et utiliser d’autres outils de débogage familiers tels que les fenêtres Espion. Dans ce scénario, vous déterminez qu'il ne semble pas y avoir d'erreurs dans le nuanceur de calcul qui exécute l'étape d'intégration.  
  
    ![Débogage du nuanceur programmable IntegrateCS. ](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-7.png "gfx_diag_demo_compute_shader_fluid_step_7")  
  
4. Pour arrêter le débogage du nuanceur de calcul, sur le **déboguer** barre d’outils, choisissez **arrêter le débogage** (clavier : MAJ + F5).  
  
5. Sélectionnez ensuite le deuxième événement `Dispatch`, puis démarrez le débogage du nuanceur de calcul comme vous l'avez fait à l'étape précédente.  
  
    ![Sélection du deuxième événement Dispatch dans l’EL](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-8.png "gfx_diag_demo_compute_shader_fluid_step_8")  
  
    Le débogueur HLSL démarre au niveau du nuanceur qui calcule les forces agissant sur chaque particule fluide.  
  
6. Examinez le code source du nuanceur de calcul pour l'étape de calcul des forces. Dans ce scénario, vous déterminez que la source de l'erreur se trouve ici.  
  
    ![Débogage de la ForceCS&#95;nuanceur de calcul Simple. ](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-9.png "gfx_diag_demo_compute_shader_fluid_step_9")  
  
   Après avoir déterminé l'emplacement de l'erreur, vous pouvez arrêter le débogage et modifier le code source du nuanceur de calcul pour calculer correctement la distance entre les particules en interaction. Dans ce scénario, vous remplacez simplement la ligne `float2 diff = N_position + P_position;` par `float2 diff = N_position - P_position;` :  
  
   ![Le calcul corrigé&#45;code du nuanceur. ](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-10.png "gfx_diag_demo_compute_shader_fluid_step_10")  
  
   Dans ce scénario, les nuanceurs de calcul étant compilés au moment de l'exécution, redémarrez simplement l'application après avoir apporté les changements nécessaires pour voir comment ils affectent la simulation. Vous n'êtes pas obligé de régénérer l'application. Quand vous exécutez l'application, vous découvrez que la simulation se comporte correctement désormais.  
  
   ![Le fluide simulé se comporte correctement. ](../debugger/media/gfx-diag-demo-compute-shader-fluid-resolution.png "gfx_diag_demo_compute_shader_fluid_resolution")



