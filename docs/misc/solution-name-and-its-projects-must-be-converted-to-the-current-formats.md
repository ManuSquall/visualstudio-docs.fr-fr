---
title: "La solution &lt;nom&gt; et ses projets doivent &#234;tre convertis aux formats actuels. | Microsoft Docs"
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
  - "vs.querymigratesolution"
ms.assetid: 1ecb09ab-1283-4ba5-874c-f675905a3b7b
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# La solution &lt;nom&gt; et ses projets doivent &#234;tre convertis aux formats actuels.
Vous avez ouvert une solution qui a été créée dans une version antérieure de Visual Studio. Les fichiers solution et projet doivent être convertis aux formats actuels avant qu’une solution puisse être ouverte et modifiée dans la version de Visual Studio qui est installée sur votre ordinateur. Vous pouvez choisir de convertir cette solution dès maintenant. Les conversions de format ne peuvent pas être annulées.  
  
> [!CAUTION]
>  Si la solution est stockée sous le contrôle de code source et que vous avez l’intention d’archiver la solution convertie, déterminez d’abord si d’autres solutions partagent un de ses projets. N’archivez pas une solution qui comprend des projets convertis toujours utilisés dans d’autres solutions non converties. Cela rompra les dépendances dans ces solutions et les empêchera de s’ouvrir ou de se générer correctement.  
  
 Vous avez tout intérêt à créer des copies de sauvegarde de votre solution et de vos fichiers projet avant de les convertir.  
  
> [!NOTE]
>  Une fois les solutions Visual Studio converties, les anciens fichiers solution sont reconnaissables à l’extension de fichier « .old » et sont enregistrés dans le répertoire de la solution de niveau supérieur. Pour certains types de projets, comme les projets Visual C\+\+, les anciens fichiers projet sont également reconnaissables à l’extension de fichier « .old » et sont enregistrés dans le répertoire projet à l’issue de la conversion.  
  
 Les projets en lecture seule ne sont pas convertis. Ces projets peuvent être convertis uniquement par les utilisateurs autorisés à les modifier. Pour pouvoir utiliser un projet dans une solution convertie, ses fichiers projet doivent être convertis aux formats actuels. Une fois qu’une solution ou l’un de ses projets est converti, vous ne pouvez plus modifier, générer ou exécuter la solution dans les versions précédentes de Visual Studio.  
  
### Pour répondre à ce message  
  
1.  Sélectionnez **Oui** ou **Non**.  
  
    -   **Oui** : le fichier solution et les fichiers de ses projets modifiables sont convertis aux formats utilisés par la version de Visual Studio qui est installée sur votre ordinateur. Si la solution convertie est stockée sous le contrôle de code source, il est extrait sur votre disque local et ouvert pour modification.  
  
    -   **Non** : la solution et ses projets ne sont pas convertis, ne sont pas extraits du contrôle de code source et ne s’ouvrent pas.  
  
 Si vous faites partie d’une équipe de développement, toutes les personnes travaillant sur une solution doivent avoir installé la même version de Visual Studio sur leur ordinateur local. Pour être certain que les solutions et les projets restent accessibles, communiquez régulièrement avec votre équipe.  
  
## Voir aussi  
 [Project Dependencies Dialog Box](http://msdn.microsoft.com/fr-fr/d66e48c3-3722-40dd-99b4-53d93cac128e)   
 [Génération d'applications dans Visual Studio](../ide/compiling-and-building-in-visual-studio.md)