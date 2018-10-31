---
title: Déboguer une application multithread
description: Déboguer à l’aide de la fenêtre Threads et la barre d’outils emplacement de débogage dans Visual Studio
ms.custom: ''
ms.date: 05/18/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f82d53d5bbc9d309ba5d7e8710f0afe2023b8965
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219885"
---
# <a name="walkthrough-debug-a-multithreaded-application-in-visual-studio-using-the-threads-window"></a>Procédure pas à pas : Déboguer une application multithread dans Visual Studio à l’aide de la fenêtre Threads
Visual Studio fournit un **Threads** fenêtre et autres l’interface utilisateur éléments pour vous aider à déboguer les applications multithread. Ce didacticiel montre comment utiliser le **Threads** fenêtre et la **emplacement de débogage** barre d’outils. Pour plus d’informations sur les autres outils, consultez [commencer le débogage d’applications multithread](../debugger/get-started-debugging-multithreaded-apps.md). Ce didacticiel vous prendra que quelques minutes, mais comment la compléter vous familiarisera avec les fonctionnalités de débogage d’applications multithread.   
  
Pour commencer ce didacticiel, vous avez besoin d’un projet d’application multithread. Pour créer ce projet, procédez comme suit.  
  
#### <a name="to-create-the-multithreaded-app-project"></a>Pour créer le projet d’application multithread  
  
1.  Sur le **fichier** menu, choisissez **New** puis cliquez sur **projet**.  
  
     La boîte de dialogue **Nouveau projet** s’affiche.  
  
2.  Dans le **Types de projets** , cliquez sur le langage de votre choix : **Visual Basic**, **Visual C#** , ou **Visual C++**.  
  
3.  Sous **Windows Desktop**, choisissez **application Console**.  
  
4.  Dans le **nom** zone, entrez le nom MyThreadWalkthroughApp.  
  
5.  Cliquez sur **OK**.  
  
     Un nouveau projet console s'affiche. Lorsque le projet a été créé, un fichier source s'affiche. En fonction du langage choisi, le fichier source peut être nommé Module1.vb, Program.cs ou MyThreadWalkthroughApp.cpp  
  
6.  Supprimez le code qui s’affiche dans le fichier source et remplacez-le par l’exemple de code qui s’affiche dans la section « Création d’un Thread » de la rubrique [création de Threads et passage de données à l’heure de début](/dotnet/standard/threading/creating-threads-and-passing-data-at-start-time).  
  
7.  Sur le **fichier** menu, cliquez sur **Enregistrer tout**.  
  
#### <a name="to-begin-the-tutorial"></a>Pour commencer le didacticiel  
  
-   Dans l’éditeur de code source, recherchez le code suivant :  
  
    ```VB  
    Thread.Sleep(3000)   
    Console.WriteLine()
    ```  
  
    ```csharp  
    Thread.Sleep(3000);  
    Console.WriteLine();  
    ```  
  
    ```C++  
    Thread::Sleep(3000);  
    Console.WriteLine();  
    ```  
  
#### <a name="to-start-debugging"></a>Pour démarrer le débogage  
  
1. Cliquez dans la marge gauche de la `Console.WriteLine` instruction pour insérer un nouveau point d’arrêt.  
  
    Dans la marge à gauche de l’éditeur de code source, un cercle rouge apparaît. Cette bille indique qu'un point d'arrêt est désormais défini à cet emplacement.  
  
2. Sur le **déboguer** menu, cliquez sur **démarrer le débogage** (**F5**).  
  
    Le débogage démarre, votre application console se lance puis s'interrompt au point d'arrêt.  
  
3. Si, à ce stade, la fenêtre d'application console a le focus, cliquez dans la fenêtre [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour retourner le focus à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4. Dans l’éditeur de code source, recherchez la ligne qui contient le code suivant :  
  
   ```VB  
   Thread.Sleep(5000)   
   ```  
  
   ```csharp  
   Thread.Sleep(3000);  
   ```  
  
   ```C++  
   Thread::Sleep(3000);  
   ```
  
#### <a name="to-discover-the-thread-marker"></a>Pour découvrir le marqueur de thread  

