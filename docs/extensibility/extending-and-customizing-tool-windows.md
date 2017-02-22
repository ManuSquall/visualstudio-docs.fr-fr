---
title: "Extension et personnalisation des fen&#234;tres Outil | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "interfaces utilisateur, essentials"
  - "fenêtres Outil, standards"
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Extension et personnalisation des fen&#234;tres Outil
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio fournit plusieurs types différents de windows, par exemple les fenêtres Outil fenêtres et boîtes de dialogue. Autres fenêtres, telles que la fenêtre Propriétés, la fenêtre Sortie et la fenêtre liste des tâches, sont des types de fenêtres Outil.  
  
## Fenêtres d'outils  
 Fenêtres Outil de Visual Studio sont généralement en lecture seule windows qui ne sont pas des fichiers. Dans ce qu'ils diffèrent des fenêtres de document, qui affichent les fichiers en mode lecture\-écriture. Le **boîte à outils**, **l'Explorateur de solutions**, **propriétés** fenêtre, et **navigateur Web** sont des exemples de fenêtres Outil.  
  
 Pour savoir comment créer une fenêtre outil simple, consultez [Ajout d’une fenêtre outil](../extensibility/adding-a-tool-window.md).  
  
 Pour enregistrer une fenêtre outil dans Visual Studio, consultez [L’inscription d’une fenêtre outil](../extensibility/registering-a-tool-window.md).  
  
 Fenêtres Outil sont uniques par défaut, ce qui signifie que seulement une instance de la fenêtre outil peut être ouvert à la fois. Après l'ouverture d'une fenêtre outil d'instance unique, elle reste ouverte jusqu'à ce que l'interface IDE est fermée. Lorsque vous fermez une fenêtre outil d'instance unique, seulement sa visibilité change. Vous pouvez également créer de multi\-instance fenêtres Outil, telles que plusieurs instances de la fenêtre peuvent être ouverts simultanément. Pour plus d'informations, voir [Création d’une fenêtre d’outil d’instances multiples](../extensibility/creating-a-multi-instance-tool-window.md).  
  
 Les fenêtres Outil peuvent être *dynamique*, ce qui signifie qu'ils sont visibles dès que leur contexte de l'interface utilisateur associée s'applique. L'utilisation de visibilité automatique peut réduire l'encombrement des fenêtres dans l'IDE. Pour plus d'informations, consultez [Ouverture d'une fenêtre outil dynamique](../extensibility/opening-a-dynamic-tool-window.md).  
  
 Fenêtres d'outils peuvent être ancrée, flottante ou à onglets dans le cadre du document. Le frame de fenêtre outil est fourni par l'IDE et est utilisé pour contrôler la taille, emplacement, état d'ancrage et les autres propriétés persistantes. Le volet de fenêtre outil affiche le contenu. La taille par défaut et l'emplacement s'applique uniquement lorsque la fenêtre outil est tout d'abord ouvert ; une fois que l'état de la fenêtre outil est rendue persistante.  
  
 Volets de la fenêtre outil peuvent héberger des contrôles utilisateur WPF et prendre en charge les barres d'outils. Vous pouvez remplacer le <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> propriété à retourner le handle du contrôle hébergé.  
  
 Vous pouvez ajouter de nombreuses fonctionnalités pour les fenêtres Outil. Par exemple, vous pouvez ajouter une barre d'outils : [Ajout d'une barre d'outils à une fenêtre outil](../extensibility/adding-a-toolbar-to-a-tool-window.md) ou un menu contextuel : [Ajout d'un Menu contextuel dans une fenêtre outil](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). Vous pouvez ajouter un contrôle de recherche qui permet de rechercher des éléments à l'intérieur de votre fenêtre outil : [Ajout de la recherche dans une fenêtre outil](../extensibility/adding-search-to-a-tool-window.md).  
  
 Vous pouvez vous abonner à des événements de fenêtre outil : [S'abonner à un événement](../extensibility/subscribing-to-an-event.md).  
  
## Extension des fenêtres Outil existantes  
 Vous pouvez ajouter des informations à propos de votre fenêtre outil vers un nouveau **Options** page et un nouveau paramètre sur le **propriétés** page, écrire dans le **liste des tâches** et **sortie** windows. Pour plus d’informations, consultez [Extension de propriétés, liste des tâches, sortie, les Options Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md) et [Extension de propriétés, liste des tâches, sortie, les Options Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).  
  
## Boîtes de dialogue modales  
 Dans une extension Visual Studio, vous devez créer des boîtes de dialogue modales par dérivation à partir de <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>, qui vous permet de contrôler les et le reste de l'interface utilisateur. Pour plus d'informations, consultez.[Créer et gérer des boîtes de dialogue modales](../extensibility/creating-and-managing-modal-dialog-boxes.md).  
  
## Voir aussi  
 [Création d'une Extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md)