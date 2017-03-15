---
title: "Impossible de convertir un ou plusieurs projets. Ces projets sont &#224; pr&#233;sent d&#233;charg&#233;s et marqu&#233;s comme non disponibles dans l’Explorateur de solutions. Rechargez ces projets pour d&#233;terminer la cause de l’erreur. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.projectmigrationsfailed"
ms.assetid: c2fd3bbd-15f0-4b30-97f5-59abeae02141
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Impossible de convertir un ou plusieurs projets. Ces projets sont &#224; pr&#233;sent d&#233;charg&#233;s et marqu&#233;s comme non disponibles dans l’Explorateur de solutions. Rechargez ces projets pour d&#233;terminer la cause de l’erreur.
Vous avez tenté d’ouvrir une solution contenant un ou plusieurs projets qui ont été créés dans une version précédente de Visual Studio. Certains projets n’ont pas pu être convertis et sont marqués comme n’étant pas disponibles dans l’Explorateur de solutions. Pour pouvoir ouvrir et modifier votre solution, de même qu’utiliser les projets réparés dans la version de Visual Studio installée sur votre ordinateur, les projets doivent être convertis aux formats actuels.  
  
### Pour répondre à ce message  
  
1.  Sélectionnez **Oui** pour fermer la boîte de dialogue.  
  
     Les projets qui n’ont pas pu être convertis sont marqués comme **\(non disponible\)** dans l’Explorateur de solutions.  
  
2.  Rechargez les projets qui n’ont pas été convertis.  
  
    1.  Dans l’Explorateur de solutions, sélectionnez chaque projet de la solution active marqué comme **\(non disponible\)**.  
  
    2.  Dans le menu **Projet**, choisissez **Recharger le projet**.  
  
3.  Passez attentivement en revue tout message d’erreur donnant des informations sur les problèmes rencontrés avec les projets. Les problèmes possibles sont les suivants :  
  
    1.  Le projet est en lecture seule. Les projets en lecture seule ne sont pas convertis. Ces projets peuvent uniquement être convertis par les utilisateurs autorisés à les modifier.  
  
    2.  Le projet est déjà extrait exclusivement à un autre utilisateur. Cet utilisateur doit réarchiver le projet pour que vous puissiez l’extraire.  
  
    3.  Le projet n’a pas pu être extrait d’un serveur réseau. Confirmez les conditions réseau et réessayez.  
  
    4.  Le projet est endommagé et doit être régénéré.  
  
4.  Résolvez les problèmes indiqués quand vous essayez de recharger les projets marqués comme **\(non disponible\)**.  
  
5.  Rouvrez et convertissez ces projets. Vous avez tout intérêt à créer des copies de sauvegarde de vos fichiers projet avant de les convertir.  
  
    > [!NOTE]
    >  Pour certains types de projets, comme les projets Visual C\+\+, les anciens fichiers projet sont reconnaissables à l’extension de fichier .old et sont enregistrés dans le répertoire projet à l’issue de la conversion.  
  
 Si vous faites partie d’une équipe de développement, toutes les personnes travaillant sur un projet doivent avoir installé la même version de Visual Studio sur leur ordinateur local. Pour être certain que les projets restent accessibles, communiquez régulièrement avec votre équipe.  
  
> [!CAUTION]
>  Si les projets de votre solution sont stockés sous le contrôle de code source et que vous avez l’intention d’archiver les projets convertis, déterminez d’abord si d’autres solutions partagent un de ses projets. N’archivez pas des projets convertis qui sont toujours utilisés dans des solutions non converties, car cela conduirait à rompre les dépendances au sein de ces solutions et empêcherait ces dernières de s’ouvrir ou de se générer correctement.  
  
## Voir aussi  
 [NIB : Comment : décharger et recharger des projets](http://msdn.microsoft.com/fr-fr/abc0155b-8fcb-4ffc-95b6-698518a7100b)   
 [Project Dependencies Dialog Box](http://msdn.microsoft.com/fr-fr/d66e48c3-3722-40dd-99b4-53d93cac128e)   
 [Génération d'applications dans Visual Studio](../ide/compiling-and-building-in-visual-studio.md)