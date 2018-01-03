---
title: "Événements de build, boîte de dialogue (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vb.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- build events, specifying
- pre-build events
- Build Events dialog box
- post-build events
ms.assetid: 3a81a7c7-39f9-47a8-ba5a-b351227f380e
caps.latest.revision: "4"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: da28d0858784a8e71006c0ec072c3aea5110037e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="build-events-dialog-box-visual-basic"></a>Événements de build, boîte de dialogue (Visual Basic)
Utilisez la boîte de dialogue **Événements de build** pour spécifier des instructions de configuration de build. Vous pouvez également spécifier les conditions dans lesquelles les événements pré-build ou post-build sont exécutés. Pour plus d’informations, consultez [Guide pratique pour spécifier des événements de build (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).  
  
 **Ligne de commande de l’événement pré-build**  
 Spécifie les commandes à exécuter avant le début de la génération. Pour taper de longues commandes, cliquez sur **Modifier pré-build** pour afficher la [boîte de dialogue Ligne de commande de l’événement pré-build/post-build](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).  
  
> [!NOTE]
>  Les événements pré-build ne s’exécutent pas si le projet est à jour et qu’aucune build n’est déclenchée.  
  
 **Ligne de commande de l’événement post-build**  
 Spécifie les commandes à exécuter à l’issue de la génération. Pour taper de longues commandes, cliquez sur **Modifier post-build** pour afficher la **boîte de dialogue Ligne de commande de l’événement pré-build/post-build**.  
  
> [!NOTE]
>  Ajoutez une instruction `call` avant toutes les commandes post-build qui exécutent des fichiers .bat. Par exemple, `call C:\MyFile.bat` ou `call C:\MyFile.bat call C:\MyFile2.bat`.  
  
 **Exécuter l’événement post-build**  
 Spécifie les conditions pour l’événement post-build à exécuter, comme indiqué dans le tableau ci-dessous.  
  
|Option|Résultat|  
|------------|------------|  
|**Toujours**|L’événement post-build est exécuté, que la build ait abouti ou échoué.|  
|**En cas de build réussie** |L’événement post-build est exécuté si la build réussit. L’événement est exécuté même pour un projet à jour, à condition que la build soit un succès. Il s'agit du paramètre par défaut.|  
|**Lorsque la build met à jour la sortie du projet**|L’événement post-build n’est exécuté que quand le fichier de sortie du compilateur (.exe ou .dll) est différent du fichier de sortie précédent. Un événement post-build n’est pas exécuté si un projet est à jour.|  
  
## <a name="see-also"></a>Voir aussi  
 [Page Compiler, Concepteur de projet (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)   
 [Guide pratique pour spécifier des événements de build (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)   
 [Ligne de commande de l’événement pré-build/post-build, boîte de dialogue](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)