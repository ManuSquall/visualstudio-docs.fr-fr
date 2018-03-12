---
title: "Comment : déboguer avec une Source Code Center Premium | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
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
- Code Center Premium
- debugging [Visual Studio], Code Center Premium
ms.assetid: 18b4769d-b007-4428-9dae-9e72c283ff0d
caps.latest.revision: "23"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d7405deed95f14314215b869a02bcf8a1afddea2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-debug-with-code-center-premium-source"></a>Comment : déboguer avec une source Code Center Premium
Avec le débogueur [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], vous pouvez déboguer une source partagée sécurisée à partir de Microsoft MSDN Code Center Premium.  
  
 Cette rubrique explique comment installer et déboguer du code source Code Center Premium dans Visual Studio.  
  
### <a name="to-prepare-for-debugging-with-code-center-premium"></a>Pour préparer le débogage avec Code Center Premium  
  
1.  Connectez votre lecteur de carte à puce et insérez la carte que vous avez obtenue via le programme « Shared Source Initiative ».  
  
2.  Lancez Visual Studio.  
  
3.  Dans le menu **Outils** , cliquez sur **Options**.  
  
4.  Dans le **Options** boîte de dialogue, ouvrez le **débogage** nœud et cliquez sur **général**.  
  
5.  Désactivez le **activer uniquement mon Code (managé uniquement)** case à cocher.  
  
6.  Sélectionnez **activer le Support du serveur Source**.  
  
7.  Désactivez **les fichiers sources doivent correspondre exactement à la version d’origine**.  
  
8.  Sous le **débogage** nœud, cliquez sur **symboles**.  
  
9. Dans le **le fichier de symboles (.pdb) emplacements** zone, désactivez la **serveurs de symboles Microsoft** case à cocher et ajoutez les emplacements suivants :  
  
     `https://codepremium.msdn.microsoft.com/symbols`  
  
     `src=https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
    > [!NOTE]
    >  Veillez à inclure la barre oblique **/**  à la fin du chemin d’accès.  
  
     Déplacez ces emplacements vers le haut de la liste afin de vous assurer que ces symboles sont chargés en premier.  
  
    > [!NOTE]
    >  Ces emplacements Code Center Premium doivent être répertoriés en premier afin qu'ils soient les premiers emplacements chargés. Dans Visual Studio 2010, vous ne pouvez pas déplacer des serveurs ci-dessus le **serveurs de symboles Microsoft** entrée, c’est pourquoi vous devez désactiver la case à cocher.  
    >   
    >  Pour charger des symboles à partir des symboles Microsoft pendant une session de débogage, procédez comme suit :  
    >   
    >  1.  Sur le **déboguer** menu, choisissez **Windows** , puis **Modules**.  
    > 2.  Sélectionnez le module pour lequel vous souhaitez des symboles, puis ouvrez le menu contextuel. Choisissez **charger les symboles depuis** , puis **serveurs de symboles Microsoft**.  
  
10. Dans le **mettre en Cache les symboles à partir des serveurs de symboles dans ce répertoire** , entrez un emplacement tel que `C:\symbols` où Code Center Premium peut mettre en cache les symboles. La mise en cache des symboles peut considérablement améliorer les performances lors du débogage.  
  
     Si vous rencontrez des difficultés lors du débogage du code source avec [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] une fois que vous avez effectué cette procédure, vérifiez si l'emplacement du cache ne contient pas des fichiers de symboles déjà mis en cache et obsolètes. Supprimez les fichiers de symboles obsolètes.  
  
11. Cliquez sur **OK**.  
  
12. Redémarrez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour vous assurer que les paramètres sont persistants.  
  
### <a name="to-debug-your-source-code-using-attach-to-process"></a>Pour déboguer votre code source en utilisant l'option Attacher au processus  
  
1.  Connectez votre lecteur de carte à puce et insérez la carte que vous avez obtenue via le programme « Shared Source Initiative ».  
  
2.  Lancez Visual Studio.  
  
3.  Ouvrez votre projet Visual Studio.  
  
4.  Sur le **outils** menu, cliquez sur **attacher au processus**.  
  
5.  Dans le **attacher au processus** boîte de dialogue, cliquez sur **sélectionnez**.  
  
6.  Dans le **sélectionner le Type de Code** boîte de dialogue **détecter ces types de codes**, sélectionnez **natif**, **Managed**, et **gérés () v4.0)**.  
  
7.  Cliquez sur **OK** pour faire disparaître la **sélectionner le Type de Code** boîte de dialogue.  
  
8.  Dans le **processus disponibles** , sélectionnez le processus que vous souhaitez déboguer.  
  
9. Cliquez sur **Attacher**.  
  
10. Lorsque vous êtes invité à confirmer votre certificat, cliquez sur **OK**. Entrez ensuite votre code confidentiel. Acceptez les conditions d'utilisation de Code Center Premium, si vous y êtes invité.  
  
     Le téléchargement des symboles peut prendre beaucoup de temps, selon la vitesse du réseau. La barre d'état indiquera le moment où tous les symboles auront été téléchargés avec succès.  
  
11. Répétez les étapes de la procédure d'attachement pour tous les projets managés de votre solution.  
  
### <a name="to-debug-source-code-from-an-existing-solution"></a>Pour déboguer le code source d'une solution existante  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel de la solution, puis sélectionnez **propriétés**.  
  
2.  Dans la boîte de dialogue Pages de propriétés de Solution, choisissez **déboguer les fichiers sources** dans les **propriétés communes** nœud.  
  
3.  Ajoutez l’emplacement suivant à la **répertoires contenant les fichiers sources** liste :  
  
     `https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
    > [!NOTE]
    >  Veillez à inclure la barre oblique **/**  à la fin du chemin d’accès.  
  
4.  Pour chaque projet managé dans votre solution, procédez comme suit :  
  
    1.  Dans l’Explorateur de solutions, ouvrez le menu contextuel du projet, puis choisissez **propriétés**.  
  
    2.  Sélectionnez **déboguer** , puis **activer le débogage de code non managé**.  
  
### <a name="to-debug-your-solution-with-code-center-premium-source"></a>Pour déboguer votre solution avec une source Code Center Premium  
  
1.  Dans votre classe `Package`, définissez un point d'arrêt dans le constructeur du package.  
  
2.  Dans le `Debug` menu, cliquez sur **démarrer le débogage**.  
  
3.  Lorsque vous atteignez le point d’arrêt dans le constructeur du package, accédez à la **pile des appels** fenêtre et avec le bouton droit le frame de pile de l’assembly à charger les symboles à partir, puis cliquez sur **charger les symboles**.  
  
     Double-cliquez sur le frame d'appel pour charger la source.  
  
### <a name="to-browse-source-code-on-code-center-premium"></a>Pour parcourir le code source sur Code Center Premium  
  
1.  Connectez votre lecteur de carte à puce et insérez la carte que vous avez obtenue via le programme « Shared Source Initiative ».  
  
2.  Lancez Internet Explorer et entrez l'URL suivante : `https://codepremium.msdn.microsoft.com`  
  
3.  Recherchez la source souhaitée.  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)   
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Code Center Premium](http://www.microsoft.com/resources/sharedsource/ccp.mspx)