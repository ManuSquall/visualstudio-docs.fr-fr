---
title: "Framework cible du projet non install&#233;, bo&#238;te de dialogue | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.TargetFrameworkNotFound"
ms.assetid: 64ce8743-d5bd-447e-ba10-54b2aafe109e
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Framework cible du projet non install&#233;, bo&#238;te de dialogue
Vous avez ouvert un projet qui cible une infrastructure qui n'est pas installée sur votre ordinateur. Pour continuer, vous devez sélectionner l'une des options de cette boîte de dialogue.  
  
> [!NOTE]
>  Chaque fois que vous téléchargez et installez une nouvelle infrastructure, vous devez redémarrer Visual Studio.  
  
## Visual Basic et Visual C\#  
 Si vous avez ouvert un projet Visual Basic ou Visual C\#, sélectionnez l'une des options suivantes.  
  
 **Remplacer la cible par .NET Framework 4.5. Vous pourrez revenir à .NET Framework** *Version* **plus tard.**  
 Recible votre projet vers .NET Framework 4.5. Vous pouvez réinstaller plus tard la version précédente, puis recibler le projet.  
  
 **Télécharger le Targeting Pack pour .NET Framework \<Version\>. Le projet n'est pas modifié.**  
 Ouvre le site web du Centre de téléchargement Microsoft, où vous pouvez télécharger la version du .NET Framework de votre choix. Votre projet est déchargé de la solution. Après avoir téléchargé et installé la version souhaitée du .NET Framework, vous devez redémarrer Visual Studio, puis rouvrir le projet.  
  
 **Ne pas charger le projet.**  
 Laisse le projet déchargé par rapport à la solution. Vous pourrez installer plus tard la version souhaitée du .NET Framework, et recharger ensuite le projet.  
  
## Visual C\+\+  
 Si vous avez ouvert un projet Visual C\+\+, sélectionnez l'une des options suivantes.  
  
 **Télécharger le Targeting Pack pour .NET Framework** *Version***. Le projet n'est pas modifié.**  
 Ouvre le site web du Centre de téléchargement Microsoft, où vous pouvez télécharger la version du .NET Framework de votre choix. Une fois le téléchargement terminé, votre projet est reciblé vers cette version. Votre projet est déchargé de la solution. Après avoir téléchargé et installé la version souhaitée du .NET Framework, vous devez redémarrer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], puis rouvrir le projet.  
  
 **Ne pas charger le projet.**  
 Laisse le projet déchargé par rapport à la solution. Vous pourrez installer plus tard la version souhaitée du .NET Framework, et recharger ensuite le projet.  
  
## Voir aussi  
 [Comment : cibler une version du .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [Troubleshooting .NET Framework Targeting Errors](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)   
 [Ajout de références](/visual-cpp/ide/adding-references-in-visual-cpp-projects)