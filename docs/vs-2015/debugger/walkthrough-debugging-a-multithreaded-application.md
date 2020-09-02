---
title: 'Procédure pas à pas : débogage d’une application multithread | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 33ce391523a256bcb195deccf0c14868b5eae707
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683093"
---
# <a name="walkthrough-debugging-a-multithreaded-application"></a>Procédure pas à pas : débogage d'une application multithread
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] fournit une fenêtre de **Threads** améliorée et d’autres améliorations de l’interface utilisateur pour faciliter le débogage d’applications multithread. Cette procédure pas à pas ne prend que quelques minutes. Elle permet de se familiariser avec la nouvelle interface de débogage des applications multithread.  
  
 Pour commencer cette procédure pas à pas, vous avez besoin d'un projet d'application multithread. Pour créer ce projet, procédez comme suit.  
  
#### <a name="to-create-the-walkthrough-project"></a>Pour créer le projet de procédure pas à pas  
  
1. Dans le menu **fichier** , choisissez **nouveau** , puis cliquez sur **projet**.  
  
     La boîte de dialogue **Nouveau projet** apparaît.  
  
2. Dans la zone **type de projet**, cliquez sur la langue de votre choix : **Visual Basic**, **Visual C#** ou **Visual C++**.  
  
3. Dans la zone **modèles** , choisissez **application console** ou **application console CLR**.  
  
4. Dans la zone **nom** , tapez le nom MyThreadWalkthroughApp.  
  
5. Cliquez sur **OK**.  
  
     Un nouveau projet console s'affiche. Lorsque le projet a été créé, un fichier source s'affiche. En fonction du langage choisi, le fichier source peut être nommé Module1.vb, Program.cs ou MyThreadWalkthroughApp.cpp  
  
6. Supprimez le code qui apparaît dans le fichier source et remplacez-le par l’exemple de code qui apparaît dans la section « création d’un thread » de la rubrique [création de threads et passage de données à l’heure de début](https://msdn.microsoft.com/library/52b32222-e185-4f42-91a7-eaca65c0ab6d).  
  
7. Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
#### <a name="to-begin-the-walkthrough"></a>Pour démarrer la procédure pas à pas  
  
- Dans la fenêtre source, recherchez le code suivant :  
  
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
  
#### <a name="to-start-debugging"></a>Pour commencer le débogage  
  
1. Cliquez avec le bouton droit sur l' `Console.WriteLine` instruction, pointez sur **point d’arrêt** , puis cliquez sur Insérer un **point d’arrêt**.  
  
     Une bille rouge apparaît au niveau de la reliure située sur le côté gauche de la fenêtre source. Cette bille indique qu'un point d'arrêt est désormais défini à cet emplacement.  
  
2. Dans le menu **Déboguer** , cliquez sur **Démarrer le débogage**.  
  
     Le débogage démarre, votre application console se lance puis s'interrompt au point d'arrêt.  
  
3. Si, à ce stade, la fenêtre d'application console a le focus, cliquez dans la fenêtre [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour retourner le focus à [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4. Dans la fenêtre source, localisez la ligne qui contient le code suivant :  
  
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
  
1. Cliquez avec le bouton droit dans la fenêtre **Threads** , puis cliquez sur **afficher les threads dans la source**.  
  
2. Examinez la reliure située sur le côté gauche de la fenêtre. Une icône ressemblant à un maillage s'affiche sur cette ligne. Un des threads est rouge et l'autre est bleu. Le marqueur de thread indique qu'un thread est interrompu à cet emplacement. Le thread s'interrompt peut-être à cet emplacement.  
  
3. Placez le pointeur sur le marqueur de thread. Un DataTip apparaît. Le DataTip vous indique le nom et le numéro d'ID de thread de chaque thread interrompu. Dans ce cas, il n'existe qu'un seul thread dont le nom est probablement `<noname>`.  
  
4. Cliquez avec le bouton droit sur le marqueur de thread. Notez les choix dans le menu contextuel.  
  
   Cette icône est un *marqueur de thread*:  
  
   ![Marqueur de thread](../debugger/media/threadmarker.gif "ThreadMarker")  
  
## <a name="flagging-and-unflagging-threads"></a>Ajout et suppression d'indicateur de threads  
 Dans [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)], vous pouvez indiquer les threads auxquels vous souhaitez accorder une attention particulière. Le signalement des threads vous permet de suivre les threads importants et d'ignorer ceux de moindre importance.  
  
#### <a name="to-flag-threads"></a>Pour ajouter des indicateurs de thread  
  
