---
title: Déboguer les Threads et processus | Microsoft Docs
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
- multiprocess debugging
- threading [Visual Studio], debugging
- processes, debugging
- debugging threads
- debugging [Visual Studio], threads
ms.assetid: 9f0c8505-b6b2-452b-adfd-076db14d8115
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: df9bc7cdb185edd27d7572c1436db442514d38e4
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "58951110"
---
# <a name="debug-threads-and-processes"></a>Déboguer les threads et processus
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Threads * et *processus* sont des concepts liés en informatique. Tous deux représentent des séquences d'instructions qui doivent s'exécuter dans un ordre spécifique. Les instructions dans des threads ou processus séparés, toutefois, peuvent s'exécuter en parallèle.  
  
 Les processus existent dans le système d'exploitation et correspondent à ce que les utilisateurs voient sous la forme de programmes ou d'applications. Un thread, en revanche, existe dans un processus. C’est pour cette raison que les threads sont parfois appelés *processus légers*. Chaque processus est constitué d'un ou de plusieurs threads.  
  
 L’existence de plusieurs processus permet à un ordinateur d’effectuer plusieurs tâches à la fois. L'existence de plusieurs threads permet à un processus de séparer le travail à exécuter en parallèle. Sur un ordinateur multiprocesseur, les processus ou les threads peuvent s'exécuter sur différents processeurs. Ce type d'exécution permet un véritable traitement en parallèle.  
  
 Le traitement en parallèle parfait n'est pas toujours possible. Les threads doivent parfois être synchronisés. Un thread peut attendre le résultat d'un autre thread ou un thread peut avoir besoin d'un accès exclusif à une ressource utilisée par un autre thread. Les problèmes de synchronisation sont une cause courante de bogues dans les applications multithread. Les threads attendent parfois une ressource qui n'est jamais disponible. Cet état est appelé *interblocage*.  
  
 Le débogueur [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] propose des outils performants mais faciles à utiliser pour déboguer les threads et les processus.  
  
## <a name="tools-for-debugging-threads-and-processes-in-visual-studio"></a>Outils pour le débogage de threads et processus dans Visual Studio  
 Les principaux outils pour des processus dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sont le **attacher au processus** boîte de dialogue, le **processus** fenêtre et le **emplacement de débogage** barre d’outils. Les principaux outils de débogage de threads sont les **Threads** fenêtre, les marqueurs de thread dans les fenêtres source et la **emplacement de débogage** barre d’outils.  
  
 Les principaux outils de débogage d’applications multithread sont les **piles parallèles** et **tâches parallèles**, **espion parallèle**, et **Threads GPU** windows.  
  
 Le tableau suivant affiche les informations disponibles et les actions que vous pouvez exécuter depuis chacun de ces emplacements :  
  
