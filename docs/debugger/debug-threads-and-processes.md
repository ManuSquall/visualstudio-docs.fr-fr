---
title: "Outils pour déboguer les threads et processus | Documents Microsoft"
ms.custom: 
ms.date: 04/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multiprocess debugging
- threading [Visual Studio], debugging
- processes, debugging
- debugging threads
- debugging [Visual Studio], threads
ms.assetid: 9f0c8505-b6b2-452b-adfd-076db14d8115
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad52c8f9b2580538b573eb2ef66164040ca66b25
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="tools-to-debug-threads-and-processes-in-visual-studio"></a>Outils pour déboguer les threads et processus dans Visual Studio
*Threads* et *processus* sont des concepts liés en informatique. Tous deux représentent des séquences d'instructions qui doivent s'exécuter dans un ordre spécifique. Les instructions dans des threads ou processus séparés, toutefois, peuvent s'exécuter en parallèle.  
  
 Les processus existent dans le système d'exploitation et correspondent à ce que les utilisateurs voient sous la forme de programmes ou d'applications. Un thread, en revanche, existe dans un processus. Pour cette raison, les threads sont parfois appelés *processus légers*. Chaque processus est constitué d'un ou de plusieurs threads.  
  
 L'existence de plusieurs processus permet à un ordinateur d'effectuer plusieurs tâches à la fois. L'existence de plusieurs threads permet à un processus de séparer le travail à exécuter en parallèle. Sur un ordinateur multiprocesseur, les processus ou les threads peuvent s'exécuter sur différents processeurs. Ce type d'exécution permet un véritable traitement en parallèle.  
  
 Le traitement en parallèle parfait n'est pas toujours possible. Les threads doivent parfois être synchronisés. Un thread peut attendre le résultat d'un autre thread ou un thread peut avoir besoin d'un accès exclusif à une ressource utilisée par un autre thread. Les problèmes de synchronisation sont une cause courante de bogues dans les applications multithread. Les threads attendent parfois une ressource qui n'est jamais disponible. Cela entraîne une condition appelée *blocage*.  
  
 Le débogueur [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] propose des outils performants mais faciles à utiliser pour déboguer les threads et les processus.  
  
## <a name="tools-and-features"></a>Outils et fonctionnalités
Les outils que vous devez utiliser dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] varient selon le type de code que vous essayez de déboguer :

- Pour les processus, les principaux outils sont le **attacher au processus** boîte de dialogue, la **processus** fenêtre et la **emplacement de débogage** barre d’outils.

- Pour les threads, les principaux outils de débogage de threads sont les **Threads** fenêtre, les marqueurs de thread dans les fenêtres source, **piles parallèles** fenêtre, **espion parallèle** fenêtre, et le **emplacement de débogage** barre d’outils.  
  
