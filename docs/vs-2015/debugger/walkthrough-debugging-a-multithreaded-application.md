---
title: 'Procédure pas à pas : Débogage d’une Application multithread | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- multithreaded debugging, walkthrough
- walkthroughs, multithreaded debugging
ms.assetid: 590ffd57-0556-43d8-8962-ee27e5b2b7d7
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5dd742411710698cb2dd626e211cb0e73b8379e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798628"
---
# <a name="walkthrough-debugging-a-multithreaded-application"></a>Procédure pas à pas : débogage d'une application multithread
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] Fournit une meilleure **Threads** fenêtre et autres l’interface utilisateur des améliorations pour le rendre plus facile à déboguer des applications multithread. Cette procédure pas à pas ne prend que quelques minutes. Elle permet de se familiariser avec les nouvelles fonctionnalités de l’interface de débogage des applications multithread.  
  
 Pour commencer cette procédure pas à pas, vous avez besoin d'un projet d'application multithread. Pour créer ce projet, procédez comme suit.  
  
#### <a name="to-create-the-walkthrough-project"></a>Pour créer le projet de procédure pas à pas  
  
1.  Sur le **fichier** menu, choisissez **New** puis cliquez sur **projet**.  
  
     La boîte de dialogue **Nouveau projet** s’affiche.  
  
2.  Dans le **Type de projet**s, cliquez sur le langage de votre choix : **Visual Basic**, **Visual C#**, ou **Visual C++**.  
  
3.  Dans le **modèles** , sélectionnez **Application Console** ou **Application Console CLR**.  
  
4.  Dans le **nom** zone, entrez le nom MyThreadWalkthroughApp.  
  
5.  Cliquez sur **OK**.  
  
     Un nouveau projet console s'affiche. Lorsque le projet a été créé, un fichier source s'affiche. En fonction du langage choisi, le fichier source peut être nommé Module1.vb, Program.cs ou MyThreadWalkthroughApp.cpp  
  
6.  Supprimez le code qui s’affiche dans le fichier source et remplacez-le par l’exemple de code qui s’affiche dans la section « Création d’un Thread » de la rubrique [création de Threads et passage de données à l’heure de début](http://msdn.microsoft.com/library/52b32222-e185-4f42-91a7-eaca65c0ab6d).  
  
7.  Sur le **fichier** menu, cliquez sur **Enregistrer tout**.  
  
#### <a name="to-begin-the-walkthrough"></a>Pour démarrer la procédure pas à pas  
  
-   Dans la fenêtre source, recherchez le code suivant :  
  
    ```vb  
    Thread.Sleep(3000)   
    Console.WriteLine(  
    ```  
  
```csharp  
Thread.Sleep(3000);  
Console.WriteLine();  
```  
  
```cpp  
Thread::Sleep(3000);  
Console.WriteLine();  
```  
  
#### <a name="to-start-debugging"></a>Pour démarrer le débogage  
  
1.  Cliquez sur le `Console.WriteLine` instruction, pointez sur **point d’arrêt** puis cliquez sur **insérer un point d’arrêt**.  
  
     Une bille rouge apparaît au niveau de la reliure située sur le côté gauche de la fenêtre source. Cette bille indique qu'un point d'arrêt est désormais défini à cet emplacement.  
  
2.  Dans le menu **Déboguer**, cliquez sur **Démarrer le débogage**.  
  
     Le débogage démarre, votre application console se lance puis s'interrompt au point d'arrêt.  
  
3.  Si, à ce stade, la fenêtre d'application console a le focus, cliquez dans la fenêtre [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour retourner le focus à [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4.  Dans la fenêtre source, localisez la ligne qui contient le code suivant :  
  
    ```vb  
    Thread.Sleep(5000)   
    ```  
  
```csharp  
Thread.Sleep(3000);  
```  
  
```cpp  
Thread::Sleep(3000);  
```  
  
1.  
  
#### <a name="to-discover-the-thread-marker"></a>Pour découvrir le marqueur de thread  
  
1. Avec le bouton droit dans le **Threads** fenêtre, puis cliquez sur **afficher les Threads dans la Source**.  
  
2. Examinez la reliure située sur le côté gauche de la fenêtre. Une icône ressemblant à un maillage s'affiche sur cette ligne. Un des threads est rouge et l'autre est bleu. Le marqueur de thread indique qu'un thread est interrompu à cet emplacement. Le thread s'interrompt peut-être à cet emplacement.  
  
3. Placez le pointeur sur le marqueur de thread. Un DataTip apparaît. Le DataTip vous indique le nom et le numéro d'ID de thread de chaque thread interrompu. Dans ce cas, il n'existe qu'un seul thread dont le nom est probablement `<noname>`.  
  
4. Cliquez avec le bouton droit sur le marqueur de thread. Notez les choix dans le menu contextuel.  
  
   Cette icône est un *marqueur de thread*:  
  
   ![Marqueur de thread](../debugger/media/threadmarker.gif "ThreadMarker")  
  
## <a name="flagging-and-unflagging-threads"></a>Ajout et suppression d'indicateur de threads  
 Dans [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)], vous pouvez indiquer les threads auxquels vous souhaitez accorder une attention particulière. Le signalement des threads vous permet de suivre les threads importants et d'ignorer ceux de moindre importance.  
  
