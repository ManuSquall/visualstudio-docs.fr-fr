---
title: 'Procédure pas à pas : Utilisation d’une commande Shell avec une extension de l’éditeur ( Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52b151b09c1bb7306b4270f9408d0f04a7600aa2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697164"
---
# <a name="walkthrough-use-a-shell-command-with-an-editor-extension"></a>Procédure pas à pas : Utilisez une commande de coquillages avec une extension d’éditeur
À partir d’un VSPackage, vous pouvez ajouter des fonctionnalités telles que des commandes de menu à l’éditeur. Cette procédure pas à pas montre comment ajouter une parure à une vue de texte dans l’éditeur en invoquant une commande de menu.

 Cette procédure pas à pas démontre l’utilisation d’un VSPackage ainsi que d’une partie composante du Cadre d’exténuabilité gérée (MEF). Vous devez utiliser un VSPackage pour enregistrer la commande de menu avec la coque Visual Studio. Et, vous pouvez utiliser la commande pour accéder à la partie composant MEF.

## <a name="prerequisites"></a>Prérequis
 A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-menu-command"></a>Créer une extension avec une commande de menu
 Créez un VSPackage qui met une commande de menu nommée **Add Adornment** sur le menu **Tools.**

1. Créez un projet VSIX `MenuCommandTest`nommé , et ajoutez un nom de modèle d’élément de commande personnalisée **AddAdornment**. Pour plus d’informations, voir [Créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Une solution nommée MenuCommandTest s’ouvre. Le fichier MenuCommandTestPackage a le code qui crée la commande du menu et le met sur le menu **Tools.** À ce stade, la commande ne fait qu’apparaître une boîte de messages. Les étapes ultérieures montreront comment changer ceci pour afficher l’ornement de commentaire.

3. Ouvrez le fichier *source.extension.vsixmanifest* dans le vsIX Manifest Editor. L’onglet `Assets` doit avoir une ligne pour un Microsoft.VisualStudio.VsPackage nommé MenuCommandTest.

4. Enregistrer et fermer le fichier *source.extension.vsixmanifest.*

## <a name="add-a-mef-extension-to-the-command-extension"></a>Ajouter une extension MEF à l’extension de commande

1. Dans **Solution Explorer**, cliquez à droite sur le nœud de solution, cliquez sur **Ajouter**, puis cliquez sur New **Project**. Dans la boîte de dialogue **Add New Project,** cliquez sur **Extensibility** sous **Visual C ,** puis **VSIX Project**. Nommez le projet `CommentAdornmentTest`.

2. Parce que ce projet interagira avec l’assemblage VSPackage fort, vous devez signer l’assemblage. Vous pouvez réutiliser le fichier clé déjà créé pour l’assemblage VSPackage.

    1. Ouvrez les propriétés du projet et sélectionnez l’onglet **Signature.**

    2. Sélectionnez **Signez l’assemblage**.

    3. Sous **Choisissez un fichier clé de nom fort**, sélectionnez le fichier *Key.snk* qui a été généré pour l’assemblage MenuCommandTest.

## <a name="refer-to-the-mef-extension-in-the-vspackage-project"></a>Se référer à l’extension du MEF dans le projet VSPackage
 Étant donné que vous ajoutez un composant MEF à l’emballage VS, vous devez spécifier les deux types d’actifs dans le manifeste.

> [!NOTE]
> Pour plus d’informations sur le MEF, voir [Cadre d’exténuabilité gérée (MEF)](/dotnet/framework/mef/index).

### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>Se référer au composant MEF du projet VSPackage

1. Dans le cadre du projet MenuCommandTest, ouvrez le fichier *source.extension.vsixmanifest* dans le fichier VSIX Manifest Editor.

2. Sur l’onglet **Actifs,** cliquez sur **Nouveau**.

3. Dans la liste **de type,** choisissez **Microsoft.VisualStudio.MefComponent**.

4. Dans la liste **Source,** choisissez **un projet dans la solution actuelle**.

5. Dans la liste **de projet,** choisissez **CommentAdornmentTest**.

6. Enregistrer et fermer le fichier *source.extension.vsixmanifest.*

7. Assurez-vous que le projet MenuCommandTest a une référence au projet CommentAdornmentTest.

8. Dans le projet CommentAdornmentTest, définissez le projet de production d’un assemblage. Dans la **solution Explorer**, sélectionnez le projet et regardez dans la fenêtre **propriétés** pour la sortie de construction de copie à la propriété **OutputDirectory,** et le définir à **vrai**.

## <a name="define-a-comment-adornment"></a>Décrivez une parure de commentaire
 L’ornement de commentaire lui-même se compose d’un <xref:Microsoft.VisualStudio.Text.ITrackingSpan> qui suit le texte sélectionné, et quelques chaînes qui représentent l’auteur et la description du texte.

#### <a name="to-define-a-comment-adornment"></a>Définir une parure de commentaire

1. Dans le projet CommentAdornmentTest, ajoutez un `CommentAdornment`nouveau fichier de classe et nommez-le .

2. Ajoutez les références suivantes :

    1. Microsoft.VisualStudio.CoreUtility (en anglais seulement)

    2. Microsoft.VisualStudio.Text.Data (en anglais seulement)

    3. Microsoft.VisualStudio.Text.Logic (en anglais seulement)

    4. Microsoft.VisualStudio.Text.UI (en anglais seulement)

    5. Microsoft.VisualStudio.Text.UI.Wpf

    6. System.ComponentModel.Composition

    7. PresentationCore

    8. PresentationFramework

    9. WindowsBase

3. Ajoutez la `using` directive suivante.

    ```csharp
    using Microsoft.VisualStudio.Text;
    ```

4. Le fichier doit contenir `CommentAdornment`une classe nommée .

    ```csharp
    internal class CommentAdornment
    ```

5. Ajoutez trois champs `CommentAdornment` à <xref:Microsoft.VisualStudio.Text.ITrackingSpan>la classe pour l’auteur, et la description.

    ```csharp
    public readonly ITrackingSpan Span;
    public readonly string Author;
    public readonly string Text;
    ```

6. Ajoutez un constructeur qui initialise les champs.

    ```csharp
    public CommentAdornment(SnapshotSpan span, string author, string text)
    {
        this.Span = span.Snapshot.CreateTrackingSpan(span, SpanTrackingMode.EdgeExclusive);
        this.Author = author;
        this.Text = text;
    }
    ```

## <a name="create-a-visual-element-for-the-adornment"></a>Créer un élément visuel pour l’ornement
 Définissez un élément visuel pour votre ornement. Pour cette procédure pas à pas, définissez un contrôle qui hérite de la classe <xref:System.Windows.Controls.Canvas>De la Windows Presentation Foundation (WPF).

1. Créez une classe dans le projet CommentAdornmentTest, et nommez-le `CommentBlock`.

2. Ajoutez les `using` directives suivantes.

    ```csharp
    using Microsoft.VisualStudio.Text;
    using System;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Media;
    using System.Windows.Shapes;
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. Faire `CommentBlock` la classe <xref:System.Windows.Controls.Canvas>hériter de .

    ```csharp
    internal class CommentBlock : Canvas
    { }
    ```

4. Ajoutez quelques champs privés pour définir les aspects visuels de la parure.

    ```csharp
    private Geometry textGeometry;
    private Grid commentGrid;
    private static Brush brush;
    private static Pen solidPen;
    private static Pen dashPen;
    ```

5. Ajoutez un constructeur qui définit l’ornement de commentaire et ajoute le texte pertinent.

    ```csharp
    public CommentBlock(double textRightEdge, double viewRightEdge,
            Geometry newTextGeometry, string author, string body)
    {
        if (brush == null)
        {
            brush = new SolidColorBrush(Color.FromArgb(0x20, 0x00, 0xff, 0x00));
            brush.Freeze();
            Brush penBrush = new SolidColorBrush(Colors.Green);
            penBrush.Freeze();
            solidPen = new Pen(penBrush, 0.5);
            solidPen.Freeze();
            dashPen = new Pen(penBrush, 0.5);
            dashPen.DashStyle = DashStyles.Dash;
            dashPen.Freeze();
        }

        this.textGeometry = newTextGeometry;

        TextBlock tb1 = new TextBlock();
        tb1.Text = author;
        TextBlock tb2 = new TextBlock();
        tb2.Text = body;

        const int MarginWidth = 8;
        this.commentGrid = new Grid();
        this.commentGrid.RowDefinitions.Add(new RowDefinition());
        this.commentGrid.RowDefinitions.Add(new RowDefinition());
        ColumnDefinition cEdge = new ColumnDefinition();
        cEdge.Width = new GridLength(MarginWidth);
        ColumnDefinition cEdge2 = new ColumnDefinition();
        cEdge2.Width = new GridLength(MarginWidth);
        this.commentGrid.ColumnDefinitions.Add(cEdge);
        this.commentGrid.ColumnDefinitions.Add(new ColumnDefinition());
        this.commentGrid.ColumnDefinitions.Add(cEdge2);

        System.Windows.Shapes.Rectangle rect = new System.Windows.Shapes.Rectangle();
        rect.RadiusX = 6;
        rect.RadiusY = 3;
        rect.Fill = brush;
        rect.Stroke = Brushes.Green;

            Size inf = new Size(double.PositiveInfinity, double.PositiveInfinity);
            tb1.Measure(inf);
            tb2.Measure(inf);
            double middleWidth = Math.Max(tb1.DesiredSize.Width, tb2.DesiredSize.Width);
            this.commentGrid.Width = middleWidth + 2 * MarginWidth;

        Grid.SetColumn(rect, 0);
        Grid.SetRow(rect, 0);
        Grid.SetRowSpan(rect, 2);
        Grid.SetColumnSpan(rect, 3);
        Grid.SetRow(tb1, 0);
        Grid.SetColumn(tb1, 1);
        Grid.SetRow(tb2, 1);
        Grid.SetColumn(tb2, 1);
        this.commentGrid.Children.Add(rect);
        this.commentGrid.Children.Add(tb1);
        this.commentGrid.Children.Add(tb2);

        Canvas.SetLeft(this.commentGrid, Math.Max(viewRightEdge - this.commentGrid.Width - 20.0, textRightEdge + 20.0));
        Canvas.SetTop(this.commentGrid, textGeometry.GetRenderBounds(solidPen).Top);

        this.Children.Add(this.commentGrid);
    }
    ```

6. Implémentez également un gestionnaire d’événements <xref:System.Windows.Controls.Panel.OnRender%2A> qui dessine la parure.

    ```csharp
    protected override void OnRender(DrawingContext dc)
    {
        base.OnRender(dc);
        if (this.textGeometry != null)
        {
            dc.DrawGeometry(brush, solidPen, this.textGeometry);
            Rect textBounds = this.textGeometry.GetRenderBounds(solidPen);
            Point p1 = new Point(textBounds.Right, textBounds.Bottom);
            Point p2 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid) - 20.0, p1.X), p1.Y);
            Point p3 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid), p1.X), (Canvas.GetTop(this.commentGrid) + p1.Y) * 0.5);
            dc.DrawLine(dashPen, p1, p2);
            dc.DrawLine(dashPen, p2, p3);
        }
    }
    ```

## <a name="add-an-iwpftextviewcreationlistener"></a>Ajouter un IWpfTextViewCreationListener
 Il <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> s’agit d’une partie composante MEF que vous pouvez utiliser pour écouter les événements de création.

1. Ajoutez un fichier de classe au projet CommentAdornmentTest et nommez-le `Connector`.

2. Ajoutez les `using` directives suivantes.

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. Déclarez une classe <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>qui met en <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> œuvre, <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> et <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>l’exporter avec un de "texte" et un de . L’attribut de type de contenu spécifie le type de contenu auquel le composant s’applique. Le type de texte est le type de base pour tous les types de fichiers non binaires. Par conséquent, presque toutes les visions de texte qui est créé seront de ce type. L’attribut de rôle de vue de texte spécifie le type de vue de texte auquel le composant s’applique. Les rôles de vue de texte de document montrent généralement le texte qui est composé de lignes et est stocké dans un fichier.

     [!code-vb[VSSDKMenuCommandTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb)]
     [!code-csharp[VSSDKMenuCommandTest#11](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]

4. Implémentez la <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> méthode `Create()` de sorte `CommentAdornmentManager`qu’elle appelle l’événement statique de la .

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        CommentAdornmentManager.Create(textView);
    }
    ```

