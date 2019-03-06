---
title: Ligne de commande de l’événement pré-build/post-build, boîte de dialogue | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuildEventsBuilder
- vb.ProjectPropertiesBuildEventsBuilder
helpviewer_keywords:
- $(SolutionExt)
- $(ProjectDir)
- $(TargetPath)
- $(ProjectExt)
- $(TargetFileName)
- $(PlatformName)
- $(SolutionName)
- macros, build events
- $(SolutionPath)
- $(ProjectPath)
- $(ProjectFileName)
- $(DevEnvDir)
- $(TargetName)
- $(TargetDir)
- $(SolutionDir)
- $(TargetExt)
- $(OutDir)
- $(ConfigurationName)
- $(SolutionFileName)
- $(ProjectName)
- build events, macros
ms.assetid: d49b2c57-24bf-4fb2-8351-5c4b6cca938f
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d3e6597e8b288e85c6bd49d3c8e843fd464bf094
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54753376"
---
# <a name="pre-build-eventpost-build-event-command-line-dialog-box"></a>Ligne de commande de l’événement pré-build/post-build, boîte de dialogue
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Vous pouvez taper des événements pré-build ou post-build pour la [page Événements de build du Concepteur de projets (C#)](../../ide/reference/build-events-page-project-designer-csharp.md) directement dans la zone d’édition, ou vous pouvez sélectionner des macros pré-build et post-build dans une liste de macros disponibles.  
  
> [!NOTE]
>  Les événements pré-build ne fonctionnent pas si le projet est à jour et qu’aucune build n’est déclenchée.  
  
## <a name="ui-element-list"></a>Liste des éléments de l'interface utilisateur  
 **Zone d’édition de la ligne de commande**  
 Contient les événements à exécuter avant ou après la génération.  
  
> [!NOTE]
>  Ajoutez une instruction `call` avant toutes les commandes post-build qui exécutent des fichiers .bat. Par exemple, `call C:\MyFile.bat` ou `call C:\MyFile.bat call C:\MyFile2.bat`.  
  
 **Macros**  
 Développe la zone d’édition pour afficher une liste de macros à insérer dans la zone d’édition de la ligne de commande.  
  
 **Table de macros**  
 Répertorie les macros disponibles et leur valeur. Consultez Macros ci-dessous pour obtenir une description de chacune. Vous pouvez sélectionner une seule macro à la fois pour l’insérer dans la zone d’édition de la ligne de commande.  
  
 **Insert**  
 Insère dans la zone d’édition de la ligne de commande la macro sélectionnée dans la table de macros.  
  
### <a name="macros"></a>Macros  
 Vous pouvez utiliser l’une de ces macros pour spécifier des emplacements de fichiers ou obtenir le nom du fichier d’entrée dans le cas de plusieurs sélections. Ces macros ne respectent pas la casse.  
  
|Macro|Description|  
|-----------|-----------------|  
|`$(ConfigurationName)`|Nom de la configuration de projet actuelle, par exemple « Debug ».|  
|`$(OutDir)`|Chemin du répertoire de fichiers de sortie par rapport au répertoire du projet. Ceci se résout en la valeur de la propriété Output Directory. Il inclut la barre oblique inverse de fin '\\'.|  
|`$(DevEnvDir)`|Répertoire d’installation de Visual Studio (défini comme étant lecteur + chemin) ; inclut la barre oblique inverse de fin '\\'.|  
|`$(PlatformName)`|Nom de la plateforme actuellement ciblée. Par exemple, « AnyCPU ».|  
|`$(ProjectDir)`|Répertoire du projet (défini comme étant lecteur + chemin) ; inclut la barre oblique inverse de fin '\\'.|  
|`$(ProjectPath)`|Nom de chemin absolu du projet (défini comme étant lecteur + chemin + nom de base + extension de fichier).|  
|`$(ProjectName)`|Le nom de base du projet.|  
|`$(ProjectFileName)`|Nom de fichier du projet (défini comme étant nom de base + extension de fichier).|  
|`$(ProjectExt)`|L’extension de fichier du projet. Elle inclut le point (« . ») avant l’extension de fichier.|  
|`$(SolutionDir)`|Répertoire de la solution (défini comme étant lecteur + chemin) ; inclut la barre oblique inverse de fin '\\'.|  
|`$(SolutionPath)`|Nom de chemin absolu de la solution (défini comme étant lecteur + chemin + nom de base + extension de fichier).|  
|`$(SolutionName)`|Le nom de base de la solution.|  
|`$(SolutionFileName)`|Nom de fichier de la solution (défini comme étant nom de base + extension de fichier).|  
|`$(SolutionExt)`|L’extension de fichier de la solution. Elle inclut le point (« . ») avant l’extension de fichier.|  
|`$(TargetDir)`|Répertoire du fichier de sortie principal pour la build (défini comme étant lecteur + chemin). Il inclut la barre oblique inverse de fin '\\'.|  
|`$(TargetPath)`|Nom de chemin absolu du fichier de sortie principal pour la build (défini comme étant lecteur + chemin + nom de base + extension de fichier).|  
|`$(TargetName)`|Le nom de base du fichier de sortie principal pour la build.|  
|`$(TargetFileName)`|Nom du fichier de sortie principal pour la build (défini comme étant nom de base + extension de fichier).|  
|`$(TargetExt)`|L’extension de fichier du fichier de sortie principal pour la build. Elle inclut le point (« . ») avant l’extension de fichier.|  
  
## <a name="see-also"></a>Voir aussi  
 [Spécification d’événements de build personnalisés dans Visual Studio](../../ide/specifying-custom-build-events-in-visual-studio.md)   
 [Événements de build, page du Concepteur de projet (C#)](../../ide/reference/build-events-page-project-designer-csharp.md)   
 [Guide pratique pour spécifier des événements de build (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)   
 [Guide pratique pour spécifier des événements de build (C#)](../../ide/how-to-specify-build-events-csharp.md)
