---
title: "Comment&#160;: d&#233;panner les &#233;checs de mise &#224; niveau de projets Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VisualStudio.SourceControl.CannotOpenFromSourceControlDSW"
  - "vs.UpgradeProjectSolution.8.0"
helpviewer_keywords: 
  - "mettre à niveau des applications, Visual Studio"
  - "mettre à niveau des projets (Visual Studio)"
  - "projets (Visual Studio), mettre à niveau"
  - "Assistant Conversion de Visual Studio"
  - "Assistant Conversion"
ms.assetid: 842fe448-c044-4343-8eae-d81711cf48ba
caps.latest.revision: 30
caps.handback.revision: 30
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# Comment&#160;: d&#233;panner les &#233;checs de mise &#224; niveau de projets Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Parfois Visual Studio ne peut pas complètement convertir un projet d'une version antérieure de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Si les conseils dans les sections suivantes ne résolvent pas le problème spécifique, vous pouvez trouver plus d'informations sur le wik TechNet [Wiki : portail de développement](http://go.microsoft.com/fwlink/?LinkId=254808).  
  
## Le projet ne s'exécute pas, car des fichiers sont introuvables  
 Un fichier projet contient des chemins d'accès de fichiers codés en dur, qui permettent à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] d'exécuter le projet lorsque vous appuyez sur F5.  Ces chemins d'accès peuvent inclure l'emplacement du fichier devenv.exe et d'autres fichiers obligatoires.  Dans une version mise à jour de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], les chemins de ces fichiers ont peut\-être été modifiés.  
  
#### Pour résoudre les chemins d'accès de fichiers incorrects  
  
1.  Ouvrez le fichier projet dans un éditeur de texte.  
  
2.  Analysez les chemins d'accès de fichiers qui peuvent être incorrects, en particulier ceux qui contiennent un numéro de version [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
3.  Modifiez les chemins d'accès de fichiers incorrects afin qu'ils pointent vers les nouvelles cibles.  
  
## Impossible de générer le projet, car des références ne sont pas valides  
 Lorsque vous mettez à niveau [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous pouvez également mettre à jour la version de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] .  Si votre projet contient des références qui n'existent plus dans la nouvelle version du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], elles risquent de ne pas être résolues correctement.  Cela se vérifie notamment pour les références qui incluent des numéros de version, par exemple, `Microsoft.VisualStudio.Shell.Interop.8.0`.  
  
 Si votre code contient de nombreuses références non valides, la solution la plus simple peut consister à utiliser la fonctionnalité de multi\-ciblage de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour cibler une version antérieure du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
#### Pour résoudre les chemins d'accès de fichiers incorrects  
  
1.  Ouvrez le fichier projet dans un éditeur de texte.  
  
2.  Ouvrez les propriétés du projet.  
  
3.  Sélectionnez la valeur correcte du **Framework cible** .  Sinon, vous pouvez modifier la valeur de l'élément du `<TargetFrameworkVersion>` directement dans le fichier projet.  
  
 Si vous voulez que votre projet s'exécute dans la version du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] mise à niveau, vous devez mettre à jour les références du projet, ainsi que toutes les instructions `Imports` ou `Using` qui appellent les références.  Si votre projet charge dans l'IDE, vous pouvez mettre à jour les références à l'aide de **Explorateur de solutions** ou de la boîte de dialogue **gestionnaire de références** .  
  
## Voir aussi  
 [\/Upgrade](../ide/reference/upgrade-devenv-exe.md)   
 [Converting to ASP.NET 4](../Topic/Converting%20to%20ASP.NET%204.md)