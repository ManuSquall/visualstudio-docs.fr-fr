---
title: Déboguer les Threads et processus | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- multiprocess debugging
- threading [Visual Studio], debugging
- processes, debugging
- debugging threads
- debugging [Visual Studio], threads
ms.assetid: 9f0c8505-b6b2-452b-adfd-076db14d8115
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6bda70d9f99b4b97623d5d9f03ca440721f9a728
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47493059"
---
# <a name="debug-threads-and-processes"></a>Déboguer les threads et processus
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [déboguer les Threads et processus](https://docs.microsoft.com/visualstudio/debugger/debug-threads-and-processes).  
  
Threads * et *processus* sont des concepts liés en informatique. Tous deux représentent des séquences d'instructions qui doivent s'exécuter dans un ordre spécifique. Les instructions dans des threads ou processus séparés, toutefois, peuvent s'exécuter en parallèle.  
  
 Les processus existent dans le système d'exploitation et correspondent à ce que les utilisateurs voient sous la forme de programmes ou d'applications. Un thread, en revanche, existe dans un processus. Pour cette raison, les threads sont parfois appelés *processus légers*. Chaque processus est constitué d'un ou de plusieurs threads.  
  
 L’existence de plusieurs processus permet à un ordinateur d’effectuer plusieurs tâches à la fois. L'existence de plusieurs threads permet à un processus de séparer le travail à exécuter en parallèle. Sur un ordinateur multiprocesseur, les processus ou les threads peuvent s'exécuter sur différents processeurs. Ce type d'exécution permet un véritable traitement en parallèle.  
  
 Le traitement en parallèle parfait n'est pas toujours possible. Les threads doivent parfois être synchronisés. Un thread peut attendre le résultat d'un autre thread ou un thread peut avoir besoin d'un accès exclusif à une ressource utilisée par un autre thread. Les problèmes de synchronisation sont une cause courante de bogues dans les applications multithread. Les threads attendent parfois une ressource qui n'est jamais disponible. Il en résulte une condition appelée *blocage*.  
  
 Le débogueur [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] propose des outils performants mais faciles à utiliser pour déboguer les threads et les processus.  
  
## <a name="tools-for-debugging-threads-and-processes-in-visual-studio"></a>Outils pour le débogage de threads et processus dans Visual Studio  
 Les principaux outils pour des processus dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sont le **attacher au processus** boîte de dialogue, le **processus** fenêtre et le **emplacement de débogage** barre d’outils. Les principaux outils de débogage de threads sont les **Threads** fenêtre, les marqueurs de thread dans les fenêtres source et la **emplacement de débogage** barre d’outils.  
  
 Les principaux outils de débogage d’applications multithread sont les **piles parallèles** et **tâches parallèles**, **espion parallèle**, et **Threads GPU** windows.  
  
 Le tableau suivant affiche les informations disponibles et les actions que vous pouvez exécuter depuis chacun de ces emplacements :  
  
|Interface utilisateur|Informations disponibles|Actions que vous pouvez effectuer|  
|--------------------|---------------------------|-----------------------------|  
|**Attacher au processus** boîte de dialogue|Processus disponibles auxquels vous pouvez attacher :<br /><br /> -Nom du processus (.exe)<br />-Numéro d’identification processus<br />: Titre de la barre de menus<br />-Type (managé v4.0 ; Managé v2.0, v1.1, v1.0 ; x86 ; x64 ; IA64)<br />-Nom d’utilisateur (nom de compte)<br />-Numéro de session|Sélectionnez un processus auquel attacher<br /><br /> Sélectionnez un ordinateur distant<br /><br /> Modifiez le type de transport pour la connexion aux ordinateurs distants|  
|**Processus** fenêtre|Processus attachés :<br /><br /> -Nom du processus<br />-Numéro d’identification processus<br />-Chemin d’accès pour traiter .exe<br />: Titre de la barre de menus<br />-État (Break. Running)<br />-Débogage (natif, managé et ainsi de suite.)<br />-Transport de type (par défaut, natif sans authentification)<br />-Qualificateur de transport (ordinateur distant)|Outils :<br /><br /> -Attach<br />-Détacher<br />-Terminer<br /><br /> Menu contextuel :<br /><br /> -Attach<br />-Détacher<br />-Détacher lorsque le débogage est arrêté<br />-Terminer|  
|**Threads** fenêtre|Threads dans le processus actuel :<br /><br /> -ID de thread<br />-ID managé<br />-Catégorie (thread principal, thread d’interface, gestionnaire d’appel de procédure distante ou thread de travail)<br />-Nom du thread<br />-Emplacement dans lequel le thread est créé<br />-Priorité<br />-Masque d’affinité<br />-Compteur suspendu<br />-Nom du processus<br />-Indicateur<br />-Indicateur suspendu|Outils :<br /><br /> -Recherche<br />-Pile des appels recherche<br />-Signaler uniquement mon Code<br />-Sélection de modules personnalisés indicateur<br />-Regrouper par<br />-Colonnes<br />-Pile des appels développer/réduire<br />-Développer/réduire les groupes<br />-Figer/libérer les Threads<br /><br /> Menu contextuel :<br /><br /> -Afficher les threads dans la source<br />-Basculer vers un thread<br />-Figer un thread en cours d’exécution<br />-Libérer un thread figé<br />-Signaler un thread pour une étude supplémentaire<br />-Un thread sans indicateur<br />-Renommer un thread<br />-Permet d’afficher et masquer des threads<br /><br /> Autres actions :<br /><br /> -Permet d’afficher la pile des appels d’un thread dans un DataTip|  
|Fenêtre source|Indicateurs de thread dans la marge gauche signalent un ou plusieurs threads (option désactivée par défaut, activée à l’aide du menu contextuel de **Threads** fenêtre)|Menu contextuel :<br /><br /> -Basculer vers un thread<br />-Signaler un thread pour une étude supplémentaire<br />-Un thread sans indicateur|  
|**Emplacement de débogage** barre d’outils|-Processus en cours<br />-Suspendre l’application<br />-Reprendre l’application<br />-Interrompre et quitter l’application<br />-Thread actuel<br />-Activer/désactiver actuel état d’indicateur de thread<br />-Afficher uniquement les threads avec indicateur<br />-Afficher uniquement le processus actuel<br />-Frame de pile actuel|-Basculer vers un autre processus<br />-Suspendre, reprendre ou arrêter l’application<br />-Basculer vers un autre thread dans le processus en cours<br />-Basculer vers un autre frame de pile dans le thread actuel<br />-Ajouter ou supprimer l’indicateur de threads actuels<br />-Afficher uniquement les threads avec indicateur<br />-Afficher uniquement le processus en cours|  
|**Piles parallèles** fenêtre|-Piles d’appels pour plusieurs threads dans une fenêtre.<br />-Frame de pile actif pour chaque thread.<br />-Appelants et appelés pour toute méthode.|-Permet de filtrer les threads spécifiés<br />-Basculer vers la vue Tâches parallèles<br />-Ajouter ou supprimer l’indicateur d’un thread<br />-Effectuer un zoom avant|  
|**Tâches parallèles** fenêtre|-Afficher les informations <xref:System.Threading.Tasks.Task> objets y compris les ID de tâche, état de la tâche (planifié, en cours d’exécution, en attente, bloqué), et le thread qui est assigné à la tâche.<br />-Emplacement en cours dans la pile des appels.<br />-Délégué transmis à la tâche lors de la création|-Passer à la tâche actuelle<br />-Ajouter ou supprimer l’indicateur d’une tâche<br />-Permet de geler ou libérer une tâche|  
|**Espion parallèle** fenêtre|-La colonne d’indicateur, dans lequel vous pouvez marquer un thread auquel vous conseille de prêter une attention particulière à.<br />-La colonne de frame dans lequel une flèche indique le frame sélectionné.<br />-Une colonne configurable qui peut afficher la machine, le processus, la vignette, la tâche et le thread.|-Ajouter ou supprimer l’indicateur d’un thread<br />-Permet d’afficher uniquement les threads avec indicateur<br />-Basculer des frames<br />-Trier une colonne<br />-Threads groupes<br />-Figer ou libérer les threads<br />-Exporter les données dans la fenêtre Espion parallèle|  
|**Threads GPU** fenêtre|-La colonne d’indicateur, dans lequel vous pouvez marquer un thread auquel vous conseille de prêter une attention particulière à.<br />-La colonne de thread actif dans lequel une flèche jaune indique un thread actif. Flèche désignant un thread sur lequel l'exécution s'est arrêtée dans le débogueur.<br />-Le **le nombre de threads** colonne qui affiche le nombre de threads au même emplacement.<br />-Le **ligne** colonne qui affiche la ligne de code où se trouve chaque groupe de threads.<br />-Le **adresse** colonne qui affiche l’adresse d’instruction où se trouve chaque groupe de threads.<br />-Le **emplacement** colonne, qui est l’emplacement dans le code de l’adresse.<br />-Le **état** colonne, ce qui indique si le thread est actif ou bloqué.<br />-Le **vignette** colonne, ce qui indique l’index de la mosaïque pour les threads dans la ligne.|-Modifier à un autre thread actif<br />-Permet d’afficher une vignette particulière et un thread<br />-Permet d’afficher ou masquer une colonne<br />-Trier par colonne<br />-Threads groupes<br />-Figer ou libérer les threads<br />-Ajouter ou supprimer l’indicateur d’un thread<br />-Permet d’afficher uniquement les threads avec indicateur|  
  
## <a name="see-also"></a>Voir aussi  
 [Attacher au processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Déboguer les Applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Débogage du code GPU](../debugger/debugging-gpu-code.md)