1. Dans le menu **affichage** , pointez sur **barres d’outils**.  
  
     Assurez-vous que la barre d’outils **emplacement de débogage** est sélectionnée.  
  
2. Accédez à la barre d’outils **emplacement de débogage** et cliquez sur la liste **thread** .  
  
    > [!NOTE]
    > Vous pouvez reconnaître cette barre d’outils par trois listes principales : **processus**, **thread**et **Frame de pile**.  
  
3. Notez le nombre de threads qui s'affichent dans la liste.  
  
4. Revenez à la fenêtre source et cliquez à nouveau avec le bouton droit sur le marqueur de **thread** .  
  
5. Dans le menu contextuel, pointez sur **indicateur**, puis cliquez sur le nom et le numéro d’ID du thread.  
  
6. Revenez à la barre d’outils **emplacement de débogage** , puis cliquez à nouveau sur la liste **thread** .  
  
     Seul le thread avec indicateur s'affiche désormais dans la liste. Bouton d’indicateur situé juste à droite de la liste des **Threads** . L'icône d'indicateur du bouton était grisée. Il est désormais rouge clair.  
  
7. Placez le pointeur sur l'icône de l'indicateur.  
  
     Un menu contextuel s'affiche. Cette fenêtre contextuelle indique le mode dans lequel se trouve la liste des **Threads** : **afficher uniquement les threads avec indicateur**.  
  
8. Cliquez sur le bouton indicateur pour revenir en arrière et **Afficher tous les threads** en mode.  
  
9. Cliquez à nouveau sur la liste des **Threads** et vérifiez que vous pouvez à présent afficher à nouveau tous les threads.  
  
10. Cliquez sur le bouton indicateur pour revenir en arrière et **afficher uniquement les threads avec indicateur**.  
  
11. Dans le menu **Déboguer**, pointez sur **Fenêtres**, puis cliquez sur **Threads**.  
  
     La fenêtre **Threads** s’affiche. Un thread possède une icône d'indicateur apparente qui lui est associée.  
  
12. Dans la fenêtre source, cliquez de nouveau avec le bouton droit sur le marqueur de thread.  
  
     Notez les choix disponibles dans le menu contextuel. Au lieu d’un **indicateur**, vous voyez maintenant **Supprimer l’indicateur**. Ne cliquez pas sur **Supprimer l’indicateur**.  
  
13. Accédez à la procédure suivante relative à la suppression des threads.  
  
#### <a name="to-unflag-threads"></a>Pour supprimer l'indicateur de threads  
  
1. Dans la fenêtre **Threads** , cliquez avec le bouton droit sur la ligne correspondant au thread avec indicateur.  
  
     Un menu contextuel s'affiche. Il possède des options pour **Supprimer l’indicateur** et supprimer l' **indicateur**.  
  
2. Pour supprimer l’indicateur de thread, cliquez sur **Supprimer l’indicateur**.  
  
3. Cliquez sur l'icône d'indicateur rouge.  
  
4. Examinez à nouveau la barre d’outils **emplacement de débogage** . Le bouton indicateur est de nouveau grisé. Vous avez supprimé l'indicateur du seul thread avec indicateur. Étant donné qu’il n’existe aucun thread avec indicateur, la barre d’outils est revenue à l' **affichage de tous les threads** en mode. Cliquez sur la liste **thread** et vérifiez que vous pouvez voir tous les threads.  
  
5. Revenez à la fenêtre **Threads** et examinez les colonnes d’informations.  
  
     Dans la partie supérieure de chaque colonne, le nom de la majorité des boutons permet d'identifier la colonne. Cependant, la première colonne de gauche ne comporte aucun titre. Elle contient une icône qui correspond au contour d'un indicateur. Notez que le contour est identique pour chaque ligne de la liste de thread. Le contour indique que le thread est sans indicateur.  
  
6. Cliquez sur le contour des indicateurs du second et du troisième threads en partant de la fin de la liste.  
  
     Les contours vides deviennent des icônes d'indicateur unies rouge.  
  
7. Cliquez sur le bouton en haut de la colonne d'indicateurs.  
  
     L'ordre de la liste de threads a été modifié lorsque vous avez cliqué sur le bouton. La liste de threads est maintenant triée et les threads avec indicateur sont situés en haut de la liste.  
  
8. Cliquez de nouveau sur le bouton en haut de la colonne d'indicateurs.  
  
     L'ordre de tri a encore changé.  
  
## <a name="more-about-the-threads-window"></a>En savoir plus sur la fenêtre Threads  
  
