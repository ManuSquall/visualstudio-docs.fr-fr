---
title: "Fichiers divers | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.newfile"
  - "VS.OpenWith"
  - "MiscellaneousFilesProject"
helpviewer_keywords: 
  - "solutions, fichier divers"
  - "builds [Visual Studio], fichiers divers"
  - "fichiers autonomes"
  - "Explorateur de solutions, fichier divers"
  - "Fichiers divers (dossier)"
  - "fichiers [Visual Studio], hors des conteneurs"
  - "fichiers [Visual Studio], dossier de fichiers divers"
ms.assetid: 5b96640b-8efe-48a4-8d0a-1ae3f9587e44
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Fichiers divers
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Il se peut que vous vouliez utiliser les éditeurs de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour travailler sur des fichiers indépendamment d'un projet ou d'une solution.  Lorsqu'une solution est ouverte, vous pouvez ouvrir des fichiers et les modifier sans avoir à les ajouter à une solution ou à un projet.  Les fichiers que vous souhaitez utiliser indépendamment des conteneurs sont appelés fichiers divers.  Il s'agit de fichiers externes aux solutions et aux projets, ne pouvant être inclus dans les générations ou avec une solution sous contrôle de code source.  
  
 L'ouverture de fichiers indépendamment d'un conteneur est utile pour diverses raisons.  Il se peut que, lors du développement d'une solution composée de plusieurs projets, vous souhaitiez visualiser un dossier qui ne fait pas partie intégrante du développement de la solution.  Les exemples les plus courants sont les instructions ou conseils de développement, les schémas de base de données ou les clips de code.  De même, vous pouvez vouloir créer un fichier autonome.  
  
 ![Projets de solutions](~/ide/reference/media/projects_solutions_misc.gif "Projects\_Solutions\_Misc")  
  
 Pour que l'Explorateur de solutions affiche le dossier Fichiers divers correspondant à ces fichiers, les options appropriées du dossier doivent être activées.  Les options peuvent être définies à partir de la [Documents, Environnement, boîte de dialogue Options](../../ide/reference/documents-environment-options-dialog-box.md).  Quand vous fermez un fichier divers, il n'est pas associé à une solution particulière ou un projet particulier si vous n'avez pas activé l'option correspondante.  
  
 Le dossier Fichiers divers représente les fichiers sous forme de liens.  Bien que ce dossier n'appartienne pas à une solution, quand vous en ouvrez une, une partie ou la totalité des fichiers divers qui étaient ouverts lorsque la solution a été fermée pour la dernière fois est rouverte, selon les paramètres définis pour le dossier.  
  
> [!NOTE]
>  Parmi les fichiers qui n'apparaissent pas dans le dossier Fichiers divers, certains ne peuvent pas être modifiés dans l'IDE. C'est le cas des fichiers .zip et des fichiers .doc.  L'IDE ne suivra pas les fichiers qui ne peuvent être modifiés que via un éditeur externe.  
  
## Commandes disponibles dans l'environnement IDE  
 Les menus, barres d'outils et commandes varient en fonction du format du fichier que vous ouvrez.  Lorsque, par exemple, vous ouvrez un fichier texte, la barre d'outils de l'éditeur de texte s'affiche avec ses commandes.  Si vous ouvrez un schéma XML, la barre d'outils correspondante s'affiche.  Lorsque vous modifiez le schéma XML, les commandes de la barre d'outils de l'éditeur de texte \(ou la barre d'outils elle\-même\) ne sont, quant à elles, pas disponibles.  Le schéma XML constitue la fenêtre active et, en tant que tel, possède le contexte de sélection en cours.  Quand vous passez d'un fichier projet à un fichier divers, toutes les commandes associées au projet disparaissent et seules celles directement associées au fichier divers s'affichent.  
  
## Options d'affichage des dossiers  
 Vous pouvez définir plusieurs options pour le dossier Fichiers divers de telle sorte que le dossier s'affiche même si vous n'avez ouvert aucun fichier divers.  Le fichier solution ne gère pas en permanence une liste des fichiers divers.  Il utilise une fonctionnalité facultative qui lui permet de se souvenir, pour chaque utilisateur, de la liste des derniers fichiers utilisés.  
  
## Voir aussi  
 [Projets et solutions](../../ide/solutions-and-projects-in-visual-studio.md)   
 [Documents, Environnement, boîte de dialogue Options](../../ide/reference/documents-environment-options-dialog-box.md)