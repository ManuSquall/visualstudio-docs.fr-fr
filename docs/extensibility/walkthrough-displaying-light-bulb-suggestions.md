---
title: "Procédure pas à pas : Affichage des Suggestions d’ampoule | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
caps.latest.revision: 16
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
ms.openlocfilehash: e3838b7f9161991840bc5498f66abcfd3ce2b248
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-displaying-light-bulb-suggestions"></a>Procédure pas à pas : Affichage des Suggestions d’ampoule
Les ampoules sont des icônes utilisées dans l’éditeur Visual Studio qui se développe pour afficher un ensemble d’actions, par exemple des correctifs pour les problèmes identifiés par les analyseurs de code intégré ou la refactorisation du code.  
  
 Dans les éditeurs Visual c# et Visual Basic, vous pouvez également utiliser la plateforme des compilateurs .NET (« Roslyn ») à écrire et à empaqueter vos propres analyseurs de code avec des actions qui affichent les ampoules automatiquement. Pour plus d'informations, voir :  
  
-   [Comment : Écrire un code c# Diagnostic et correction du Code](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)  
  
-   [Comment : Écrire un Diagnostic de Visual Basic et de correction du Code](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)  
  
 Autres langages tels que C++ fournissent également des ampoules pour certaines actions rapides, comme une suggestion pour créer une implémentation de stub de cette fonction.  
  
 Voici à quoi ressemble une ampoule. Dans un projet Visual Basic ou Visual c#, une ligne ondulée rouge s’affiche sous un nom de variable lorsqu’il n’est pas valide. Lorsque vous déplacez la souris sur l’identificateur non valide, une ampoule apparaît près du curseur.  
  
 ![ampoule](~/extensibility/media/lightbulb.png "l’ampoule")  
  
 Si vous cliquez sur la flèche vers le bas par l’ampoule, un ensemble d’actions suggérées s’affiche, avec un aperçu de l’action sélectionnée. Dans ce cas, il indique les modifications qui seront apportées à votre code si vous exécutez l’action.  
  
 ![aperçu d’ampoule](~/extensibility/media/lightbulbpreview.png "LightBulbPreview")  
  
 Vous pouvez utiliser les ampoules pour fournir vos propres actions suggérées. Par exemple, vous pouvez fournir des actions pour déplacer l’ouverture des accolades pour une nouvelle ligne ou de les déplacer vers la fin de la ligne précédente. La procédure suivante explique comment créer une ampoule qui s’affiche sur le mot en cours et a deux actions suggérées : **convertir en majuscules** et **convertir en minuscules**.  
  
## <a name="prerequisites"></a>Conditions préalables  
 À partir de Visual Studio 2015, vous n’installez pas Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le Kit de développement logiciel Visual Studio plus tard. Pour plus d’informations, consultez [l’installation du Kit de développement logiciel Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Création d’un projet Managed Extensibility Framework (MEF)  
  
1.  Créez un projet VSIX c#. (Dans le **nouveau projet** boîte de dialogue, sélectionnez **Visual C# / extensibilité**, puis **projet VSIX**.) Nommez la solution `LightBulbTest`.  
  
2.  Ajouter un **éditeur classifieur** modèle d’élément au projet. Pour plus d’informations, consultez [avec un éditeur de modèle d’élément pour créer une Extension](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Supprimez les fichiers de classe existants.  
  
4.  Ajoutez la référence suivante au projet et définissez **copie locale** à `False`:  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
5.  Ajoutez un nouveau fichier de classe et nommez-le **LightBulbTest**.  
  
6.  Ajoutez le code suivant à l’aide des instructions :  
  
    ```c#  
    using System;  
    using System.Linq;  
    using System.Collections.Generic;  
    using System.Threading.Tasks;  
    using Microsoft.VisualStudio.Language.Intellisense;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Operations;  
    using Microsoft.VisualStudio.Utilities;  
    using System.ComponentModel.Composition;  
    using System.Threading;  
  
    ```  
  
## <a name="implementing-the-light-bulb-source-provider"></a>Implémentation du fournisseur de Source d’ampoule  
  
1.  Dans le fichier de classe LightBulbTest.cs, supprimez la classe LightBulbTest. Ajoutez une classe nommée **TestSuggestedActionsSourceProvider** qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider> Exporter avec un nom de **Actions suggérées de Test** et un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>de « texte ».</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>  
  
    ```c#  
    [Export(typeof(ISuggestedActionsSourceProvider))]  
    [Name("Test Suggested Actions")]  
    [ContentType("text")]  
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider  
    ```  
  
2.  Dans la classe de fournisseur source, importez le <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>et l’ajouter en tant que propriété.</xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>  
  
    ```c#  
    [Import(typeof(ITextStructureNavigatorSelectorService))]  
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }  
    ```  
  
3.  Implémentez la <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A>méthode pour retourner un <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>objet.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> </xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> Nous aborderons la source dans la section suivante.  
  
    ```c#  
    public ISuggestedActionsSource CreateSuggestedActionsSource(ITextView textView, ITextBuffer textBuffer)  
    {  
        if (textBuffer == null && textView == null)  
        {  
            return null;  
        }  
        return new TestSuggestedActionsSource(this, textView, textBuffer);  
    }  
    ```  
  
## <a name="implementing-the-isuggestedactionsource"></a>L’implémentation de la ISuggestedActionSource  
 La source de l’action suggérée est responsable de la collecte de l’ensemble d’actions suggérées et les ajouter dans le bon contexte. Dans ce cas le contexte est le mot en cours et les actions suggérées sont **UpperCaseSuggestedAction** et **LowerCaseSuggestedAction**, qui seront abordées dans la section suivante.  
  
1.  Ajoutez une classe **TestSuggestedActionsSource** qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>  
  
    ```c#  
    internal class TestSuggestedActionsSource : ISuggestedActionsSource  
    ```  
  
2.  Ajouter des champs en lecture seule privés pour le fournisseur de code source action suggérée, la mémoire tampon de texte et l’affichage de texte.  
  
    ```c#  
    private readonly TestSuggestedActionsSourceProvider m_factory;  
    private readonly ITextBuffer m_textBuffer;  
    private readonly ITextView m_textView;  
    ```  
  
3.  Ajoutez un constructeur qui définit les champs privés.  
  
    ```c#  
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)  
    {  
        m_factory = testSuggestedActionsSourceProvider;  
        m_textBuffer = textBuffer;  
        m_textView = textView;  
    }  
    ```  
  
4.  Ajoutez une méthode privée qui retourne le mot qui est actuellement en cours du curseur. La méthode suivante se présente à l’emplacement actuel du curseur et demande le navigateur de structure de texte de l’étendue du mot. Si le curseur se trouve sur un mot, le <xref:Microsoft.VisualStudio.Text.Operations.TextExtent>est retournée dans le paramètre out ; sinon la `out` paramètre est `null` et la méthode retourne `false`.</xref:Microsoft.VisualStudio.Text.Operations.TextExtent>  
  
    ```c#  
    private bool TryGetWordUnderCaret(out TextExtent wordExtent)  
    {  
        ITextCaret caret = m_textView.Caret;  
        SnapshotPoint point;  
  
        if (caret.Position.BufferPosition > 0)  
        {  
            point = caret.Position.BufferPosition - 1;  
        }  
        else  
        {  
            wordExtent = default(TextExtent);  
            return false;  
        }  
  
        ITextStructureNavigator navigator = m_factory.NavigatorService.GetTextStructureNavigator(m_textBuffer);  
  
        wordExtent = navigator.GetExtentOfWord(point);  
        return true;  
    }  
    ```  
  
5.  Implémentez la <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A>méthode.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A> L’éditeur appelle cette méthode pour déterminer s’il faut afficher l’ampoule. Cet appel est effectué souvent, par exemple, chaque fois que le curseur se déplace d’une ligne à un autre, ou lorsque la souris pointe sur un soulignement ondulé d’erreur. Il est asynchrone afin d’autoriser d’autres opérations de l’interface utilisateur d’exercer pendant que cette méthode fonctionne. Dans la plupart des cas, que cette méthode doit effectuer certaines l’analyse et l’analyse de la ligne actuelle, par conséquent, le traitement peut prendre du temps.  
  
     Dans notre implémentation il obtient de façon asynchrone le <xref:Microsoft.VisualStudio.Text.Operations.TextExtent>et détermine si l’étendue est significative, par exemple, si il y a une autre que des espaces blancs.</xref:Microsoft.VisualStudio.Text.Operations.TextExtent>  
  
    ```c#  
    public Task<bool> HasSuggestedActionsAsync(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)  
    {  
        return Task.Factory.StartNew(() =>  
        {  
            TextExtent extent;  
            if (TryGetWordUnderCaret(out extent))  
            {  
                // don't display the action if the extent has whitespace  
                return extent.IsSignificant;  
              }  
            return false;  
        });  
    }  
    ```  
  
6.  Implémentez la <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A>méthode qui retourne un tableau de <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet>objets qui contiennent les différentes <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>objets.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> </xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> </xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> Cette méthode est appelée lorsque l’ampoule est développé.  
  
    > [!WARNING]
    >  Vous devez vous assurer que les implémentations de `HasSuggestedActionsAsync()` et `GetSuggestedActions()` sont cohérent ; que, si `HasSuggestedActionsAsync()` retourne `true`, puis `GetSuggestedActions()` doit avoir certaines actions à afficher. Dans de nombreux cas `HasSuggestedActionsAsync()` est appelé juste avant `GetSuggestedActions()`, mais cela n’est pas toujours le cas. Par exemple, si l’utilisateur appelle les actions de l’ampoule en appuyant sur (CTRL +.) uniquement `GetSuggestedActions()` est appelée.  
  
    ```c#  
    public IEnumerable<SuggestedActionSet> GetSuggestedActions(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)  
    {  
        TextExtent extent;  
        if (TryGetWordUnderCaret(out extent) && extent.IsSignificant)  
        {  
            ITrackingSpan trackingSpan = range.Snapshot.CreateTrackingSpan(extent.Span, SpanTrackingMode.EdgeInclusive);  
            var upperAction = new UpperCaseSuggestedAction(trackingSpan);  
            var lowerAction = new LowerCaseSuggestedAction(trackingSpan);  
            return new SuggestedActionSet[] { new SuggestedActionSet(new ISuggestedAction[] { upperAction, lowerAction }) };  
        }  
        return Enumerable.Empty<SuggestedActionSet>();  
    }   
    ```  
  
7.  Définir un `SuggestedActionsChanged` événement.  
  
    ```c#  
    public event EventHandler<EventArgs> SuggestedActionsChanged;  
    ```  
  
8.  Pour effectuer la mise en oeuvre, ajouter des implémentations pour les `Dispose()` et `TryGetTelemetryId()` méthodes. Nous ne voulons pas faire de télémétrie, donc renvoient la valeur false et le GUID du jeu vide.  
  
    ```c#  
    public void Dispose()  
    {  
    }  
  
    public bool TryGetTelemetryId(out Guid telemetryId)  
    {  
        // This is a sample provider and doesn't participate in LightBulb telemetry  
        telemetryId = Guid.Empty;  
        return false;  
    }  
    ```  
  
## <a name="implementing-light-bulb-actions"></a>Mise en œuvre des Actions d’ampoule  
  
1.  Dans le projet, ajoutez une référence à Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll et affectez **copie locale** à `False`.  
  
2.  Créer deux classes, le premier nommé `UpperCaseSuggestedAction` et le second nommé `LowerCaseSuggestedAction`. Les deux classes implémentent <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>  
  
    ```c#  
    internal class UpperCaseSuggestedAction : ISuggestedAction   
    internal class LowerCaseSuggestedAction : ISuggestedAction  
    ```  
  
     Les deux classes sont similaires à ceci près qu’un appelle <xref:System.String.ToUpper%2A>et d’autres appels <xref:System.String.ToLower%2A>.</xref:System.String.ToLower%2A> </xref:System.String.ToUpper%2A> Les étapes suivantes traitent uniquement de la classe d’action de mise en majuscules, mais vous devez implémenter les deux classes. Appliquez les étapes d’implémentation de l’action de mise en majuscules comme modèle pour l’implémentation de l’action de mise en minuscules.  
  
3.  Ajoutez le code suivant à l’aide des instructions pour ces classes :  
  
    ```c#  
    using Microsoft.VisualStudio.Imaging.Interop;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Documents;  
    using System.Windows.Media;  
  
    ```  
  
4.  Déclarez un ensemble de champs privés.  
  
    ```c#  
    private ITrackingSpan m_span;  
    private string m_upper;  
    private string m_display;  
    private ITextSnapshot m_snapshot;  
    ```  
  
5.  Ajoutez un constructeur qui définit les champs.  
  
    ```c#  
    public UpperCaseSuggestedAction(ITrackingSpan span)  
    {  
        m_span = span;  
        m_snapshot = span.TextBuffer.CurrentSnapshot;  
        m_upper = span.GetText(m_snapshot).ToUpper();  
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));  
    }  
    ```  
  
6.  Implémentez la <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A>méthode afin qu’elle affiche l’aperçu de l’action.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A>  
  
    ```c#  
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)  
    {  
        var textBlock = new TextBlock();  
        textBlock.Padding = new Thickness(5);  
        textBlock.Inlines.Add(new Run() { Text = m_upper });  
        return Task.FromResult<object>(textBlock);  
    }  
    ```  
  
7.  Implémentez la <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A>méthode afin qu’elle retourne la valeur vide <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet>énumération.</xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> </xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A>  
  
    ```c#  
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)  
    {  
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);  
    }  
    ```  
  
8.  Implémentez les propriétés comme suit.  
  
    ```c#  
    public bool HasActionSets  
    {  
        get { return false; }  
    }  
    public string DisplayText  
    {  
        get { return m_display; }  
    }  
    public ImageMoniker IconMoniker  
    {  
       get { return default(ImageMoniker); }  
    }  
    public string IconAutomationText  
    {  
        get  
        {  
            return null;  
        }  
    }  
    public string InputGestureText  
    {  
        get  
        {  
            return null;  
        }  
    }  
    public bool HasPreview  
    {  
        get { return true; }  
    }  
    ```  
  
9. Implémentez la <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A>méthode en remplaçant le texte dans l’étendue par son équivalent en majuscule.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A>  
  
    ```c#  
    public void Invoke(CancellationToken cancellationToken)  
    {  
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);  
    }  
    ```  
  
    > [!WARNING]
    >  L’action de l’ampoule **Invoke** méthode n’est pas attendue pour afficher l’interface utilisateur.  Si votre action apporte de la nouvelle interface utilisateur (par exemple un dialogue Aperçu ou sélection), ne pas afficher l’interface utilisateur directement à partir du **Invoke** méthode mais au lieu de cela planifier pour afficher votre interface utilisateur après le retour **Invoke**.  
  
10. Pour compléter l’implémentation, ajoutez le `Dispose()` et `TryGetTelemetryId()` méthodes.  
  
    ```c#  
    public void Dispose()  
    {  
    }  
  
    public bool TryGetTelemetryId(out Guid telemetryId)  
    {  
        // This is a sample action and doesn't participate in LightBulb telemetry  
        telemetryId = Guid.Empty;  
        return false;  
    }  
    ```  
  
11. N’oubliez pas de faire la même chose `LowerCaseSuggestedAction` modifier le texte d’affichage à « Convertir '{0}' en minuscules » et l’appel <xref:System.String.ToUpper%2A>à <xref:System.String.ToLower%2A>.</xref:System.String.ToLower%2A> </xref:System.String.ToUpper%2A>  
  
## <a name="building-and-testing-the-code"></a>Création et test du code  
 Pour tester ce code, générez la solution LightBulbTest et exécutez-le dans l’instance expérimentale.  
  
1.  Générez la solution.  
  
2.  Lorsque vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est instanciée.  
  
3.  Créez un fichier texte et tapez du texte. Vous devez voir une ampoule apparaît à gauche du texte.  
  
     ![tester l’ampoule](~/extensibility/media/testlightbulb.png "TestLIghtBulb")  
  
4.  Pointez sur l’ampoule. Vous devez voir une flèche vers le bas.  
  
5.  Lorsque vous cliquez sur l’ampoule, deux actions suggérées doivent être affichées, ainsi que la version préliminaire de l’action sélectionnée.  
  
     ![tester l’ampoule, développé](~/extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")  
  
6.  Si vous cliquez sur la première action, tout le texte du mot actuel doit être converti en majuscules. Si vous cliquez sur la deuxième action, tout le texte doit être converti en minuscules.
