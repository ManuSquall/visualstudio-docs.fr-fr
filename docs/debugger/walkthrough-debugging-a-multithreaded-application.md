---
title: "Proc&#233;dure pas &#224; pas&#160;: d&#233;bogage d&#39;une application multithread | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "débogage multithread, procédure pas à pas"
  - "procédures pas à pas, débogage multithread"
ms.assetid: 590ffd57-0556-43d8-8962-ee27e5b2b7d7
caps.latest.revision: 38
caps.handback.revision: 38
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Proc&#233;dure pas &#224; pas&#160;: d&#233;bogage d&#39;une application multithread
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] dispose d'une fenêtre **Threads** améliorée et d'autres améliorations de l'interface utilisateur facilitant le débogage d'applications multithread.  Cette procédure pas à pas ne prend que quelques minutes. Elle permet de se familiariser avec la nouvelle interface de débogage des applications multithread.  
  
 Pour commencer cette procédure pas à pas, vous avez besoin d'un projet d'application multithread.  Pour créer ce projet, procédez comme suit.  
  
#### Pour créer le projet de procédure pas à pas  
  
1.  Dans le menu **Fichier**, sélectionnez **Nouveau**, puis cliquez sur **Projet**.  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
2.  Dans la zone **Types de projets**, cliquez sur le langage de votre choix : **Visual Basic**, **Visual C\#** ou **Visual C\+\+**.  
  
3.  Dans la zone **Modèles**, sélectionnez **Application console** ou **Application console CLR**.  
  
4.  Dans la zone **Nom**, entrez le nom MyThreadWalkthroughApp.  
  
5.  Cliquez sur **OK**.  
  
     Un nouveau projet console s'affiche.  Lorsque le projet a été créé, un fichier source s'affiche.  En fonction du langage choisi, le fichier source peut être nommé Module1.vb, Program.cs ou MyThreadWalkthroughApp.cpp  
  
6.  Supprimez le code qui apparaît dans le fichier source et remplacez\-le par l'exemple de code de la section "Création d'un Thread" dans la rubrique [Creating Threads and Passing Data at Start Time](../Topic/Creating%20Threads%20and%20Passing%20Data%20at%20Start%20Time.md).  
  
7.  Dans le menu **Fichier**, cliquez sur **Enregistrer tout**.  
  
#### Pour démarrer la procédure pas à pas  
  
-   Dans la fenêtre source, recherchez le code suivant :  
  
    ```vb  
    Thread.Sleep(3000)   
    Console.WriteLine(  
    ```  
  
```c#  
Thread.Sleep(3000);  
Console.WriteLine();  
```  
  
```cpp  
Thread::Sleep(3000);  
Console.WriteLine();  
```  
  
#### Pour démarrer le débogage  
  
1.  Cliquez avec le bouton droit sur l'instruction `Console.WriteLine`, pointez sur **Point d'arrêt**, puis cliquez sur **Insérer un point d'arrêt**.  
  
     Une bille rouge apparaît au niveau de la reliure située sur le côté gauche de la fenêtre source.  Cette bille indique qu'un point d'arrêt est désormais défini à cet emplacement.  
  
2.  Dans le menu **Déboguer**, cliquez sur **Démarrer le débogage**.  
  
     Le débogage démarre, votre application console se lance puis s'interrompt au point d'arrêt.  
  
3.  Si, à ce stade, la fenêtre d'application console a le focus, cliquez dans la fenêtre [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour retourner le focus à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  Dans la fenêtre source, localisez la ligne qui contient le code suivant :  
  
    ```vb  
    Thread.Sleep(5000)   
    ```  
  
```c#  
Thread.Sleep(3000);  
```  
  
```cpp  
Thread::Sleep(3000);  
```  
  
#### Pour découvrir le marqueur de thread  
  
1.  Cliquez avec le bouton droit dans la fenêtre **Threads**, puis cliquez sur **Afficher les threads dans la source**.  
  
2.  Examinez la reliure située sur le côté gauche de la fenêtre.  Une icône ressemblant à un maillage s'affiche sur cette ligne.  Un des threads est rouge et l'autre est bleu.  Le marqueur de thread indique qu'un thread est interrompu à cet emplacement.  Le thread s'interrompt peut\-être à cet emplacement.  
  
3.  Placez le pointeur sur le marqueur de thread.  Un DataTip apparaît.  Le DataTip vous indique le nom et le numéro d'ID de thread de chaque thread interrompu.  Dans ce cas, il n'existe qu'un seul thread dont le nom est probablement `<noname>`.  
  
4.  Cliquez avec le bouton droit sur le marqueur de thread.  Notez les choix dans le menu contextuel.  
  
 Cette icône est un *marqueur de thread* :  
  
 ![Marqueur de thread](../debugger/media/threadmarker.png "ThreadMarker")  
  
