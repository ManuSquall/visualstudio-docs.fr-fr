---
title: 'Procédure pas à pas : Displaying Light Bulb Suggestions | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 717e8f721b57ec3d7bde04deed167fa2d6461517
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500512"
---
# <a name="walkthrough-display-light-bulb-suggestions"></a>Procédure pas à pas : Affichage de suggestions ampoule
Les ampoules sont des icônes dans l’éditeur Visual Studio développent pour afficher un ensemble d’actions, par exemple, des correctifs pour les problèmes identifiés par les analyseurs de code intégrés ou la refactorisation de code.  
  
 Dans les éditeurs Visual c# et Visual Basic, vous pouvez également utiliser .NET Compiler Platform (« Roslyn ») pour écrire et empaqueter vos propres analyseurs de code avec des actions qui s’affiche automatiquement les ampoules. Pour plus d'informations, voir :  
  
-   [Comment : Écrire un c# diagnostic et un correctif de code](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)  
  
-   [Comment : Écrire un diagnostic de Visual Basic et la correction du code](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)  
  
 Autres langages tels que C++ fournissent également des ampoules pour certaines actions rapides, par exemple, une suggestion pour créer une implémentation de stub de cette fonction.  
  
 Voici à quoi ressemble une ampoule. Dans un projet Visual Basic ou Visual c#, une ligne ondulée rouge s’affiche sous un nom de variable lorsqu’il n’est pas valide. Si vous déplacez la souris sur l’identificateur non valide, une ampoule apparaît près du curseur.  
  
 ![ampoule](../extensibility/media/lightbulb.png "LightBulb")  
  
 Si vous cliquez sur la flèche orientée vers l’ampoule, un ensemble d’actions suggérées s’affiche, ainsi que d’un aperçu de l’action sélectionnée. Dans ce cas, il affiche les modifications sont apportées à votre code si vous exécutez l’action.  
  
 ![aperçu d’ampoule](../extensibility/media/lightbulbpreview.png "LightBulbPreview")  
  
 Vous pouvez utiliser des ampoules pour fournir vos propres actions suggérées. Par exemple, vous pouvez fournir des actions pour déplacer l’ouverture des accolades pour une nouvelle ligne ou les déplacer à la fin de la ligne précédente. La procédure suivante montre comment créer une ampoule qui s’affiche sur le mot actuel et suggère deux actions : **convertir en majuscules** et **convertir en minuscules**.  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [installer le SDK Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-managed-extensibility-framework-mef-project"></a>Créer un projet Managed Extensibility Framework (MEF)  
  
1.  Créez un projet c# VSIX. (Dans le **nouveau projet** boîte de dialogue, sélectionnez **Visual c# / extensibilité**, puis **projet VSIX**.) Nommez la solution `LightBulbTest`.  
  
2.  Ajouter un **classifieur d’éditeur** modèle d’élément au projet. Pour plus d’informations, consultez [créer une extension avec un éditeur de modèle d’élément](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Supprimez les fichiers de classe existants.  
  
4.  Ajoutez la référence suivante au projet et définissez **copie locale** à `False`:  
  
     *Microsoft.VisualStudio.Language.Intellisense*  
  
5.  Ajoutez un nouveau fichier de classe et nommez-le **LightBulbTest**.  
  
6.  Ajoutez le code suivant à l’aide d’instructions :  
  
    ```csharp  
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
  
## <a name="implement-the-light-bulb-source-provider"></a>Implémenter le fournisseur de code source d’ampoule  
  
1.  Dans le *LightBulbTest.cs* fichier de classe, de supprimer la classe LightBulbTest. Ajoutez une classe nommée **TestSuggestedActionsSourceProvider** qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>. Exporter avec un nom de **Actions suggérées de Test** et un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « texte ».  
  
    ```csharp  
    [Export(typeof(ISuggestedActionsSourceProvider))]  
    [Name("Test Suggested Actions")]  
    [ContentType("text")]  
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider  
    ```  
  
2.  Dans la classe de fournisseur de source, importez le <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> et l’ajouter en tant que propriété.  
  
    ```csharp  
    [Import(typeof(ITextStructureNavigatorSelectorService))]  
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }  
    ```  
  
3.  Implémentez le <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> méthode pour retourner un <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> objet. La source est abordée dans la section suivante.  
  
    ```csharp  
    public ISuggestedActionsSource CreateSuggestedActionsSource(ITextView textView, ITextBuffer textBuffer)  
    {  
        if (textBuffer == null || textView == null)  
        {  
            return null;  
        }  
        return new TestSuggestedActionsSource(this, textView, textBuffer);  
    }  
    ```  
  
## <a name="implement-the-isuggestedactionsource"></a>Implémenter le ISuggestedActionSource  
 La source de l’action suggérée est responsable de la collecte de l’ensemble des actions suggérées et les ajouter dans le contexte approprié. Dans ce cas, le contexte est le mot actuel et les actions suggérées sont **UpperCaseSuggestedAction** et **LowerCaseSuggestedAction**, qui est abordé dans la section suivante.  
  
1.  Ajoutez une classe **TestSuggestedActionsSource** qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.  
  
    ```csharp  
    internal class TestSuggestedActionsSource : ISuggestedActionsSource  
    ```  
  
2.  Ajouter des champs privés, en lecture seule pour le fournisseur de code source action suggérée, la mémoire tampon de texte et l’affichage de texte.  
  
    ```csharp  
    private readonly TestSuggestedActionsSourceProvider m_factory;  
    private readonly ITextBuffer m_textBuffer;  
    private readonly ITextView m_textView;  
    ```  
  
3.  Ajoutez un constructeur qui définit les champs privés.  
  
    ```csharp  
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)  
    {  
        m_factory = testSuggestedActionsSourceProvider;  
        m_textBuffer = textBuffer;  
        m_textView = textView;  
    }  
    ```  
  
4.  Ajoutez une méthode privée qui retourne le mot qui est actuellement sous le curseur. La méthode suivante ressemble à l’emplacement actuel du curseur et vous demande le navigateur de structure de texte pour l’étendue du mot. Si le curseur se trouve sur un mot, le <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> est retourné dans le paramètre out ; sinon, le `out` paramètre est `null` et la méthode retourne `false`.  
  
    ```csharp  
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
  
5.  Implémentez la méthode <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A>. L’éditeur appelle cette méthode pour déterminer s’il faut afficher l’ampoule. Cet appel est effectué souvent, par exemple, chaque fois que le curseur se déplace d’une ligne vers un autre, ou lorsque la souris pointe sur un soulignement ondulé d’erreur. Il est asynchrone afin d’autoriser d’autres opérations de l’interface utilisateur à effectuer pendant l’utilisation de cette méthode. Dans la plupart des cas, cette méthode doit effectuer certaines l’analyse et l’analyse de la ligne active, donc le traitement peut prendre un certain temps.  
  
     Dans cette implémentation, il obtient de manière asynchrone le <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> et détermine si l’étendue est significative, par exemple, s’il comporte du texte autre qu’un espace blanc.  
  
    ```csharp  
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
  
6.  Implémentez le <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> (méthode), qui retourne un tableau de <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> objets qui contiennent les différentes <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> objets. Cette méthode est appelée lorsque l’ampoule est développé.  
  
    > [!WARNING]
    >  Vous devez vous assurer que les implémentations de `HasSuggestedActionsAsync()` et `GetSuggestedActions()` sont cohérent ; qui est, si `HasSuggestedActionsAsync()` retourne `true`, puis `GetSuggestedActions()` doit avoir certaines actions à afficher. Dans de nombreux cas, `HasSuggestedActionsAsync()` est appelé juste avant `GetSuggestedActions()`, mais cela n’est pas toujours le cas. Par exemple, si l’utilisateur appelle l’ampoule actions en appuyant sur (**CTRL +** .) uniquement `GetSuggestedActions()` est appelée.  
  
    ```csharp  
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
  
    ```csharp  
    public event EventHandler<EventArgs> SuggestedActionsChanged;  
    ```  
  
8.  Pour effectuer l’implémentation, ajoutez des implémentations pour les `Dispose()` et `TryGetTelemetryId()` méthodes. Vous ne souhaitez pas effectuer de télémétrie, alors retourner simplement `false` et la valeur est le GUID `Empty`.  
  
    ```csharp  
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
  
## <a name="implement-light-bulb-actions"></a>Implémenter des actions d’ampoule  
  
1.  Dans le projet, ajoutez une référence à *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll* et définissez **copie locale** à `False`.  
  
2.  Créer deux classes, le premier nommé `UpperCaseSuggestedAction` et la seconde nommée `LowerCaseSuggestedAction`. Ces deux classes implémentent <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>.  
  
    ```csharp  
    internal class UpperCaseSuggestedAction : ISuggestedAction   
    internal class LowerCaseSuggestedAction : ISuggestedAction  
    ```  
  
     Les deux classes sont similaires à ceci près que l’une appelle <xref:System.String.ToUpper%2A> et les autres appels <xref:System.String.ToLower%2A>. Les étapes suivantes traitent uniquement de la classe d’action de mise en majuscules, mais vous devez implémenter les deux classes. Appliquez les étapes d’implémentation de l’action de mise en majuscules comme modèle pour l’implémentation de l’action de mise en minuscules.  
  
3.  Ajoutez le code suivant à l’aide des instructions pour ces classes :  
  
    ```csharp  
    using Microsoft.VisualStudio.Imaging.Interop;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Documents;  
    using System.Windows.Media;  
  
    ```  
  
4.  Déclarez un ensemble de champs privés.  
  
    ```csharp  
    private ITrackingSpan m_span;  
    private string m_upper;  
    private string m_display;  
    private ITextSnapshot m_snapshot;  
    ```  
  
5.  Ajoutez un constructeur qui définit les champs.  
  
    ```csharp  
    public UpperCaseSuggestedAction(ITrackingSpan span)  
    {  
        m_span = span;  
        m_snapshot = span.TextBuffer.CurrentSnapshot;  
        m_upper = span.GetText(m_snapshot).ToUpper();  
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));  
    }  
    ```  
  
6.  Implémentez la <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> méthode afin qu’elle affiche l’aperçu de l’action.  
  
    ```csharp  
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)  
    {  
        var textBlock = new TextBlock();  
        textBlock.Padding = new Thickness(5);  
        textBlock.Inlines.Add(new Run() { Text = m_upper });  
        return Task.FromResult<object>(textBlock);  
    }  
    ```  
  
7.  Implémentez le <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> méthode afin qu’elle retourne un vide <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> énumération.  
  
    ```csharp  
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)  
    {  
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);  
    }  
    ```  
  
8.  Implémentez les propriétés comme suit.  
  
    ```csharp  
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
  