|Interface utilisateur|Informations disponibles|Actions que vous pouvez effectuer|  
|--------------------|---------------------------|-----------------------------|  
|Boîte de dialogue **Attacher au processus**|Processus disponibles auxquels vous pouvez attacher :<br /><br /> -   Nom de processus (.exe)<br />-   Numéro d’identification de processus<br />-   Titre de barre de menus<br />-   Type (Managé v4.0 ; Managé v2.0, v1.1, v1.0 ; x86 ; x64 ; IA64)<br />-   Nom d’utilisateur (nom du compte)<br />-   Numéro de session|Sélectionnez un processus auquel attacher<br /><br /> Sélectionnez un ordinateur distant<br /><br /> Modifiez le type de transport pour la connexion aux ordinateurs distants|  
|Fenêtre **Processus**|Processus attachés :<br /><br /> -   Nom du processus<br />-   Numéro d’identification de processus<br />-   Chemin pour traiter .exe<br />-   Titre de barre de menus<br />-   État (Break. Running)<br />-   Débogage (natif, managé, etc.)<br />-   Type de transport (par défaut, natif sans authentification)<br />-   Qualificateur de transport (ordinateur distant)|Outils :<br /><br /> -   Attacher<br />-   Détacher<br />-   Terminer<br /><br /> Menu contextuel :<br /><br /> -   Attacher<br />-   Détacher<br />-   Détacher lorsque le débogage est arrêté<br />-   Terminer|  
|Fenêtre **Threads**|Threads dans le processus actuel :<br /><br /> -   ID de thread<br />-   ID managé<br />-   Catégorie (thread principal, thread d’interface, gestionnaire d’appel de procédure distante ou thread de travail)<br />-   Nom du thread<br />-   Emplacement de création du thread<br />-   Priorité<br />-   Masque d’affinité<br />-   Compteur suspendu<br />-   Nom du processus<br />-   Indicateur<br />-   Indicateur suspendu|Outils :<br /><br /> -   Rechercher<br />-   Rechercher la pile des appels<br />-   Signaler uniquement mon code<br />-   Signaler la sélection de modules personnalisés<br />-   Regrouper par<br />-   Colonnes<br />-   Développer/réduire la pile des appels<br />-   Développer/Réduire les groupes<br />-   Figer/libérer les threads<br /><br /> Menu contextuel :<br /><br /> -   Afficher les threads dans la source<br />-   Basculer vers un thread<br />-   Figer un thread en cours d’exécution<br />-   Libérer un thread figé<br />-   Marquer un thread pour un examen plus détaillé<br />-   Supprimer l’indicateur d’un thread<br />-   Renommer un thread<br />-   Afficher et masquer des threads<br /><br /> Autres actions :<br /><br /> -   Afficher la pile d’appel d’un thread dans un DataTip|  
|Fenêtre source|Les indicateurs de thread de la marge gauche signalent un ou plusieurs threads (option désactivée par défaut, activée à l’aide du menu contextuel de la fenêtre **Threads**)|Menu contextuel :<br /><br /> -   Basculer vers un thread<br />-   Marquer un thread pour un examen plus détaillé<br />-   Supprimer l’indicateur d’un thread|  
|Barre d’outils **Emplacement de débogage**|-   Processus en cours<br />-   Interrompre l’application<br />-   Reprendre l’application<br />-   Interrompre et quitter l’application<br />-   Thread en cours<br />-   Activer/désactiver l’état actuel de l’indicateur de thread<br />-   Afficher seulement des threads avec indicateur<br />-   Afficher uniquement le processus actuel<br />-   Frame de pile en cours|-   Basculer vers un autre processus<br />-   Interrompre, reprendre ou quitter l’application<br />-   Basculer vers un autre thread dans le processus en cours<br />-   Basculer vers un autre frame de pile dans le thread en cours<br />-   Ajouter ou supprimer l’indicateur de threads actuels<br />-   Afficher seulement des threads avec indicateur<br />-   Afficher uniquement le processus actuel|  
|Fenêtre **Piles parallèles**|-   Piles des appels pour plusieurs threads dans une fenêtre.<br />-   -   Frame de pile actif pour chaque thread.<br />-   Appelants et appelés pour une méthode.|-   Éliminer les threads spécifiés par filtrage<br />-Basculer vers la vue Tâches parallèles<br />-   Ajouter ou supprimer l’indicateur d’un thread<br />-   Zoomer|  
|**Tâches parallèles** fenêtre|-   Affichez des informations sur les objets <xref:System.Threading.Tasks.Task>, notamment l’ID de la tâche, son état (planifié, en cours, en attente, bloqué), ainsi que le thread qui lui est assigné.<br />-   Emplacement actuel dans la pile des appels<br />-   Délégué passé à la tâche au moment de la création|-   Basculer vers la tâche actuelle<br />-   Ajouter ou supprimer l’indicateur d’une tâche<br />-   Figer ou libérer une tâche|  
|Fenêtre **Espion parallèle**|-   La colonne d’indicateur, où vous pouvez marquer un thread auquel vous souhaitez apporter une attention spéciale.<br />-   La colonne de frame, dans laquelle une flèche indique le frame sélectionné.<br />-   Une colonne configurable qui peut afficher l’ordinateur, le processus, la mosaïque, la tâche et le thread.|-   Ajouter ou supprimer l’indicateur d’un thread<br />-   Afficher uniquement les threads avec indicateur<br />-   Basculer les frames<br />-   Trier une colonne<br />-   Regrouper des threads<br />-   Figer ou libérer les threads<br />-   Exporter les données dans la fenêtre Espion parallèle|  
|Fenêtre **Threads GPU**|-   La colonne d’indicateur, où vous pouvez marquer un thread auquel vous souhaitez apporter une attention spéciale.<br />-La colonne de thread actif dans lequel une flèche jaune indique un thread actif. Flèche désignant un thread sur lequel l'exécution s'est arrêtée dans le débogueur.<br />-   Colonne **Nombre de threads**, qui affiche le nombre de threads au même emplacement.<br />-   Colonne **Ligne**, qui affiche la ligne de code où chaque groupe de threads est situé.<br />-   Colonne **Adresse**, qui affiche l’adresse de l’instruction où chaque groupe de threads est localisé.<br />-   Colonne **Emplacement**, qui correspond à l’emplacement dans le code de l’adresse.<br />-   Colonne **État**, qui indique si le thread est actif ou bloqué.<br />-   Colonne **Mosaïque**, qui indique l’index de la mosaïque des threads dans la ligne.|-Modifier à un autre thread actif<br />-   Afficher une mosaïque et un thread particuliers<br />-   Afficher ou masquer une colonne<br />-   Trier par colonne<br />-   Regrouper des threads<br />-   Figer ou libérer les threads<br />-   Ajouter ou supprimer l’indicateur d’un thread<br />-   Afficher uniquement les threads avec indicateur|  
  
## <a name="see-also"></a>Voir aussi  
 [Attacher à des processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Déboguer les applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Débogage du code GPU](../debugger/debugging-gpu-code.md)