5. Ajoutez une méthode que vous pouvez utiliser pour exécuter la commande.

    ```csharp
    static public void Execute(IWpfTextViewHost host)
    {
        IWpfTextView view = host.TextView;
        //Add a comment on the selected text. 
        if (!view.Selection.IsEmpty)
        {
            //Get the provider for the comment adornments in the property bag of the view.
            CommentAdornmentProvider provider = view.Properties.GetProperty<CommentAdornmentProvider>(typeof(CommentAdornmentProvider));

            //Add some arbitrary author and comment text. 
            string author = System.Security.Principal.WindowsIdentity.GetCurrent().Name;
            string comment = "Four score....";

            //Add the comment adornment using the provider.
            provider.Add(view.Selection.SelectedSpans[0], author, comment);
        }
    }
    ```

## <a name="define-an-adornment-layer"></a>Décrivez une couche d’ornement
 Pour ajouter une nouvelle parure, vous devez définir une couche d’ornement.

### <a name="to-define-an-adornment-layer"></a>Définir une couche d’ornement

1. Dans `Connector` la classe, déclarez <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>un champ public <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de type, et exportez-le avec un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> qui spécifie un nom unique pour la couche d’ornement et un qui définit la relation Z-ordre de cette couche d’ornement aux autres couches de vue de texte (texte, caret, et sélection).

    ```csharp
    [Export(typeof(AdornmentLayerDefinition))]
    [Name("CommentAdornmentLayer")]
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
    public AdornmentLayerDefinition commentLayerDefinition;

    ```

