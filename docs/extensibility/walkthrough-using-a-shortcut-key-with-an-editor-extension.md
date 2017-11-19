---
title: "Procédure pas à pas : Utilisation une touche de raccourci avec une Extension de l’éditeur | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
caps.latest.revision: "32"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8066ac52076afd9c0f8cb697ca51327188c9c216
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-using-a-shortcut-key-with-an-editor-extension"></a>Procédure pas à pas : Utilisation une touche de raccourci avec une Extension de l’éditeur
Vous pouvez répondre aux touches de raccourci dans votre extension de l’éditeur. La procédure suivante montre comment ajouter un ornement de la vue à une vue de texte à l’aide d’une touche de raccourci. Cette procédure pas à pas est basée sur le modèle de l’éditeur d’ornement de la fenêtre d’affichage, et il vous permet d’ajouter l’ornement à l’aide du caractère « + ».  
  
## <a name="prerequisites"></a>Conditions préalables  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS ultérieurement. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Création d’un projet Managed Extensibility Framework (MEF)  
  
1.  Créez un projet VSIX c#. (Dans le **nouveau projet** boîte de dialogue, sélectionnez **Visual c# / extensibilité**, puis **projet VSIX**.) Nommez la solution `KeyBindingTest`.  
  
2.  Ajouter un modèle d’élément ornement de texte de l’éditeur au projet et nommez-le `KeyBindingTest`. Pour plus d’informations, consultez [création d’une Extension avec un éditeur de modèle d’élément](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Ajoutez les références suivantes et définissez **CopyLocal** à `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Assemblys Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
 Dans le fichier de classe KeyBindingTest, modifiez le nom de classe pour PurpleCornerBox. Utilisez l’ampoule qui s’affiche dans la marge de gauche pour effectuer les autres modifications appropriées. Dans le constructeur, modifier le nom de la couche d’ornement de **KeyBindingTest** à **PurpleCornerBox**:  
  
```csharp  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  
  
## <a name="defining-the-command-filter"></a>Définir le filtre de commande  
 Le filtre de commande est une implémentation de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, qui gère la commande en instanciant l’ornement.  
  
1.  Ajoutez un fichier de classe et nommez-le `KeyBindingCommandFilter`.  
  
2.  Ajoutez les instructions using suivantes.  
  
    ```csharp  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Text.Editor;  
  
    ```  
  
3.  Doit hériter de la classe nommée KeyBindingCommandFilter <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
    ```csharp  
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4.  Ajouter des champs privés pour l’affichage de texte, la commande suivante dans la chaîne de commande et d’un indicateur pour représenter si le filtre de commande a déjà été ajouté.  
  
    ```csharp  
    private IWpfTextView m_textView;  
    internal IOleCommandTarget m_nextTarget;  
    internal bool m_added;  
    internal bool m_adorned;  
    ```  
  
5.  Ajoutez un constructeur qui définit l’affichage de texte.  
  
    ```csharp  
    public KeyBindingCommandFilter(IWpfTextView textView)  
    {  
        m_textView = textView;  
        m_adorned = false;  
    }  
    ```  
  
6.  Implémentez la `QueryStatus()` méthode comme suit.  
  
    ```vb  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7.  Implémentez la `Exec()` méthode afin qu’il ajoute une zone violette à la vue si un + caractère est tapé.  
  
    ```csharp  
    int IOleCommandTarget.Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)  
    {  
        if (m_adorned == false)  
        {  
            char typedChar = char.MinValue;  
  
            if (pguidCmdGroup == VSConstants.VSStd2K && nCmdID == (uint)VSConstants.VSStd2KCmdID.TYPECHAR)  
            {  
                typedChar = (char)(ushort)Marshal.GetObjectForNativeVariant(pvaIn);  
                if (typedChar.Equals('+'))  
                {  
                    new PurpleCornerBox(m_textView);  
                    m_adorned = true;  
                }  
            }  
        }  
        return m_nextTarget.Exec(ref pguidCmdGroup, nCmdID, nCmdexecopt, pvaIn, pvaOut);  
    }  
  
    ```  
  
## <a name="adding-the-command-filter"></a>Ajout du filtre de commande  
 Le fournisseur d’ornement doit ajouter un filtre de commande à l’affichage de texte. Dans cet exemple, le fournisseur implémente <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> pour écouter les événements de création de vue de texte. Ce fournisseur d’ornement exporte également la couche d’ornement, qui définit l’ordre de plan de l’ornement.  
  
1.  Dans le fichier KeyBindingTestTextViewCreationListener, ajoutez le code suivant à l’aide des instructions :  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio.Utilities;  
    using Microsoft.VisualStudio.Editor;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.TextManager.Interop;  
  
    ```  
  
2.  Dans la définition de la couche d’ornement, modifier le nom de la AdornmentLayer de **KeyBindingTest** à **PurpleCornerBox**.  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  
  
3.  Pour obtenir de l’adaptateur de vue de texte, vous devez importer le <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>.  
  
    ```csharp  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
4.  Modifier la <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> méthode afin qu’il ajoute le `KeyBindingCommandFilter`.  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
5.  Le `AddCommandFilter` gestionnaire obtient l’adaptateur de vue de texte et ajoute le filtre de commande.  
  
    ```csharp  
    void AddCommandFilter(IWpfTextView textView, KeyBindingCommandFilter commandFilter)  
    {  
        if (commandFilter.m_added == false)  
        {  
            //get the view adapter from the editor factory  
            IOleCommandTarget next;   
            IVsTextView view = editorFactory.GetViewAdapter(textView);  
  
            int hr = view.AddCommandFilter(commandFilter, out next);  
  
            if (hr == VSConstants.S_OK)  
            {      
                commandFilter.m_added = true;  
                 //you'll need the next target for Exec and QueryStatus   
                if (next != null)  
                commandFilter.m_nextTarget = next;  
            }  
        }  
    }  
    ```  
  
## <a name="making-the-adornment-appear-on-every-line"></a>Rendre l’ornement apparaissent sur chaque ligne.  
 L’ornement d’origine figurait sur tous les caractères « a » dans un fichier texte. Maintenant que nous avons modifié le code pour ajouter l’ornement en réponse au caractère « + », il ajoute l’ornement uniquement sur la ligne où le « + » est tapée. Nous pouvons modifier le code d’ornement afin qu’une fois de plus l’ornement apparaisse sur chaque « a ».  
  
 Dans le fichier KeyBindingTest.cs, modifier la méthode CreateVisuals() pour parcourir toutes les lignes dans la vue pour décorer le caractère « a ».  
  
```csharp  
private void CreateVisuals(ITextViewLine line)  
{  
    IWpfTextViewLineCollection textViewLines = this.view.TextViewLines;  
  
    foreach (ITextViewLine textViewLine in textViewLines)  
    {  
        if (textViewLine.ToString().Contains("a"))  
        {  
            // Loop through each character, and place a box around any 'a'   
            for (int charIndex = textViewLine.Start; charIndex < textViewLine.End; charIndex++)  
            {  
                if (this.view.TextSnapshot[charIndex] == 'a')  
                {  
                    SnapshotSpan span = new SnapshotSpan(this.view.TextSnapshot, Span.FromBounds(charIndex, charIndex + 1));  
                    Geometry geometry = textViewLines.GetMarkerGeometry(span);  
                    if (geometry != null)  
                    {  
                        var drawing = new GeometryDrawing(this.brush, this.pen, geometry);  
                        drawing.Freeze();  
  
                        var drawingImage = new DrawingImage(drawing);  
                        drawingImage.Freeze();  
  
                        var image = new Image  
                        {  
                            Source = drawingImage,  
                        };  
  
                        // Align the image with the top of the bounds of the text geometry  
                        Canvas.SetLeft(image, geometry.Bounds.Left);  
                        Canvas.SetTop(image, geometry.Bounds.Top);  
  
                        this.layer.AddAdornment(AdornmentPositioningBehavior.TextRelative, span, null, image, null);  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="building-and-testing-the-code"></a>Création et test du code  
  
1.  Générez la solution KeyBindingTest et l’exécuter dans l’instance expérimentale.  
  
2.  Créez ou ouvrez un fichier texte. Tapez des mots contenant le caractère « a », puis tapez + n’importe où dans l’affichage de texte.  
  
     Un carré violet doit apparaître sur chaque caractère « a » dans le fichier.