#### <a name="to-flag-threads"></a>Pour ajouter des indicateurs de thread  
  
1.  Sur **vue** menu, pointez sur **barres d’outils**.  
  
     Assurez-vous que le **emplacement de débogage** barre d’outils est sélectionné.  
  
2.  Accédez à la **emplacement de débogage** barre d’outils et cliquez sur le **Thread** liste.  
  
    > [!NOTE]
    >  Vous pouvez reconnaître cette barre d’outils de trois listes principales : **processus**, **Thread**, et **Frame de pile**.  
  
3.  Notez le nombre de threads qui s'affichent dans la liste.  
  
4.  Revenez à la fenêtre source et un clic droit la **Thread** marqueur à nouveau.  
  
5.  Dans le menu contextuel, pointez sur **indicateur**, puis cliquez sur le nom de thread et le numéro d’identification.  
  
6.  Revenez à **emplacement de débogage** barre d’outils et cliquez sur le **Thread** liste à nouveau.  
  
     Seul le thread avec indicateur s'affiche désormais dans la liste. Le bouton indicateur situé à droite de la **Thread** liste. L'icône d'indicateur du bouton était grisée. Il est désormais rouge clair.  
  
7.  Placez le pointeur sur l'icône de l'indicateur.  
  
     Un menu contextuel s'affiche. Cette fenêtre contextuelle vous indique le mode le **Thread** liste se trouve dans : **afficher uniquement les Threads avec indicateur**.  
  
8.  Cliquez sur le bouton indicateur pour revenir au **afficher tous les Threads** mode.  
  
9. Cliquez sur le **Thread** répertorier à nouveau et vérifier que vous pouvez maintenant voir tous les threads à nouveau.  
  
10. Cliquez sur le bouton indicateur pour revenir au **afficher uniquement les Threads avec indicateur**.  
  
11. Sur le **déboguer** menu, pointez sur **Windows** puis cliquez sur **Threads**.  
  
     Le **Threads** fenêtre s’affiche. Un thread possède une icône d'indicateur apparente qui lui est associée.  
  
12. Dans la fenêtre source, cliquez de nouveau avec le bouton droit sur le marqueur de thread.  
  
     Notez les choix disponibles dans le menu contextuel. Au lieu de **indicateur**, vous recevez à présent **supprimer l’indicateur**. Ne cliquez pas sur **supprimer l’indicateur**.  
  
13. Accédez à la procédure suivante relative à la suppression des threads.  
  
#### <a name="to-unflag-threads"></a>Pour supprimer l'indicateur de threads  
  
1.  Sur le **Threads** fenêtre, cliquez sur la ligne correspondant au thread avec indicateur.  
  
     Un menu contextuel s'affiche. Il contient les options **supprimer l’indicateur** et **tous les indicateurs**.  
  
2.  Pour supprimer l’indicateur de thread, cliquez sur **supprimer l’indicateur**.  
  
3.  Cliquez sur l'icône d'indicateur rouge.  
  
4.  Examinez le **emplacement de débogage** barre d’outils à nouveau. Le bouton indicateur est de nouveau grisé. Vous avez supprimé l'indicateur du seul thread avec indicateur. Comme il n’existe aucun thread avec indicateur, la barre d’outils est revenue en **afficher tous les Threads** mode. Cliquez sur le **Thread** répertorier et vérifier que vous pouvez voir tous les threads.  
  
5.  Revenez à la **Threads** fenêtre et examinez les colonnes d’informations.  
  
     Dans la partie supérieure de chaque colonne, le nom de la majorité des boutons permet d'identifier la colonne. Cependant, la première colonne de gauche ne comporte aucun titre. Elle contient une icône qui correspond au contour d'un indicateur. Notez que le contour est identique pour chaque ligne de la liste de thread. Le contour indique que le thread est sans indicateur.  
  
6.  Cliquez sur le contour des indicateurs du second et du troisième threads en partant de la fin de la liste.  
  
     Les contours vides deviennent des icônes d'indicateur unies rouge.  
  
7.  Cliquez sur le bouton en haut de la colonne d'indicateurs.  
  
     L'ordre de la liste de threads a été modifié lorsque vous avez cliqué sur le bouton. La liste de threads est maintenant triée et les threads avec indicateur sont situés en haut de la liste.  
  