## <a name="provide-comment-adornments"></a>Fournir des parures de commentaires
 Lorsque vous définissez une parure, implémentez également un fournisseur d’ornement de commentaire et un gestionnaire d’ornement de commentaire. Le fournisseur d’ornements de commentaire tient une liste <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> d’ornements de commentaires, écoute des événements sur le tampon de texte sous-jacent, et supprime les ornements de commentaire lorsque le texte sous-jacent est supprimé.

1. Ajoutez un nouveau fichier de classe au projet `CommentAdornmentProvider`CommentAdornmentTest et nommez-le .

2. Ajoutez les `using` directives suivantes.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Collections.ObjectModel;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    ```

3. Ajoutez une classe nommée `CommentAdornmentProvider`.

    ```csharp
    internal class CommentAdornmentProvider
    {
    }
    ```

4. Ajoutez des champs privés pour le tampon de texte et la liste des ornements de commentaires liés au tampon.

    ```csharp
    private ITextBuffer buffer;
    private IList<CommentAdornment> comments = new List<CommentAdornment>();

    ```

5. Ajouter un constructeur `CommentAdornmentProvider`pour . Ce constructeur doit avoir un accès privé parce `Create()` que le fournisseur est instantané par la méthode. Le constructeur ajoute `OnBufferChanged` le gestionnaire <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> de l’événement à l’événement.

    ```csharp
    private CommentAdornmentProvider(ITextBuffer buffer)
    {
        this.buffer = buffer;
        //listen to the Changed event so we can react to deletions. 
        this.buffer.Changed += OnBufferChanged;
    }

    ```

6. Ajoutez la méthode `Create()`.

    ```csharp
    public static CommentAdornmentProvider Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentProvider>(delegate { return new CommentAdornmentProvider(view.TextBuffer); });
    }

    ```

7. Ajoutez la méthode `Detach()`.

    ```csharp
    public void Detach()
    {
        if (this.buffer != null)
        {
            //remove the Changed listener 
            this.buffer.Changed -= OnBufferChanged;
            this.buffer = null;
        }
    }
    ```

8. Ajoutez `OnBufferChanged` le gestionnaire de l’événement.

     [!code-csharp[VSSDKMenuCommandTest#21](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_2.cs)]
     [!code-vb[VSSDKMenuCommandTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_2.vb)]

9. Ajoutez une déclaration `CommentsChanged` pour un événement.

    ```csharp
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;
    ```

10. Créez `Add()` une méthode pour ajouter la parure.

    ```csharp
    public void Add(SnapshotSpan span, string author, string text)
    {
        if (span.Length == 0)
            throw new ArgumentOutOfRangeException("span");
        if (author == null)
            throw new ArgumentNullException("author");
        if (text == null)
            throw new ArgumentNullException("text");

        //Create a comment adornment given the span, author and text.
        CommentAdornment comment = new CommentAdornment(span, author, text);

        //Add it to the list of comments. 
        this.comments.Add(comment);

        //Raise the changed event.
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;
        if (commentsChanged != null)
            commentsChanged(this, new CommentsChangedEventArgs(comment, null));
    }

    ```

11. Ajoutez `RemoveComments()` une méthode.

    ```csharp
    public void RemoveComments(SnapshotSpan span)
    {
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;

        //Get a list of all the comments that are being kept
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);

        foreach (CommentAdornment comment in this.comments)
        {
            //find out if the given span overlaps with the comment text span. If two spans are adjacent, they do not overlap. To consider adjacent spans, use IntersectsWith. 
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))
            {
                //Raise the change event to delete this comment. 
                if (commentsChanged != null)
                    commentsChanged(this, new CommentsChangedEventArgs(null, comment));
            }
            else
                keptComments.Add(comment);
        }

        this.comments = keptComments;
    }
    ```

12. Ajoutez `GetComments()` une méthode qui renvoie tous les commentaires dans une durée d’instantané donnée.

    ```csharp
    public Collection<CommentAdornment> GetComments(SnapshotSpan span)
    {
        IList<CommentAdornment> overlappingComments = new List<CommentAdornment>();
        foreach (CommentAdornment comment in this.comments)
        {
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))
                overlappingComments.Add(comment);
        }

        return new Collection<CommentAdornment>(overlappingComments);
    }
    ```

13. Ajoutez une `CommentsChangedEventArgs`classe nommée , comme suit.

    ```csharp
    internal class CommentsChangedEventArgs : EventArgs
    {
        public readonly CommentAdornment CommentAdded;

        public readonly CommentAdornment CommentRemoved;

        public CommentsChangedEventArgs(CommentAdornment added, CommentAdornment removed)
        {
            this.CommentAdded = added;
            this.CommentRemoved = removed;
        }
    }
    ```

## <a name="manage-comment-adornments"></a>Gérer les ornements de commentaires
 Le gestionnaire d’ornement de commentaire crée la parure et l’ajoute à la couche d’ornement. Il écoute les <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> et les événements afin qu’il puisse déplacer ou supprimer la parure. Il écoute également `CommentsChanged` l’événement qui est tiré par le fournisseur d’ornement de commentaire lorsque les commentaires sont ajoutés ou supprimés.

1. Ajoutez un fichier de classe au projet CommentAdornmentTest et nommez-le `CommentAdornmentManager`.

2. Ajoutez les `using` directives suivantes.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Windows.Media;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Formatting;
    ```

