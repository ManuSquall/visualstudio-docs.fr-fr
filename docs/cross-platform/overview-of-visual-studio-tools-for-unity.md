---
title: "Vue d’ensemble de Visual Studio Tools pour Unity | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b4231bb9-45c4-4c77-ac3c-d05033b26393
caps.latest.revision: "4"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: f8c436730023ebd534cc8fb7794f3724d371568c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="overview-of-visual-studio-tools-for-unity"></a>Vue d'ensemble de Visual Studio Tools pour Unity
Dans cette section, vous allez en savoir plus sur les fonctionnalités de Visual Studio Tools pour Unity et apprendre à les utiliser pour être plus productif avec Unity.  
  
 Avec Visual Studio Tools for Unity (*VSTU*), vous pouvez utiliser Visual Studio pour écrire des scripts d’éditeur et de jeu en C#, puis utiliser son débogueur performant pour rechercher et corriger les erreurs. La dernière mise en production de VSTU inclut la coloration de la syntaxe pour le langage ShaderLab de Unity, des visualisations du débogueur améliorées et une génération de code améliorée pour l’Assistant MonoBehavior. VSTU apporte également vos fichiers de projet Unity et vos messages de console, et offre la possibilité de démarrer votre jeu dans Visual Studio, afin de perdre moins de temps à aller et venir de l’éditeur Unity en cours d’écriture.  
  
 Continuez à lire pour en savoir plus sur ces fonctionnalités.  
  
## <a name="integration-with-unity"></a>Intégration à Unity  
 Visual Studio Tools pour Unity ne serait pas un activateur de productivité, si vous deviez passer en permanence de l'éditeur Unity à Visual Studio, et inversement. C'est pourquoi Visual Studio Tools pour Unity facilite la conservation de votre travail sans que vous ayez à quitter Visual Studio.  
  
-   L’**Explorateur de projets Unity** affiche l’ensemble du projet Unity à l’intérieur de Visual Studio à l’aide de la même hiérarchie affichée dans l’éditeur Unity.  
  
-   L'intégration de la console Unity affiche la sortie de la console Unity directement dans la fenêtre d'erreur de Visual Studio.  
  
-   Démarrez le débogage de votre jeu à partir de Visual Studio. Inutile de revenir dans Unity, appuyez simplement sur F5.  
  
## <a name="superior-debugging"></a>Débogage de qualité supérieure  
 Connectez le puissant débogueur de Visual Studio à votre jeu Unity pour déboguer vos scripts C# et DLL que l'exécution se déroule de façon autonome ou dans l'éditeur Unity. Vous pouvez utiliser toutes les fonctionnalités de débogage souhaitées à partir de Visual Studio.  
  
-   Points d'arrêt, y compris les points d'arrêt conditionnels.  
  
-   Évaluer les expressions complexes dans la fenêtre Espion  
  
-   Inspectez et modifiez la valeur des variables et des arguments.  
  
-   Explorez les objets et structures de données complexes.  
  
 Vous pouvez même déboguer votre jeu Unity lorsqu'il s'exécute sur un autre ordinateur de votre réseau.  
  
## <a name="productivity"></a>Productivité  
 En plus de la productivité établie de Visual Studio pour l'écriture et la refactorisation de code en C#, Visual Studio Tools pour Unity fournit des fonctionnalités de productivité supplémentaires pour les développeurs Unity.  
  
-   Les couleurs de syntaxe pour le langage ShaderLab d'Unity vous permet de repérer les erreurs dans vos nuanceurs avant qu'elles ne deviennent des bogues. Ouvrez simplement vos fichiers ShaderLab dans Visual Studio.  
  
-   L'Assistant MonoBehavior vous permet de parcourir la liste des comportements Unity et crée un code réutilisable pour des comportements que vous ne connaissez peut-être pas. Appuyez sur Ctrl+Maj+M.  
  
-   Une fois que vous êtes familiarisé avec les comportements  Unity que vous utilisez le plus, l'Assistant MonoBehavior rapide vous les place à portée de main. Appuyez sur Ctrl+Alt+Q.  
  
-   Accédez à la documentation Unity à partir de Visual Studio. Sélectionnez simplement l’appel d’API sur lequel vous souhaitez en savoir plus, puis appuyez sur Ctrl+Alt+M, Ctrl+H.  
  
-   Accédez à toutes ces fonctionnalités et bien plus encore avec les raccourcis clavier.  
  
## <a name="visual-studio-tools-for-unity-api"></a>API Visual Studio Tools pour Unity  
 Personnalisez et étendez le comportement de Visual Studio Tools pour Unity à l'aide des API fournies.  
  
-   Visual Studio Tools pour Unity enregistre un rappel de journal pour pouvoir diffuser la console Unity vers Visual Studio. Si vous avez des scripts de l'éditeur qui enregistrent les informations, vous pouvez les incorporer au même rappel pour envoyer vos messages à Visual Studio. Pour plus d'informations, consultez l'exemple Rappel de journal.  
  
-   Vous pouvez modifier la façon dont Visual Studio Tools for Unity génère les fichiers projet à l'aide du rappel de style Unity ProjectFileGeneration. Pour plus d'informations, consultez l'exemple Génération de fichier projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Page d’accueil d’Unity](http://unity3d.com)