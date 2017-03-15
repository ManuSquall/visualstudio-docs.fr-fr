---
title: "Le projet &lt;nom&gt; doit &#234;tre converti au format de projet actuel. | Microsoft Docs"
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
  - "VC.Project.Conversion7"
  - "vs.UpgradeWarningDlg"
ms.assetid: e27d58e5-c270-468b-bb98-3163d40900bc
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Le projet &lt;nom&gt; doit &#234;tre converti au format de projet actuel.
Vous avez ouvert un projet qui a été créé dans une version précédente de Visual Studio. Pour pouvoir ouvrir et modifier un projet dans la version de Visual Studio installée sur votre ordinateur, les fichiers projet doivent être convertis aux formats actuels. Vous pouvez choisir de convertir ou non ce projet dès à présent. Les conversions de format ne peuvent pas être annulées.  
  
> [!CAUTION]
>  Si le projet est stocké sous le contrôle de code source et que vous avez l’intention d’archiver le projet converti, déterminez tout d’abord si d’autres solutions le partagent. N’archivez pas un projet récemment converti qui est encore utilisé dans d’autres solutions non converties, car cela conduirait à rompre les dépendances au sein de ces solutions et empêcherait ces dernières de s’ouvrir ou de se générer correctement.  
  
 Vous avez tout intérêt à créer des copies de sauvegarde de vos fichiers projet avant de les convertir.  
  
> [!NOTE]
>  Pour certains types de projets, comme les projets Visual C\+\+, les anciens fichiers projet sont reconnaissables à l’extension de fichier « .old » et sont enregistrés dans le répertoire projet à l’issue de la conversion.  
  
 Les projets en lecture seule ne sont pas convertis. Ces projets peuvent uniquement être convertis par les utilisateurs autorisés à les modifier. Pour pouvoir utiliser un projet dans une solution convertie, ses fichiers projet doivent être convertis aux formats actuels. Une fois qu’un projet est converti, vous ne pouvez plus modifier, générer ou exécuter les solutions incluant ce projet dans les versions précédentes de Visual Studio.  
  
### Pour répondre à ce message  
  
1.  Sélectionnez **Oui** ou **Non**.  
  
    -   **Oui** : si le projet est modifiable, il est converti au format utilisé par la version de Visual Studio installée sur votre ordinateur. Si le projet converti est stocké sous le contrôle de code source, il est extrait sur votre disque local et ouvert pour que vous puissiez le modifier.  
  
    -   **Non** : le projet n’est pas converti, n’est pas extrait du contrôle de code source et n’est pas ouvert.  
  
 Si vous faites partie d’une équipe de développement, toutes les personnes travaillant sur un projet doivent avoir installé la même version de Visual Studio sur leur ordinateur local. Pour être certain que les projets restent accessibles, communiquez régulièrement avec votre équipe.  
  
## Voir aussi  
 [Project Dependencies Dialog Box](http://msdn.microsoft.com/fr-fr/d66e48c3-3722-40dd-99b4-53d93cac128e)   
 [Génération d'applications dans Visual Studio](../ide/compiling-and-building-in-visual-studio.md)