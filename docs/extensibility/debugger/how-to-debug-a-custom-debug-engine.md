---
title: "Comment : D&#233;boguer un moteur de d&#233;bogage personnalis&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "moteurs de débogage, le débogage"
  - "débogage [Debugging SDK], les moteurs de débogage personnalisés"
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Comment : D&#233;boguer un moteur de d&#233;bogage personnalis&#233;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

un type de projet lance le moteur de débogage \(DE\) de la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> .  Cela signifie que le du est lancé sous le contrôle de l'instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] du type de projet.  Toutefois, cette instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] impossible de déboguer le De.  Voici les étapes pour vous permettre de déboguer votre personnalisé De.  
  
> [!NOTE]
>  :     Procédure dans « debug du moteur de débogage personnalisé », vous devez attendre le du pour commencer avant de pouvoir se joindre à celui\-ci.  Si vous placez un message vers le début de votre De qui s'affiche lorsque le De démarre, vous pouvez à ce stade puis attacher désactivez le message à continuer.  de cette façon, vous pouvez intercepter tout le DE events.  
  
> [!WARNING]
>  Vous devez installer le débogage distant avant de tenter les procédures suivantes.  Pour plus d'informations, consultez [Débogage distant](../../debugger/remote-debugging.md).  
  
### déboguer un moteur de débogage personnalisé  
  
1.  début msvsmon.exe, Remote Debugging Monitor.  
  
2.  Dans le menu d' **Outils** dans msvsmon.exe, sélectionnez **Options** pour ouvrir la boîte de dialogue d' **Options** .  
  
3.  Sélectionnez l'option « aucune authentification » et cliquez sur **OK**.  
  
4.  Démarrez une instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et ouvrez votre custom DE project.  
  
5.  Démarrez une deuxième instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et ouvrez votre projet personnalisé qui lance le De \(pour le développement, il s'agit généralement dans la ruche expérimentale de Registre configuré lorsque VSIP est installé\).  
  
6.  Dans cette seconde instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], charger un fichier source de votre projet personnalisé et commencez le programme à déboguer.  Attendez quelques minutes pour permettre le De à charger, ou l'attente jusqu'à un point d'arrêt est atteint.  
  
7.  En premier lieu de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(avec votre DE project\), sélectionnez **Attacher au processus** dans le menu de **Débogage** .  
  
8.  dans la boîte de dialogue d' **Attacher au processus** , modifiez **Transport** à **Distant \(natif uniquement sans authentification\)**.  
  
9. modifiez **Qualificateur** au nom de votre ordinateur \(remarque : il existe un historique des entrées, vous devez entrer dans ce nom qu'une seule fois\).  
  
10. dans la liste de **Processus disponibles** , sélectionnez l'instance de votre De qui exécute et cliquez sur le bouton d' **Attacher** .  
  
11. Une fois les symboles aient chargé dans votre DE, placez des points d'arrêt dans votre code de.  
  
12. Chaque fois que vous arrêtez et redémarrez le processus de débogage, répétez les étapes 6 à 10.  
  
### Débogage d'un type personnalisé de projet  
  
1.  Démarrez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dans la ruche normale de Registre et chargez votre projet de type de projet \(c'est, la source à votre type de projet, pas une instanciation de votre type de projet\).  
  
2.  Ouvrez les propriétés et accédez à **Débogage** la page.  Pour **Commande**, tapez le chemin d'accès à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'IDE \(par défaut, la valeur est *\[lecteur\]*\\Program Files\\Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8 \\Common7\\IDE \\ devenv.exe\).  
  
3.  Pour **Arguments de la commande**, tapez `/rootsuffix exp` pour la ruche expérimentale de Registre \(créée lorsque VSIP a été installé\).  
  
4.  Cliquez sur **OK** pour accepter les modifications.  
  
5.  Démarrez votre type de projet en appuyant sur F5.  Cette opération permet d'activer une deuxième instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
6.  À ce stade, vous pouvez placer des points d'arrêt dans votre code source du type de projet.  
  
7.  Dans la deuxième instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], la charge ou créent une instance de votre type de projet.  Lors de le chargement ou la conception, vos points d'arrêt peuvent être correspondance.  
  
8.  déboguez votre type de projet.  
  
9. Si vous choisissez de déboguer le processus de lancer un De, vous pouvez exécuter les étapes procédure dans « debug du moteur de débogage personnalisé » pour attacher votre De une fois qu'il est lancé.  Cela présente trois instances d'effectuer de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] : un pour votre source de type de projet, seconde pour votre type instancié de projet, et une troisième attaché à votre De.  
  
## Voir aussi  
 [Création d'un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)