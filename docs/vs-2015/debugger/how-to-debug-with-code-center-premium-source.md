---
title: 'Comment : déboguer avec une source code Center Premium | Microsoft Docs'
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
- Code Center Premium
- debugging [Visual Studio], Code Center Premium
ms.assetid: 18b4769d-b007-4428-9dae-9e72c283ff0d
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db9a3e08e14e7fadca6df9e32361c0b042f565e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839350"
---
# <a name="how-to-debug-with-code-center-premium-source"></a>Comment : déboguer avec une source Code Center Premium
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Avec le débogueur [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], vous pouvez déboguer une source partagée sécurisée à partir de Microsoft MSDN Code Center Premium.  
  
 Cette rubrique explique comment installer et déboguer du code source Code Center Premium dans Visual Studio.  
  
### <a name="to-prepare-for-debugging-with-code-center-premium"></a>Pour préparer le débogage avec Code Center Premium  
  
1. Connectez votre lecteur de carte à puce et insérez la carte que vous avez obtenue via le programme « Shared Source Initiative ».  
  
2. Lancez Visual Studio.  
  
3. Dans le menu **Outils** , cliquez sur **Options**.  
  
4. Dans la boîte de dialogue **options** , ouvrez le nœud **débogage** et cliquez sur **général**.  
  
5. Désactivez la case à cocher **activer uniquement mon code (managé uniquement)** .  
  
6. Sélectionnez **activer la prise en charge du serveur source**.  
  
7. Clear **exiger que les fichiers sources correspondent exactement à la version d’origine**.  
  
8. Sous le nœud **débogage** , cliquez sur **symboles**.  
  
9. Dans la zone **emplacements du fichier de symboles (. pdb)** , désactivez la case à cocher **symboles du serveur Microsoft** et ajoutez les emplacements suivants :  
  
     `https://codepremium.msdn.microsoft.com/symbols`  
  
     `src=https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
   > [!NOTE]
   > Veillez à inclure la barre oblique <strong>/</strong> de fin à la fin du chemin d’accès.  
  
     Déplacez ces emplacements vers le haut de la liste afin de vous assurer que ces symboles sont chargés en premier.  
  
   > [!NOTE]
   > Ces emplacements Code Center Premium doivent être répertoriés en premier afin qu'ils soient les premiers emplacements chargés. Dans Visual Studio 2010, vous ne pouvez pas déplacer les serveurs au-dessus de l’entrée **serveurs de symboles Microsoft** . c’est la raison pour laquelle vous devez désactiver la case à cocher.  
   > 
   >  Pour charger des symboles à partir des symboles Microsoft pendant une session de débogage, procédez comme suit :  
   > 
   > 1. Dans le menu **Déboguer** , choisissez **fenêtres** , puis **modules**.  
   >    2.  Sélectionnez le module pour lequel vous souhaitez des symboles, puis ouvrez le menu contextuel. Choisissez **charger les symboles à partir de** , puis choisissez **serveurs de symboles Microsoft**.  
  
10. Dans la zone mettre en **cache les symboles des serveurs de symboles dans ce répertoire** , entrez un emplacement tel que `C:\symbols` où Code Center Premium peut mettre en cache les symboles. La mise en cache des symboles peut considérablement améliorer les performances lors du débogage.  
  
     Si vous rencontrez des difficultés lors du débogage du code source avec [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] une fois que vous avez effectué cette procédure, vérifiez si l'emplacement du cache ne contient pas des fichiers de symboles déjà mis en cache et obsolètes. Supprimez les fichiers de symboles obsolètes.  
  
11. Cliquez sur **OK**.  
  
12. Redémarrez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour vous assurer que les paramètres sont persistants.  
  
### <a name="to-debug-your-source-code-using-attach-to-process"></a>Pour déboguer votre code source en utilisant l'option Attacher au processus  
  
1. Connectez votre lecteur de carte à puce et insérez la carte que vous avez obtenue via le programme « Shared Source Initiative ».  
  
2. Lancez Visual Studio.  
  
3. Ouvrez votre projet Visual Studio.  
  
4. Dans le menu **Outils** , cliquez sur **attacher au processus**.  
  
5. Dans la boîte de dialogue **attacher au processus** , cliquez sur **Sélectionner**.  
  
6. Dans la boîte de dialogue **Sélectionner le type de code** , sous **détecter ces types de codes**, sélectionnez **natif**, **géré**et **géré (v 4.0)**.  
  
7. Cliquez sur **OK** pour fermer la boîte de dialogue **Sélectionner le type de code** .  
  
8. Dans la zone **processus disponibles** , sélectionnez le processus que vous souhaitez déboguer.  
  
9. Cliquez sur **Attacher**.  
  
10. Lorsque vous êtes invité à confirmer votre certificat, cliquez sur **OK**. Entrez ensuite votre code confidentiel. Acceptez les conditions d'utilisation de Code Center Premium, si vous y êtes invité.  
  
     Le téléchargement des symboles peut prendre beaucoup de temps, selon la vitesse du réseau. La barre d'état indiquera le moment où tous les symboles auront été téléchargés avec succès.  
  
11. Répétez les étapes de la procédure d'attachement pour tous les projets managés de votre solution.  
  
### <a name="to-debug-source-code-from-an-existing-solution"></a>Pour déboguer le code source d'une solution existante  
  
1. Dans **Explorateur de solutions**, ouvrez le menu contextuel de la solution, puis choisissez **Propriétés**.  
  
2. Dans la boîte de dialogue pages de propriétés de la solution, choisissez **fichiers sources pour le débogage** dans le nœud **Propriétés communes** .  
  
3. Ajoutez l’emplacement suivant à la liste **répertoires contenant les fichiers sources** :  
  
    `https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
   > [!NOTE]
   > Veillez à inclure la barre oblique <strong>/</strong> de fin à la fin du chemin d’accès.  
  
4. Pour chaque projet managé dans votre solution, procédez comme suit :  
  
   1. Dans Explorateur de solutions, ouvrez le menu contextuel du projet, puis choisissez **Propriétés**.  
  
   2. Sélectionnez **Déboguer** , puis choisissez **activer le débogage de code non managé**.  
  
### <a name="to-debug-your-solution-with-code-center-premium-source"></a>Pour déboguer votre solution avec une source Code Center Premium  
  
1. Dans votre classe `Package`, définissez un point d'arrêt dans le constructeur du package.  
  
2. Dans le `Debug` menu, cliquez sur **Démarrer le débogage**.  
  
3. Quand vous atteignez le point d’arrêt dans le constructeur du package, accédez à la fenêtre **pile des appels** , cliquez avec le bouton droit sur le frame de pile de l’assembly à partir duquel vous souhaitez charger les symboles, puis cliquez sur **charger les symboles**.  
  
     Double-cliquez sur le frame d'appel pour charger la source.  
  
### <a name="to-browse-source-code-on-code-center-premium"></a>Pour parcourir le code source sur Code Center Premium  
  
1. Connectez votre lecteur de carte à puce et insérez la carte que vous avez obtenue via le programme « Shared Source Initiative ».  
  
2. Lancez Internet Explorer et entrez l'URL suivante : `https://codepremium.msdn.microsoft.com`  
  
3. Recherchez la source souhaitée.  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)   
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Code Center Premium](https://www.microsoft.com/en-us/sharedsource/code-center-premium.aspx)
