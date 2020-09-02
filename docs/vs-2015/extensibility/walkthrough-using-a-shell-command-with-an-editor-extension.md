---
title: 'Procédure pas à pas : utilisation d’une commande shell avec une extension d’éditeur | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
caps.latest.revision: 47
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0312d98dd6959cb5d67d593c4bf0af39fa1889eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65693356"
---
# <a name="walkthrough-using-a-shell-command-with-an-editor-extension"></a>Procédure pas à pas : utilisation d’une commande Shell avec une extension de l’éditeur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

À partir d’un VSPackage, vous pouvez ajouter des fonctionnalités telles que des commandes de menu à l’éditeur. Cette procédure pas à pas montre comment ajouter un ornement à une vue de texte dans l’éditeur en appelant une commande de menu.  
  
 Cette procédure pas à pas illustre l’utilisation d’un VSPackage avec une partie de composant Managed Extensibility Framework (MEF). Vous devez utiliser un VSPackage pour enregistrer la commande de menu avec le shell Visual Studio, et vous pouvez utiliser la commande pour accéder à la partie du composant MEF.  
  
## <a name="prerequisites"></a>Prérequis  
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installation du kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-an-extension-with-a-menu-command"></a>Création d’une extension avec une commande de menu  
 Créez un VSPackage qui place une commande de menu nommée **Ajouter un ornement** dans le menu **Outils** .  
  
1. Créez un projet VSIX C# nommé `MenuCommandTest` et ajoutez un nom de modèle d’élément de commande personnalisé **AddAdornment**. Pour plus d’informations, consultez [création d’une extension à l’aide d’une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2. Une solution nommée MenuCommandTest est ouverte. Le fichier MenuCommandTestPackage contient le code qui crée la commande de menu et le place dans le menu **Outils** . À ce stade, la commande provoque simplement l’affichage d’une boîte de message. Les étapes ultérieures montrent comment modifier cette valeur pour afficher l’ornement de commentaire.  
  
3. Ouvrez le fichier source.extension.vsixmanifest dans l’éditeur de manifeste VSIX. L' `Assets` onglet doit avoir une ligne pour un Microsoft. VisualStudio. VSPackage nommé MenuCommandTest.  
  
4. Enregistrez et fermez le fichier source. extension. vsixmanifest.  
  
## <a name="adding-a-mef-extension-to-the-command-extension"></a>Ajout d’une extension MEF à l’extension de commande  
  
1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de la solution, cliquez sur **Ajouter**, puis sur **nouveau projet**. Dans la boîte de dialogue **Ajouter un nouveau projet** , cliquez sur **extensibilité** sous **Visual C#**, puis sur **projet VSIX**. Nommez le projet `CommentAdornmentTest`.  
  
2. Étant donné que ce projet interagira avec l’assembly VSPackage avec nom fort, vous devez signer l’assembly. Vous pouvez réutiliser le fichier de clé déjà créé pour l’assembly VSPackage.  
  
    1. Ouvrez les propriétés du projet et sélectionnez l’onglet **signature** .  
  
    2. Sélectionnez **signer l’assembly**.  
  
    3. Sous **choisir un fichier de clé de nom fort**, sélectionnez le fichier. snk de clé qui a été généré pour l’assembly MenuCommandTest.  
  
## <a name="referring-to-the-mef-extension-in-the-vspackage-project"></a>Référence à l’extension MEF dans le projet VSPackage  
 Étant donné que vous ajoutez un composant MEF au VSPackage, vous devez spécifier les deux types de ressources dans le manifeste.  
  
