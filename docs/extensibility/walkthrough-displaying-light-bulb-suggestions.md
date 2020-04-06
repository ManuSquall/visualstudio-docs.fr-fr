---
title: 'Procédure pas à pas : Affichage des suggestions d’ampoules Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09773e2be81ce51971709db590a07ca9960104fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697474"
---
# <a name="walkthrough-display-light-bulb-suggestions"></a>Procédure pas à pas : Afficher les suggestions d’ampoules
Les ampoules sont des icônes de l’éditeur Visual Studio qui s’étendent pour afficher un ensemble d’actions, par exemple, des correctifs pour les problèmes identifiés par les analyseurs de code intégrés ou la refactoration du code.

 Dans les éditeurs Visual CMD et Visual Basic, vous pouvez également utiliser la plateforme de compilateur .NET («Roslyn») pour écrire et emballer vos propres analyseurs de code avec des actions qui affichent automatiquement des ampoules. Pour plus d'informations, consultez les pages suivantes :

- [Comment : Écrire un diagnostic et un correctif de code CMD](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)

- [Comment: Écrire un diagnostic de base visuelle et correctif de code](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)

  D’autres langues telles que le CMD fournissent également des ampoules pour certaines actions rapides, telles que, une suggestion pour créer une mise en œuvre de talon de cette fonction.

  Voici à quoi ressemble une ampoule. Dans un projet Visual Basic ou Visual C, un gribouillis rouge apparaît sous un nom variable lorsqu’il est invalide. Si vous souris sur l’identifiant invalide, une ampoule apparaît près du curseur.

  ![ampoule](../extensibility/media/lightbulb.png "Ampoule")

  Si vous cliquez sur la flèche vers le bas par l’ampoule, un ensemble d’actions suggérées apparaît, ainsi qu’un aperçu de l’action sélectionnée. Dans ce cas, il affiche les modifications apportées à votre code si vous exécutez l’action.

  ![aperçu d'ampoule](../extensibility/media/lightbulbpreview.png "LightBulbPréview")

  Vous pouvez utiliser des ampoules pour fournir vos propres actions suggérées. Par exemple, vous pouvez fournir des mesures pour déplacer les accolades bouclées d’ouverture vers une nouvelle ligne ou les déplacer à la fin de la ligne précédente. La procédure pas à pas suivante montre comment créer une ampoule qui apparaît sur le mot actuel et a deux actions suggérées: **Convertir en cas supérieur** et convertir en cas **inférieur**.

## <a name="prerequisites"></a>Prérequis
 A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Créer un projet de cadre d’exténuabilité gérée (MEF)

1. Créez un projet VSIX CMD. (Dans le dialogue du **nouveau projet,** sélectionnez **Visual C / Extensibility**, puis **VSIX Project**.) Nommez `LightBulbTest`la solution .

2. Ajoutez un modèle d’élément **Classificateur d’éditeur** au projet. Pour plus d’informations, voir [Créer une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Supprimez les fichiers de classe existants.

4. Ajoutez la référence suivante au projet et `False`définissez Copy **Local** à :

     *Microsoft.VisualStudio.Language.Intellisense*

5. Ajouter un nouveau fichier de classe et le nommer **LightBulbTest**.

6. Ajoutez les directives using suivantes :

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

## <a name="implement-the-light-bulb-source-provider"></a>Mettre en œuvre le fournisseur de source d’ampoules

1. Dans le fichier de classe *LightBulbTest.cs,* supprimez la classe LightBulbTest. Ajouter une classe nommée **TestSuggestedActionsSourceProvider** qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>. Exportez-le avec un nom <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> **d’actions suggérées** par le test et un « texte ».

    ```csharp
    [Export(typeof(ISuggestedActionsSourceProvider))]
    [Name("Test Suggested Actions")]
    [ContentType("text")]
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider
    ```

2. À l’intérieur de <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> la classe fournisseur source, importez le et ajoutez-le comme une propriété.

    ```csharp
    [Import(typeof(ITextStructureNavigatorSelectorService))]
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }
    ```

3. Implémentez <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> la <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> méthode pour retourner un objet. La source est discutée dans la section suivante.

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

## <a name="implement-the-isuggestedactionsource"></a>Mettre en œuvre l’ISuggestedActionSource
 La source d’action suggérée est responsable de la collecte de l’ensemble des actions suggérées et de leur ajout dans le bon contexte. Dans ce cas, le contexte est le mot actuel et les actions suggérées sont **UpperCaseSuggestedAction** et **LowerCaseSuggestedAction**, qui est discuté dans la section suivante.

1. Ajouter une classe **TestSuggestedActionsSource** qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.

    ```csharp
    internal class TestSuggestedActionsSource : ISuggestedActionsSource
    ```

2. Ajoutez des champs privés et lus uniquement pour le fournisseur de source d’action suggéré, le tampon de texte et la vue textuelle.

    ```csharp
    private readonly TestSuggestedActionsSourceProvider m_factory;
    private readonly ITextBuffer m_textBuffer;
    private readonly ITextView m_textView;
    ```

3. Ajouter un constructeur qui définit les champs privés.

    ```csharp
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)
    {
        m_factory = testSuggestedActionsSourceProvider;
        m_textBuffer = textBuffer;
        m_textView = textView;
    }
    ```

4. Ajoutez une méthode privée qui renvoie le mot qui est actuellement sous le curseur. La méthode suivante examine l’emplacement actuel du curseur et demande au navigateur de structure de texte l’étendue du mot. Si le curseur est sur <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> un mot, le est retourné dans le paramètre de sortie; autrement, `out` le `null` paramètre est `false`et la méthode revient .

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

5. Implémentez la méthode <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A>. L’éditeur appelle cette méthode pour savoir s’il faut afficher l’ampoule. Cet appel est fait souvent, par exemple, chaque fois que le curseur se déplace d’une ligne à l’autre, ou lorsque la souris plane au-dessus d’une erreur squiggle. Il est asynchrone afin de permettre à d’autres opérations d’interface utilisateur de continuer pendant que cette méthode fonctionne. Dans la plupart des cas, cette méthode doit effectuer un certain analyse et l’analyse de la ligne actuelle, de sorte que le traitement peut prendre un certain temps.

     Dans cette mise en œuvre, <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> il obtient asynchronement le et détermine si l’étendue est significative, comme dans, si elle a un texte autre que l’espace blanc.

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

6. Implémenter la <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> méthode, <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> qui renvoie <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> une gamme d’objets qui contiennent les différents objets. Cette méthode est appelée lorsque l’ampoule est agrandie.

    > [!WARNING]
    > Vous devez vous assurer que `HasSuggestedActionsAsync()` `GetSuggestedActions()` les implémentations et sont cohérentes; c’est-à-dire, si `HasSuggestedActionsAsync()` les retours `true`, alors `GetSuggestedActions()` devrait avoir quelques actions à afficher. Dans de `HasSuggestedActionsAsync()` nombreux cas, `GetSuggestedActions()`est appelé juste avant , mais ce n’est pas toujours le cas. Par exemple, si l’utilisateur invoque les actions de l’ampoule en appuyant sur **(CTRL .)** seulement `GetSuggestedActions()` est appelé.

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

7. Définissez `SuggestedActionsChanged` un événement.

    ```csharp
    public event EventHandler<EventArgs> SuggestedActionsChanged;
    ```

8. Pour compléter la mise en `Dispose()` œuvre, ajoutez des implémentations pour les méthodes et `TryGetTelemetryId()` les méthodes. Vous ne voulez pas faire de télémétrie, alors il suffit de revenir `false` et de définir le GUID à `Empty`.

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

## <a name="implement-light-bulb-actions"></a>Mettre en œuvre des actions d’ampoule

1. Dans le projet, ajouter une référence à *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll* et définir **Copy Local** à `False`.

2. Créez deux classes, la première nommée `UpperCaseSuggestedAction` et la seconde nommée `LowerCaseSuggestedAction`. Ces deux classes implémentent <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>.

    ```csharp
    internal class UpperCaseSuggestedAction : ISuggestedAction
    internal class LowerCaseSuggestedAction : ISuggestedAction
    ```

     Elles sont identiques, sauf que l’une appelle <xref:System.String.ToUpper%2A> et l’autre appelle <xref:System.String.ToLower%2A>. Les étapes suivantes traitent uniquement de la classe d’action de mise en majuscules, mais vous devez implémenter les deux classes. Appliquez les étapes d’implémentation de l’action de mise en majuscules comme modèle pour l’implémentation de l’action de mise en minuscules.

3. Ajoutez les directives suivantes à l’aide de ces classes :

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

6. Implémentez la <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> méthode afin qu’elle affiche l’aperçu d’action.

    ```csharp
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)
    {
        var textBlock = new TextBlock();
        textBlock.Padding = new Thickness(5);
        textBlock.Inlines.Add(new Run() { Text = m_upper });
        return Task.FromResult<object>(textBlock);
    }
    ```

7. Implémentez la <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> méthode <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> de sorte qu’elle renvoie une énumération vide.

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
    > L’action ampoule **Invoke** méthode ne devrait pas montrer l’interface utilisateur. Si votre action fait état d’une nouvelle interface utilisateur (par exemple un aperçu ou un dialogue de sélection), n’affichez pas l’interface utilisateur directement à partir de la méthode **Invoke,** mais planifiez plutôt d’afficher votre interface utilisateur après son retour **d’Invoke**.

10. Pour compléter la mise `Dispose()` `TryGetTelemetryId()` en œuvre, ajoutez les méthodes et les méthodes.

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

11. N’oubliez pas de faire `LowerCaseSuggestedAction` la même chose pour{0}changer le texte d’affichage en "Convertir' à cas inférieur" et l’appel <xref:System.String.ToUpper%2A> à <xref:System.String.ToLower%2A>.

## <a name="build-and-test-the-code"></a>Construire et tester le code
 Pour tester ce code, créez la solution LightBulbTest et exécutez-la dans l’instance expérimentale.

1. Générez la solution.

2. Lorsque vous exécutez ce projet dans le débbugger, une deuxième instance de Visual Studio est lancée.

3. Créez un fichier texte et tapez du texte. Vous devriez voir une ampoule à gauche du texte.

     ![tester l'ampoule](../extensibility/media/testlightbulb.png "TestLIghtBulb")

4. Pointez vers l’ampoule. Tu devrais voir une flèche vers le bas.

5. Lorsque vous cliquez sur l’ampoule, deux actions suggérées doivent s’afficher, ainsi que l’aperçu de l’action sélectionnée.

     ![tester l’ampoule, développé](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")

6. Si vous cliquez sur la première action, tout le texte dans le mot actuel doit être converti en cas supérieur. Si vous cliquez sur la deuxième action, tout le texte doit être converti en boîtier inférieur.
