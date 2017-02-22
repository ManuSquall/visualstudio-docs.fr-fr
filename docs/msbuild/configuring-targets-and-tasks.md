---
title: "Configuring Targets and Tasks | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9aabe67a-1720-4bbf-80d3-822b3ccf75c0
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# Configuring Targets and Tasks
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Configurez les cibles et les tâches MSBuild pour qu'elle s'exécutent hors processus avec MSBuild afin que vous puissiez cibler les contextes qui diffèrent de celui sur lequel vous fonctionnez.  Par exemple, ciblez une application sur .NET Framework 2.0 à 32\-bit pendant que l'ordinateur de développement s'exécute sur un système d'exploitation 64 bits avec .NET Framework 4,5.  Ciblez également les ordinateurs qui s'exécutent avec .NET Framework 4 ou une version antérieure.  La combinaison de 32 ou 64 bits et la version spécifique Net Framework est appelée *contexte cible*.  
  
## Installation  
 . Net Framework 4,5 et 4.5.1 remplacent le Common Langage Runtime \(CLR\), les cibles, tâches, et les outils .NET Framework 4 sans les renommer.  .NET Framework. 4.5.1 est installé comme partie [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)].  
  
 Si vous souhaitez installer MSBuild séparément de Visual Studio, il vous est possible de télécharger le package d'installation depuis [Téléchargement MSBuild](http://go.microsoft.com/fwlink/?LinkId=309745).  Vous devez également installer les versions du. Net Framework que vous souhaitez également utiliser.  
  
## Cibles et tâches  
 MSBuild exécute certaines tâches de génération en\-dehors du processus pour cibler un plus grand ensemble de contextes.  Par exemple, MSBuild 32 bits peut exécuter une tâche de génération dans un processus 64 bits pour cibler un ordinateur 64 bits.  Cela est contrôlé par les arguments `UsingTask` et les paramètres `Task`.  Les cibles installées par le .NET Framework 4,5 définissent ces arguments et paramètres, et aucune modification n'est requise pour générer des applications de différents contextes cibles.  
  
 Si vous voulez créer votre propre contexte cible, vous devez définir ces arguments et paramètres correctement.  Consultez le fichier .NET Framework 4,5 Microsoft.Common.targets et le fichier de Microsoft.Common.Tasks pour des exemples.  Pour plus d'informations sur la création d'une tâche personnalisée qui peut utiliser des contextes cibles, ou comment modifier des tâches existantes, consultez [How to: Configure Targets and Tasks](../msbuild/how-to-configure-targets-and-tasks.md).  
  
## Voir aussi  
 [Multitargeting](../msbuild/msbuild-multitargeting-overview.md)