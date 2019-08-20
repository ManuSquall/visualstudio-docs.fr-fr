---
title: 'Procédure : Déboguer des Workflows basés sur ASP.NET (hérité) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- ASP.NET, debugging workflows
- debugging workflows, ASP.NET workflows
- ASP.NET workflows, debugging
- debugging, ASP.NET workflows
ms.assetid: 79b21edc-9e7d-410d-af68-09c1598b9c30
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a8fc6c951f1da3fc37fe8e1189a3ec8de9609a48
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68144651"
---
# <a name="how-to-debug-aspnet-based-workflows-legacy"></a>Procédure : Déboguer des workflows basés sur ASP.NET (hérités)
Cette rubrique décrit comment déboguer des applications [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] basées sur [!INCLUDE[wf](../includes/wf-md.md)] qui ciblent le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] dans le [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité.  
  
 Vous pouvez déboguer des workflows hérités démarrés dans les ASP.NET ou des workflows hérités publiés en tant que services Web en les attachant au processus dans lequel le workflow est hébergé.  
  
### <a name="to-debug-an-aspnet-based-workflow"></a>Pour déboguer des workflows basés sur ASP.NET  
  
1. Activer le débogage pour l’application ASP.NET en définissant **debug = true** dans le fichier web.config.  
  
2. Définissez la bibliothèque de workflow comme projet de démarrage, et définissez des points d'arrêt sur le workflow.  
  
3. Entrez l’URL de la page Web par défaut dans les propriétés de projet de flux de travail **déboguer** option **démarrer le navigateur avec l’URL externe** zone de texte.  
  
4. Sélectionnez **attacher au processus** sur le **déboguer** menu.  
  
5. Sélectionnez le processus à attacher dans la **processus disponibles** liste.  
  
     Effectuez une jointure au processus w3wp.exe, webdev.webserver, ou aspnet_wp dans lequel le workflow est hébergé.  
  
6. Cliquez sur **sélectionnez** à côté du **attacher au** zone de texte.  
  
     Le **sélectionner le Type de Code** boîte de dialogue s’affiche.  
  
7. Sélectionnez **déboguer ces types de codes** et sélectionnez **Workflow**.  
  
8. Cliquez sur **OK**.  
  
9. Cliquez sur **Attacher**.  
  
10. Ouvrez la page web par défaut dans un navigateur et démarrez le workflow.  
  
## <a name="see-also"></a>Voir aussi  
 [Appel du débogueur Visual Studio pour Windows Workflow Foundation (hérité)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)   
 [Guide pratique : Définissez des points d’arrêt dans le flux de travail (hérité)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)   
 [Débogage de flux de travail hérités](../workflow-designer/debugging-legacy-workflows.md)