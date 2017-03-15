---
title: "Extension des fen&#234;tres Outil | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "fenêtres (SDK Visual Studio), outil"
  - "fenêtres de document"
  - "fenêtres Outil"
  - "fenêtres (SDK Visual Studio), document"
ms.assetid: 252f7b99-b44a-4a63-88d9-3a0ca48ac4f1
caps.latest.revision: 37
caps.handback.revision: 37
manager: "douge"
---
# Extension des fen&#234;tres Outil
Les fenêtres Outil Visual Studio sont en général des fenêtres en lecture seule qui ne sont pas basées sur des fichiers. En cela, elles diffèrent des fenêtres de document qui affichent des fichiers en mode lecture\-écriture. La **Boîte à outils**, l’**Explorateur de solutions**, la fenêtre **Propriétés** et le **Navigateur web** sont des exemples de fenêtres Outil.  
  
 Toutes les fenêtres Outil dans Visual Studio 2010 et versions ultérieures sont basées sur WPF. Dans les versions de Visual Studio antérieures à Visual Studio 2010, les fenêtres Outil étaient basées sur Windows Forms. Vous pouvez toujours afficher des fenêtres basées sur Windows Forms, mais les nouvelles fenêtres Outil doivent être basées sur WPF.  
  
## Éléments de base des fenêtres Outil  
 Pour fournir une fenêtre Outil, vous devez l’inscrire auprès de Visual Studio et spécifier sa taille et son emplacement par défaut. Pour plus d’informations, consultez [Fenêtres Outil dans le Registre](../extensibility/tool-windows-in-the-registry.md).  
  
 Pour créer ou ouvrir des fenêtres Outil, vous devez généralement cliquer sur une commande de menu. Pour créer une fenêtre Outil par programmation, consultez [Ouverture d’une fenêtre Outil par programmation](../misc/opening-a-tool-window-programmatically.md).  
  
 Les fenêtres Outil sont par défaut à instance unique, ce qui signifie que seule une instance de la fenêtre Outil peut être ouverte à la fois. Quand une fenêtre Outil à instance unique est ouverte, elle le reste jusqu’à la fermeture de l’IDE. Si vous cliquez sur le bouton Fermer d’une fenêtre Outil à instance unique, seule sa visibilité change. Vous pouvez également créer des fenêtres Outil multi\-instances, ce qui vous permet d’ouvrir simultanément plusieurs instances de la fenêtre. Pour plus d’informations, consultez [Création d’une fenêtre d’outil d’instances multiples](../extensibility/creating-a-multi-instance-tool-window.md).  
  
 Dans le frame de document, les fenêtres Outils peuvent être des fenêtres ancrées,  flottantes ou avec onglets. Le frame de fenêtre Outil, fourni par l’IDE, permet de contrôler la taille, l’emplacement, l’état d’ancrage et d’autres propriétés persistantes. Le volet de la fenêtre Outil affiche le contenu. La taille et l’emplacement par défaut s’appliquent uniquement à la première ouverture de la fenêtre Outil ; après cela, l’état de la fenêtre Outil est rendu persistant.  
  
 Les volets de la fenêtre Outil peuvent héberger des contrôles utilisateur WPF et prendre en charge des barres d’outils. Vous pouvez substituer la propriété <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> pour retourner le handle du contrôle hébergé.  
  
 Les fenêtres Outil peuvent être *dynamiques* \(c’est\-à\-dire *visibles automatiquement*\). Les fenêtres Outil dynamiques sont visibles dès que le contexte d’interface utilisateur associé s’applique. La visibilité automatique peut permettre de réduire l’encombrement des fenêtres dans l’IDE. Pour plus d’informations, consultez [Ouverture d'une fenêtre outil dynamique](../extensibility/opening-a-dynamic-tool-window.md).  
  
 Les VSPackages ne sont pas la seule façon de créer une fenêtre Outil. Vous pouvez utiliser des compléments pour créer une fenêtre Outil à l’aide du modèle Automation de Visual Studio. Pour plus d’informations, consultez [Comment : créer et contrôler des fenêtres Outil](../Topic/How%20to:%20Create%20and%20Control%20Tool%20Windows.md).  
  
## Voir aussi  
 [Tool Windows](../misc/extending-tool-windows.md)   
 [Fenêtres de document](../extensibility/internals/document-windows.md)   
 [Ajout de la recherche dans une fenêtre outil](../extensibility/adding-search-to-a-tool-window.md)