---
title: "&#201;v&#233;nements de build, bo&#238;te de dialogue (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesBuildEvents"
helpviewer_keywords: 
  - "événements de build"
  - "événements de build, spécification"
  - "événements pré-build"
  - "Événements de build, boîte de dialogue"
  - "événements post-build"
ms.assetid: 3a81a7c7-39f9-47a8-ba5a-b351227f380e
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# &#201;v&#233;nements de build, bo&#238;te de dialogue (Visual Basic)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilisez la boîte de dialogue **Événements de build** pour spécifier des instructions de configuration de build.  Vous pouvez également spécifier les conditions selon lesquelles les événements pre\-build et post\-build sont exécutés.  Pour plus d'informations, consultez [Comment : spécifier des événements de build \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md).  
  
 **Ligne de commande de l'événement pré\-build**  
 Spécifie les commandes à exécuter avant que la génération commence.  Pour taper de longues commandes, cliquez sur **Modifier avant génération** pour afficher la boîte de dialogue Ligne de commande de l'événement pre\-build\/post\-build \([Ligne de commande de l’événement pré\-build\/post\-build, boîte de dialogue](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)\).  
  
> [!NOTE]
>  Les événements pre\-build ne s'exécutent pas si le projet est à jour et si aucune génération n'est déclenchée.  
  
 **Ligne de commande de l'événement post\-build**  
 Spécifie les commandes à exécuter à l'issue de la génération.  Pour taper de longues commandes, cliquez sur **Modifier après génération** pour afficher la boîte de dialogue **Ligne de commande de l'événement pre\-build\/post\-build**.  
  
> [!NOTE]
>  Ajoutez une instruction `call` avant toutes les commandes post\-build qui exécutent des fichiers .bat.  Par exemple, `call C:\MyFile.bat` ou `call C:\MyFile.bat call C:\MyFile2.bat`.  
  
 **Exécuter l'événement post\-build**  
 Indique les conditions liées à l'événement post\-build à exécuter, comme indiquées dans le tableau suivant.  
  
|Option|Résultat|  
|------------|--------------|  
|**Toujours**|L'événement post\-build est exécuté, indépendamment de la réussite de la génération.|  
|**En cas de génération réussie**|L'événement post\-build est exécuté si la génération se déroule correctement.  Ainsi, l'événement est même exécuté pour un projet à jour, à condition que la génération soit un succès.  Il s'agit de l'option par défaut.|  
|**Lorsque la génération met à jour la sortie du projet**|L'événement post\-build est exécuté uniquement lorsque le fichier de sortie du compilateur \(.exe ou .dll\) est différent du fichier de sortie précédent.  Un événement post\-build n'est pas exécuté si un projet est à jour.|  
  
## Voir aussi  
 [Page Compiler, Concepteur de projets \(Visual Basic\)](../../ide/reference/compile-page-project-designer-visual-basic.md)   
 [Comment : spécifier des événements de build \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md)   
 [Ligne de commande de l’événement pré\-build\/post\-build, boîte de dialogue](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)