## Ajout et suppression d'indicateur de threads  
 Dans [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)], vous pouvez indiquer les threads auxquels vous souhaitez accorder une attention particulière.  Le signalement des threads vous permet de suivre les threads importants et d'ignorer ceux de moindre importance.  
  
#### Pour ajouter des indicateurs de thread  
  
1.  Dans le menu **Affichage**, pointez sur **Barres d'outils**.  
  
     Assurez\-vous que la barre d'outils **Emplacement de débogage** est sélectionnée.  
  
2.  Allez à la barre d'outils **Emplacement de débogage**, puis cliquez sur la liste **Thread**.  
  
    > [!NOTE]
    >  Cette barre d'outils se compose de trois listes principales : **Processus**, **Thread** et **Frame de pile**.  
  
3.  Notez le nombre de threads qui s'affichent dans la liste.  
  
4.  Revenez à la fenêtre source, puis cliquez de nouveau avec le bouton droit sur le marqueur de **Thread**.  
  
5.  Dans le menu contextuel, pointez sur **Signaler l'indicateur**, puis cliquez sur le nom et le numéro d'ID du thread.  
  
6.  Revenez à la barre d'outils **Emplacement de débogage**, puis cliquez de nouveau sur la liste **Thread**.  
  
     Seul le thread avec indicateur s'affiche désormais dans la liste.  Le bouton indicateur situé à droite de la liste **Thread**.  L'icône d'indicateur du bouton était grisée.  Il est désormais rouge clair.  
  
7.  Placez le pointeur sur l'icône de l'indicateur.  
  
     Un menu contextuel s'affiche.  Ce menu contextuel vous indique le mode de la liste **Thread** dans **Afficher uniquement les threads avec indicateur**.  
  
8.  Cliquez sur le bouton indicateur pour revenir au mode **Afficher tous les threads**.  
  
9. Cliquez de nouveau sur la liste **Thread** et vérifiez que vous pouvez visualiser de nouveau tous les threads.  
  
10. Cliquez sur le bouton indicateur pour revenir au mode **Afficher uniquement les threads avec indicateur**.  
  
11. Dans le menu **Déboguer**, pointez sur **Fenêtres**, puis cliquez sur **Threads**.  
  
     La fenêtre **Threads** s'affiche.  Un thread possède une icône d'indicateur apparente qui lui est associée.  
  
12. Dans la fenêtre source, cliquez de nouveau avec le bouton droit sur le marqueur de thread.  
  
     Notez les choix disponibles dans le menu contextuel.  Au lieu de **Signaler l'indicateur**, vous visualisez maintenant **Supprimer l'indicateur**.  Ne cliquez pas sur **Supprimer l'indicateur**.  
  
13. Accédez à la procédure suivante relative à la suppression des threads.  
  
#### Pour supprimer l'indicateur de threads  
  
1.  Dans la fenêtre **Threads**, cliquez avec le bouton droit sur la ligne correspondante au thread avec indicateur.  
  
     Un menu contextuel s'affiche.  Il contient les options **Supprimer l'indicateur** et **Supprimer tous les indicateurs**.  
  
2.  Pour supprimer l'indicateur de thread, cliquez sur **Supprimer l'indicateur**.  
  
3.  Cliquez sur l'icône d'indicateur rouge.  
  
4.  Consultez de nouveau la barre d'outils **Emplacement de débogage**.  Le bouton indicateur est de nouveau grisé.  Vous avez supprimé l'indicateur du seul thread avec indicateur.  Comme il n'y a plus aucun thread avec indicateur, la barre d'outils est revenue en mode **Afficher tous les threads**.  Cliquez sur la liste **Thread** et vérifiez que vous pouvez visualiser tous les threads.  
  
5.  Revenez à la fenêtre **Threads** et examinez les colonnes d'informations.  
  
     Dans la partie supérieure de chaque colonne, le nom de la majorité des boutons permet d'identifier la colonne.  Cependant, la première colonne de gauche ne comporte aucun titre.  Elle contient une icône qui correspond au contour d'un indicateur.  Notez que le contour est identique pour chaque ligne de la liste de thread.  Le contour indique que le thread est sans indicateur.  
  
6.  Cliquez sur le contour des indicateurs du second et du troisième threads en partant de la fin de la liste.  
  
     Les contours vides deviennent des icônes d'indicateur unies rouge.  
  
7.  Cliquez sur le bouton en haut de la colonne d'indicateurs.  
  
     L'ordre de la liste de threads a été modifié lorsque vous avez cliqué sur le bouton.  La liste de threads est maintenant triée et les threads avec indicateur sont situés en haut de la liste.  
  
