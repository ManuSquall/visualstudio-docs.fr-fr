---
title: 'Procédure pas à pas : utilisation d’une touche de raccourci avec une extension d’éditeur | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 094cb590d5b2a3bf062916985bfc61b1cf76d365
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85904397"
---
# <a name="walkthrough-use-a-shortcut-key-with-an-editor-extension"></a>Procédure pas à pas : utiliser une touche de raccourci avec une extension d’éditeur
Vous pouvez répondre aux touches de raccourci dans votre extension d’éditeur. La procédure pas à pas suivante montre comment ajouter un ornement de vue à un affichage de texte à l’aide d’une touche de raccourci. Cette procédure pas à pas est basée sur le modèle de l’éditeur d’ornements Viewport et vous permet d’ajouter l’ornement à l’aide du caractère +.

## <a name="prerequisites"></a>Prérequis
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Créer un projet Managed Extensibility Framework (MEF)

1. Créez un projet VSIX C#. (Dans la boîte de dialogue **nouveau projet** , sélectionnez **Visual C#/extensibilité**, puis **projet VSIX**.) Nommez la solution `KeyBindingTest` .

2. Ajoutez un modèle d’élément d’ornement de texte de l’éditeur au projet et nommez-le `KeyBindingTest` . Pour plus d’informations, consultez [créer une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Ajoutez les références suivantes et affectez à **CopyLocal** la valeur `false` :

    Microsoft. VisualStudio. Editor

    Microsoft. VisualStudio. OLE. Interop

    Microsoft. VisualStudio. Shell. 14.0

    Microsoft. VisualStudio. TextManager. Interop

   Dans le fichier de classe KeyBindingTest, remplacez le nom de classe par PurpleCornerBox. Utilisez l’ampoule qui apparaît dans la marge de gauche pour apporter les autres modifications appropriées. Dans le constructeur, remplacez le nom de la couche d’ornement **KeyBindingTest** par **PurpleCornerBox**:

```csharp
this.layer = view.GetAdornmentLayer("PurpleCornerBox");
```

Dans le fichier de classe KeyBindingTestTextViewCreationListener.cs, modifiez le nom du AdornmentLayer de **KeyBindingTest** en **PurpleCornerBox**:

```csharp
[Export(typeof(AdornmentLayerDefinition))]
[Name("PurpleCornerBox")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
public AdornmentLayerDefinition editorAdornmentLayer;
```

## <a name="handle-typechar-command"></a>Handle TYPECHAR, commande
Avant Visual Studio 2017 version 15,6, le seul moyen de gérer les commandes dans une extension d’éditeur consistait à implémenter un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> filtre de commande basé sur. Visual Studio 2017 version 15,6 a introduit une approche simplifiée moderne basée sur les gestionnaires de commandes de l’éditeur. Les deux sections suivantes montrent comment gérer une commande à l’aide de l’approche héritée et moderne.

## <a name="define-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Définir le filtre de commande (avant Visual Studio 2017 version 15,6)

 Le filtre de commande est une implémentation de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , qui gère la commande en instanciant l’ornement.

1. Ajoutez un fichier de classe et nommez-le `KeyBindingCommandFilter`.

2. Ajoutez les directives d’utilisation suivantes.

    ```csharp
    using System;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.OLE.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Text.Editor;

    ```

3. La classe nommée KeyBindingCommandFilter doit hériter de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

    ```csharp
    internal class KeyBindingCommandFilter : IOleCommandTarget
    ```

4. Ajoutez des champs privés pour l’affichage de texte, la commande suivante dans la chaîne de commande et un indicateur pour indiquer si le filtre de commande a déjà été ajouté.

    ```csharp
    private IWpfTextView m_textView;
    internal IOleCommandTarget m_nextTarget;
    internal bool m_added;
    internal bool m_adorned;
    ```

5. Ajoutez un constructeur qui définit l’affichage de texte.

    ```csharp
    public KeyBindingCommandFilter(IWpfTextView textView)
    {
        m_textView = textView;
        m_adorned = false;
    }
    ```

6. Implémentez la `QueryStatus()` méthode comme suit.

    ```csharp
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)
    {
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);
    }
    ```

7. Implémentez la `Exec()` méthode afin qu’elle ajoute une zone violette à la vue si un caractère de signe plus ( **+** ) est tapé.

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

## <a name="add-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Ajoutez le filtre de commande (avant Visual Studio 2017 version 15,6)
 Le fournisseur d’ornements doit ajouter un filtre de commande à l’affichage de texte. Dans cet exemple, le fournisseur implémente <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> pour écouter les événements de création d’une vue de texte. Ce fournisseur d’ornements exporte également la couche d’ornement, qui définit l’ordre de plan de l’ornement.

1. Dans le fichier KeyBindingTestTextViewCreationListener, ajoutez les directives d’utilisation suivantes :

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

2. Pour obtenir l’adaptateur de vue de texte, vous devez importer le <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> .

    ```csharp
    [Import(typeof(IVsEditorAdaptersFactoryService))]
    internal IVsEditorAdaptersFactoryService editorFactory = null;

    ```

3. Modifiez la <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> méthode afin qu’elle ajoute le `KeyBindingCommandFilter` .

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));
    }
    ```

4. Le `AddCommandFilter` Gestionnaire obtient l’adaptateur de vue de texte et ajoute le filtre de commande.

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

## <a name="implement-a-command-handler-starting-in-visual-studio-2017-version-156"></a>Implémenter un gestionnaire de commandes (à partir de Visual Studio 2017 version 15,6)

Tout d’abord, mettez à jour les références NuGet du projet pour référencer la dernière API Editor :

1. Cliquez avec le bouton droit sur le projet et sélectionnez **gérer les packages NuGet**.

2. Dans le **Gestionnaire de package NuGet**, sélectionnez l’onglet **mises à jour** , activez la case à cocher **Sélectionner tous les packages** , puis sélectionnez **mettre à jour**.

Le gestionnaire de commandes est une implémentation de <xref:Microsoft.VisualStudio.Commanding.ICommandHandler%601> , qui gère la commande en instanciant l’ornement.

1. Ajoutez un fichier de classe et nommez-le `KeyBindingCommandHandler`.

2. Ajoutez les directives d’utilisation suivantes.

   ```csharp
   using Microsoft.VisualStudio.Commanding;
   using Microsoft.VisualStudio.Text.Editor;
   using Microsoft.VisualStudio.Text.Editor.Commanding.Commands;
   using Microsoft.VisualStudio.Utilities;
   using System.ComponentModel.Composition;
   ```

3. La classe nommée KeyBindingCommandHandler doit hériter de `ICommandHandler<TypeCharCommandArgs>` et l’exporter en tant que <xref:Microsoft.VisualStudio.Commanding.ICommandHandler> :

   ```csharp
   [Export(typeof(ICommandHandler))]
   [ContentType("text")]
   [Name("KeyBindingTest")]
   internal class KeyBindingCommandHandler : ICommandHandler<TypeCharCommandArgs>
   ```

4. Ajoutez un nom complet du gestionnaire de commandes :

   ```csharp
   public string DisplayName => "KeyBindingTest";
   ```

5. Implémentez la `GetCommandState()` méthode comme suit. Étant donné que ce gestionnaire de commandes gère la commande TYPECHAR de l’éditeur principal, il peut déléguer l’activation de la commande à l’éditeur principal.

   ```csharp
   public CommandState GetCommandState(TypeCharCommandArgs args)
   {
       return CommandState.Unspecified;
   }
   ```

6. Implémentez la `ExecuteCommand()` méthode afin qu’elle ajoute une zone violette à la vue si un caractère de signe plus ( **+** ) est tapé.

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

   7. Copiez la définition de la couche d’ornement à partir du fichier *KeyBindingTestTextViewCreationListener.cs* vers *KeyBindingCommandHandler.cs* , puis supprimez le fichier *KeyBindingTestTextViewCreationListener.cs* :

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

## <a name="make-the-adornment-appear-on-every-line"></a>Faire apparaître l’ornement sur chaque ligne

L’ornement d’origine est apparu sur chaque caractère’a’dans un fichier texte. Maintenant que nous avons modifié le code pour ajouter l’ornement en réponse au **+** caractère, il ajoute l’ornement uniquement sur la ligne où le **+** caractère est tapé. Nous pouvons modifier le code d’ornement afin que l’ornement apparaisse une fois de plus sur chaque « a ».

Dans le fichier *KeyBindingTest.cs* , modifiez la `CreateVisuals()` méthode pour itérer au sein de toutes les lignes de la vue afin de décorer le caractère « a ».

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

1. Générez la solution KeyBindingTest et exécutez-la dans l’instance expérimentale.

2. Créez ou ouvrez un fichier texte. Tapez des mots contenant le caractère « a », puis tapez **+** n’importe où dans l’affichage de texte.

     Un carré violet doit apparaître sur chaque caractère’a’du fichier.
