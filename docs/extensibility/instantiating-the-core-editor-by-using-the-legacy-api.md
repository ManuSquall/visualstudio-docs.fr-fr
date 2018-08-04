---
title: L’instanciation de l’éditeur principal à l’aide de l’API héritée | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 602adf27a0a165a8919d4be928a330dc3a212cf3
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500473"
---
# <a name="instantiate-the-core-editor-by-using-the-legacy-api"></a>Instancier l’éditeur principal à l’aide de l’API héritée
L’éditeur est responsable de la modification des fonctions telles que l’insertion, suppression, copier et coller de texte. Il combine ces fonctions avec les fonctions fournies par les services de langage, telles que la coloration du texte, de mise en retrait et de saisie semi-automatique des instructions IntelliSense.  
  
 Vous pouvez instancier une instance de l’éditeur principal de l’une des trois façons :  
  
-   Créer explicitement une instance de la base éditeur dans une fenêtre.  
  
-   Fournir une fabrique d’éditeur qui retourne une instance de l’éditeur principal  
  
-   Ouvrez un fichier à partir de la hiérarchie de projet.  
  
 Les sections suivantes expliquent comment utiliser l’API héritée pour instancier l’éditeur.  
  
## <a name="explicitly-open-a-core-editor-instance"></a>Ouvrir explicitement une instance d’éditeur core  
 Lors de l’obtention explicitement une instance de l’éditeur principal :  
  
-   Obtenir un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> doit contenir l’objet de données de document en cours de modification.  
  
-   Créer une représentation sous forme de ligne de l’objet de données de document en créant un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> de l’interface à partir de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interface.  
  
-   Définissez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> en tant que l’objet de données pour une instance de l’implémentation par défaut de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> interface, à l’aide de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> (méthode).  
  
     Hôte du <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> d’instance dans un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interface à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> (méthode).  
  
 À ce stade, affichant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interface fournit une fenêtre qui contient une instance de l’éditeur principal.  
  
 Toutefois, cela n’est pas une instance de très utile, car il n’ont des touches de raccourci, ni accéder aux fonctionnalités avancées. Pour obtenir l’accès à des touches de raccourci et des fonctionnalités avancées :  
  
-   Utilisez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> pour associer un service de langage et de l’objet de données de document qui utilise l’éditeur.  
  
-   Créer vos propres touches de raccourci, ou utiliser la valeur par défaut du système en définissant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objets affichent les propriétés. Pour ce faire, appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A> méthode avec le <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> propriété.  
  
     Pour obtenir et utiliser les touches de raccourci non standard, les générer à l’aide de la *.vsct* fichier. Pour plus d’informations, consultez [fichiers Visual Studio command table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>Comment utiliser une fabrique d’éditeur pour obtenir de l’éditeur principal  
 Lors de l’implémentation d’un éditeur principal avec une fabrique d’éditeur à l’aide la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> (méthode), suivez les étapes décrites dans la section précédente pour héberger explicitement un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> à l’aide un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> d’objet de données de document, dans un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objet.  
  
 Pour afficher le texte, vous devez obtenir un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> de l’interface à partir de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> objet et appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> (méthode).  
  
 Pour fournir un service de langage à l’éditeur, appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> méthode au sein de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> (méthode).  
  
 Pour obtenir par défaut des touches de raccourci, contrairement à la section précédente, vous utilisez le contexte de la commande retourné par la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> méthode lors de l’obtention de l’éditeur principal à partir de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> (méthode).  
  
 Si le <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> méthode retourne la même commande GUID en tant que l’éditeur de texte, l’instance de l’éditeur principal obtient automatiquement la valeur par défaut des touches de raccourci.  
  
 Pour obtenir des informations générales, consultez [procédure pas à pas : créer un cœur éditeur et l’inscription d’un type de fichier éditeur](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md).  
  
## <a name="see-also"></a>Voir aussi  
 [À l’intérieur de l’éditeur principal](../extensibility/inside-the-core-editor.md)   
 [Ouvrir et enregistrer des éléments de projet](../extensibility/internals/opening-and-saving-project-items.md)   
 [Procédure pas à pas : Créer un éditeur de base et l’inscription d’un type de fichier d’éditeur](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)