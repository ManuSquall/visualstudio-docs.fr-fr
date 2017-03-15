---
title: "Comment&#160;: utiliser la fen&#234;tre Threads | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.threads"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "threads (Visual Studio), débogage"
  - "Thread.Name (propriété)"
  - "débogueur, fenêtre Threads"
  - "SetThreadName (fonction)"
  - "Threads (fenêtre)"
  - "@TIB"
  - "débogage (Visual Studio), threads"
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
caps.latest.revision: 44
caps.handback.revision: 44
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment&#160;: utiliser la fen&#234;tre Threads
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans la fenêtre **Threads**, vous pouvez visualiser et utiliser les threads de l'application que vous déboguez.  
  
 La fenêtre **Threads** contient un tableau où chaque ligne représente un thread de votre application.  Par défaut, ce tableau répertorie tous les threads de votre application, mais vous pouvez filtrer la liste de façon à afficher uniquement les threads qui vous intéressent.  Chaque colonne contient un type d'informations différent.  Vous pouvez également masquer certaines colonnes.  Si vous affichez toutes les colonnes, les informations suivantes s'affichent, de gauche à droite :  
  
-   La colonne d'indicateur, où vous pouvez marquer un thread auquel vous souhaitez apporter une attention spéciale.  Pour plus d'informations sur la façon de signaler un thread, consultez [Comment : ajouter et supprimer les indicateurs des threads](../Topic/How%20to:%20Flag%20and%20Unflag%20Threads.md).  
  
-   La colonne de thread active, où une flèche jaune indique un thread actif.  Un contour de flèche indique le thread où l'exécution s'est arrêtée dans le débogueur.  
  
-   La colonne **ID**, qui contient le numéro d'identification de chaque thread.  
  
-   La colonne **ID managé**, qui contient les numéros d'identification managés des threads managés.  
  
-   La colonne **Catégorie**, qui classe les threads en tant que threads d'interface utilisateur, gestionnaires d'appel de procédure distante ou threads de travail.  Une catégorie spéciale identifie le thread principal de l'application.  
  
-   La colonne **Nom**, qui identifie chaque thread par son nom, s'il en a un, ou en tant que \<Sans nom\>.  
  
-   La colonne **Emplacement**, qui indique où le thread s'exécute.  Vous pouvez développer cet emplacement de façon à afficher l'ensemble de la pile des appels du thread.  
  
-   La colonne **Priorité**, qui contient la priorité ou précédence que le système a assignée à chaque thread.  
  
-   La colonne **Masque d'affinité**, qui est une colonne avancée généralement masquée.  Cette colonne indique le masque d'affinité de processeur pour chaque thread.  Dans un système multiprocesseurs, le masque d'affinité détermine les processeurs sur lesquels un thread peut s'exécuter.  
  
-   La colonne **Compteur suspendu**, qui contient le compteur suspendu.  Ce compteur détermine si un thread peut s'exécuter.  Pour obtenir une explication sur le compteur suspendu, consultez « Gel et libération des threads » plus loin dans cette rubrique.  
  
-   La colonne **Nom du processus**, qui contient le processus auquel chaque thread appartient.  Cette colonne peut être utile lorsque vous déboguez plusieurs processus, mais elle est généralement masquée.  
  
### Pour afficher la fenêtre Threads en mode arrêt ou en mode exécution  
  
-   Dans le menu **Déboguer**, pointez sur **Fenêtres**, puis cliquez sur **Threads**.  
  
### Pour afficher ou masquer une colonne  
  
-   Dans la barre d'outils en haut de la fenêtre **Threads**, cliquez sur **Colonnes**, puis activez ou désactivez le nom de la colonne que vous souhaitez afficher ou masquer.  
  
### Pour basculer le thread actif  
  
-   Effectuez l'une des étapes suivantes :  
  
    -   Double\-cliquez sur un thread.  
  
    -   Cliquez avec le bouton droit sur un thread, puis cliquez sur **Basculer vers le thread**.  
  
         La flèche jaune s'affiche en regard du nouveau thread actif.  Un contour gris de flèche identifie le thread où l'exécution s'est arrêtée dans le débogueur.  
  
## Regroupement et tri de threads  
 Lorsque vous regroupez des threads, un titre s'affiche dans le tableau pour chaque groupe.  Ce titre contient une description du groupe, telle que « Thread de travail » ou « Threads sans indicateur », ainsi qu'un contrôle d'arborescence.  Les threads membres de chaque groupe apparaissent sous le titre approprié.  Si vous souhaitez masquer les threads membres d'un groupe, vous pouvez utiliser le contrôle d'arborescence pour réduire ce groupe.  
  
 Étant donné que le regroupement est prioritaire sur le tri, vous pouvez grouper des threads par catégorie, par exemple, puis les trier par ID dans chaque catégorie.  
  
#### Pour trier des threads  
  
1.  Dans la barre d'outils en haut de la fenêtre **Threads**, cliquez sur le bouton situé au\-dessus de l'une des colonnes.  
  
     Les threads sont alors triés en fonction des valeurs de la colonne choisie.  
  
2.  Si vous souhaitez inverser l'ordre de tri, cliquez de nouveau sur le bouton.  
  
     Les threads qui figuraient au début de la liste s'affichent maintenant à la fin.  
  