8.  Cliquez de nouveau sur le bouton en haut de la colonne d'indicateurs.  
  
     L'ordre de tri a encore changé.  
  
## En savoir plus sur la fenêtre Threads  
  
#### Pour en savoir plus sur la fenêtre Threads  
  
1.  Dans la fenêtre **Threads**, examinez la troisième colonne en partant de la gauche.  Le bouton en haut de cette colonne indique l'**ID**.  
  
2.  Cliquez sur **ID**.  
  
     La liste de threads est maintenant triée par numéro d'ID de thread.  
  
3.  Cliquez avec le bouton droit sur un thread de la liste.  Dans le menu contextuel, cliquez sur **Affichage hexadécimal**.  
  
     Le format des numéros d'ID de thread se modifie.  
  
4.  Placez le pointeur de la souris sur un thread de la liste.  
  
     Un DataTip s'affiche peu après.  Il représente une pile des appels partielle du thread.  
  
5.  Examinez la quatrième colonne en partant de la gauche, appelée **Catégorie**.  Les threads sont classés dans des catégories.  
  
     Le premier thread créé dans un processus correspond au thread principal.  Localisez\-le dans la liste de threads.  
  
6.  Cliquez avec le bouton droit sur le thread principal, puis sur **Basculer vers le Thread**.  
  
     Une boîte de dialogue d'avertissement s'affiche.  Elle vous indique que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ne peut pas afficher le code source du thread principal.  
  
     Cliquez sur **OK**.  
  
7.  Examinez la fenêtre **Pile des appels** ainsi que la barre d'outils **Emplacement de débogage**.  
  
     Le contenu de la fenêtre **Pile des appels** a été modifié.  
  
## Basculement du Thread actif  
  
#### Pour basculer les threads  
  
1.  Dans la fenêtre **Threads**, examinez la deuxième colonne en partant de la gauche.  Le bouton en haut de cette colonne ne comporte aucun texte ou icône.  Cette colonne correspond à la colonne **Thread actif**.  
  
2.  Examinez la colonne **Thread actif** et notez qu'un thread comporte une flèche jaune.  Il s'agit de l'*indicateur de thread actif*.  
  
3.  Notez le numéro d'ID du thread dans lequel se trouve l'indicateur de thread actif.  Vous allez déplacer l'indicateur de thread actif vers un autre thread, mais vous devrez le remettre à sa place lorsque vous aurez fini.  
  
4.  Cliquez avec le bouton droit sur un autre thread puis sur **Basculer vers le Thread**.  
  
5.  Observez la fenêtre **Pile des appels** dans la fenêtre source.  Le contenu a été modifié.  
  
6.  Examinez la barre d'outils **Emplacement de débogage**.  Le thread actif a également été modifié.  
  
7.  Accédez à la barre d'outils **Emplacement de débogage**.  Cliquez sur la zone **Thread**, puis sélectionnez un thread différent dans la liste déroulante.  
  
8.  Observez la fenêtre **Threads**.  L'indicateur de thread actif a également été modifié.  
  
9. Dans la fenêtre source, cliquez avec le bouton droit sur un marqueur de thread.  Dans le menu contextuel, pointez sur **Basculer vers**, puis cliquez sur le nom et le numéro d'ID d'un thread.  
  
     Trois manières de modifier le thread actif vous ont été présentées : à l'aide de la fenêtre **Threads**, de la zone **Thread** dans la barre d'outils **Emplacement de débogage** et à l'aide de l'indicateur de thread dans la fenêtre source.  
  
     L'indicateur de thread vous permet de basculer uniquement vers les threads interrompus à cet emplacement précis.  La fenêtre **Threads** et la barre d'outils **Emplacement de débogage** vous permettent de basculer vers tous les threads.  
  
## Gel et libération de l'exécution de thread  
  
#### Pour figer et dégeler les threads  
  
1.  Dans la fenêtre **Threads**, cliquez avec le bouton droit sur un thread, puis sur **Figer**.  
  
2.  Observez la colonne de threads actifs.  Les deux barres verticales y sont maintenant affichées.  Ces barres bleues indiquent que le thread est figé.  
  
3.  Observez la colonne **Suspendre**.  Le compteur de suspension du thread est désormais à 1.  
  
4.  Cliquez avec le bouton droit sur le thread figé, puis sur **Libérer**.  
  
     La colonne de threads actifs ainsi que la colonne **Suspendre** ont été modifiées.  
  
## Voir aussi  
 [Déboguer les applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Comment : basculer vers un autre thread pendant un débogage](../debugger/how-to-switch-to-another-thread-while-debugging.md)