3. Ajoutez une classe nommée `CommentAdornmentManager`.

    ```csharp
    internal class CommentAdornmentManager
        {
        }
    ```

4. Ajoutez quelques champs privés.

    ```csharp
    private readonly IWpfTextView view;
    private readonly IAdornmentLayer layer;
    private readonly CommentAdornmentProvider provider;
    ```

5. Ajoutez un constructeur qui souscrit <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> le <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> gestionnaire aux événements `CommentsChanged` et aux événements, ainsi qu’à l’événement. Le constructeur est privé parce que le gestionnaire `Create()` est instantané par la méthode statique.

    ```csharp
    private CommentAdornmentManager(IWpfTextView view)
    {
        this.view = view;
        this.view.LayoutChanged += OnLayoutChanged;
        this.view.Closed += OnClosed;

        this.layer = view.GetAdornmentLayer("CommentAdornmentLayer");

        this.provider = CommentAdornmentProvider.Create(view);
        this.provider.CommentsChanged += OnCommentsChanged;
    }
    ```

6. Ajoutez `Create()` la méthode qui obtient un fournisseur ou en crée une si nécessaire.

    ```csharp
    public static CommentAdornmentManager Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });
    }
    ```

7. Ajouter `CommentsChanged` le gestionnaire.

    ```csharp
    private void OnCommentsChanged(object sender, CommentsChangedEventArgs e)
    {
        //Remove the comment (when the adornment was added, the comment adornment was used as the tag). 
        if (e.CommentRemoved != null)
            this.layer.RemoveAdornmentsByTag(e.CommentRemoved);

        //Draw the newly added comment (this will appear immediately: the view does not need to do a layout). 
        if (e.CommentAdded != null)
            this.DrawComment(e.CommentAdded);
    }
    ```

