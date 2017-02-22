---
title: "Comment&#160;: d&#233;boguer un fichier ex&#233;cutable ne faisant pas partie d&#39;une solution Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "déboguer (Visual Studio), exécutables"
  - "fichiers exécutables, déboguer hors des projets"
  - "fichiers exécutables, importer"
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# Comment&#160;: d&#233;boguer un fichier ex&#233;cutable ne faisant pas partie d&#39;une solution Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez être amené à déboguer un exécutable qui ne fait pas partie d'un projet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Il peut s'agir d'un exécutable créé en dehors de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou reçu de la part d'un tiers.  
  
 La réponse usuelle à ce problème consiste à démarrer l'exécutable en dehors de Visual Studio, puis à l'attacher à l'aide du débogueur [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Pour plus d'informations, consultez [Attacher aux processus en cours d'exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 L'attachement à une application requiert quelques étapes manuelles, qui prennent tout de même quelques secondes.  Ce léger décalage peut rendre l'attachement inutile si vous essayez de déboguer un problème survenant au démarrage.  De même, si vous déboguez un programme qui n'attend aucune entrée d'utilisateur et se termine rapidement, vous risquez de ne pas avoir le temps de l'attacher.  Si [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)] est installé, vous pouvez créer un projet EXE pour un tel programme.  
  
### Pour créer un projet EXE pour un exécutable existant  
  
1.  Dans le menu **Fichier**, cliquez sur **Ouvrir** et sélectionnez **Projet**.  
  
2.  Dans la boîte de dialogue **Ouvrir un projet**, cliquez sur la liste déroulante située en regard de la zone **Nom de fichier**, puis sélectionnez **Tous les fichiers projet**.  
  
3.  Recherchez l'exécutable, puis cliquez sur **OK**.  
  
     Cela permet de créer une solution temporaire contenant l'exécutable.  
  
### Pour importer un exécutable dans une solution Visual Studio  
  
1.  Dans le menu **Fichier**, pointez sur **Ajouter un projet**, puis cliquez sur **Projet existant**.  
  
2.  Dans la boîte de dialogue **Ajouter un projet existant**, cliquez sur la liste déroulante située en regard de la zone **Nom de fichier**, puis sélectionnez **Tous les fichiers projet**.  
  
3.  Recherchez et sélectionnez l'exécutable.  
  
4.  Cliquez sur **OK**.  
  
5.  Démarrez l'exécutable en choisissant une commande d'exécution, telle que **Démarrer**, dans le menu **Déboguer**.  
  
    > [!NOTE]
    >  Tous les langages de programmation ne prennent pas en charge les projets EXE.  Installez [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)] si vous devez utiliser cette fonctionnalité.  
  
     Lorsque vous déboguez un exécutable sans le code source, les fonctionnalités de débogage disponibles sont limitées, que vous attachiez l'exécutable en cours d'exécution ou que vous l'ajoutiez à une solution [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Si l'exécutable a été généré sans informations de débogage dans un format compatible, les fonctionnalités disponibles sont encore plus limitées.  Si vous disposez du code source, la meilleure approche consiste à l'importer dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour y créer une version Debug de l'exécutable.  
  
## Voir aussi  
 [Paramètres et préparation du débogage](../debugger/debugger-settings-and-preparation.md)   
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [DBG Files](http://msdn.microsoft.com/fr-fr/91e449e9-8b65-4123-960f-2107cd1f1cfd)