> [!NOTE]
> Pour plus d’informations sur MEF, consultez [Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
#### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>Pour faire référence au composant MEF dans le projet VSPackage  
  
1. Dans le projet MenuCommandTest, ouvrez le fichier source. extension. vsixmanifest dans l’éditeur de manifeste VSIX.  
  
2. Sous l’onglet **ressources** , cliquez sur **nouveau**.  
  
3. Dans la liste **type** , choisissez **Microsoft. VisualStudio. MEFComponent**.  
  
4. Dans la liste **source** , choisissez **un projet dans la solution actuelle**.  
  
5. Dans la liste **projet** , choisissez **CommentAdornmentTest**.  
  
6. Enregistrez et fermez le fichier source. extension. vsixmanifest.  
  
7. Assurez-vous que le projet MenuCommandTest a une référence au projet CommentAdornmentTest.  
  
8. Dans le projet CommentAdornmentTest, définissez le projet de façon à produire un assembly. Dans la **Explorateur de solutions**, sélectionnez le projet et recherchez la propriété copier la sortie de la **génération vers OutputDirectory** dans la fenêtre **Propriétés** et affectez-lui la valeur **true**.  
  
## <a name="defining-a-comment-adornment"></a>Définition d’un ornement de commentaire  
 L’ornement de commentaire lui-même se compose d’un <xref:Microsoft.VisualStudio.Text.ITrackingSpan> qui effectue le suivi du texte sélectionné et de certaines chaînes qui représentent l’auteur et la description du texte.  
  
#### <a name="to-define-a-comment-adornment"></a>Pour définir un ornement de commentaire  
  
1. Dans le projet CommentAdornmentTest, ajoutez un nouveau fichier de classe et nommez-le `CommentAdornment` .  
  
2. Ajoutez les références suivantes :  
  
    1. Microsoft. VisualStudio. CoreUtility  
  
    2. Microsoft. VisualStudio. Text. Data  
  
    3. Microsoft. VisualStudio. Text. Logic  
  
    4. Microsoft. VisualStudio. Text. UI  
  
    5. Microsoft. VisualStudio. Text. UI. WPF  
  
    6. System.ComponentModel.Composition  
  
    7. PresentationCore  
  
    8. PresentationFramework  
  
    9. WindowsBase  
  
3. Ajoutez l’instruction `using` suivante :  
  
    ```vb  
    using Microsoft.VisualStudio.Text;  
    ```  
  
4. Le fichier doit contenir une classe nommée `CommentAdornment` .  
  
    ```  
    internal class CommentAdornment  
    ```  
  
5. Ajoutez trois champs à la `CommentAdornment` classe pour <xref:Microsoft.VisualStudio.Text.ITrackingSpan> , l’auteur et la description.  
  
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
  
## <a name="creating-a-visual-element-for-the-adornment"></a>Création d’un élément visuel pour l’ornement  
 Vous devez également définir un élément visuel pour votre ornement. Pour cette procédure pas à pas, définissez un contrôle qui hérite de la classe Windows Presentation Foundation (WPF) <xref:System.Windows.Controls.Canvas> .  
  
1. Créez une classe dans le projet CommentAdornmentTest et nommez-la `CommentBlock` .  
  
2. Ajoutez les instructions `using` suivantes.  
  
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
  
3. Faites en sorte que la `CommentBlock` classe hérite de <xref:System.Windows.Controls.Canvas> .  
  
    ```csharp  
    internal class CommentBlock : Canvas  
    { }  
    ```  
  
4. Ajoutez des champs privés pour définir les aspects visuels de l’ornement.  
  
    ```csharp  
    private Geometry textGeometry;  
    private Grid commentGrid;  
    private static Brush brush;  
    private static Pen solidPen;  
    private static Pen dashPen;  
    ```  
  
5. Ajoutez un constructeur qui définit l’ornement de commentaire et ajoute le texte approprié.  
  
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
  
6. Implémentez également un <xref:System.Windows.Controls.Panel.OnRender%2A> Gestionnaire d’événements qui dessine l’ornement.  
  
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
  
## <a name="adding-an-iwpftextviewcreationlistener"></a>Ajout d’un IWpfTextViewCreationListener  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>Est une partie du composant MEF que vous pouvez utiliser pour écouter les événements de création de l’affichage.  
  
1. Ajoutez un fichier de classe au projet CommentAdornmentTest et nommez-le `Connector` .  
  
2. Ajoutez les instructions `using` suivantes.  
  
    ```csharp  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Utilities;  
    ```  
  
3. Déclarez une classe qui implémente <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> et exportez-la avec un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de type « text » et un <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> de <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> . L’attribut de type de contenu spécifie le type de contenu auquel le composant s’applique. Le type de texte est le type de base pour tous les types de fichiers non binaires. Par conséquent, presque chaque affichage de texte créé sera de ce type. L’attribut de rôle d’affichage de texte spécifie le type de vue de texte à laquelle le composant s’applique. Les rôles d’affichage de texte de document affichent généralement du texte composé de lignes et stockées dans un fichier.  
  
     [!code-csharp[VSSDKMenuCommandTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkmenucommandtest/cs/commentadornmenttest/connector.cs#11)]
     [!code-vb[VSSDKMenuCommandTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkmenucommandtest/vb/commentadornmenttest/connector.vb#11)]  
  
4. Implémentez la <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> méthode afin qu’elle appelle l' `Create()` événement statique du `CommentAdornmentManager` .  
  
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
  
## <a name="defining-an-adornment-layer"></a>Définition d’une couche d’ornement  
 Pour ajouter un nouvel ornement, vous devez définir une couche d’ornement.  
  
#### <a name="to-define-an-adornment-layer"></a>Pour définir une couche d’ornement  
  
1. Dans la `Connector` classe, déclarez un champ public de type <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition> , puis exportez-le avec un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> qui spécifie un nom unique pour la couche d’ornement et un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> qui définit la relation d’ordre de plan de cette couche d’ornement aux autres couches d’affichage de texte (texte, signe insertion et sélection).  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("CommentAdornmentLayer")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition commentLayerDefinition;  
  
    ```  
  
## <a name="providing-comment-adornments"></a>Fournir des ornements de commentaires  
 Lorsque vous définissez un ornement, implémentez également un fournisseur d’ornements de commentaires et un gestionnaire d’ornements de commentaire. Le fournisseur d’ornements de commentaire conserve une liste d’ornements de commentaires, écoute <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> les événements sur la mémoire tampon de texte sous-jacente et supprime les ornements de commentaires lorsque le texte sous-jacent est supprimé.  
  
1. Ajoutez un nouveau fichier de classe au projet CommentAdornmentTest et nommez-le `CommentAdornmentProvider` .  
  
2. Ajoutez les instructions `using` suivantes.  
  
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
  
4. Ajoutez des champs privés pour la mémoire tampon de texte et la liste des ornements de commentaires relatifs à la mémoire tampon.  
  
    ```csharp  
    private ITextBuffer buffer;  
    private IList<CommentAdornment> comments = new List<CommentAdornment>();  
  
    ```  
  
5. Ajoutez un constructeur pour `CommentAdornmentProvider` . Ce constructeur doit avoir un accès privé, car le fournisseur est instancié par la `Create()` méthode. Le constructeur ajoute le `OnBufferChanged` Gestionnaire d’événements à l' <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> événement.  
  
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
  
8. Ajoutez le `OnBufferChanged` Gestionnaire d’événements.  
  
    ```csharp  
    private void OnBufferChanged(object sender, TextContentChangedEventArgs e)  
    {  
        //Make a list of all comments that have a span of at least one character after applying the change. There is no need to raise a changed event for the deleted adornments. The adornments are deleted only if a text change would cause the view to reformat the line and discard the adornments.  
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);  
  
        foreach (CommentAdornment comment in this.comments)  
        {  
            Span span = comment.Span.GetSpan(e.After);  
            //if a comment does not span at least one character, its text was deleted.   
            if (span.Length != 0)  
            {  
                keptComments.Add(comment);  
            }  
        }  
  
        this.comments = keptComments;  
    }  
  
    ```  
  
     [!code-csharp[VSSDKMenuCommandTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdkmenucommandtest/cs/commentadornmenttest/commentadornmentprovider.cs#21)]
     [!code-vb[VSSDKMenuCommandTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkmenucommandtest/vb/commentadornmenttest/commentadornmentprovider.vb#21)]  
  
9. Ajoutez une déclaration pour un `CommentsChanged` événement.  
  
    ```csharp  
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;  
    ```  
  
10. Créez une `Add()` méthode pour ajouter l’ornement.  
  
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
  
11. Ajoutez une `RemoveComments()` méthode.  
  
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
  
12. Ajoutez une `GetComments()` méthode qui retourne tous les commentaires dans une étendue d’instantanés donnée.  
  
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
  
13. Ajoutez une classe nommée `CommentsChangedEventArgs` , comme suit.  
  
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
  
## <a name="managing-comment-adornments"></a>Gestion des ornements de commentaires  
 Le gestionnaire d’ornements de commentaire crée l’ornement et l’ajoute à la couche d’ornement. Il écoute les <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> événements et <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> afin qu’il puisse déplacer ou supprimer l’ornement. Il écoute également l' `CommentsChanged` événement déclenché par le fournisseur d’ornements de commentaire lorsque des commentaires sont ajoutés ou supprimés.  
  
1. Ajoutez un fichier de classe au projet CommentAdornmentTest et nommez-le `CommentAdornmentManager` .  
  
2. Ajoutez les instructions `using` suivantes.  
  
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
  
4. Ajoutez des champs privés.  
  
    ```csharp  
    private readonly IWpfTextView view;  
    private readonly IAdornmentLayer layer;  
    private readonly CommentAdornmentProvider provider;  
    ```  
  
5. Ajoutez un constructeur qui abonne le gestionnaire aux <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> événements et <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> , ainsi qu’à l' `CommentsChanged` événement. Le constructeur est privé, car le gestionnaire est instancié par la `Create()` méthode statique.  
  
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
  
6. Ajoutez la `Create()` méthode qui obtient un fournisseur ou en crée une si nécessaire.  
  
    ```csharp  
    public static CommentAdornmentManager Create(IWpfTextView view)  
    {  
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });  
    }  
    ```  
  
7. Ajoutez le `CommentsChanged` Gestionnaire.  
  
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
  
8. Ajoutez le <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> Gestionnaire.  
  
    ```csharp  
    private void OnClosed(object sender, EventArgs e)  
    {  
        this.provider.Detach();  
        this.view.LayoutChanged -= OnLayoutChanged;  
        this.view.Closed -= OnClosed;  
    }  
    ```  
  
9. Ajoutez le <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> Gestionnaire.  
  
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
  
10. Ajoutez la méthode privée qui dessine le commentaire.  
  
     [!code-csharp[VSSDKMenuCommandTest#35](../snippets/csharp/VS_Snippets_VSSDK/vssdkmenucommandtest/cs/commentadornmenttest/commentadornmentmanager.cs#35)]
     [!code-vb[VSSDKMenuCommandTest#35](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkmenucommandtest/vb/commentadornmenttest/commentadornmentmanager.vb#35)]  
  
## <a name="using-the-menu-command-to-add-the-comment-adornment"></a>Utilisation de la commande de menu pour ajouter l’ornement de commentaire  
 Vous pouvez utiliser la commande de menu pour créer un ornement de commentaire en implémentant la `MenuItemCallback` méthode du VSPackage.  
  
1. Ajoutez les références suivantes au projet MenuCommandTest :  
  
    - Microsoft. VisualStudio. TextManager. Interop  
  
    - Microsoft. VisualStudio. Editor  
  
    - Microsoft. VisualStudio. Text. UI. WPF  
  
2. Ouvrez le fichier AddAdornment.cs et ajoutez les `using` instructions suivantes.  
  
    ```csharp  
    using Microsoft.VisualStudio.TextManager.Interop;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Editor;  
    using CommentAdornmentTest;  
    ```  
  
3. Supprimez la méthode méthode ShowMessageBox () et ajoutez le gestionnaire de commandes suivant.  
  
    ```csharp  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
4. Ajoutez du code pour obtenir la vue active. Vous devez disposer du `SVsTextManager` Shell Visual Studio pour l’activer `IVsTextView` .  
  
    ```csharp  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
        IVsTextManager txtMgr = (IVsTextManager)ServiceProvider.GetService(typeof(SVsTextManager));  
        IVsTextView vTextView = null;  
        int mustHaveFocus = 1;  
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);  
    }  
    ```  
  
5. Si cet affichage de texte est une instance de la vue de texte de l’éditeur, vous pouvez effectuer un cast de celui-ci en interface, puis <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> obtenir le <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> et son associé <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> . Utilisez <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> pour appeler la `Connector.Execute()` méthode, qui obtient le fournisseur d’ornements de commentaire et ajoute l’ornement. Le gestionnaire de commandes doit maintenant ressembler à ceci :  
  
    ```csharp  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
        IVsTextManager txtMgr = (IVsTextManager)ServiceProvider.GetService(typeof(SVsTextManager));  
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
  
6. Définissez la méthode AddAdornmentHandler comme gestionnaire de la commande AddAdornment dans le constructeur AddAdornment.  
  
    ```csharp  
    private AddAdornment(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
            EventHandler eventHandler = this.AddAdornmentHandler;  
            MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
## <a name="building-and-testing-the-code"></a>Création et test du code  
  
1. Générez la solution et commencez le débogage. L’instance expérimentale doit apparaître.  
  
2. Créer un fichier texte. Tapez du texte, puis sélectionnez-le.  
  
3. Dans le menu **Outils** , cliquez sur **appeler ajouter un ornement**. Une bulle doit être affichée sur le côté droit de la fenêtre texte et doit contenir du texte qui ressemble au texte suivant.  
  
     YourUserName  
  
     Fourscore...  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Liaison d’un type de contenu à une extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