8. Ajouter <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> le gestionnaire.

    ```csharp
    private void OnClosed(object sender, EventArgs e)
    {
        this.provider.Detach();
        this.view.LayoutChanged -= OnLayoutChanged;
        this.view.Closed -= OnClosed;
    }
    ```

9. Ajouter <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> le gestionnaire.

    ```csharp
    private void OnLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
    {
        //Get all of the comments that intersect any of the new or reformatted lines of text.
        List<CommentAdornment> newComments = new List<CommentAdornment>();

        //The event args contain a list of modified lines and a NormalizedSpanCollection of the spans of the modified lines.  
        //Use the latter to find the comments that intersect the new or reformatted lines of text. 
        foreach (Span span in e.NewOrReformattedSpans)
        {
            newComments.AddRange(this.provider.GetComments(new SnapshotSpan(this.view.TextSnapshot, span)));
        }

        //It is possible to get duplicates in this list if a comment spanned 3 lines, and the first and last lines were modified but the middle line was not. 
        //Sort the list and skip duplicates.
        newComments.Sort(delegate(CommentAdornment a, CommentAdornment b) { return a.GetHashCode().CompareTo(b.GetHashCode()); });

        CommentAdornment lastComment = null;
        foreach (CommentAdornment comment in newComments)
        {
            if (comment != lastComment)
            {
                lastComment = comment;
                this.DrawComment(comment);
            }
        }
    }
    ```

