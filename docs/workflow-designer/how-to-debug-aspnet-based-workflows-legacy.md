---
title: 'Le Concepteur de flux de travail - Comment : déboguer des Workflows basés sur ASP.NET (héritée)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- ASP.NET, debugging workflows
- debugging workflows, ASP.NET workflows
- ASP.NET workflows, debugging
- debugging, ASP.NET workflows
ms.assetid: 79b21edc-9e7d-410d-af68-09c1598b9c30
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 7bf16a6a88c5d4cd063f1c32ca846031d8b2588d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31975870"
---
# <a name="how-to-debug-aspnet-based-workflows-legacy"></a>Procédure : déboguer des workflows basés sur ASP.NET (héritée)

Cette rubrique décrit comment déboguer les applications basés sur ASP.NET Windows Workflow Foundation (WF) qui ciblent soit la version .NET Framework 3.5 ou le WinFX dans le Concepteur de flux de travail Windows hérité.

Vous pouvez déboguer des workflows hérités démarrés dans les ASP.NET ou des workflows hérités publiés en tant que services Web en les attachant au processus dans lequel le workflow est hébergé.

## <a name="to-debug-an-aspnet-based-workflow"></a>Pour déboguer des workflows basés sur ASP.NET

1.  Activer le débogage de l’application ASP.NET en affectant **debug = true** dans le fichier web.config.

2.  Définissez la bibliothèque de workflow comme projet de démarrage, et définissez des points d'arrêt sur le workflow.

3.  Entrez l’URL de la page Web par défaut dans les propriétés de projet de flux de travail **déboguer** option **démarrer le navigateur avec l’URL externe** zone de texte.

4.  Sélectionnez **attacher au processus** sur la **déboguer** menu.

5.  Sélectionnez le processus à joindre dans le **processus disponibles** liste.

     Effectuez une jointure au processus w3wp.exe, webdev.webserver, ou aspnet_wp dans lequel le workflow est hébergé.

6.  Cliquez sur **sélectionnez** à côté du **attacher au** zone de texte.

     Le **sélectionner le Type de Code** boîte de dialogue s’affiche.

7.  Sélectionnez **déboguer ces types de codes** et sélectionnez **Workflow**.

8.  Cliquez sur **OK**.

9. Cliquez sur **Attacher**.

10. Ouvrez la page web par défaut dans un navigateur et démarrez le workflow.

## <a name="see-also"></a>Voir aussi

- [Appel du débogueur Visual Studio pour Windows Workflow Foundation (hérité)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)
- [Guide pratique pour définir des points d’arrêt dans les flux de travail (hérité)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)
- [Débogage de flux de travail hérités](../workflow-designer/debugging-legacy-workflows.md)