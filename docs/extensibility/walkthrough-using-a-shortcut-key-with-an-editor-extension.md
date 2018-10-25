---
title: 'Procédure pas à pas : Utilisation d’une touche de raccourci avec une Extension d’éditeur | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d009351efdd36e0d415d0e2e457f7974608ab665
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886498"
---
# <a name="walkthrough-use-a-shortcut-key-with-an-editor-extension"></a>Procédure pas à pas : Utiliser une touche de raccourci avec une extension de l’éditeur
Vous pouvez répondre aux touches de raccourci dans votre extension de l’éditeur. La procédure suivante montre comment ajouter un ornement de la vue à une vue de texte à l’aide d’une touche de raccourci. Cette procédure pas à pas est basée sur le modèle d’éditeur ornement fenêtre d’affichage, et il vous permet d’ajouter l’ornement à l’aide du caractère « + ».  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [installer le SDK Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-managed-extensibility-framework-mef-project"></a>Créer un projet de Managed Extensibility Framework (MEF)  
  
1. Créez un projet c# VSIX. (Dans le **nouveau projet** boîte de dialogue, sélectionnez **Visual c# / extensibilité**, puis **projet VSIX**.) Nommez la solution `KeyBindingTest`.  
  
2. Ajouter un modèle d’élément ornement de texte de l’éditeur au projet et nommez-le `KeyBindingTest`. Pour plus d’informations, consultez [créer une Extension avec un éditeur de modèle d’élément](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Ajoutez les références suivantes et définissez **CopyLocal** à `false`:  
  
    Microsoft.VisualStudio.Editor  
  
    Assemblys Microsoft.VisualStudio.OLE.Interop  
  
    Microsoft.VisualStudio.Shell.14.0  
  
    Microsoft.VisualStudio.TextManager.Interop  
  
   Dans le fichier de classe KeyBindingTest, modifiez le nom de classe pour PurpleCornerBox. Utilisez l’ampoule qui s’affiche dans la marge de gauche pour rendre les autres modifications appropriées. Dans le constructeur, modifier le nom de la couche d’ornement de **KeyBindingTest** à **PurpleCornerBox**:  
  
```csharp  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  

Dans le fichier de classe KeyBindingTestTextViewCreationListener.cs, modifiez le nom de la AdornmentLayer de **KeyBindingTest** à **PurpleCornerBox**:
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  

## <a name="handle-typechar-command"></a>Commande TYPECHAR de handle
Avant Visual Studio 2017 version 15.6, la seule façon de gérer les commandes dans une extension de l’éditeur a été mise en œuvre un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> en fonction de filtre de commande. Visual Studio 2017 version 15.6 a introduit une approche simplifiée moderne, basée sur les gestionnaires de commandes de l’éditeur. Les deux sections suivantes montrent comment gérer une commande en utilisant à la fois l’approche hérité et moderne.

## <a name="define-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Définir le filtre de commande (avant Visual Studio 2017 version 15.6)

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
  
3.  La classe nommée KeyBindingCommandFilter doit hériter <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
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
  
    ```csharp  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7.  Implémentez le `Exec()` méthode afin qu’il ajoute une zone de violet à la vue si un signe plus (**+**) caractère est tapé.  
  
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
  
## <a name="add-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Ajoutez le filtre de commande (avant Visual Studio 2017 version 15.6)
 Le fournisseur de l’ornement doit ajouter un filtre de commande à l’affichage de texte. Dans cet exemple, le fournisseur implémente <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> pour écouter les événements de création de vue de texte. Ce fournisseur d’ornement exporte également la couche d’ornement, qui définit l’ordre de plan de l’ornement.  
  
1.  Dans le fichier KeyBindingTestTextViewCreationListener, ajoutez le code suivant à l’aide d’instructions :  
  
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
  
2.  Pour obtenir de l’adaptateur de vue de texte, vous devez importer le <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>.  
  
    ```csharp  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
3.  Modifier le <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> méthode afin qu’elle ajoute le `KeyBindingCommandFilter`.  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
4.  Le `AddCommandFilter` gestionnaire obtient l’adaptateur de vue de texte et ajoute le filtre de commande.  
  
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

## <a name="implement-a-command-handler-starting-in-visual-studio-2017-version-156"></a>Implémenter un gestionnaire de commandes (à partir de Visual Studio 2017 version 15.6)

Tout d’abord, mettez à jour les références du projet Nuget pour faire référence à l’API plus récente de l’éditeur :

1. Avec le bouton droit sur le projet, puis sélectionnez **gérer les Packages Nuget**.

2. Dans **Gestionnaire de Package Nuget**, sélectionnez le **mises à jour** onglet, sélectionnez le **sélectionner tous les packages** case à cocher, puis sélectionnez **mise à jour**.

Le Gestionnaire de commandes est une implémentation de <xref:Microsoft.VisualStudio.Commanding.ICommandHandler%601>, qui gère la commande en instanciant l’ornement.  
  
1. Ajoutez un fichier de classe et nommez-le `KeyBindingCommandHandler`.  
  
2. Ajoutez les instructions using suivantes.  
  
   ```csharp  
   using Microsoft.VisualStudio.Commanding;
   using Microsoft.VisualStudio.Text.Editor;
   using Microsoft.VisualStudio.Text.Editor.Commanding.Commands;
   using Microsoft.VisualStudio.Utilities;
   using System.ComponentModel.Composition;   
   ```  
  
3. La classe nommée KeyBindingCommandHandler doit hériter `ICommandHandler<TypeCharCommandArgs>`et exportez-le en tant que <xref:Microsoft.VisualStudio.Commanding.ICommandHandler>:
  
   ```csharp  
   [Export(typeof(ICommandHandler))]
   [ContentType("text")]
   [Name("KeyBindingTest")]
   internal class KeyBindingCommandHandler : ICommandHandler<TypeCharCommandArgs>  
   ```  
  
4. Ajouter un nom d’affichage du Gestionnaire de commande :  
  
   ```csharp  
   public string DisplayName => "KeyBindingTest";
   ```  
    
5. Implémentez la `GetCommandState()` méthode comme suit. Étant donné que ce gestionnaire de commande gère la commande TYPECHAR de l’éditeur core, elle peut déléguer l’activation de la commande pour l’éditeur principal.
  
   ```csharp  
   public CommandState GetCommandState(TypeCharCommandArgs args)
   {
       return CommandState.Unspecified;
   } 
   ```  
  
6. Implémentez le `ExecuteCommand()` méthode afin qu’il ajoute une zone de violet à la vue si un signe plus (**+**) caractère est tapé. 
  
   ```csharp  
   public bool ExecuteCommand(TypeCharCommandArgs args, CommandExecutionContext executionContext)
   {
       if (args.TypedChar == '+')
       {
           bool alreadyAdorned = args.TextView.Properties.TryGetProperty(
               "KeyBindingTextAdorned", out bool adorned) && adorned;
           if (!alreadyAdorned)
           {
               new PurpleCornerBox((IWpfTextView)args.TextView);
               args.TextView.Properties.AddProperty("KeyBindingTextAdorned", true);
           }
       }

       return false;
   }
   ```  
   7. Copier la définition de couche d’ornement à partir de *KeyBindingTestTextViewCreationListener.cs* de fichiers à la *KeyBindingCommandHandler.cs* , puis supprimez  *KeyBindingTestTextViewCreationListener.cs* fichier :
 
   ```csharp  
   /// <summary>
   /// Defines the adornment layer for the adornment. This layer is ordered
   /// after the selection layer in the Z-order.
   /// </summary>
   [Export(typeof(AdornmentLayerDefinition))]
   [Name("PurpleCornerBox")]
   [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
   private AdornmentLayerDefinition editorAdornmentLayer;    
   ```  

## <a name="make-the-adornment-appear-on-every-line"></a>Afficher l’ornement sur chaque ligne  

L’ornement d’origine figurait sur tous les caractères « a » dans un fichier texte. Maintenant que nous avons modifié le code pour ajouter l’ornement en réponse à la **+** caractère, il ajoute l’ornement uniquement sur la ligne où le **+** caractère est tapé. Nous pouvons modifier le code de l’ornement afin qu’une fois de plus l’ornement apparaisse sur chaque « a ».  
  
Dans le *KeyBindingTest.cs* , modifiez le `CreateVisuals()` méthode pour effectuer une itération dans toutes les lignes dans la vue pour décorer le caractère « a ».  
  
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
  
## <a name="build-and-test-the-code"></a>Générer et tester le code  
  
1.  Générez la solution KeyBindingTest et exécutez-le dans l’instance expérimentale.  
  
2.  Créez ou ouvrez un fichier texte. Tapez des mots contenant le caractère « a », puis tapez **+** n’importe où dans l’affichage de texte.  
  
     Un carré violets doit apparaître sur chaque caractère « a » dans le fichier.
