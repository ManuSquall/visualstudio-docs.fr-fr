---
title: "&#201;v&#233;nements de build, page du Concepteur de projets (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cs.ProjectPropertiesBuildEvents"
helpviewer_keywords: 
  - "événements de build"
  - "Concepteur de projets, page Événements de build"
  - "événements pré-build"
  - "événements post-build"
ms.assetid: 3fff9ae5-213c-46ea-a660-1d70acb6c922
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# &#201;v&#233;nements de build, page du Concepteur de projets (C#)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilisez la page **Événements de build** du **Concepteur de projets** pour spécifier des instructions de configuration de build.  Vous pouvez également spécifier les conditions dans lesquelles les événements post\-build sont exécutés.  Pour plus d'informations, consultez [Comment : spécifier des événements de build \(C\#\)](../../ide/how-to-specify-build-events-csharp.md) et [Comment : spécifier des événements de build \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md).  
  
## Liste UIElement  
 **Configuration**  
 Ce contrôle n'est pas modifiable sur cette page.  Pour obtenir une description de ce contrôle, consultez [Générer, page du Concepteur de projets \(C\#\)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Plateforme**  
 Ce contrôle n'est pas modifiable sur cette page.  Pour obtenir une description de ce contrôle, consultez [Générer, page du Concepteur de projets \(C\#\)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Ligne de commande de l'événement pré\-build**  
 Spécifie les commandes à exécuter avant que la génération commence.  Pour taper de longues commandes, cliquez sur **Modifier avant génération** pour afficher la boîte de dialogue Ligne de commande de l'événement pre\-build\/post\-build \([Ligne de commande de l’événement pré\-build\/post\-build, boîte de dialogue](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)\).  
  
> [!NOTE]
>  Les événements avant génération ne s'exécutent pas si le projet est à jour et si aucune génération n'est déclenchée.  
  
 **Ligne de commande de l'événement post\-build**  
 Spécifie les commandes à exécuter à l'issue de la génération.  Pour taper de longues commandes, cliquez sur **Modifier après génération** pour afficher la boîte de dialogue **Ligne de commande de l'événement pre\-build\/post\-build**.  
  
> [!NOTE]
>  Ajoutez une instruction `call` avant toutes les commandes post\-build qui exécutent des fichiers .bat.  Par exemple, `call C:\MyFile.bat` ou `call C:\MyFile.bat call C:\MyFile2.bat`.  
  
 **Exécuter l'événement post\-build**  
 Indique les conditions liées à l'événement post\-build à exécuter, comme indiquées dans le tableau ci\-dessous.  
  
|Option|Résultat|  
|------------|--------------|  
|**Toujours**|L'événement post\-build est exécuté en cas de succès ou d'échec de la génération.|  
|**En cas de génération réussie**|L'événement post\-build est exécuté si la génération se déroule correctement.  Ainsi, l'événement est même exécuté pour un projet à jour, à condition que la génération soit un succès.|  
|**Lorsque la génération met à jour la sortie du projet**|L'événement post\-build n'est exécuté que lorsque le fichier de sortie du compilateur \(.exe ou .dll\) est différent du fichier de sortie précédent.  Ainsi, un événement post\-build n'est pas exécuté si un projet est à jour.|  
  
## Voir aussi  
 [Comment : spécifier des événements de build \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md)   
 [Comment : spécifier des événements de build \(C\#\)](../../ide/how-to-specify-build-events-csharp.md)   
 [Référence de propriétés de projet](../../ide/reference/project-properties-reference.md)   
 [Génération d'applications dans Visual Studio](../../ide/compiling-and-building-in-visual-studio.md)