8.  Cliquez de nouveau sur le bouton en haut de la colonne d'indicateurs.  
  
     L'ordre de tri a encore changé.  
  
## <a name="more-about-the-threads-window"></a>En savoir plus sur la fenêtre Threads  
  
#### <a name="to-learn-more-about-the-threads-window"></a>Pour en savoir plus sur la fenêtre Threads  
  
1.  Dans le **Threads** fenêtre, examinez la troisième colonne de gauche. Le bouton en haut de cette colonne est **ID**.  
  
2.  Cliquez sur **ID**.  
  
     La liste de threads est maintenant triée par numéro d'ID de thread.  
  
3.  Cliquez avec le bouton droit sur un thread de la liste. Dans le menu contextuel, cliquez sur **affichage hexadécimal**.  
  
     Le format des numéros d'ID de thread se modifie.  
  
4.  Placez le pointeur de la souris sur un thread de la liste.  
  
     Un DataTip s'affiche peu après. Il représente une pile des appels partielle du thread.  
  
5.  Examinez la quatrième colonne de gauche, qui est étiquetée **catégorie**. Les threads sont classés dans des catégories.  
  
     Le premier thread créé dans un processus correspond au thread principal. Localisez-le dans la liste de threads.  
  
6.  Cliquez sur le thread principal, puis sur **basculer vers Thread**.  
  
     Une boîte de dialogue d'avertissement s'affiche. Elle vous indique que [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ne peut pas afficher le code source du thread principal.  
  
     Cliquez sur **OK**.  
  
7.  Examinez le **pile des appels** fenêtre et la **emplacement de débogage** barre d’outils.  
  
     Le contenu de la **pile des appels** fenêtre ont changé.  
  
## <a name="switching-the-active-thread"></a>Basculement du Thread actif  
  
#### <a name="to-switch-threads"></a>Pour basculer les threads  
  
1.  Dans le **Threads** fenêtre, examinez la deuxième colonne de gauche. Le bouton en haut de cette colonne ne comporte aucun texte ou icône. Cette colonne est la **Thread actif** colonne.  
  
2.  Examinez le **Thread actif** colonne et notez qu’un thread comporte une flèche jaune. Il s’agit du *indicateur de thread actif*.  
  
3.  Notez le numéro d'ID du thread dans lequel se trouve l'indicateur de thread actif. Vous allez déplacer l'indicateur de thread actif vers un autre thread, mais vous devrez le remettre à sa place lorsque vous aurez fini.  
  
4.  Cliquez sur un autre thread, puis sur **basculer vers Thread**.  
  
5.  Examinez le **pile des appels** fenêtre dans la fenêtre source. Le contenu a été modifié.  
  
6.  Examinez le **emplacement de débogage** barre d’outils. Le thread actif a également été modifié.  
  
7.  Accédez à la **emplacement de débogage** barre d’outils. Cliquez sur le **Thread** et sélectionnez un thread différent dans la liste déroulante.  
  
8.  Examinez le **Threads** fenêtre. L'indicateur de thread actif a également été modifié.  
  
9. Dans la fenêtre source, cliquez avec le bouton droit sur un marqueur de thread. Dans le menu contextuel, pointez sur **basculer vers** et cliquez sur un numéro d’ID/nom de thread.  
  
     Vous avez maintenant vu trois manières de modifier le thread actif : à l’aide de la **Threads** fenêtre, le **Thread** zone le **emplacement de débogage** barre d’outils et l’indicateur de thread dans le fenêtre source.  
  
     L'indicateur de thread vous permet de basculer uniquement vers les threads interrompus à cet emplacement précis. À l’aide de la **Threads** fenêtre et **emplacement de débogage** barre d’outils, que vous pouvez basculer vers n’importe quel thread.  
  
## <a name="freezing-and-thawing-thread-execution"></a>Gel et libération de l'exécution de thread  
  
#### <a name="to-freeze-and-unfreeze-threads"></a>Pour figer et dégeler les threads  
  
1.  Dans le **Threads** fenêtre, avec le bouton droit n’importe quel thread, puis cliquez sur **Figer**.  
  
2.  Observez la colonne de threads actifs. Les deux barres verticales y sont maintenant affichées. Ces barres bleues indiquent que le thread est figé.  
  
3.  Examinez le **Suspend** colonne. Le compteur de suspension du thread est désormais à 1.  
  
4.  Cliquez sur le thread figé, puis sur **libérer**.  
  
     La colonne de thread actif et le **Suspend** modification de la colonne.  
  
## <a name="see-also"></a>Voir aussi  
 [Déboguer les Applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Guide pratique pour basculer vers un autre thread pendant un débogage](../debugger/how-to-switch-to-another-thread-while-debugging.md)



