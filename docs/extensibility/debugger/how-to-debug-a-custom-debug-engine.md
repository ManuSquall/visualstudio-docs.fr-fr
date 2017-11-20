---
title: "Comment : Déboguer un moteur de débogage personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6a91dbb7797d69ec71b776eeef5e34e0ced21ad9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Comment : Déboguer un moteur de débogage personnalisé
Un type de projet lance le moteur de débogage (DE) à partir de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> (méthode). Cela signifie que la D’est démarrée sous le contrôle de l’instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] contrôle le type de projet. Toutefois, cette instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ne peut pas déboguer le DE. Voici les étapes permettant de vous permettent de déboguer votre DE personnalisé.  
  
> [!NOTE]
>  : Dans la procédure « Débogage un personnalisé déboguer moteur », vous devez attendre le DE démarrer avant que vous pouvez attacher à celui-ci. Si vous placez une zone de message vers le début de votre DE qui s’affiche au démarrage de la DE, vous pouvez attacher à ce stade et désactivez la boîte de message pour continuer. De cette façon, vous pouvez intercepter tous les événements DE.  
  
> [!WARNING]
>  Vous devez disposer de débogage à distance est installé avant de commencer les procédures suivantes. Consultez [débogage distant](../../debugger/remote-debugging.md) pour plus d’informations.  
  
### <a name="debugging-a-custom-debug-engine"></a>Débogage d’un moteur de débogage personnalisé  
  
1.  Démarrez msvsmon.exe, le Remote Debug Monitor.  
  
2.  À partir de la **outils** menu msvsmon.exe, sélectionnez **Options** pour ouvrir le **Options** boîte de dialogue.  
  
3.  Sélectionnez l’option « Aucune authentification » et cliquez sur **OK**.  
  
4.  Démarrez une instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et ouvrez votre projet DE personnalisé.  
  
5.  Démarrez une deuxième instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et ouvrez votre projet personnalisé qui lance le DE (pour le développement, il s’agit généralement de la ruche du Registre expérimentale configuré lors de l’installation de VSIP).  
  
6.  Dans cette deuxième instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], de charger un fichier source à partir de votre projet personnalisé et démarrez le programme à déboguer. Attendez quelques instants pour autoriser le DE chargement, ou patientez jusqu'à ce qu’un point d’arrêt est atteint.  
  
7.  Dans la première instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (avec votre projet DE), sélectionnez **attacher au processus** à partir de la **déboguer** menu.  
  
8.  Dans le **attacher au processus** boîte de dialogue, choisissez le **Transport** à **distant (natif uniquement avec aucune authentification)**.  
  
9. Modifier la **qualificateur** pour le nom de votre ordinateur (Remarque : est un historique des entrées, donc vous devez taper une seule fois dans ce nom).  
  
10. Dans le **processus disponibles** , sélectionnez l’instance de votre DE est en cours d’exécution, puis cliquez sur le **attacher** bouton.  
  
11. Après le chargement des symboles dans vos DE, placez des points d’arrêt dans votre code DE.  
  
12. Chaque fois que vous arrêtez et redémarrez le processus de débogage, répétez les étapes 6 à 10.  
  
### <a name="debugging-a-custom-project-type"></a>Débogage d’un Type de projet personnalisés  
  
1.  Démarrer [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dans la ruche du Registre normal et le chargement de votre projet type projet (il s’agit, la source de votre type de projet, pas une instanciation de votre type de projet).  
  
2.  Ouvrez les propriétés du projet et accédez à la **déboguer** page. Pour le **commande**, tapez le chemin d’accès à la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE (par défaut, il s’agit de *[lecteur]*\Program Files\Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8\Common7\IDE\devenv.exe).  
  
3.  Pour le **Arguments de commande**, type `/rootsuffix exp` pour la ruche du Registre expérimentale (créée lors de l’installation VSIP).  
  
4.  Cliquez sur **OK** pour accepter les modifications.  
  
5.  Démarrez votre type de projet en appuyant sur F5. Cette action lance une deuxième instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
6.  À ce stade, vous pouvez placer des points d’arrêt dans votre code de source de type de projet.  
  
7.  Dans la deuxième instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], charger ou créer une nouvelle instance de votre type de projet. Pendant la création ou de charge, vos points d’arrêt peuvent être atteint.  
  
8.  Déboguer votre type de projet.  
  
9. Si vous choisissez de déboguer le processus de lancement d’un DE, vous pouvez effectuer les étapes de la procédure « Débogage un personnalisé déboguer moteur » à attacher à votre DE après son lancement. Cela vous donnera trois instances de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en cours d’exécution : un pour votre source de type de projet, une seconde pour votre type de projet instancié et un troisième attaché à votre DE.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)