#### Pour regrouper des threads  
  
-   Dans la barre d'outils de la fenêtre **Threads**, cliquez sur la liste **Grouper par**, puis sur le critère souhaité pour le regroupement des threads.  
  
#### Pour trier des threads au sein de groupes  
  
1.  Dans la barre d'outils en haut de la fenêtre **Threads**, cliquez sur la liste **Grouper par**, puis sur le critère souhaité pour le regroupement des threads.  
  
2.  Dans la fenêtre **Threads**, cliquez sur le bouton situé au\-dessus des colonnes.  
  
     Les threads sont alors triés en fonction des valeurs de la colonne choisie.  
  
#### Pour développer ou réduire tous les groupes  
  
-   Dans la barre d'outils en haut de la fenêtre **Threads**, cliquez sur **Développer les groupes** ou **Réduire les groupes**.  
  
## Recherche de threads spécifiques  
 Dans [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], vous pouvez rechercher des threads qui correspondent à une chaîne spécifiée.  Lorsque vous recherchez des threads dans la fenêtre **Threads**, celle\-ci affiche tous les threads qui correspondent à la chaîne recherchée dans toute colonne.  Ces informations incluent l'emplacement de thread qui s'affiche en haut de la pile des appels dans la colonne **Emplacement**.  Par défaut, cependant, la recherche ne porte pas sur l'ensemble de la pile des appels.  
  
#### Pour rechercher des threads spécifiques  
  
-   Dans la barre d'outils en haut de la fenêtre **Threads**, accédez à la zone **Rechercher** et effectuez l'une des opérations suivantes :  
  
    -   Tapez une chaîne recherchée et appuyez sur ENTRÉE.  
  
         \- ou \-  
  
    -   Cliquez dans la liste déroulante en regard de la zone **Rechercher** et sélectionnez une chaîne d'une recherche précédente.  
  
-   \(Facultatif\) Pour inclure l'ensemble de la pile des appels dans la recherche, sélectionnez **Rechercher la pile des appels**.  
  
## Gel et libération des threads  
 Lorsque vous gelez un thread, le système ne démarre pas son exécution même si les ressources sont disponibles.  
  
 En code natif, vous pouvez interrompre ou reprendre des threads en appelant les fonctions Windows `SuspendThread` et `ResumeThread` ou les fonctions MFC [CWinThread::SuspendThread](../Topic/CWinThread::SuspendThread.md) et [CWinThread::ResumeThread](../Topic/CWinThread::ResumeThread.md).  Si vous appelez `SuspendThread` ou `ResumeThread`, vous modifiez le *compteur suspendu*, qui s'affiche dans la fenêtre **Threads**.  Toutefois, si vous gelez ou libérez un thread natif, vous ne changez pas le compteur suspendu.  En code natif, un thread ne peut pas s'exécuter sauf s'il est libéré et que son compteur suspendu est égal à zéro.  
  
 En code managé, le gel ou la libération d'un thread modifie le compteur suspendu.  En code managé, un thread gelé possède un compteur suspendu de 1.  En code natif, un thread gelé possède un compteur suspendu de 0, à moins qu'il ait été interrompu par un appel `SuspendThread`.  
  
> [!NOTE]
>  Lors du débogage d'un appel entre code natif et code managé, le code managé s'exécute dans le même thread physique que le code natif qui l'a appelé.  Si vous suspendez ou figez le thread natif, le code managé sera également figé.  
  
#### Pour geler ou libérer l'exécution d'un thread  
  
-   Dans la barre d'outils en haut de la fenêtre **Threads**, cliquez sur **Figer les threads** ou **Libérer les threads**.  
  
     Cette action affecte uniquement les threads sélectionnés dans la fenêtre **Threads**.  
  
## Affichage des threads avec indicateur  
 Vous pouvez signaler un thread auquel vous souhaitez accorder une attention particulière en le marquant avec une icône dans la fenêtre **Threads**.  Pour plus d'informations, consultez [Comment : ajouter et supprimer les indicateurs des threads](../Topic/How%20to:%20Flag%20and%20Unflag%20Threads.md).  Dans la fenêtre Threads, vous pouvez choisir d'afficher tous les threads ou uniquement les threads avec indicateur.  
  
#### Pour afficher seulement les threads avec indicateur  
  
-   Cliquez sur le bouton indicateur dans le coin supérieur gauche de la fenêtre **Threads**.  
  
## Affichage des piles d'appel de thread et commutation entre les frames  
 Dans un programme multithread, chaque thread possède sa propre pile d'appel.  La fenêtre **Threads** permet d'afficher facilement ces piles.  
  
#### Pour afficher la pile d'appel d'un thread  
  
-   Dans la colonne **Emplacement**, cliquez sur le triangle inversé en regard de l'emplacement de thread.  
  
     L'emplacement se développe pour indiquer la pile des appels du thread.  
  
#### Pour afficher ou réduire les piles d'appels de tous les threads  
  
-   Dans la barre d'outils en haut de la fenêtre **Threads**, cliquez sur **Développer la pile des appels** ou **Réduire la pile des appels**.  
  
## Voir aussi  
 [Déboguer les applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Procédure pas à pas : débogage d'une application multithread](../debugger/walkthrough-debugging-a-multithreaded-application.md)