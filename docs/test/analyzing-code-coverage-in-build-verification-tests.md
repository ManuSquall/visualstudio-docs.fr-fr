---
title: "Analyse de la couverture du code dans les tests de v&#233;rification de build | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 59c07d15-511e-4fd0-b398-bde9d5ed00d9
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "mlearned"
manager: "douge"
---
# Analyse de la couverture du code dans les tests de v&#233;rification de build
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'analyse de couverture du code dans Microsoft Visual Studio indique quelle proportion de votre code est testé par les tests automatisés.  Pour plus d'informations, consultez [Utilisation de la couverture du code pour déterminer la quantité de code testé](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).  
  
 Lorsque vous archivez votre code, vos tests s'exécutent sur le serveur de builds, ainsi que tous les autres tests des autres membres de l'équipe. \(Si vous n'avez pas déjà établi cela, consultez [Exécuter des tests dans votre processus de génération](../Topic/Run%20tests%20in%20your%20build%20process.md).\) Il est utile d'analyser la couverture du code sur le service de build, car cela fournit l'image la plus récente et la plus complète de la couverture du projet entier.  Il inclut également les tests système automatisés et d'autres tests codés que vous n'exécutez généralement pas sur les ordinateurs de développement.  
  
1.  Dans Team Explorer, ouvrez **Builds**, puis ajouter ou modifier une définition de build.  
  
2.  Dans la page **Processus**, développez **Tests automatisés**, **Source de test**, **Paramètres d'exécution**.  Définissez **Type du fichier de paramètres d'exécution** à **Couverture du code activée**.  
  
     Si vous avez plusieurs définitions de source de test, répétez cette étape pour chaque définitions.  
  
    -   *Mais il n'y a aucun champ nommé **Type du fichier de paramètres d'exécution**.*  
  
         Sous **Tests automatisés**, sélectionnez **Examiner l'assembly** et choisissez le bouton de sélection **\[…\]** à la fin de la ligne.  Dans la boîte de dialogue **Ajoutez\/Editez l'exécution de tests**, sous **Test Runner**, choisissez **Visual Studio Test Runner**.  
  
 ![Définition de build pour la couverture du code](../test/media/codecoverage-plaincc.png "CodeCoverage\-plainCC")  
  
 Après l'exécution de la build, les résultats de la couverture du code s'affichent dans le résumé de la build.  
  
## Voir aussi  
 [Utilisation de la couverture du code pour déterminer la quantité de code testé](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)