9. Implémentez la <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A> méthode en remplaçant le texte dans l’étendue par son équivalent en majuscule.  
  
    ```csharp  
    public void Invoke(CancellationToken cancellationToken)  
    {  
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);  
    }  
    ```  
  
    > [!WARNING]
    >  L’action d’ampoule **Invoke** méthode n’est pas censée afficher l’interface utilisateur. Si votre action qu’apporte de la nouvelle interface utilisateur (par exemple une version préliminaire ou la sélection de boîte de dialogue), ne pas afficher l’interface utilisateur directement depuis le **Invoke** méthode mais au lieu de cela planifier pour afficher votre interface utilisateur après le retour **Invoke**.  
  
10. Pour terminer l’implémentation, ajoutez le `Dispose()` et `TryGetTelemetryId()` méthodes.  
  
    ```csharp  
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
  
11. N’oubliez pas de faire la même chose `LowerCaseSuggestedAction` modifier le texte d’affichage à « convertir »{0}» en minuscules » et l’appel <xref:System.String.ToUpper%2A> à <xref:System.String.ToLower%2A>.  
  
## <a name="build-and-test-the-code"></a>Générer et tester le code  
 Pour tester ce code, générez la solution LightBulbTest et exécutez-le dans l’instance expérimentale.  
  
1.  Générez la solution.  
  
2.  Lorsque vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est démarrée.  
  
3.  Créez un fichier texte et tapez du texte. Vous devez voir une ampoule à gauche du texte.  
  
     ![tester l’ampoule](../extensibility/media/testlightbulb.png "TestLIghtBulb")  
  
4.  Pointez sur l’ampoule. Vous devez voir une flèche vers le bas.  
  
5.  Lorsque vous cliquez sur l’ampoule, deux actions suggérées doivent s’afficher, ainsi que la version préliminaire de l’action sélectionnée.  
  
     ![tester l’ampoule, développé](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")  
  
6.  Si vous cliquez sur la première action, tout le texte du mot actuel doit être converti en majuscules. Si vous cliquez sur la deuxième action, tout le texte doit être converti en minuscules.  
  