- Pour le code qui utilise le <xref:System.Threading.Tasks.Task> dans les [bibliothèque parallèle de tâches (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl), le [Runtime d’accès concurrentiel](/cpp/parallel/concrt/concurrency-runtime/) (code natif), les principaux outils de débogage d’applications multithread sont les **Piles parallèles** fenêtre, le **espion parallèle** fenêtre et la **tâches** fenêtre (la **tâches** fenêtre prend également en charge le Objet promise JavaScript).

- Pour déboguer des threads sur le GPU, le principal outil est la **Threads GPU** windows.  
  
 Le tableau suivant affiche les informations disponibles et les actions que vous pouvez exécuter depuis chacun de ces emplacements :  
  
|Interface utilisateur|Informations disponibles|Actions que vous pouvez effectuer|  
|--------------------|---------------------------|-----------------------------|  
|**Attacher au processus** boîte de dialogue|Processus disponibles auxquels vous pouvez attacher :<br /><br /> -Nom du processus (.exe)<br />-Numéro d’identification processus<br />-Titre de la barre de menus<br />-Type (managé v4.0 ; Managé v2.0, v1.1, v1.0 ; x86 ; x64 ; IA64)<br />-Nom d’utilisateur (nom de compte)<br />-Numéro de la session|Sélectionnez un processus auquel attacher<br /><br /> Sélectionnez un ordinateur distant<br /><br /> Modifiez le type de transport pour la connexion aux ordinateurs distants|  
|**Processus** fenêtre|Processus attachés :<br /><br /> -Nom du processus<br />-Numéro d’identification processus<br />-Chemin d’accès pour traiter .exe<br />-Titre de la barre de menus<br />-État (Break. Running)<br />-Le débogage (natif, managé et ainsi de suite.)<br />-Type (par défaut, natif sans authentification) de transport<br />-Qualificateur de transport (ordinateur distant)|Outils :<br /><br /> -Attach<br />-Détacher<br />-Terminer<br /><br /> Menu contextuel :<br /><br /> -Attach<br />-Détacher<br />-Détacher lorsque le débogage s’est arrêté<br />-Terminer|  
|**Threads** fenêtre|Threads dans le processus actuel :<br /><br /> -ID de thread<br />-ID géré<br />-Catégorie (thread principal, thread d’interface, gestionnaire d’appel de procédure distante ou thread de travail)<br />-Nom du thread<br />-Emplacement où le thread est créé<br />-Priorité<br />-Masque d’affinité<br />-Compteur suspendu<br />-Nom du processus<br />-Indicateur<br />-Indicateur suspendu|Outils :<br /><br /> -Recherche<br />-Rechercher la pile des appels<br />-Signaler uniquement mon Code<br />-Sélection de modules personnalisés indicateur<br />-Regrouper par<br />-Colonnes<br />-Pile des appels développer/réduire<br />-Développer/réduire les groupes<br />-Figer/libérer les Threads<br /><br /> Menu contextuel :<br /><br /> -Afficher les threads dans la source<br />-Basculer vers un thread<br />-Figer un thread en cours d’exécution<br />-Libérer un thread figé<br />-Indicateur d’un thread d’une étude supplémentaire<br />-Supprimer l’indicateur d’un thread<br />-Renommer un thread<br />-Permet d’afficher et masquer des threads<br /><br /> Autres actions :<br /><br /> -Permet d’afficher la pile des appels d’un thread dans un DataTip|  
|Fenêtre source|Les indicateurs de thread dans la marge de gauche signalent un ou plusieurs threads (option désactivée par défaut, activée à l’aide du menu contextuel de **Threads** fenêtre)|Menu contextuel :<br /><br /> -Basculer vers un thread<br />-Indicateur d’un thread d’une étude supplémentaire<br />-Supprimer l’indicateur d’un thread|  
|**Emplacement de débogage** barre d’outils|-Processus en cours<br />-Suspendre l’application<br />-Reprise de l’application<br />-Interrompre et quitter l’application<br />-Thread en cours<br />-Basculer l’état actuel de l’indicateur thread<br />-Afficher uniquement les threads avec indicateur<br />-Permet d’afficher uniquement les processus en cours<br />-Frame de pile actuel|-Commutateur à un autre processus<br />-Suspendre, reprendre ou arrêter l’application<br />-Basculer vers un autre thread dans le processus en cours<br />-Basculer vers un autre frame de pile dans le thread actuel<br />-Ajouter ou supprimer l’indicateur de threads actuels<br />-Afficher uniquement les threads avec indicateur<br />-Permet d’afficher uniquement le processus en cours|  
|**Parallèle piles** fenêtre|-Les piles d’appels pour plusieurs threads dans une fenêtre.<br />-Frame de pile active pour chaque thread.<br />-Appelants et appelés pour toute méthode.|-Permet de filtrer les threads spécifiés<br />-Basculer vers la vue tâches<br />-Ajouter un indicateur ou un thread<br />-Zoom|   
|**Espion parallèle** fenêtre|-La colonne d’indicateur, dans laquelle vous pouvez marquer un thread que vous souhaitez apporter une attention spéciale.<br />-La colonne de frame, dans laquelle une flèche indique le frame sélectionné.<br />-Une colonne configurable qui peut afficher les ordinateur, un processus, une vignette, une tâche et un thread.|-Ajouter un indicateur ou un thread<br />-Permet d’afficher uniquement les threads avec indicateur<br />-Basculer des frames<br />-Trier une colonne<br />-Threads groupes<br />-Figer ou libérer les threads<br />-Exporter les données dans la fenêtre Espion parallèle| 
|**Tâches** fenêtre|-Permet d’afficher des informations sur les <xref:System.Threading.Tasks.Task> objets, y compris l’ID de tâche, état de la tâche (planifié, en cours d’exécution, en attente, bloqué), et que le thread qui est assigné à la tâche.<br />-Emplacement en cours dans la pile des appels.<br />-Passé à la tâche lors de la création de délégué|-Basculer vers la tâche actuelle<br />-Indicateur ou d’une tâche<br />-Geler ou libérer une tâche|  
|**Threads GPU** fenêtre|-La colonne d’indicateur, dans laquelle vous pouvez marquer un thread que vous souhaitez apporter une attention spéciale.<br />-Thread colonne active, dans laquelle une flèche jaune indique que le thread actuel.<br />-La **le nombre de threads** colonne, qui affiche le nombre de threads au même emplacement.<br />-La **ligne** colonne, qui affiche la ligne de code où se trouve chaque groupe de threads.<br />-La **adresse** colonne qui affiche l’adresse d’instruction où chaque groupe de threads est localisé.<br />-La **emplacement** colonne, qui est l’emplacement dans le code de l’adresse.<br />-La **état** colonne, ce qui indique si le thread est actif ou bloqué.<br />-La **vignette** colonne, ce qui indique l’index de mosaïque des threads dans la ligne.|-Modifier à un autre thread.<br />-Permet d’afficher une vignette particulier et un thread<br />-Permet d’afficher ou masquer une colonne<br />-Trier par colonne<br />-Threads groupes<br />-Figer ou libérer les threads<br />-Ajouter un indicateur ou un thread<br />-Permet d’afficher uniquement les threads avec indicateur|  
  
## <a name="see-also"></a>Voir aussi  
 [Attacher au processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Débogage d’Applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Débogage du code GPU](../debugger/debugging-gpu-code.md)