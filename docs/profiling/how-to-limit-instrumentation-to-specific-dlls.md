---
title: "Proc&#233;dure&#160;: limiter l’instrumentation &#224; des DLL sp&#233;cifiques | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "outils d’analyse des performances, fenêtre de contrôle du profilage au moment de l’exécution"
ms.assetid: 17c5996f-e3d0-4e44-b175-52b401b0f2d5
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Proc&#233;dure&#160;: limiter l’instrumentation &#224; des DLL sp&#233;cifiques
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Grâce à la méthode de profilage par instrumentation, vous pouvez limiter la collecte de données de profilage à une ou plusieurs DLL d'une application.  Pour profiler une ou plusieurs DLL d'une application, vous créez une session de performance qui inclut les fichiers .dll en tant que cibles.  Vous pouvez spécifier les DLL à profiler en tant que projets dans une solution [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou en tant que fichiers binaires indépendants.  
  
### Pour limiter l'instrumentation à des DLL spécifiques dans une solution Visual Studio  
  
1.  Ouvrez la solution qui contient la DLL dans [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
  
2.  Dans le menu **Analyser** , cliquez sur **Lancer l'Assistant Performance**.  
  
3.  Sélectionnez la méthode de profilage **Instrumentation** , puis cliquez sur **Suivant**.  
  
4.  Dans la liste déroulante **Laquelle des cibles disponibles suivantes souhaiteriez\-vous profiler ?**, choisissez le nom du projet .dll, puis cliquez sur **Suivant**.  
  
5.  Cliquez sur **Terminer** pour quitter l'Assistant et afficher la nouvelle session de performance dans la fenêtre **Explorateur de performances** .  
  
6.  Cliquez avec le bouton droit sur **Cibles** , puis cliquez sur **Ajouter un projet cible**.  
  
7.  Dans la liste **Ajouter un projet cible** , sélectionnez le projet exécutable souhaité pour utiliser la DLL.  
  
     Optionnel.  Vous pouvez ajouter des projets de DLL que vous souhaitez profiler.  
  
8.  Pour empêcher la collecte de données pour un projet ajouté, cliquez avec le bouton droit sur le nom du projet, puis désactivez la case à cocher **Instrumenter**.  
  
### Pour spécifier des DLL spécifiques à profiler en tant que binaires indépendants  
  
1.  Ouvrez [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
  
2.  Dans le menu **Analyser** , cliquez sur **Lancer l'Assistant Performance**.  
  
3.  Dans la liste déroulante **Laquelle des cibles disponibles suivantes souhaiteriez\-vous profiler ?**, choisissez **Profiler une bibliothèque de liens dynamiques \(.DLL\)**, puis cliquez sur **Suivant**.  
  
4.  Dans la deuxième page de l'Assistant, effectuez les actions suivantes :  
  
    -   Dans le champ **Chemin d'accès de la DLL**, tapez le chemin d'accès et le nom du fichier .dll que vous souhaitez profiler.  Vous pouvez également cliquer sur le bouton de sélection pour identifier le fichier dans la boîte de dialogue **Bibliothèque de liens dynamiques à profiler** .  Notez que vous devez spécifier la copie du fichier .dll qui sera lancé par le fichier exécutable \(.exe\) que vous sélectionnerez.  
  
    -   Dans le champ **Chemin d'accès de l'exécutable**, tapez le chemin d'accès et le nom du fichier exécutable \(.exe\) qui doit exécuter le fichier .dll.  Vous pouvez également cliquer sur le bouton de sélection pour identifier le fichier dans la boîte de dialogue **Exécutable à lancer** .  
  
    -   Optionnel.  Dans la zone **Arguments de la ligne de commande**, tapez tous les arguments de ligne de commande que vous voulez transmettre au fichier exécutable.  Si nécessaire, spécifiez le répertoire de travail de l'application dans le champ **Répertoire de travail**.  
  
    -   Cliquez sur **Suivant**.  
  
5.  Sélectionnez la méthode de profilage **Instrumentation** , puis cliquez sur **Suivant**.  
  
6.  Cliquez sur **Terminer** pour quitter l'Assistant et afficher la nouvelle session de performance dans la fenêtre **Explorateur de performances** .  
  
7.  Optionnel.  Pour ajouter d'autres fichiers .dll, cliquez avec le bouton droit sur **Cibles** , puis cliquez sur **Ajouter un fichier binaire cible**.  Sélectionnez les fichiers dans la boîte de dialogue **Ajouter un fichier binaire cible** .  
  
    > [!NOTE]
    >  Ne spécifiez pas le fichier exécutable \(.exe\) qui exécute les DLL.  
  
## Voir aussi  
 [Contrôle de la collecte de données](../profiling/controlling-data-collection.md)   
 [Comment : limiter l’instrumentation à des fonctions spécifiques](../profiling/how-to-limit-instrumentation-to-specific-functions.md)