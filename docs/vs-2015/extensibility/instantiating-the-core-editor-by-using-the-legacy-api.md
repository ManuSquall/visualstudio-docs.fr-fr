---
title: Instanciation de l’éditeur principal à l’aide de l’API héritée | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 29306a16390039c8ee6e424b81a5ff617e533ab4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203908"
---
# <a name="instantiating-the-core-editor-by-using-the-legacy-api"></a>Instanciation de l’éditeur de base à l’aide de l’API héritée
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’éditeur est responsable des fonctions d’édition de texte telles que l’insertion, la suppression, la copie et le collage. Il combine ces fonctions avec celles fournies par les services de langage, telles que la coloration du texte, la mise en retrait et la saisie semi-automatique des instructions IntelliSense.  
  
 Vous pouvez instancier une instance de l’éditeur principal de l’une des trois façons suivantes :  
  
- Créez explicitement une instance de l’éditeur principal dans une fenêtre.  
  
- Fournir une fabrique d’éditeur qui retourne une instance de l’éditeur principal  
  
- Ouvrez un fichier à partir de la hiérarchie du projet.  
  
  Les sections suivantes expliquent comment utiliser l’API héritée pour instancier l’éditeur.  
  
## <a name="explicitly-opening-a-core-editor-instance"></a>Ouverture explicite d’une instance de l’éditeur principal  
 Lors de l’obtention explicite d’une instance de l’éditeur principal :  
  
- Obtenez un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> pour contenir l’objet de données de document en cours de modification.  
  
- Créez une représentation orientée ligne de l’objet de données de document en créant une <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> interface à partir de l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interface.  
  
- Définissez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> en tant qu’objet de données de document pour une instance de l’implémentation par défaut de l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> interface, à l’aide de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> méthode.  
  
   Hébergez l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> instance dans une <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interface à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> méthode.  
  
  À ce stade, l’affichage de l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interface fournit une fenêtre qui contient une instance de l’éditeur principal.  
  
  Toutefois, il ne s’agit pas d’une instance très utile, car elle n’a pas de touches de raccourci, ni d’accès à des fonctionnalités avancées. Pour obtenir l’accès aux touches de raccourci et aux fonctionnalités avancées :  
  
- Utilisez la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> méthode pour associer un service de langage et l’objet de données de document que l’éditeur utilise.  
  
- Vous pouvez créer vos propres touches de raccourci ou utiliser le système par défaut en définissant les <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> propriétés d’affichage des objets. Pour ce faire, appelez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A> méthode avec la <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> propriété.  
  
   Pour obtenir et utiliser des touches de raccourci non standard, générez-les à l’aide du fichier. vsct. Pour plus d'informations, consultez [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>Comment utiliser une fabrique d’éditeur pour obtenir l’éditeur de base  
 Lors de l’implémentation d’un éditeur principal avec une fabrique d’éditeur à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> méthode, suivez toutes les étapes décrites dans la section précédente pour héberger explicitement un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> objet à l’aide d’un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> objet de données de document dans un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objet.  
  
 Pour afficher le texte, obtenez une <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface à partir de l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> objet et appelez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> méthode.  
  
 Pour fournir un service de langage à l’éditeur, appelez la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> méthode dans la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> méthode.  
  
 Pour obtenir les touches de raccourci par défaut, contrairement à la section précédente, vous utilisez le contexte de commande retourné par la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> méthode lors de l’obtention de l’éditeur de base à partir de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> méthode.  
  
 Si la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> méthode retourne le même GUID de commande que l’éditeur de texte, l’instance de l’éditeur principal obtient automatiquement les touches de raccourci par défaut.  
  
 Pour obtenir des informations générales, consultez [procédure pas à pas : création d’un éditeur principal et inscription d’un type de fichier d’éditeur](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Dans l’éditeur de base](../extensibility/inside-the-core-editor.md)   
 [Ouverture et enregistrement d’éléments de projet](../extensibility/internals/opening-and-saving-project-items.md)   
 [Procédure pas à pas : création d’un éditeur de base et inscription d’un type de fichier d’éditeur](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)
