---
title: 'Procédure pas à pas : Utilisation d’une clé de raccourci avec une extension de l’éditeur ( Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 651598c0dbe746a9a26a6d60ce72b02853f98d47
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697152"
---
# <a name="walkthrough-use-a-shortcut-key-with-an-editor-extension"></a>Procédure pas à pas : Utilisez une clé raccourcie avec une extension de l’éditeur
Vous pouvez répondre aux touches de raccourci dans votre extension de l’éditeur. La procédure pas à pas suivante montre comment ajouter une parure de vue à une vue de texte en utilisant une clé de raccourci. Cette procédure pas à pas est basée sur le modèle d’éditeur d’ornement viewport, et il vous permet d’ajouter la parure en utilisant le caractère .

## <a name="prerequisites"></a>Prérequis
 A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Créer un projet de cadre d’exténuabilité gérée (MEF)

1. Créez un projet VSIX CMD. (Dans le dialogue du **nouveau projet,** sélectionnez **Visual C / Extensibility**, puis **VSIX Project**.) Nommez `KeyBindingTest`la solution .

2. Ajoutez un modèle d’élément d’ornement de `KeyBindingTest`texte d’éditeur au projet et nommez-le. Pour plus d’informations, voir [Créer une extension avec un modèle d’article d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Ajoutez les références suivantes et `false`définissez **CopyLocal** à :

    Microsoft.VisualStudio.Éditeur

    Microsoft.VisualStudio.OLE.Interop

    Microsoft.VisualStudio.Shell.14.0

    Microsoft.VisualStudio.TextManager.Interop

   Dans le fichier de classe KeyBindingTest, changez le nom de la classe en PurpleCornerBox. Utilisez l’ampoule qui apparaît dans la marge gauche pour apporter les autres modifications appropriées. À l’intérieur du constructeur, changez le nom de la couche d’ornement de **KeyBindingTest** à **PurpleCornerBox**:

```csharp
this.layer = view.GetAdornmentLayer("PurpleCornerBox");
```

Dans le fichier de classe KeyBindingTestTextViewCreationListener.cs, changez le nom de l’AdornmentLayer de **KeyBindingTest** à **PurpleCornerBox**:

```csharp
[Export(typeof(AdornmentLayerDefinition))]
[Name("PurpleCornerBox")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
public AdornmentLayerDefinition editorAdornmentLayer;
```

## <a name="handle-typechar-command"></a>Poignée de commande TYPECHAR
Avant Visual Studio 2017 version 15.6 la seule façon de gérer <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> les commandes dans une extension d’éditeur était la mise en œuvre d’un filtre de commande basé. Visual Studio 2017 version 15.6 a introduit une approche moderne simplifiée basée sur les gestionnaires de commande éditeur. Les deux sections suivantes montrent comment gérer une commande en utilisant à la fois l’héritage et l’approche moderne.

## <a name="define-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Décrivez le filtre de commande (avant visual Studio 2017 version 15.6)

 Le filtre de commande <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>est une implémentation de , qui gère la commande en instantanéisant la parure.

1. Ajoutez un fichier de classe et nommez-le `KeyBindingCommandFilter`.

2. Ajoutez ce qui suit à l’aide de directives.

    ```csharp
    using System;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.OLE.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Text.Editor;

    ```

3. La classe nommée KeyBindingCommandFilter <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>devrait hériter de .

    ```csharp
    internal class KeyBindingCommandFilter : IOleCommandTarget
    ```

4. Ajoutez des champs privés pour la vue de texte, la prochaine commande dans la chaîne de commandement, et un drapeau pour représenter si le filtre de commande a déjà été ajouté.

    ```csharp
    private IWpfTextView m_textView;
    internal IOleCommandTarget m_nextTarget;
    internal bool m_added;
    internal bool m_adorned;
    ```

5. Ajouter un constructeur qui définit la vue du texte.

    ```csharp
    public KeyBindingCommandFilter(IWpfTextView textView)
    {
        m_textView = textView;
        m_adorned = false;
    }
    ```

6. Implémenter la `QueryStatus()` méthode comme suit.

    ```csharp
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)
    {
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);
    }
    ```

7. Implémentez la `Exec()` méthode de sorte qu’elle ajoute**+** une boîte violette à la vue si un signe plus ( ) caractère est tapé.

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

## <a name="add-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Ajouter le filtre de commande (avant Visual Studio 2017 version 15.6)
 Le fournisseur d’ornement doit ajouter un filtre de commande à la vue de texte. Dans cet exemple, le <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> fournisseur met en œuvre pour écouter des événements de création de vision texte. Ce fournisseur d’ornement exporte également la couche d’ornement, qui définit l’ordre Z de l’ornement.

1. Dans le fichier KeyBindingTestTextViewCreationListener, ajoutez ce qui suit à l’aide de directives :

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

2. Pour obtenir l’adaptateur de <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>vue de texte, vous devez importer le .

    ```csharp
    [Import(typeof(IVsEditorAdaptersFactoryService))]
    internal IVsEditorAdaptersFactoryService editorFactory = null;

    ```

3. Modifier <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> la méthode de `KeyBindingCommandFilter`sorte qu’il ajoute le .

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));
    }
    ```

4. Le `AddCommandFilter` gestionnaire obtient l’adaptateur de vue de texte et ajoute le filtre de commande.

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

## <a name="implement-a-command-handler-starting-in-visual-studio-2017-version-156"></a>Implémenter un gestionnaire de commande (à partir de Visual Studio 2017 version 15.6)

Tout d’abord, mettre à jour les références Nuget du projet pour référencer le dernier éditeur API:

1. Cliquez à droite sur le projet et **sélectionnez Manage Nuget Packages**.

2. Dans **Nuget Package Manager**, sélectionnez **l’onglet Mises à jour,** sélectionnez la case à cocher **de tous les paquets,** puis sélectionnez **Mise à jour**.

Le gestionnaire de commande <xref:Microsoft.VisualStudio.Commanding.ICommandHandler%601>est une implémentation de , qui gère la commande en instantanéisant la parure.

1. Ajoutez un fichier de classe et nommez-le `KeyBindingCommandHandler`.

2. Ajoutez ce qui suit à l’aide de directives.

   ```csharp
   using Microsoft.VisualStudio.Commanding;
   using Microsoft.VisualStudio.Text.Editor;
   using Microsoft.VisualStudio.Text.Editor.Commanding.Commands;
   using Microsoft.VisualStudio.Utilities;
   using System.ComponentModel.Composition;
   ```

3. La classe nommée KeyBindingCommandHandler `ICommandHandler<TypeCharCommandArgs>`devrait hériter de , et l’exporter comme: <xref:Microsoft.VisualStudio.Commanding.ICommandHandler>

   ```csharp
   [Export(typeof(ICommandHandler))]
   [ContentType("text")]
   [Name("KeyBindingTest")]
   internal class KeyBindingCommandHandler : ICommandHandler<TypeCharCommandArgs>
   ```

4. Ajouter un nom d’affichage du gestionnaire de commande :

   ```csharp
   public string DisplayName => "KeyBindingTest";
   ```

5. Implémenter la `GetCommandState()` méthode comme suit. Étant donné que ce gestionnaire de commande gère la commande typeCHAR de l’éditeur de base, il peut déléguer l’activation de la commande à l’éditeur de base.

   ```csharp
   public CommandState GetCommandState(TypeCharCommandArgs args)
   {
       return CommandState.Unspecified;
   }
   ```

6. Implémentez la `ExecuteCommand()` méthode de sorte qu’elle ajoute**+** une boîte violette à la vue si un signe plus ( ) caractère est tapé.

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

   7. Copiez la définition de couche *d’ornement* de KeyBindingTestTextViewCreationListener.cs fichier au *KeyBindingCommandHandler.cs,* puis supprimez *KeyBindingTestTextViewCreationListener.cs* fichier :

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

La parure originale est apparue sur chaque personnage 'a' dans un fichier texte. Maintenant que nous avons changé le code pour ajouter **+** la parure en réponse au personnage, **+** il ajoute l’ornement que sur la ligne où le personnage est tapé. Nous pouvons changer le code d’ornement de sorte que la parure apparaît une fois de plus sur chaque «a».

Dans le fichier *KeyBindingTest.cs,* `CreateVisuals()` changer la méthode pour itérer à travers toutes les lignes de la vue pour décorer le caractère «a».

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

## <a name="build-and-test-the-code"></a>Construire et tester le code

1. Construisez la solution KeyBindingTest et exécutez-la dans le cas expérimental.

2. Créez ou ouvrez un fichier texte. Tapez quelques mots contenant le caractère **+** 'a', puis tapez n’importe où dans la vue de texte.

     Un carré violet doit apparaître sur chaque personnage 'a' dans le fichier.