1.  Dans la barre d’outils Déboguer, cliquez sur le **afficher les Threads dans la Source** bouton ![afficher les Threads dans la Source](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker"). 
  
2.  Examinez la reliure située sur le côté gauche de la fenêtre. Sur cette ligne, vous verrez un *marqueur de thread* icône ![marqueur de Thread](../debugger/media/dbg-thread-marker.png "ThreadMarker") qui ressemble à deux threads de maillage. Le marqueur de thread indique qu'un thread est interrompu à cet emplacement.  
  
3.  Placez le pointeur sur le marqueur de thread. Un DataTip apparaît. Le DataTip vous indique le nom et le numéro d'ID de thread de chaque thread interrompu. Dans ce cas, il n'existe qu'un seul thread dont le nom est probablement `<noname>`.  

    > [!TIP]
    > Il peut s’avérer utile d’identifier les threads sans nom en les renommant. Dans la fenêtre Threads, choisissez **renommer** après clic droit sur le **nom** colonne dans la ligne du thread.
  
4.  Cliquez sur le marqueur de thread pour afficher les options disponibles dans le menu contextuel. 
    
  
## <a name="flagging-and-unflagging-threads"></a>Ajout et suppression d'indicateur de threads  
Vous pouvez marquer les threads auxquels vous souhaitez accorder une attention particulière. Marquage des threads est un bon moyen pour effectuer le suivi des threads importants et ignorer les threads que vous ne vous souciez pas.  
  
#### <a name="to-flag-threads"></a>Pour ajouter des indicateurs de thread   

1.  Sur **vue** menu, pointez sur **barres d’outils**.  
  
    Assurez-vous que le **emplacement de débogage** barre d’outils est sélectionné.

2.  Accédez à la **emplacement de débogage** barre d’outils et cliquez sur le **Thread** liste.  
  
    > [!NOTE]
    >  Vous pouvez reconnaître cette barre d’outils de trois listes principales : **processus**, **Thread**, et **Frame de pile**.  
  
3.  Notez le nombre de threads qui s'affichent dans la liste.  
  
4.  Revenez à l’éditeur de code source et cliquez sur le marqueur de thread ![marqueur de Thread](../debugger/media/dbg-thread-marker.png "ThreadMarker") à nouveau.  
  
5.  Dans le menu contextuel, pointez sur **indicateur**, puis cliquez sur le nom de thread et le numéro d’identification.  
  
6.  Revenez à **emplacement de débogage** barre d’outils et de trouver la **afficher uniquement les Threads avec indicateur** icône ![afficher les Threads avec indicateur](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker") à la droit de la **Thread** liste.  
  
    L’icône des indicateurs sur le bouton était grisée. Il est maintenant, un bouton actif.  
  
7.  Cliquez sur le **afficher uniquement les Threads avec indicateur** icône.  
  
    Seul le thread avec indicateur s'affiche désormais dans la liste. (Vous pouvez cliquer sur le bouton indicateur unique pour rebasculer **afficher tous les Threads** mode.)

8. Ouvrez la fenêtre Threads en choisissant **Déboguer > Windows > Threads**.

    ![Threads, fenêtre](../debugger/media/dbg-threads-window.png "ThreadsWindow")  
  
    Dans le **Threads** fenêtre, le thread avec indicateur a une icône d’indicateur rouge apparente attachée.

    > [!TIP]
    > Lorsque vous avez des threads avec indicateur, vous pouvez cliquez sur une ligne de code dans l’éditeur de code et choisissez **exécuter les Threads avec indicateur au curseur** (veillez à choisir le code que tous les threads avec indicateur atteindront). Cela va suspendre des threads sur la ligne sélectionnée de code, rendant ainsi plus facile de contrôler l’ordre d’exécution par [gel et libération des threads](#bkmk_freeze).
  
11. Dans l’éditeur de code source, cliquez à nouveau sur le marqueur de thread.  
  
     Notez les choix disponibles dans le menu contextuel. Au lieu de **indicateur**, vous recevez à présent **supprimer l’indicateur**. Ne cliquez pas sur **supprimer l’indicateur**.  

     Pour savoir comment supprimer les indicateurs des threads, accédez à la procédure suivante.  
  
#### <a name="to-unflag-threads"></a>Pour supprimer l'indicateur de threads  
  
1.  Dans le **Threads** fenêtre, cliquez sur la ligne correspondant au thread avec indicateur.  
  
     Un menu contextuel s'affiche. Il contient les options **supprimer l’indicateur** et **supprimer l’indicateur de tous les Threads**.  
  
2.  Pour supprimer l’indicateur de thread, cliquez sur **supprimer l’indicateur**.  

    Examinez le **emplacement de débogage** barre d’outils à nouveau. Le **afficher uniquement les Threads avec indicateur** bouton est de nouveau grisé. Vous avez supprimé l'indicateur du seul thread avec indicateur. Comme il n’existe aucun thread avec indicateur, la barre d’outils est revenue en **afficher tous les Threads** mode. Cliquez sur le **Thread** répertorier et vérifier que vous pouvez voir tous les threads.  
  
5.  Revenez à la **Threads** fenêtre et examinez les colonnes d’informations.  
  
    Dans la première colonne, vous remarquerez une icône d’indicateur plan dans chaque ligne de la liste des threads. (Le contour indique que le thread est sans indicateur).  
  
6.  Cliquez sur les icônes de plan d’indicateur pour deux threads, les deuxième et le troisième à partir du bas de la liste. 

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
  
4.  Placez le pointeur de la souris sur le **emplacement** colonne pour n’importe quel thread dans la liste.  
  
     Un DataTip s'affiche peu après. Il représente une pile des appels partielle du thread.

     > [!TIP]
     > Pour obtenir une vue graphique des piles d’appels des threads, ouvrez le [piles parallèles](../debugger/using-the-parallel-stacks-window.md) fenêtre (pendant le débogage, choisissez **déboguer / Windows / piles parallèles**).  
  
5.  Examinez la quatrième colonne de gauche, qui est étiquetée **catégorie**. Les threads sont classés dans des catégories.  
  
     Le premier thread créé dans un processus correspond au thread principal. Localisez-le dans la liste de threads.  
  
6.  Cliquez sur le thread principal, puis sur **basculer vers Thread**.  
  
     Un **Mode arrêt** fenêtre s’affiche. Elle vous indique que le débogueur n'est pas en cours d’exécution de code qu’il peut afficher (car il est le thread principal).   
  
7.  Examinez le **pile des appels** fenêtre et la **emplacement de débogage** barre d’outils.  
  
     Le contenu de la **pile des appels** fenêtre ont changé. 

## <a name="bkmk_freeze"></a> Gel et libération de l’exécution du thread 

Vous pouvez figer et libérer (suspendre et reprendre) les threads pour contrôler l’ordre dans lequel threads exécutent le travail. Cela peut vous aider à résoudre les problèmes d’accès concurrentiel tels que les interblocages et conditions de concurrence critique.

> [!TIP]
> Si vous souhaitez suivre un seul thread sans bloquer les autres threads (également un scénario de débogage courants), consultez [commencer le débogage d’applications multithread](../debugger/get-started-debugging-multithreaded-apps.md#bkmk_follow_a_thread).
  
#### <a name="to-freeze-and-unfreeze-threads"></a>Pour figer et dégeler les threads  
  
1.  Dans le **Threads** fenêtre, avec le bouton droit n’importe quel thread, puis cliquez sur **Figer**.  
  
2.  Examinez la deuxième colonne (la colonne de thread actuelle). L’icône de pause apparaît maintenant il. Ces icône de pause indique que le thread est figé.  
  
3.  Afficher le **compteur suspendu** colonne en le sélectionnant dans le **colonnes** liste.

    Le compteur de suspension du thread est désormais à 1.  
  
4.  Cliquez sur le thread figé, puis sur **libérer**.  
  
     La colonne de thread actuelle et la **compteur suspendu** modification de la colonne. 
  
## <a name="switching-the-to-another-thread"></a>Basculer le vers un autre thread 
  
#### <a name="to-switch-threads"></a>Pour basculer les threads  
  
1.  Dans le **Threads** fenêtre, examinez la deuxième colonne de gauche (la colonne de thread actuelle). Le bouton en haut de cette colonne ne comporte aucun texte ou icône.
  
2.  Examinez la colonne de thread en cours et notez qu’un thread comporte une flèche jaune. La flèche jaune indique que ce thread est le thread actuel (il s’agit de l’emplacement actuel du pointeur d’exécution).
  
    Notez le numéro d’ID de thread où vous voyez l’icône de thread en cours. Vous allez déplacer l’icône de thread actuel vers un autre thread, mais vous devrez le remettre lorsque vous avez terminé. 
  
3.  Cliquez sur un autre thread, puis sur **basculer vers Thread**.  
  
4.  Examinez le **pile des appels** fenêtre dans l’éditeur de code source. Le contenu a été modifié.  
  
5.  Examinez le **emplacement de débogage** barre d’outils. L’icône de thread actuel a été modifié, trop.  
  
6.  Accédez à la **emplacement de débogage** barre d’outils. Sélectionnez un thread différent de la **Thread** liste.  
  
7.  Examinez le **Threads** fenêtre. L’icône de thread actuel a changé.  
  
8. Dans l’éditeur de code source, cliquez sur un marqueur de thread. Dans le menu contextuel, pointez sur **basculer vers Thread** et cliquez sur un numéro d’ID/nom de thread.  
  
     Vous avez maintenant vu trois manières de modifier l’icône de thread actuel vers un autre thread : à l’aide de la **Threads** fenêtre, le **Thread** liste dans le **emplacement de débogage** barre d’outils et le marqueur de thread dans l’éditeur de code source.  
  
     Avec le marqueur de thread, vous pouvez basculer uniquement vers les threads sont arrêtés à cet emplacement précis. À l’aide de la **Threads** fenêtre et **emplacement de débogage** barre d’outils, que vous pouvez basculer vers n’importe quel thread.   
  
## <a name="see-also"></a>Voir aussi  
 [Déboguer les Applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Guide pratique pour basculer vers un autre thread pendant un débogage](../debugger/how-to-switch-to-another-thread-while-debugging.md)
