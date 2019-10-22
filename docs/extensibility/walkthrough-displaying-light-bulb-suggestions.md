---
title: 'Procédure pas à pas : affichage des suggestions d’ampoules | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c9d0c0893e7e8bee2b28b095cab08165c8cafa08
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72632618"
---
# <a name="walkthrough-display-light-bulb-suggestions"></a>Procédure pas à pas : afficher les suggestions d’ampoules
Les ampoules sont des icônes de l’éditeur Visual Studio qui se développent pour afficher un ensemble d’actions, par exemple, des correctifs pour les problèmes identifiés par les analyseurs de code intégrés ou la refactorisation de code.

 Dans les éditeurs C# Visual et Visual Basic, vous pouvez également utiliser la .NET Compiler Platform (« Roslyn ») pour écrire et empaqueter vos propres analyseurs de code avec des actions qui affichent automatiquement des ampoules. Pour plus d'informations, voir :

- [Comment : écrire un C# correctif de diagnostic et de code](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)

- [Comment : écrire un correctif de diagnostic et de code Visual Basic](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)

  D’autres langages C++ , tels que, fournissent également des ampoules pour certaines actions rapides, telles que, une suggestion pour créer une implémentation de stub de cette fonction.

  Voici à quoi ressemble une ampoule. Dans un Visual Basic ou un C# projet visuel, un tilde rouge apparaît sous un nom de variable lorsqu’il n’est pas valide. Si vous pointez avec la souris sur l’identificateur non valide, une ampoule apparaît près du curseur.

  ![ampoule](../extensibility/media/lightbulb.png "Ampoule")

  Si vous cliquez sur la flèche vers le bas en regard de l’ampoule, un ensemble d’actions suggérées s’affiche, ainsi qu’un aperçu de l’action sélectionnée. Dans ce cas, il affiche les modifications apportées à votre code si vous exécutez l’action.

  ![Aperçu de la lumière](../extensibility/media/lightbulbpreview.png "LightBulbPreview")

  Vous pouvez utiliser des ampoules pour fournir vos propres actions suggérées. Par exemple, vous pouvez fournir des actions pour déplacer des accolades ouvrantes vers une nouvelle ligne ou les déplacer à la fin de la ligne précédente. La procédure pas à pas suivante montre comment créer une ampoule qui apparaît sur le mot actuel et a deux actions suggérées : **convertir en majuscules** et **convertir en**minuscules.

## <a name="prerequisites"></a>Configuration requise
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Créer un projet Managed Extensibility Framework (MEF)

1. Créez un C# projet VSIX. (Dans la boîte de dialogue **nouveau projet** , sélectionnez **Visual C# /extensibilité**, puis **projet VSIX**.) Nommez la solution `LightBulbTest`.

2. Ajoutez un modèle d’élément de **classifieur d’éditeur** au projet. Pour plus d’informations, consultez [créer une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Supprimez les fichiers de classe existants.

4. Ajoutez la référence suivante au projet et définissez **copie locale** sur `False` :

     *Microsoft. VisualStudio. Language. IntelliSense*

5. Ajoutez un nouveau fichier de classe et nommez-le **LightBulbTest**.

6. Ajoutez les directives d’utilisation suivantes :

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

## <a name="implement-the-light-bulb-source-provider"></a>Implémenter le fournisseur de la source de l’ampoule

1. Dans le fichier de classe *LightBulbTest.cs* , supprimez la classe LightBulbTest. Ajoutez une classe nommée **TestSuggestedActionsSourceProvider** qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>. Exportez-le avec un nom de **test actions suggérées** et une <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « Text ».

    ```csharp
    [Export(typeof(ISuggestedActionsSourceProvider))]
    [Name("Test Suggested Actions")]
    [ContentType("text")]
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider
    ```

2. À l’intérieur de la classe de fournisseur source, importez le <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> et ajoutez-le en tant que propriété.

    ```csharp
    [Import(typeof(ITextStructureNavigatorSelectorService))]
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }
    ```

3. Implémentez la méthode <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> pour retourner un objet <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>. La source est traitée dans la section suivante.

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

## <a name="implement-the-isuggestedactionsource"></a>Implémenter ISuggestedActionSource
 La source d’action suggérée est chargée de collecter l’ensemble des actions suggérées et de les ajouter dans le contexte approprié. Dans ce cas, le contexte est le mot actuel et les actions suggérées sont **UpperCaseSuggestedAction** et **LowerCaseSuggestedAction**, ce qui est abordé dans la section suivante.

1. Ajoutez une classe **TestSuggestedActionsSource** qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.

    ```csharp
    internal class TestSuggestedActionsSource : ISuggestedActionsSource
    ```

2. Ajoutez des champs privés en lecture seule pour le fournisseur de source d’action suggéré, la mémoire tampon de texte et l’affichage de texte.

    ```csharp
    private readonly TestSuggestedActionsSourceProvider m_factory;
    private readonly ITextBuffer m_textBuffer;
    private readonly ITextView m_textView;
    ```

3. Ajoutez un constructeur qui définit les champs privés.

    ```csharp
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)
    {
        m_factory = testSuggestedActionsSourceProvider;
        m_textBuffer = textBuffer;
        m_textView = textView;
    }
    ```

4. Ajoutez une méthode privée qui retourne le mot qui se trouve actuellement sous le curseur. La méthode suivante examine l’emplacement actuel du curseur et demande au navigateur de structure de texte l’étendue du mot. Si le curseur se trouve sur un mot, le <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> est retourné dans le paramètre out ; Sinon, le paramètre `out` est `null` et la méthode retourne `false`.

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

5. Implémentez la méthode <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A>. L’éditeur appelle cette méthode pour déterminer s’il faut afficher l’ampoule. Cet appel est souvent effectué, par exemple, chaque fois que le curseur passe d’une ligne à l’autre, ou lorsque la souris pointe sur un tilde d’erreur. Elle est asynchrone pour permettre l’exécution d’autres opérations de l’interface utilisateur pendant que cette méthode fonctionne. Dans la plupart des cas, cette méthode doit effectuer une analyse et une analyse de la ligne en cours, de sorte que le traitement peut prendre un certain temps.

     Dans cette implémentation, elle obtient de manière asynchrone le <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> et détermine si l’étendue est significative, comme dans, si elle a un texte autre que l’espace blanc.

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

6. Implémentez la méthode <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A>, qui retourne un tableau d’objets <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> qui contiennent les différents objets <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>. Cette méthode est appelée lorsque l’ampoule est développée.

    > [!WARNING]
    > Vous devez vous assurer que les implémentations de `HasSuggestedActionsAsync()` et `GetSuggestedActions()` sont cohérentes ; autrement dit, si `HasSuggestedActionsAsync()` retourne `true`, `GetSuggestedActions()` doit afficher certaines actions. Dans de nombreux cas, `HasSuggestedActionsAsync()` est appelé juste avant `GetSuggestedActions()`, mais ce n’est pas toujours le cas. Par exemple, si l’utilisateur appelle les actions de l’ampoule en appuyant sur (**CTRL +** .) seul `GetSuggestedActions()` est appelé.

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

7. Définissez un événement `SuggestedActionsChanged`.

    ```csharp
    public event EventHandler<EventArgs> SuggestedActionsChanged;
    ```

8. Pour terminer l’implémentation, ajoutez des implémentations pour les méthodes `Dispose()` et `TryGetTelemetryId()`. Si vous ne souhaitez pas effectuer de télémétrie, il vous suffit de retourner `false` et de définir le GUID sur `Empty`.

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

## <a name="implement-light-bulb-actions"></a>Implémenter des actions d’ampoules

1. Dans le projet, ajoutez une référence à *Microsoft. VisualStudio. Imaging. Interop. 14.0. designtime. dll* et définissez **copie locale** sur `False`.

2. Créez deux classes, la première nommée `UpperCaseSuggestedAction` et la seconde nommée `LowerCaseSuggestedAction`. Ces deux classes implémentent <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>.

    ```csharp
    internal class UpperCaseSuggestedAction : ISuggestedAction
    internal class LowerCaseSuggestedAction : ISuggestedAction
    ```

     Elles sont identiques, sauf que l’une appelle <xref:System.String.ToUpper%2A> et l’autre appelle <xref:System.String.ToLower%2A>. Les étapes suivantes traitent uniquement de la classe d’action de mise en majuscules, mais vous devez implémenter les deux classes. Appliquez les étapes d’implémentation de l’action de mise en majuscules comme modèle pour l’implémentation de l’action de mise en minuscules.

3. Ajoutez les directives d’utilisation suivantes pour ces classes :

    ```csharp
    using Microsoft.VisualStudio.Imaging.Interop;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Documents;
    using System.Windows.Media;

    ```

4. Déclarez un ensemble de champs privés.

    ```csharp
    private ITrackingSpan m_span;
    private string m_upper;
    private string m_display;
    private ITextSnapshot m_snapshot;
    ```

5. Ajoutez un constructeur qui définit les champs.

    ```csharp
    public UpperCaseSuggestedAction(ITrackingSpan span)
    {
        m_span = span;
        m_snapshot = span.TextBuffer.CurrentSnapshot;
        m_upper = span.GetText(m_snapshot).ToUpper();
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));
    }
    ```

6. Implémentez la méthode <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> pour qu’elle affiche l’aperçu de l’action.

    ```csharp
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)
    {
        var textBlock = new TextBlock();
        textBlock.Padding = new Thickness(5);
        textBlock.Inlines.Add(new Run() { Text = m_upper });
        return Task.FromResult<object>(textBlock);
    }
    ```

7. Implémentez la méthode <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> pour qu’elle retourne une énumération <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> vide.

    ```csharp
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)
    {
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);
    }
    ```

8. Implémentez les propriétés comme suit.

    ```csharp
    public bool HasActionSets
    {
        get { return false; }
    }
    public string DisplayText
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

9. Implémentez la méthode <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A> en remplaçant le texte dans l’étendue par son équivalent en majuscules.

    ```csharp
    public void Invoke(CancellationToken cancellationToken)
    {
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);
    }
    ```

    > [!WARNING]
    > La méthode **Invoke** de l’action d’ampoule n’est pas censée afficher l’interface utilisateur. Si votre action fait apparaître une nouvelle interface utilisateur (par exemple, une boîte de dialogue d’aperçu ou de sélection), n’affichez pas l’interface utilisateur directement à partir de la méthode **Invoke** , mais planifiez l’affichage de votre interface utilisateur après avoir retourné l' **appel**.

10. Pour terminer l’implémentation, ajoutez les méthodes `Dispose()` et `TryGetTelemetryId()`.

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

11. N’oubliez pas de faire la même chose pour `LowerCaseSuggestedAction` la modification du texte d’affichage en « Convert » {0} « en minuscules » et l’appel <xref:System.String.ToUpper%2A> pour <xref:System.String.ToLower%2A>.

## <a name="build-and-test-the-code"></a>Générer et tester le code
 Pour tester ce code, générez la solution LightBulbTest et exécutez-la dans l’instance expérimentale.

1. Générez la solution.

2. Quand vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est démarrée.

3. Créez un fichier texte et tapez du texte. Vous devriez voir une ampoule à gauche du texte.

     ![tester l’ampoule](../extensibility/media/testlightbulb.png "TestLIghtBulb")

4. Pointez sur l’ampoule. Une flèche vers le bas doit s’afficher.

5. Lorsque vous cliquez sur l’ampoule, deux actions suggérées doivent s’afficher, ainsi que l’aperçu de l’action sélectionnée.

     ![ampoule de test, développée](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")

6. Si vous cliquez sur la première action, tout le texte du mot actuel doit être converti en majuscules. Si vous cliquez sur la deuxième action, tout le texte doit être converti en minuscules.