#### <a name="to-learn-more-about-the-threads-window"></a>Pour en savoir plus sur la fenêtre Threads  
  
1. Dans la fenêtre **Threads** , examinez la troisième colonne à partir de la gauche. Le bouton en haut de cette colonne indique **ID**.  
  
2. Cliquez sur **ID**.  
  
     La liste de threads est maintenant triée par numéro d'ID de thread.  
  
3. Cliquez avec le bouton droit sur un thread de la liste. Dans le menu contextuel, cliquez sur **affichage hexadécimal**.  
  
     Le format des numéros d'ID de thread se modifie.  
  
4. Placez le pointeur de la souris sur un thread de la liste.  
  
     Un DataTip s'affiche peu après. Il représente une pile des appels partielle du thread.  
  
5. Examinez la quatrième colonne à partir de la gauche, qui est intitulée **Category**. Les threads sont classés dans des catégories.  
  
     Le premier thread créé dans un processus correspond au thread principal. Localisez-le dans la liste de threads.  
  
6. Cliquez avec le bouton droit sur le thread principal, puis cliquez sur **basculer vers le thread**.  
  
     Une boîte de dialogue d’avertissement apparaît. Elle vous indique que [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ne peut pas afficher le code source du thread principal.  
  
     Cliquez sur **OK**.  
  
7. Examinez la fenêtre **pile des appels** et la barre d’outils emplacement de **débogage** .  
  
     Le contenu de la fenêtre **pile des appels** a changé.  
  
## <a name="switching-the-active-thread"></a>Basculement du Thread actif  
  
#### <a name="to-switch-threads"></a>Pour basculer les threads  
  
1. Dans la fenêtre **Threads** , examinez la deuxième colonne à partir de la gauche. Le bouton en haut de cette colonne ne comporte aucun texte ou icône. Cette colonne est la colonne de **threads actifs** .  
  
2. Examinez la colonne **thread active** et remarquez qu’un thread a une flèche jaune. Il s’agit de l' *indicateur de thread actif*.  
  
3. Notez le numéro d'ID du thread dans lequel se trouve l'indicateur de thread actif. Vous allez déplacer l'indicateur de thread actif vers un autre thread, mais vous devrez le remettre à sa place lorsque vous aurez fini.  
  
4. Cliquez avec le bouton droit sur un autre thread, puis cliquez sur **basculer vers le thread**.  
  
5. Examinez la fenêtre **pile des appels** dans la fenêtre source. Le contenu a été modifié.  
  
6. Examinez la barre d’outils **emplacement de débogage** . Le thread actif a également été modifié.  
  
7. Accédez à la barre d’outils **emplacement de débogage** . Cliquez sur la zone **thread** et choisissez un autre thread dans la liste déroulante.  
  
8. Examinez la fenêtre **Threads** . L'indicateur de thread actif a également été modifié.  
  
9. Dans la fenêtre source, cliquez avec le bouton droit sur un marqueur de thread. Dans le menu contextuel, pointez sur **basculer vers** , puis cliquez sur le nom/ID du thread.  
  
     Vous avez maintenant vu trois façons de modifier le thread actif : à l’aide de la fenêtre **Threads** , de la zone **thread** dans la barre d’outils d' **emplacement de débogage** et de l’indicateur de thread dans la fenêtre source.  
  
     L'indicateur de thread vous permet de basculer uniquement vers les threads interrompus à cet emplacement précis. La fenêtre **Threads** et la barre d’outils **Emplacement de débogage** vous permettent de basculer vers n’importe quel thread.  
  
## <a name="freezing-and-thawing-thread-execution"></a>Gel et libération de l'exécution de thread  
  
#### <a name="to-freeze-and-unfreeze-threads"></a>Pour figer et dégeler les threads  
  
1. Dans la fenêtre **Threads** , cliquez avec le bouton droit sur n’importe quel thread, puis cliquez sur **figer**.  
  
2. Observez la colonne de threads actifs. Les deux barres verticales y sont maintenant affichées. Ces barres bleues indiquent que le thread est figé.  
  
3. Examinez la colonne **suspendre** . Le compteur de suspension du thread est désormais à 1.  
  
4. Cliquez avec le bouton droit sur le thread figé, puis cliquez sur **libérer**.  
  
     La colonne de thread active et la colonne de **suspension** changent.  
  
## <a name="see-also"></a>Voir aussi  
 [Déboguer des applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Comment : basculer vers un autre thread pendant le débogage](../debugger/how-to-switch-to-another-thread-while-debugging.md)
