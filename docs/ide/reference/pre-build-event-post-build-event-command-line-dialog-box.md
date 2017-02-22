---
title: "Ligne de commande de l’&#233;v&#233;nement pr&#233;-build/post-build, bo&#238;te de dialogue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cs.ProjectPropertiesBuildEventsBuilder"
  - "vb.ProjectPropertiesBuildEventsBuilder"
helpviewer_keywords: 
  - "$(SolutionExt)"
  - "$(ProjectDir)"
  - "$(TargetPath)"
  - "$(ProjectExt)"
  - "$(TargetFileName)"
  - "$(PlatformName)"
  - "$(SolutionName)"
  - "macros, événements de build"
  - "$(SolutionPath)"
  - "$(ProjectPath)"
  - "$(ProjectFileName)"
  - "$(DevEnvDir)"
  - "$(TargetName)"
  - "$(TargetDir)"
  - "$(SolutionDir)"
  - "$(TargetExt)"
  - "$(OutDir)"
  - "$(ConfigurationName)"
  - "$(SolutionFileName)"
  - "$(ProjectName)"
  - "événements de build, macros"
ms.assetid: d49b2c57-24bf-4fb2-8351-5c4b6cca938f
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Ligne de commande de l’&#233;v&#233;nement pr&#233;-build/post-build, bo&#238;te de dialogue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Vous pouvez taper des événements pre\-build ou post\-build pour le [Événements de build, page du Concepteur de projets \(C\#\)](../../ide/reference/build-events-page-project-designer-csharp.md) directement dans la zone d'édition, ou vous pouvez sélectionner des macros pre\-build ou post\-build dans une liste de macros disponibles.  
  
> [!NOTE]
>  Les événements avant génération ne s'exécutent pas si le projet est à jour et si aucune génération n'est déclenchée.  
  
## Liste des éléments de l'interface utilisateur  
 **Zone d'édition de la ligne de commande**  
 Contient les événements à exécuter avant ou après la génération.  
  
> [!NOTE]
>  Ajoutez une instruction `call` avant toutes les commandes post\-build qui exécutent des fichiers .bat.  Par exemple, `call C:\MyFile.bat` ou `call C:\MyFile.bat call C:\MyFile2.bat`.  
  
 **Macros**  
 Développe la zone d'édition pour afficher une liste de macros à insérer dans la zone d'édition de la ligne de commande.  
  
 **Table de macros**  
 Répertorie les macros disponibles et leur valeur.  Consultez Macros ci\-dessous pour une description de chacune.  Vous pouvez sélectionner une seule macro à la fois pour l'insérer dans la zone d'édition de la ligne de commande.  
  
 **Insert**  
 Insère dans la zone d'édition de la ligne de commande la macro sélectionnée dans la table de macros.  
  
### Macros  
 Vous pouvez utiliser la macro de votre choix pour spécifier des emplacements de fichiers ou obtenir le nom du fichier d'entrée dans le cas de sélections multiples.  Ces macros ne respectent pas la casse.  
  
|Macro|Description|  
|-----------|-----------------|  
|`$(ConfigurationName)`|Nom de la configuration du projet en cours \(par exemple, "Debug"\).|  
|`$(OutDir)`|Chemin d'accès du répertoire de fichiers de sortie par rapport au répertoire du projet.  Cela résout la valeur de la propriété Output Directory.  Il inclut la barre oblique inverse \("\\"\)|  
|`$(DevEnvDir)`|Le répertoire d'installation de Visual Studio \(défini avec le lecteur et le chemin\) ; inclut la barre oblique inverse »\\".|  
|`$(PlatformName)`|Nom de la plateforme actuellement ciblée.  Par exemple, "AnyCPU".|  
|`$(ProjectDir)`|Répertoire du projet \(avec lecteur et chemin d'accès\) ; inclut la barre oblique inverse "\\".|  
|`$(ProjectPath)`|Nom du chemin d'accès absolu du projet \(avec lecteur, chemin d'accès, nom de base et extension de fichier\).|  
|`$(ProjectName)`|Nom de base du projet.|  
|`$(ProjectFileName)`|Nom de fichier du projet \(avec nom de base et extension de fichier\).|  
|`$(ProjectExt)`|Extension du fichier du projet.  Elle inclut un point \(« . »\) comme premier caractère.|  
|`$(SolutionDir)`|Répertoire de la solution \(avec lecteur et chemin d'accès\) ; inclut la barre oblique inverse "\\".|  
|`$(SolutionPath)`|Nom du chemin d'accès absolu de la solution \(avec lecteur, chemin d'accès, nom de base et extension de fichier\).|  
|`$(SolutionName)`|Nom de base de la solution.|  
|`$(SolutionFileName)`|Nom de fichier de la solution \(avec nom de base et extension de fichier\).|  
|`$(SolutionExt)`|Extension de fichier de la solution.  Elle inclut un point \(« . »\) comme premier caractère.|  
|`$(TargetDir)`|Répertoire du fichier de sortie principale \(avec lecteur et chemin d'accès\).  Il inclut la barre oblique inverse \("\\"\)|  
|`$(TargetPath)`|Nom du chemin d'accès absolu du fichier de sortie principale \(avec lecteur, chemin d'accès, nom de base et extension de fichier\).|  
|`$(TargetName)`|Nom de base du fichier de sortie principale pour la génération.|  
|`$(TargetFileName)`|Nom du fichier de sortie principale pour la génération \(avec nom de base et extension de fichier\).|  
|`$(TargetExt)`|Extension du fichier de sortie principale pour la génération.  Elle inclut un point \(« . »\) comme premier caractère.|  
  
## Voir aussi  
 [Spécification d'événements de build personnalisés dans Visual Studio](../../ide/specifying-custom-build-events-in-visual-studio.md)   
 [Événements de build, page du Concepteur de projets \(C\#\)](../../ide/reference/build-events-page-project-designer-csharp.md)   
 [Comment : spécifier des événements de build \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md)   
 [Comment : spécifier des événements de build \(C\#\)](../../ide/how-to-specify-build-events-csharp.md)