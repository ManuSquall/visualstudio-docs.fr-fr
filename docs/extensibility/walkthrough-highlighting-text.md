---
title: 'Procédure pas à pas : Mettre en surbrillance le texte Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c35b1a032993a6c183191aafff77d8adeba4a3ef
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697401"
---
# <a name="walkthrough-highlight-text"></a>Procédure pas à pas : Mettre en évidence le texte
Vous pouvez ajouter différents effets visuels à l’éditeur en créant des composants du Cadre d’exténuabilité gérée (MEF). Cette procédure pas à pas montre comment mettre en évidence chaque occurrence du mot actuel dans un fichier texte. Si un mot se produit plus d’une fois dans un fichier texte, et que vous placez le caret dans un événement, chaque événement est mis en évidence.

## <a name="prerequisites"></a>Prérequis
 A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Créer un projet MEF

1. Créez un projet VSIX CMD. (Dans le dialogue du **nouveau projet,** sélectionnez **Visual C / Extensibility**, puis **VSIX Project**.) Nommez `HighlightWordTest`la solution .

2. Ajoutez un modèle d’élément Classificateur d’éditeur au projet. Pour plus d’informations, voir [Créer une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Supprimez les fichiers de classe existants.

## <a name="define-a-textmarkertag"></a>Décrivez un TextMarkerTag
 La première étape dans la <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> mise en évidence du texte est de sous-classer et de définir son apparence.

### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>Définir un TextMarkerTag et un MarkerFormatDefinition

1. Ajoutez un fichier de classe et **nommez-le HighlightWordTag**.

2. Ajoutez les références suivantes :

    1. Microsoft.VisualStudio.CoreUtility (en anglais seulement)

    2. Microsoft.VisualStudio.Text.Data (en anglais seulement)

    3. Microsoft.VisualStudio.Text.Logic (en anglais seulement)

    4. Microsoft.VisualStudio.Text.UI (en anglais seulement)

    5. Microsoft.VisualStudio.Text.UI.Wpf

    6. System.ComponentModel.Composition

    7. Presentation.Core

    8. Présentation.Cadre

3. Importez les espaces nom suivants.

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

4. Créez une classe qui <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> hérite `HighlightWordTag`et nomme-la .

    ```csharp
    internal class HighlightWordTag : TextMarkerTag
    {

    }
    ```

5. Créer une deuxième classe <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>qui hérite `HighlightWordFormatDefinition`de , et le nommer . Afin d’utiliser cette définition de format pour votre balise, vous devez l’exporter avec les attributs suivants :

    - <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: les balises l’utilisent pour référencer ce format

    - <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: cela provoque l’apparition du format dans l’interface utilisateur

    ```csharp

    [Export(typeof(EditorFormatDefinition))]
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]
    [UserVisible(true)]
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition
    {

    }
    ```

6. Dans le constructeur de HighlightWordFormatDefinition, définissez son nom d’affichage et son apparence. La propriété Background définit la couleur de remplissage, tandis que la propriété de premier plan définit la couleur de la frontière.

    ```csharp
    public HighlightWordFormatDefinition()
    {
                this.BackgroundColor = Colors.LightBlue;
        this.ForegroundColor = Colors.DarkBlue;
        this.DisplayName = "Highlight Word";
        this.ZOrder = 5;
    }
    ```

7. Dans le constructeur de HighlightWordTag, passez au nom de la définition de format que vous avez créée.

    ```
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }
    ```

## <a name="implement-an-itagger"></a>Mettre en œuvre un ITagger
 L’étape suivante consiste <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> à implémenter l’interface. Cette interface attribue, à un tampon de texte donné, des balises qui fournissent la mise en évidence du texte et d’autres effets visuels.

### <a name="to-implement-a-tagger"></a>Pour mettre en œuvre un tagger

1. Créer une classe <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> qui `HighlightWordTag`met en `HighlightWordTagger`œuvre le type , et le nommer .

    ```csharp
    internal class HighlightWordTagger : ITagger<HighlightWordTag>
    {

    }
    ```

2. Ajoutez les champs et les propriétés privés suivants à la classe :

    - Un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, qui correspond à la vue de texte actuelle.

    - Un <xref:Microsoft.VisualStudio.Text.ITextBuffer>, qui correspond au tampon de texte qui sous-tend la vue de texte.

    - Un <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>, qui est utilisé pour trouver du texte.

    - Un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, qui a des méthodes pour naviguer dans les travées de texte.

    - A <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>, qui contient l’ensemble de mots à mettre en évidence.

    - A <xref:Microsoft.VisualStudio.Text.SnapshotSpan>, qui correspond au mot actuel.

    - A <xref:Microsoft.VisualStudio.Text.SnapshotPoint>, qui correspond à la position actuelle du caret.

    - Un objet de serrure.

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

3. Ajoutez un constructeur qui initialise les propriétés énumérées plus tôt et ajoute <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> et <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> les gestionnaires d’événements.

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

4. Les gestionnaires de l’événement appellent tous les deux la `UpdateAtCaretPosition` méthode.

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

5. Vous devez également `TagsChanged` ajouter un événement qui est appelé par la méthode de mise à jour.

     [!code-csharp[VSSDKHighlightWordTest#10](../extensibility/codesnippet/CSharp/walkthrough-highlighting-text_1.cs)]
     [!code-vb[VSSDKHighlightWordTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-highlighting-text_1.vb)]

6. La `UpdateAtCaretPosition()` méthode trouve chaque mot dans le tampon de texte qui est identique au mot <xref:Microsoft.VisualStudio.Text.SnapshotSpan> où le curseur est positionné et construit une liste d’objets qui correspondent aux occurrences du mot. Il appelle `SynchronousUpdate`alors , `TagsChanged` ce qui soulève l’événement.

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

7. Le `SynchronousUpdate` effectue une mise à `WordSpans` jour `CurrentWord` synchrone sur `TagsChanged` le et les propriétés, et soulève l’événement.

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

8. Vous devez <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> implémenter la méthode. Cette méthode prend <xref:Microsoft.VisualStudio.Text.SnapshotSpan> une collection d’objets et renvoie un recensement des travées d’étiquette.

     Dans C, implémentez cette méthode en tant qu’itérateur de rendement, qui permet une évaluation paresseuse (c’est-à-dire l’évaluation de l’ensemble seulement lorsque des éléments individuels sont consultés) des balises. Dans Visual Basic, ajoutez les balises à une liste et retournez la liste.

     Ici, la <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> méthode renvoie un <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>objet qui a un "bleu" , qui fournit un fond bleu.

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

## <a name="create-a-tagger-provider"></a>Créer un fournisseur Tagger
 Pour créer votre tagger, <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>vous devez implémenter un . Cette classe est une partie composante MEF, de sorte que vous devez définir les attributs corrects afin que cette extension soit reconnue.

> [!NOTE]
> Pour plus d’informations sur le MEF, voir [Cadre d’exténuabilité gérée (MEF)](/dotnet/framework/mef/index).

### <a name="to-create-a-tagger-provider"></a>Créer un fournisseur de tagger

1. Créer une `HighlightWordTaggerProvider` classe nommée <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>qui met en <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> œuvre , <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>et l’exporter avec un de "texte" et un de .

    ```csharp
    [Export(typeof(IViewTaggerProvider))]
    [ContentType("text")]
    [TagType(typeof(TextMarkerTag))]
    internal class HighlightWordTaggerProvider : IViewTaggerProvider
    { }
    ```

2. Vous devez importer deux <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> services <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>d’éditeur, le et le , pour instantané le tagger.

    ```csharp
    [Import]
    internal ITextSearchService TextSearchService { get; set; }

    [Import]
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }

    ```

3. Mettre <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> en œuvre `HighlightWordTagger`la méthode pour retourner une instance de .

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

## <a name="build-and-test-the-code"></a>Construire et tester le code
 Pour tester ce code, créez la solution HighlightWordTest et exécutez-la dans l’instance expérimentale.

### <a name="to-build-and-test-the-highlightwordtest-solution"></a>Pour construire et tester la solution HighlightWordTest

1. Générez la solution.

2. Lorsque vous exécutez ce projet dans le débbugger, une deuxième instance de Visual Studio est lancée.

3. Créez un fichier texte et tapez un texte dans lequel les mots sont répétés, par exemple, "bonjour bonjour".

4. Placez le curseur dans l’un des événements de "bonjour". Chaque événement doit être mis en évidence en bleu.

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : liez un type de contenu à une extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
