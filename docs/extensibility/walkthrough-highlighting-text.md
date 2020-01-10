---
title: 'Procédure pas à pas : mise en surbrillance du texte | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd19077424aa5f67cd1d3a8d7f9c6be0e822e351
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75403596"
---
# <a name="walkthrough-highlight-text"></a>Procédure pas à pas : texte en surbrillance
Vous pouvez ajouter différents effets visuels à l’éditeur en créant des composants de Managed Extensibility Framework (MEF). Cette procédure pas à pas montre comment mettre en surbrillance chaque occurrence du mot actuel dans un fichier texte. Si un mot apparaît plusieurs fois dans un fichier texte et que vous placez le signe insertion dans une occurrence, chaque occurrence est mise en surbrillance.

## <a name="prerequisites"></a>Configuration requise
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Créer un projet MEF

1. Créez un C# projet VSIX. (Dans la boîte de dialogue **nouveau projet** , sélectionnez **Visual C# /extensibilité**, puis **projet VSIX**.) Nommez la solution `HighlightWordTest`.

2. Ajoutez un modèle d’élément de classifieur d’éditeur au projet. Pour plus d’informations, consultez [créer une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Supprimez les fichiers de classe existants.

## <a name="define-a-textmarkertag"></a>Définir un TextMarkerTag
 La première étape de la mise en surbrillance du texte consiste à sous-classe <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> et à définir son apparence.

### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>Pour définir un TextMarkerTag et un MarkerFormatDefinition

1. Ajoutez un fichier de classe et nommez-le **HighlightWordTag**.

2. Ajoutez les références suivantes :

    1. Microsoft.VisualStudio.CoreUtility

    2. Microsoft.VisualStudio.Text.Data

    3. Microsoft.VisualStudio.Text.Logic

    4. Microsoft.VisualStudio.Text.UI

    5. Microsoft.VisualStudio.Text.UI.Wpf

    6. System.ComponentModel.Composition

    7. Presentation. Core

    8. Presentation. Framework

3. Importez les espaces de noms suivants.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using System.Linq;
    using System.Threading;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Classification;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Operations;
    using Microsoft.VisualStudio.Text.Tagging;
    using Microsoft.VisualStudio.Utilities;
    using System.Windows.Media;
    ```

4. Créez une classe qui hérite de <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> et nommez-la `HighlightWordTag`.

    ```csharp
    internal class HighlightWordTag : TextMarkerTag
    {

    }
    ```

5. Créez une deuxième classe qui hérite de <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>et nommez-la `HighlightWordFormatDefinition`. Pour pouvoir utiliser cette définition de format pour votre balise, vous devez l’exporter avec les attributs suivants :

    - <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: les balises utilisent ce format pour référencer ce format

    - <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: le format apparaît alors dans l’interface utilisateur

    ```csharp

    [Export(typeof(EditorFormatDefinition))]
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]
    [UserVisible(true)]
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition
    {

    }
    ```

6. Dans le constructeur de HighlightWordFormatDefinition, définissez son nom d’affichage et son apparence. La propriété Background définit la couleur de remplissage, tandis que la propriété Foreground définit la couleur de la bordure.

    ```csharp
    public HighlightWordFormatDefinition()
    {
                this.BackgroundColor = Colors.LightBlue;
        this.ForegroundColor = Colors.DarkBlue;
        this.DisplayName = "Highlight Word";
        this.ZOrder = 5;
    }
    ```

7. Dans le constructeur de HighlightWordTag, transmettez le nom de la définition de format que vous avez créée.

    ```
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }
    ```

## <a name="implement-an-itagger"></a>Implémenter un ITagger
 L’étape suivante consiste à implémenter l’interface <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>. Cette interface affecte à une mémoire tampon de texte donnée des balises qui fournissent une mise en surbrillance du texte et d’autres effets visuels.

### <a name="to-implement-a-tagger"></a>Pour implémenter une balise

1. Créez une classe qui implémente <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> de type `HighlightWordTag`et nommez-la `HighlightWordTagger`.

    ```csharp
    internal class HighlightWordTagger : ITagger<HighlightWordTag>
    {

    }
    ```

2. Ajoutez les propriétés et champs privés suivants à la classe :

    - <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, qui correspond à la vue de texte actuelle.

    - <xref:Microsoft.VisualStudio.Text.ITextBuffer>, qui correspond à la mémoire tampon de texte sous-jacente de la vue de texte.

    - <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>utilisé pour rechercher du texte.

    - <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, qui a des méthodes pour naviguer dans les étendues de texte.

    - <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>, qui contient l’ensemble de mots à mettre en surbrillance.

    - <xref:Microsoft.VisualStudio.Text.SnapshotSpan>, qui correspond au mot actuel.

    - <xref:Microsoft.VisualStudio.Text.SnapshotPoint>, qui correspond à la position actuelle du signe insertion.

    - Objet Lock.

    ```csharp
    ITextView View { get; set; }
    ITextBuffer SourceBuffer { get; set; }
    ITextSearchService TextSearchService { get; set; }
    ITextStructureNavigator TextStructureNavigator { get; set; }
    NormalizedSnapshotSpanCollection WordSpans { get; set; }
    SnapshotSpan? CurrentWord { get; set; }
    SnapshotPoint RequestedPoint { get; set; }
    object updateLock = new object();

    ```

3. Ajoutez un constructeur qui initialise les propriétés répertoriées précédemment et ajoute des gestionnaires d’événements <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> et <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged>.

    ```csharp
    public HighlightWordTagger(ITextView view, ITextBuffer sourceBuffer, ITextSearchService textSearchService,
    ITextStructureNavigator textStructureNavigator)
    {
        this.View = view;
        this.SourceBuffer = sourceBuffer;
        this.TextSearchService = textSearchService;
        this.TextStructureNavigator = textStructureNavigator;
        this.WordSpans = new NormalizedSnapshotSpanCollection();
        this.CurrentWord = null;
        this.View.Caret.PositionChanged += CaretPositionChanged;
        this.View.LayoutChanged += ViewLayoutChanged;
    }

    ```

4. Les gestionnaires d’événements appellent la méthode `UpdateAtCaretPosition`.

    ```csharp
    void ViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
    {
        // If a new snapshot wasn't generated, then skip this layout 
        if (e.NewSnapshot != e.OldSnapshot)
        {
            UpdateAtCaretPosition(View.Caret.Position);
        }
    }

    void CaretPositionChanged(object sender, CaretPositionChangedEventArgs e)
    {
        UpdateAtCaretPosition(e.NewPosition);
    }
    ```

5. Vous devez également ajouter un événement `TagsChanged` qui est appelé par la méthode de mise à jour.

     [!code-csharp[VSSDKHighlightWordTest#10](../extensibility/codesnippet/CSharp/walkthrough-highlighting-text_1.cs)]
     [!code-vb[VSSDKHighlightWordTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-highlighting-text_1.vb)]

6. La méthode `UpdateAtCaretPosition()` recherche dans la mémoire tampon de texte chaque mot identique au mot où le curseur est positionné et construit une liste d’objets <xref:Microsoft.VisualStudio.Text.SnapshotSpan> qui correspondent aux occurrences du mot. Il appelle ensuite `SynchronousUpdate`, qui déclenche l’événement `TagsChanged`.

    ```csharp
    void UpdateAtCaretPosition(CaretPosition caretPosition)
    {
        SnapshotPoint? point = caretPosition.Point.GetPoint(SourceBuffer, caretPosition.Affinity);

        if (!point.HasValue)
            return;

        // If the new caret position is still within the current word (and on the same snapshot), we don't need to check it 
        if (CurrentWord.HasValue
            && CurrentWord.Value.Snapshot == View.TextSnapshot
            && point.Value >= CurrentWord.Value.Start
            && point.Value <= CurrentWord.Value.End)
        {
            return;
        }

        RequestedPoint = point.Value;
        UpdateWordAdornments();
    }

    void UpdateWordAdornments()
    {
        SnapshotPoint currentRequest = RequestedPoint;
        List<SnapshotSpan> wordSpans = new List<SnapshotSpan>();
        //Find all words in the buffer like the one the caret is on
        TextExtent word = TextStructureNavigator.GetExtentOfWord(currentRequest);
        bool foundWord = true;
        //If we've selected something not worth highlighting, we might have missed a "word" by a little bit
        if (!WordExtentIsValid(currentRequest, word))
        {
            //Before we retry, make sure it is worthwhile 
            if (word.Span.Start != currentRequest
                 || currentRequest == currentRequest.GetContainingLine().Start
                 || char.IsWhiteSpace((currentRequest - 1).GetChar()))
            {
                foundWord = false;
            }
            else
            {
                // Try again, one character previous.  
                //If the caret is at the end of a word, pick up the word.
                word = TextStructureNavigator.GetExtentOfWord(currentRequest - 1);

                //If the word still isn't valid, we're done 
                if (!WordExtentIsValid(currentRequest, word))
                    foundWord = false;
            }
        }

        if (!foundWord)
        {
            //If we couldn't find a word, clear out the existing markers
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(), null);
            return;
        }

        SnapshotSpan currentWord = word.Span;
        //If this is the current word, and the caret moved within a word, we're done. 
        if (CurrentWord.HasValue && currentWord == CurrentWord)
            return;

        //Find the new spans
        FindData findData = new FindData(currentWord.GetText(), currentWord.Snapshot);
        findData.FindOptions = FindOptions.WholeWord | FindOptions.MatchCase;

        wordSpans.AddRange(TextSearchService.FindAll(findData));

        //If another change hasn't happened, do a real update 
        if (currentRequest == RequestedPoint)
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(wordSpans), currentWord);
    }
    static bool WordExtentIsValid(SnapshotPoint currentRequest, TextExtent word)
    {
        return word.IsSignificant
            && currentRequest.Snapshot.GetText(word.Span).Any(c => char.IsLetter(c));
    }

    ```

7. L' `SynchronousUpdate` effectue une mise à jour synchrone sur les propriétés de `WordSpans` et de `CurrentWord`, et déclenche l’événement `TagsChanged`.

    ```csharp
    void SynchronousUpdate(SnapshotPoint currentRequest, NormalizedSnapshotSpanCollection newSpans, SnapshotSpan? newCurrentWord)
    {
        lock (updateLock)
        {
            if (currentRequest != RequestedPoint)
                return;

            WordSpans = newSpans;
            CurrentWord = newCurrentWord;

            var tempEvent = TagsChanged;
            if (tempEvent != null)
                tempEvent(this, new SnapshotSpanEventArgs(new SnapshotSpan(SourceBuffer.CurrentSnapshot, 0, SourceBuffer.CurrentSnapshot.Length)));
        }
    }
    ```

8. Vous devez implémenter la méthode <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>. Cette méthode prend une collection d’objets <xref:Microsoft.VisualStudio.Text.SnapshotSpan> et retourne une énumération des étendues de balises.

     Dans C#, implémentez cette méthode en tant qu’itérateur de rendement, qui active l’évaluation paresseuse (autrement dit, l’évaluation du jeu uniquement lorsque des éléments individuels sont accédés) des balises. Dans Visual Basic, ajoutez les balises à une liste et renvoyez la liste.

     Ici, la méthode retourne un objet <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> qui a un <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>« Blue », qui fournit un arrière-plan bleu.

    ```csharp
    public IEnumerable<ITagSpan<HighlightWordTag>> GetTags(NormalizedSnapshotSpanCollection spans)
    {
        if (CurrentWord == null)
            yield break;

        // Hold on to a "snapshot" of the word spans and current word, so that we maintain the same
        // collection throughout
        SnapshotSpan currentWord = CurrentWord.Value;
        NormalizedSnapshotSpanCollection wordSpans = WordSpans;

        if (spans.Count == 0 || wordSpans.Count == 0)
            yield break;

        // If the requested snapshot isn't the same as the one our words are on, translate our spans to the expected snapshot 
        if (spans[0].Snapshot != wordSpans[0].Snapshot)
        {
            wordSpans = new NormalizedSnapshotSpanCollection(
                wordSpans.Select(span => span.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive)));

            currentWord = currentWord.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive);
        }

        // First, yield back the word the cursor is under (if it overlaps) 
        // Note that we'll yield back the same word again in the wordspans collection; 
        // the duplication here is expected. 
        if (spans.OverlapsWith(new NormalizedSnapshotSpanCollection(currentWord)))
            yield return new TagSpan<HighlightWordTag>(currentWord, new HighlightWordTag());

        // Second, yield all the other words in the file 
        foreach (SnapshotSpan span in NormalizedSnapshotSpanCollection.Overlap(spans, wordSpans))
        {
            yield return new TagSpan<HighlightWordTag>(span, new HighlightWordTag());
        }
    }
    ```

## <a name="create-a-tagger-provider"></a>Créer un fournisseur de balises
 Pour créer votre balise, vous devez implémenter un <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>. Cette classe est une partie de composant MEF. vous devez donc définir les attributs appropriés afin que cette extension soit reconnue.

> [!NOTE]
> Pour plus d’informations sur MEF, consultez [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-create-a-tagger-provider"></a>Pour créer un fournisseur de balises

1. Créez une classe nommée `HighlightWordTaggerProvider` qui implémente <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>et exportez-la avec une <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « Text » et une <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.

    ```csharp
    [Export(typeof(IViewTaggerProvider))]
    [ContentType("text")]
    [TagType(typeof(TextMarkerTag))]
    internal class HighlightWordTaggerProvider : IViewTaggerProvider
    { }
    ```

2. Vous devez importer deux services de l’éditeur, le <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> et le <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>pour instancier la balise.

    ```csharp
    [Import]
    internal ITextSearchService TextSearchService { get; set; }

    [Import]
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }

    ```

3. Implémentez la méthode <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> pour retourner une instance de `HighlightWordTagger`.

    ```csharp
    public ITagger<T> CreateTagger<T>(ITextView textView, ITextBuffer buffer) where T : ITag
    {
        //provide highlighting only on the top buffer 
        if (textView.TextBuffer != buffer)
            return null;

        ITextStructureNavigator textStructureNavigator =
            TextStructureNavigatorSelector.GetTextStructureNavigator(buffer);

        return new HighlightWordTagger(textView, buffer, TextSearchService, textStructureNavigator) as ITagger<T>;
    }
    ```

## <a name="build-and-test-the-code"></a>Générer et tester le code
 Pour tester ce code, générez la solution HighlightWordTest et exécutez-la dans l’instance expérimentale.

### <a name="to-build-and-test-the-highlightwordtest-solution"></a>Pour générer et tester la solution HighlightWordTest

1. Générez la solution.

2. Quand vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est démarrée.

3. Créez un fichier texte et tapez du texte dans lequel les mots sont répétés, par exemple, « Hello Hello Hello ».

4. Placez le curseur dans l’une des occurrences de « Hello ». Chaque occurrence doit être mise en surbrillance en bleu.

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : liaison d’un type de contenu à une extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
