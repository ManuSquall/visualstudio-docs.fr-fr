---
title: "Comment&#160;: d&#233;boguer avec une source Code Center Premium | Microsoft Docs"
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
helpviewer_keywords: 
  - "Code Center Premium"
  - "déboguer (Visual Studio), Code Center Premium"
ms.assetid: 18b4769d-b007-4428-9dae-9e72c283ff0d
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# Comment&#160;: d&#233;boguer avec une source Code Center Premium
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Avec le débogueur [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], vous pouvez déboguer une source partagée sécurisée à partir de Microsoft MSDN Code Center Premium.  
  
 Cette rubrique explique comment installer et déboguer du code source Code Center Premium dans Visual Studio.  
  
### Pour préparer le débogage avec Code Center Premium  
  
1.  Connectez votre lecteur de carte à puce et insérez la carte que vous avez obtenue via le programme « Shared Source Initiative ».  
  
2.  Lancez Visual Studio.  
  
3.  Dans le menu **Outils**, cliquez sur **Options**.  
  
4.  Dans la boîte de dialogue **Options**, ouvrez le nœud **Débogage** et cliquez sur **Général**.  
  
5.  Désactivez la case à cocher **Activer Uniquement mon code \(Managé uniquement\)**.  
  
6.  Sélectionnez **Activer le support du serveur source**.  
  
7.  Désactivez **Les fichiers sources doivent correspondre exactement à la version d'origine**.  
  
8.  Sous le nœud **Débogage**, cliquez sur **Symboles**.  
  
9. Dans la zone **Emplacements du fichier de symboles \(.pdb\)**, désactivez la case à cocher **Serveurs de symboles Microsoft**, puis ajoutez les emplacements suivants :  
  
     `https://codepremium.msdn.microsoft.com/symbols`  
  
     `src=https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
    > [!NOTE]
    >  Veillez à inclure la barre oblique finale**\/** à la fin du chemin d'accès.  
  
     Déplacez ces emplacements vers le haut de la liste afin de vous assurer que ces symboles sont chargés en premier.  
  
    > [!NOTE]
    >  Ces emplacements Code Center Premium doivent être répertoriés en premier afin qu'ils soient les premiers emplacements chargés.  Dans Visual Studio 2010, vous ne pouvez déplacer aucun serveur au\-dessus de l'entrée **Serveurs de symboles Microsoft**, c'est pourquoi vous devez désactiver la case à cocher.  
    >   
    >  Pour charger des symboles à partir des symboles Microsoft pendant une session de débogage, procédez comme suit :  
    >   
    >  1.  Dans le menu **Déboguer**, cliquez sur **Fenêtres**, puis choisissez **Modules**.  
    > 2.  Sélectionnez le module pour lequel vous souhaitez des symboles, puis ouvrez le menu contextuel.  Choisissez **Charger les symboles à partir de**, puis **Serveurs de symboles Microsoft**.  
  
10. Dans la zone **Mettre en cache les symboles des serveurs de symboles dans ce répertoire**, entrez un emplacement tel que `C:\symbols` où Code Center Premium peut mettre en cache les symboles.  La mise en cache des symboles peut considérablement améliorer les performances lors du débogage.  
  
     Si vous rencontrez des difficultés lors du débogage du code source avec [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] une fois que vous avez effectué cette procédure, vérifiez si l'emplacement du cache ne contient pas des fichiers de symboles déjà mis en cache et obsolètes.  Supprimez les fichiers de symboles obsolètes.  
  
11. Cliquez sur **OK**.  
  
12. Redémarrez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour vous assurer que les paramètres sont persistants.  
  
### Pour déboguer votre code source en utilisant l'option Attacher au processus  
  
1.  Connectez votre lecteur de carte à puce et insérez la carte que vous avez obtenue via le programme « Shared Source Initiative ».  
  
2.  Lancez Visual Studio.  
  
3.  Ouvrez votre projet Visual Studio.  
  
4.  Dans le menu **Outils**, cliquez sur **Attacher au processus**.  
  
5.  Dans la boîte de dialogue **Attacher au processus**, cliquez sur **Sélectionner**.  
  
6.  Dans la boîte de dialogue **Sélectionner le type de code**, sous **Déboguer ces types de codes**, sélectionnez **Natif**, **Managé** et **Managé \(v4.0\)**.  
  
7.  Cliquez sur **OK** pour refermer la boîte de dialogue **Sélectionner le type de code**.  
  
8.  Dans la zone **Processus disponibles**, sélectionnez le processus à déboguer.  
  
9. Cliquez sur **Attacher**.  
  
10. Lorsque vous êtes invité à confirmer votre certificat, cliquez sur **OK**.  Entrez ensuite votre code confidentiel.  Acceptez les conditions d'utilisation de Code Center Premium, si vous y êtes invité.  
  
     Le téléchargement des symboles peut prendre beaucoup de temps, selon la vitesse du réseau.  La barre d'état indiquera le moment où tous les symboles auront été téléchargés avec succès.  
  
11. Répétez les étapes de la procédure d'attachement pour tous les projets managés de votre solution.  
  
### Pour déboguer le code source d'une solution existante  
  
1.  Dans l'**Explorateur de solutions**, ouvrez le menu contextuel de la solution, puis choisissez **Propriétés**.  
  
2.  Dans la boîte de dialogue Pages de propriétés de Solution, choisissez **Fichiers sources pour le débogage** dans le nœud **Propriétés communes**.  
  
3.  Ajoutez l'emplacement suivant à la liste **Répertoires contenant des fichiers sources** :  
  
     `https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
    > [!NOTE]
    >  Veillez à inclure la barre oblique finale**\/** à la fin du chemin d'accès.  
  
4.  Pour chaque projet managé dans votre solution, procédez comme suit :  
  
    1.  Dans l'Explorateur de solutions, ouvrez le menu contextuel du projet et choisissez **Propriétés**.  
  
    2.  Sélectionnez **Déboguer**, puis choisissez **Activer le débogage de code non managé**.  
  
### Pour déboguer votre solution avec une source Code Center Premium  
  
1.  Dans votre classe `Package`, définissez un point d'arrêt dans le constructeur du package.  
  
2.  Dans le menu `Debug`, cliquez sur **Démarrer le débogage**.  
  
3.  Lorsque vous avez atteint le point d'arrêt dans le constructeur du package, accédez à la fenêtre **Pile des appels**, cliquez avec le bouton droit sur le frame de pile de l'assembly à partir duquel vous voulez charger les symboles, puis cliquez sur **Charger les symboles**.  
  
     Double\-cliquez sur le frame d'appel pour charger la source.  
  
### Pour parcourir le code source sur Code Center Premium  
  
1.  Connectez votre lecteur de carte à puce et insérez la carte que vous avez obtenue via le programme « Shared Source Initiative ».  
  
2.  Lancez Internet Explorer et entrez l'URL suivante : `https://codepremium.msdn.microsoft.com`  
  
3.  Recherchez la source souhaitée.  
  
## Voir aussi  
 [Paramètres et préparation du débogage](../debugger/debugger-settings-and-preparation.md)   
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Code Center Premium](http://www.microsoft.com/resources/sharedsource/ccp.mspx)