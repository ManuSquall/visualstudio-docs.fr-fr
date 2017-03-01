---
title: "L’instanciation de l’éditeur principal à l’aide de l’API héritée | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e18118d73d46aeee7612eb7dff64f778726778f0
ms.lasthandoff: 02/22/2017

---
# <a name="instantiating-the-core-editor-by-using-the-legacy-api"></a>L’instanciation de l’éditeur principal à l’aide de l’API héritée
L’éditeur est responsable de la modification des fonctions telles que l’insertion, suppression, copier et coller de texte. Il combine ces fonctions avec celles fournies par les services de langage, telles que la coloration du texte, le retrait et saisie semi-automatique des instructions IntelliSense.  
  
 Vous pouvez instancier une instance de l’éditeur principal de trois manières :  
  
-   Créer explicitement une instance de la base éditeur dans une fenêtre.  
  
-   Fournir une fabrique d’éditeur qui retourne une instance de l’éditeur de base  
  
-   Ouvrez un fichier à partir de la hiérarchie de projet.  
  
 Les sections suivantes expliquent comment utiliser l’API héritée pour instancier l’éditeur.  
  
## <a name="explicitly-opening-a-core-editor-instance"></a>Ouvrir explicitement une Instance de l’éditeur de base  
 Lors de l’obtention explicitement une instance de l’éditeur de base :  
  
-   Obtenir un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>pour contenir l’objet de données de document en cours de modification.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>  
  
-   Créer une représentation sous forme de ligne de l’objet de données de document en créant un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>à partir de l’interface du <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>  
  
-   Définir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>que l’objet de données de document d’une instance de l’implémentation par défaut de le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>de l’interface, à l’aide de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A>(méthode).</xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>  
  
     Hôte la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>d’instance dans un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>interface à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A>méthode.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>  
  
 À ce stade, affichant les <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>interface fournit une fenêtre qui contient une instance de l’éditeur principal.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>  
  
 Toutefois, cela n’est pas une instance très utile, car elle ne pas avoir des touches de raccourci, ou accéder à des fonctionnalités avancées. Pour obtenir l’accès à des touches de raccourci et des fonctionnalités avancées :  
  
-   Utilisez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>pour associer un service de langage et l’objet de données de document qui utilise l’éditeur.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>  
  
-   Créez vos propres touches de raccourci, ou utiliser la valeur par défaut du système en définissant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>objets affichent les propriétés.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> Pour ce faire, appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A>méthode avec la <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>propriété.</xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> </xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A>  
  
     Pour obtenir et utiliser les touches de raccourci non standard, les générer à l’aide du fichier .vsct. Pour plus d’informations, consultez [Table de commandes Visual Studio (. Les fichiers VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>L’utilisation d’une fabrique d’éditeur pour obtenir de l’éditeur de base  
 Lors de l’implémentation d’un éditeur de base avec une fabrique d’éditeur à l’aide la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>(méthode), suivez les étapes décrites dans la section précédente pour héberger explicitement un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>à l’aide un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>des données du document de l’objet, dans un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>objet.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> </xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>  
  
 Pour afficher le texte, vous devez obtenir un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>à partir de l’interface du <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>objet et appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>(méthode).</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>  
  
 Pour fournir un service de langage pour l’éditeur, appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>méthode au sein de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>méthode.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>  
  
 Pour obtenir par défaut des touches de raccourci, contrairement à la section précédente, vous utilisez le contexte de commande retourné par la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>méthode lors de l’obtention de l’éditeur de base à partir de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>méthode.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>  
  
 Si le <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>méthode renvoie la même commande GUID en tant que l’éditeur de texte, l’instance de l’éditeur principal obtient automatiquement la valeur par défaut des touches de raccourci.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>  
  
 Pour plus d’informations, consultez [procédure pas à pas : création d’un éditeur de base et l’inscription d’un Type de fichier éditeur](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Dans l’éditeur de base](../extensibility/inside-the-core-editor.md)   
 [Ouvrir et enregistrer des éléments de projet](../extensibility/internals/opening-and-saving-project-items.md)   
 [Procédure pas à pas : Création d’un éditeur de base et l’inscription d’un Type de fichier de l’éditeur](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)