10. Ajoutez la méthode privée qui attire le commentaire.

     [!code-csharp[VSSDKMenuCommandTest#35](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_3.cs)]
     [!code-vb[VSSDKMenuCommandTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_3.vb)]

## <a name="use-the-menu-command-to-add-the-comment-adornment"></a>Utilisez la commande du menu pour ajouter l’ornement de commentaire
 Vous pouvez utiliser la commande du menu pour créer `MenuItemCallback` une parure de commentaire en implémentant la méthode du VSPackage.

1. Ajoutez les références suivantes au projet MenuCommandTest :

    - Microsoft.VisualStudio.TextManager.Interop

    - Microsoft.VisualStudio.Éditeur

    - Microsoft.VisualStudio.Text.UI.Wpf

2. Ouvrez le *fichier AddAdornment.cs* et `using` ajoutez les directives suivantes.

    ```csharp
    using Microsoft.VisualStudio.TextManager.Interop;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Editor;
    using CommentAdornmentTest;
    ```

3. Supprimer `Execute()` la méthode et ajouter le gestionnaire de commande suivant.

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
    }
    ```

4. Ajoutez du code pour obtenir la vue active. Vous devez `SVsTextManager` obtenir la coquille de la `IVsTextView`coquille Visual Studio pour obtenir l’actif .

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
    }
    ```

5. Si cette vue de texte est une instance d’une <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> vue de <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> texte d’éditeur, vous pouvez la jeter à l’interface et puis obtenir le et son associé <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>. Utilisez <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> le pour `Connector.Execute()` appeler la méthode, qui obtient le fournisseur d’ornement de commentaire et ajoute la parure. Le gestionnaire de commande doit maintenant ressembler à ce code :

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
        IVsUserData userData = vTextView as IVsUserData;
         if (userData == null)
        {
            Console.WriteLine("No text view is currently open");
            return;
        }
        IWpfTextViewHost viewHost;
        object holder;
        Guid guidViewHost = DefGuidList.guidIWpfTextViewHost;
        userData.GetData(ref guidViewHost, out holder);
        viewHost = (IWpfTextViewHost)holder;
        Connector.Execute(viewHost);
    }
    ```

6. Définissez la méthode AddAdornmentHandler comme gestionnaire pour la commande AddAdornment dans le constructeur AddAdornment.

    ```csharp
    private AddAdornment(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));

        var menuCommandID = new CommandID(CommandSet, CommandId);
        var menuItem = new MenuCommand(this.AddAdornmentHandler, menuCommandID);
        commandService.AddCommand(menuItem);
    }
    ```

## <a name="build-and-test-the-code"></a>Construire et tester le code

1. Générez la solution et commencez le débogage. L’instance expérimentale devrait apparaître.

2. Créer un fichier texte. Tapez un peu de texte et sélectionnez-le.

3. Sur le menu **Tools,** cliquez sur **Invoke Add Adornment**. Un ballon doit s’afficher sur le côté droit de la fenêtre de texte, et doit contenir du texte qui ressemble au texte suivant.

     VotreUserName

     Fourscore...

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : liez un type de contenu à une extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
