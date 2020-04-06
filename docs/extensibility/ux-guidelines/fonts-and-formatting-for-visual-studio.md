---
title: Fonts et formatage pour Visual Studio (fr) Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf1550026fb5c9d9395d931f21d48bc4739ea8c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698578"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Polices et mise en forme pour Visual Studio
## <a name="the-environment-font"></a><a name="BKMK_TheEnvironmentFont"></a>La police de l’environnement
 Toutes les polices de Visual Studio doivent être exposées à l’utilisateur pour la personnalisation. Ceci est principalement fait par le biais de la page **Fonts et Couleurs** dans le dialogue **Tools > Options.** Les trois principales catégories de paramètres de police sont les :

- **Police de l’environnement** - la police principale pour l’IDE (environnement de développement intégré), utilisé pour tous les éléments d’interface, y compris les dialogues, menus, fenêtres d’outils, et les fenêtres de documents. Par défaut, la police de l’environnement est liée à une police système qui apparaît comme 9 pt Segoe interface utilisateur dans les versions actuelles de Windows. L’utilisation d’une police pour tous les éléments d’interface permet d’assurer une apparence de police cohérente tout au long de l’IDE.

- **Éditeur de texte** - éléments qui font surface dans le code et d’autres éditeurs basés sur le texte peuvent être personnalisés dans la page de l’éditeur de texte dans **Tools > Options**.

- **Collections spécifiques** - fenêtres de concepteur qui offrent la personnalisation de leurs éléments d’interface peut exposer des polices spécifiques à leur surface de conception dans leur propre page de paramètres dans **Tools > Options**.

### <a name="editor-font-customization-and-resizing"></a>Personnalisation et resizing de police d’éditeur
 Les utilisateurs agrandissent ou zooment souvent la taille et/ou la couleur du texte dans l’éditeur en fonction de leur préférence, indépendamment de l’interface utilisateur générale. Étant donné que la police de l’environnement est utilisée sur des éléments qui peuvent apparaître à l’intérieur ou dans le cadre d’un éditeur/concepteur, il est important de noter le comportement attendu lorsque l’une de ces classifications de police est modifiée.

 Lors de la création d’éléments d’interface utilisateur qui apparaissent dans l’éditeur, mais ne font pas partie du *contenu,* il est important d’utiliser la police de l’environnement et non pas la police de texte de sorte que les éléments resize d’une manière prévisible.

1. Pour le texte de code dans l’éditeur, resize avec le réglage de police de texte de code et répondre au niveau de zoom du texte de l’éditeur.

2. Tous les autres éléments de l’interface doivent être liés au réglage de la police de l’environnement et répondre à tout changement global dans l’environnement. Cela comprend (mais ne se limite pas à):

    - Textes dans les menus contextuels

    - Texte dans une parure d’éditeur, comme le texte de menu d’ampoule, rapide trouver la vitre d’éditeur, et naviguer à la vitre

    - Étiquette texte dans les boîtes de dialogue, comme **Trouver dans les fichiers** ou **Refactor**

### <a name="accessing-the-environment-font"></a>Accès à la police de l’environnement
 Dans le code Native ou WinForms, la police `IUIHostLocale::GetDialogFont` de l’environnement peut `SID_SUIHostLocale` être consultée en appelant la méthode après avoir interrogé l’interface à partir du service.

 Pour Windows Presentation Foundation (WPF), retirez votre classe `DialogWindow` de fenêtre de `Window` dialogue de la classe de la coquille au lieu de la classe de WPF.

 Dans XAML, le code ressemble à ceci:

```xaml
<ui:DialogWindow
    x:Class"MyNameSpace.MyWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:s="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:ui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"
    ShowInTaskbar="False"
    WindowStartupLocation="CenterOwner"
    Title="My Dialog">
</ui:DialogWindow>
```

Code derrière :

```csharp
internal partial class WebConfigModificationWindow : DialogWindow
{
}
```

 (Remplacer `Microsoft.VisualStudio.Shell.11.0` par la version actuelle de la dll MPF.)

 Pour afficher le dialogue,`ShowModal()`appelez " `ShowDialog()`sur la classe plus . `ShowModal()`définit l’état modal correct dans la coquille, assure que le dialogue est centré dans la fenêtre parente, et ainsi de suite.

 Le code est le suivant :

```csharp
MyWindow window = new MyWindow();
window.ShowModal()
```

 `ShowModal`retourne un bool? (Boolean nul) avec `DialogResult`le , qui peut être utilisé si nécessaire. La valeur de retour est vraie si le dialogue a été fermé avec **OK**.

 Si vous avez besoin d’afficher une interface utilisateur WPF qui `HwndSource`n’est pas un dialogue et est hébergé dans son propre , comme une fenêtre popup ou une fenêtre enfant WPF d’une fenêtre parente Win32/WinForms, vous aurez besoin de définir l’élément `FontFamily` racine et `FontSize` sur l’élément WPF. (La coquille définit les propriétés sur la fenêtre principale, mais elles ne seront pas héritées du passé). `HWND` La coquille fournit des ressources auxquelles les propriétés peuvent être liées, comme ceci :

```xaml
<Setter Property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
<Setter Property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />
```

### <a name="formatting-scalingbolding-reference"></a><a name="BKMK_Formatting"></a>Référence de mise en forme (mise à l’échelle/bolding)
 Certains dialogues exigent que le texte particulier soit audacieux ou une taille autre que la police de l’environnement. Auparavant, les polices plus grandes que`environment font +2`la police de l’environnement étaient codées comme « ou similaires . L’utilisation des extraits de code fournis prendra en charge les moniteurs À haute teneur en DPI et s’assurera que le texte d’affichage apparaît toujours à la bonne taille et poids (comme Light ou Semilight).

> [!NOTE]
> Avant d’appliquer le formatage, assurez-vous de suivre les conseils trouvés dans le [style texte](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

 Pour mettre à l’échelle la police de l’environnement, définissez le style du TextBlock ou de l’Étiquette tel qu’indiqué. Chacun de ces extraits de code, correctement utilisés, générera la police correcte, y compris la taille appropriée et les variations de poids.

 Où`vsui`" est une référence `Microsoft.VisualStudio.Shell`à l’espace de nom :

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

#### <a name="375-environment-font--light"></a>375% Police de l’environnement - Lumière

**Apparaît comme:** 34 pt Segoe UI Light

::: moniker range="vs-2017"

**Utilisation pour :** (rare) interface utilisateur de marque unique, comme dans la page De démarrage

::: moniker-end

::: moniker range=">=vs-2019"

**Utilisation pour :** (rare) interface utilisateur de marque unique

::: moniker-end

**Code de procédure:** Où `textBlock` est un TextBlock précédemment défini et `label` est une étiquette précédemment définie:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);
```

**XAML:** Définissez le style du TextBlock ou de l’Étiquette tel qu’il est indiqué.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>
```

#### <a name="310-environment-font--light"></a>310% Police de l’environnement - Lumière
 **Apparaît comme:** 28 pt Segoe UI Light **Use for:** large signature dialog titles, main heading in reports

 **Code de procédure:** Où `textBlock` est un TextBlock précédemment défini et `label` est une étiquette précédemment définie:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);
```

 **XAML:** Définissez le style du TextBlock ou de l’Étiquette tel qu’il est indiqué.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>
```

#### <a name="200-environment-font--semilight"></a>200% Police de l’environnement - Semilight
 **Apparaît comme:** 18 pt Segoe UI Semilight **Use for:** subheadings, titles in small and medium dialogs

 **Code de procédure:** Où `textBlock` est un TextBlock précédemment défini et `label` est une étiquette précédemment définie:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);
```

 **XAML:** Définissez le style du TextBlock ou de l’Étiquette tel qu’il est indiqué :

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>
```

#### <a name="155-environment-font"></a>155% Police de l’environnement
 **Apparaît comme:** 14 pt Segoe UI **Utilisation pour:** titres de section dans document bien l’interface utilisateur ou des rapports

 **Code de procédure:** Où `textBlock` est un TextBlock précédemment défini et `label` est une étiquette précédemment définie:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);
```

 **XAML:** Définissez le style du TextBlock ou de l’Étiquette tel qu’il est indiqué :

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>
```

#### <a name="133-environment-font"></a>133% Police de l’environnement
 **Apparaît comme:** 12 pt Segoe UI **Utilisation pour:** sous-têtes plus petits dans les dialogues signature et documenter bien l’interface utilisateur

 **Code de procédure:** Où `textBlock` est un TextBlock précédemment défini et `label` est une étiquette précédemment définie:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);
```

 **XAML:** Définissez le style du TextBlock ou de l’Étiquette tel qu’il est indiqué :

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>
```

#### <a name="122-environment-font"></a>122% Police de l’environnement
 **Apparaît comme:** 11 pt Segoe UI **Utilisation pour:** titres de section dans les dialogues signature, noeuds supérieurs dans la vue des arbres, navigation onglet vertical

 **Code de procédure:** Où `textBlock` est un TextBlock précédemment défini et `label` est une étiquette précédemment définie:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);
```

 **XAML:** Définissez le style du TextBlock ou de l’Étiquette tel qu’il est indiqué :

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>
```

#### <a name="environment-font--bold"></a>Police de l’environnement et gras
 **Apparaît comme:** audacieux 9 pt Segoe UI **Utilisation pour:** étiquettes et sous-têtes dans les dialogues signature, rapports, et document bien l’interface utilisateur

 **Code de procédure:** Où `textBlock` est un TextBlock précédemment défini et `label` est une étiquette précédemment définie:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironmentBoldStyleKey);
```

 **XAML:** Définissez le style du TextBlock ou de l’Étiquette tel qu’il est indiqué :

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>
```

### <a name="localizable-styles"></a>Styles localisables
 Dans certains cas, les localisateurs devront modifier les styles de police pour différents endroits, tels que l’élimination de l’audace du texte pour les langues d’Asie de l’Est. Pour rendre possible la localisation des styles de police, ces styles doivent être dans le fichier .resx. La meilleure façon d’accomplir cela et encore modifier les styles de police dans le concepteur de formulaire Visual Studio est de définir explicitement les styles de police au moment de la conception. Bien que cela crée un objet de police complète et peut sembler briser l’héritage des polices parent, seule la propriété FontStyle est utilisé pour définir la police.

 La solution est d’accrocher l’événement du formulaire de `FontChanged` dialogue. Dans `FontChanged` le cas où, marchez tous les contrôles et vérifiez si leur police est définie. Si elle est réglée, changez-la en nouvelle police en fonction de la police du formulaire et du style de police précédent du contrôle. Un exemple de ceci dans le code est :

```csharp
private void Form1_FontChanged(object sender, System.EventArgs e)
{
          SetFontStyles();
}

/// <summary>
/// SetFontStyles - This function will iterate all controls on a page
/// and recreate their font with the desired fontstyle.
/// It should be called in the OnFontChanged handler (and also in the constructor
/// in case the IUIService is not available so OnFontChange doesn't fire).
/// This way, when the VS shell font is given to us the controls that have
/// a different style for the font (bolded for example) will recreate their font
/// and use the VS shell font but with a style variation (bolded ...).
/// </summary>
protected void SetFontStyles()
{
     SetFontStyles(this, this, this.Font);
}

protected static void SetFontStyles(Control topControl, Control parent, Font referenceFont)
{
     foreach(Control c in parent.Controls)
     {
          if (c.Controls != null && c.Controls.Count > 0) {
               SetFontStyles(topControl, c, referenceFont);
          }
          if (c.Font != topControl.Font) {
               c.Font = new Font(referenceFont, c.Font.Style);
          }
     }
}
```

 L’utilisation de ce code garantit que lorsque la police du formulaire est mise à jour, les polices de contrôles seront également mises à jour. Cette méthode devrait également être appelée à partir du constructeur du formulaire, `IUIService` parce `FontChanged` que le dialogue pourrait ne pas obtenir un exemple de et l’événement ne sera jamais tirer. Le `FontChanged` crochet permettra aux dialogues de reprendre dynamiquement la nouvelle police même si le dialogue est déjà ouvert.

### <a name="testing-the-environment-font"></a>Test de la police de l’environnement
 Pour vous assurer que votre interface utilisateur utilise la police de l’environnement et respecte les paramètres de taille, ouvrez **des outils > options > environnement > fontes et couleurs** et sélectionnez « Police de l’environnement » dans le cadre du menu « Afficher » le menu d’abandon.

 ![Paramètres de polices et &gt; de couleurs dans le dialogue Tools Options](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201-a_OptionsFonts")<br />Paramètres de polices et &gt; de couleurs dans le dialogue Tools Options

 Définissez la police à quelque chose de très différent de la valeur par défaut. Pour rendre évident que l’interface utilisateur ne met pas à jour, choisissez une police avec serifs (comme "Times New Roman") et définir une très grande taille. Ensuite, testez votre interface utilisateur pour vous assurer qu’elle respecte l’environnement. Voici un exemple utilisant le dialogue de licence :

 ![Exemple de texte d’interface utilisateur qui ne respecte pas la police de l’environnement](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201-b_WrongFontDialog")<br />Exemple de texte d’interface utilisateur qui ne respecte pas la police de l’environnement

 Dans ce cas, les « informations utilisateur » et « informations sur les produits » ne respectent pas la police. Dans certains cas, cela peut être un choix de conception explicite, mais il peut être un bug si la police explicite n’est pas spécifiée dans le cadre des spécifications redline.

 Pour réinitialiser la police, cliquez sur « Utilisez par défaut » sous **Outils > Options > environnement > fontes et couleurs**.

## <a name="text-style"></a><a name="BKMK_TextStyle"></a>Style de texte
 Le style de texte se réfère à la taille de police, le poids, et le boîtier. Pour obtenir des conseils en matière de mise en œuvre, voir [La police de l’environnement](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

### <a name="text-casing"></a>Boîtier de texte

#### <a name="all-caps"></a>Toutes les casquettes
 N’utilisez pas toutes les casquettes pour les titres ou les étiquettes de Visual Studio.

#### <a name="all-lowercase"></a>Tous les lowercase
 N’utilisez pas toutes les minuscules pour les titres ou les étiquettes dans Visual Studio.

#### <a name="sentence-and-title-case"></a>Cas de peine et de titre
 Le texte de Visual Studio doit utiliser soit le cas de titre, soit le cas de phrase, selon la situation.

|Utilisez le cas de titre pour :|Utilisez le boîtier de phrase pour :|
|-------------------------|----------------------------|
|Titres Dialog|Étiquettes|
|Boîtes de groupe|Cases à cocher|
|Éléments de menu|Cases d’option|
|Éléments de menu contextuel|Liste des articles de boîte|
|Boutons|Barres d'état|
|Étiquettes de table||
|En-têtes de colonne||
|Info-bulles||

##### <a name="title-case"></a>Première lettre des mots en majuscule
 Le cas de titre est un style dans lequel les premières lettres de la plupart ou de la totalité des mots dans une phrase sont capitalisées. Dans Visual Studio, le boîtier titre est utilisé pour de nombreux articles, y compris:

- **Tooltips.** Exemple : « Aperçu des éléments sélectionnés »

- **En-têtes de colonne.** Exemple : « Réponse du système »

- **Articles de menu.** Exemple : « Sauvez tous »

  Lors de l’utilisation du cas de titre, ce sont les lignes directrices pour savoir quand capitaliser les mots et quand les laisser minuscules:

|Majuscules|Commentaires et exemples|
|---------------|---------------------------|
|Tous les noms||
|All verbs|Y compris "Est" et d’autres formes de "être"|
|Tous les adverbes|Y compris "Than" et "Quand"|
|Tous les adjectifs|Y compris "Ceci" et "That"|
|Tous les pronoms|Y compris le possessif "Its" ainsi que "It’s", une contraction du pronom "il" et le verbe "est"|
|Premiers et derniers mots, quelles que soient les parties de la parole||
|Prépositions qui font partie d’une phrase verbe|"Closing Out All Windows" ou "Shutting Down the System"|
|Toutes les lettres d’un acronyme|HTML, XML, URL, IDE, RGB|
|Le deuxième mot dans un mot composé s’il s’agit d’un nom ou d’un adjectif approprié, ou si les mots ont le poids égal|Cross-Reference, Logiciel Pré-Microsoft, Lire/Écrire l’accès, Run-Time|

|Minuscules|Exemples|
|---------------|--------------|
|Le deuxième mot dans un mot composé s’il s’agit d’une autre partie de la parole ou d’un participant modifiant le premier mot|Comment faire, Décollage|
|Articles, sauf si l’on est le premier mot dans le titre|a, an, the|
|Coordonner les conjonctions|et, mais, pour, ni, ou|
|Prépositions avec des mots de quatre lettres ou moins en dehors d’une phrase de verbe|dans, sur, comme pour, hors de, sur le dessus de|
|"To" lorsqu’il est utilisé dans une phrase infinitive|"Comment formater votre disque dur"|

##### <a name="sentence-case"></a>Affaire de condamnation
 Le cas de la peine est la méthode de capitalisation standard pour l’écriture dans laquelle seul le premier mot de la phrase est capitalisé, avec tous les noms appropriés et le pronom "je.". En général, le cas de phrase est plus facile à lire pour un public mondial, en particulier lorsque le contenu sera traduit par une machine. Utilisez le boîtier de phrase pour :

1. **Messages de barre d’état.** Ceux-ci sont simples, courts, et ne fournissent que des informations sur l’état. Exemple : « Fichier de projet de chargement »

2. **Tous les autres éléments de l’interface utilisateur,** y compris les étiquettes, les cases à cocher, les boutons radio et les articles de la boîte de liste. Exemple : « Sélectionnez tous les éléments de liste »

### <a name="text-formatting"></a>Mise en forme de texte
 Le formatage de texte par défaut dans Visual Studio 2013 est contrôlé par [La police de l’environnement](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont). Ce service permet d’assurer une apparence de police cohérente tout au long de l’IDE (environnement de développement intégré), et vous devez l’utiliser pour garantir une expérience cohérente pour vos utilisateurs.

 La taille par défaut utilisée par le service de police Visual Studio provient de Windows et apparaît comme 9 pt.

 Vous pouvez appliquer le formatage à la police de l’environnement. Ce sujet couvre comment et où utiliser les styles. Pour obtenir des informations sur la mise en œuvre, consultez [la police de l’environnement](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

#### <a name="bold-text"></a>Texte audacieux
 Le texte audacieux est utilisé avec parcimonie dans Visual Studio et doit être réservé à :

- étiquettes d’interrogation dans les sorciers

- désigner le projet actif dans Solution Explorer

- valeurs dépassées dans la fenêtre d’outils Properties

- certains événements dans les listes d’abandon de l’éditeur Visual Basic

- contenu généré par le serveur dans le document pour les pages Web

- en-têtes de section dans le dialogue complexe ou l’interface utilisateur de concepteur

#### <a name="italics"></a>Italique
 Visual Studio n’utilise ni le texte italique ni le texte italique audacieux.

#### <a name="color"></a>Couleur

- Le bleu est réservé aux hyperliens (navigation et commandement) et ne doit jamais être utilisé pour l’orientation.

- Les titres plus grands (police de l’environnement x 155 % ou plus) peuvent être colorés à ces fins :

  - Pour attirer visuellement l’interface utilisateur Visual Studio signature

  - Attirer l’attention sur un domaine spécifique

  - Pour offrir un soulagement de la couleur standard de texte gris foncé/noir

- La couleur dans les rubriques devrait tirer parti des couleurs existantes de la marque Visual Studio, principalement le violet principal, #FF68217A.

- Lorsque vous utilisez la couleur dans les rubriques, vous devez adhérer aux [directives de couleur Windows](/windows/desktop/uxguide/vis-color), y compris le rapport de contraste et d’autres considérations d’accessibilité.

### <a name="font-size"></a>Taille de la police
 Visual Studio UI conception dispose d’un aspect plus léger avec plus d’espace blanc. Dans la mesure du possible, les barres de chrome et de titre ont été réduites ou supprimées. Bien que la densité de l’information soit une exigence dans Visual Studio, la typographie continue d’être importante, en mettant l’accent sur un espacement plus ouvert des lignes et une variation de la taille et des poids des polices.

 Les tableaux ci-dessous comprennent des détails de conception et des exemples visuels pour les polices d’affichage utilisées dans Visual Studio. Certaines variations de police d’affichage ont à la fois la taille et le poids, tels que Semilight ou Light, codés dans leur apparence.

 Des extraits de code d’implémentation pour toutes les polices d’affichage peuvent être trouvés dans [la référence De formatage (mise à l’échelle/bolding).](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting)

#### <a name="375-environment-font--light"></a>375% Police de l’environnement - Lumière

|||
|-|-|
|**Utilisation:** Rare. Interface utilisateur de marque unique seulement.<br /><br /> **faire:**<br /><br /> - Utiliser l’affaire de la peine<br />- Utilisez toujours le poids léger<br /><br /> **Ne pas:**<br /><br /> - Utilisation de l’interface utilisateur autre que l’interface utilisateur signature telle que La page De démarrage<br />- Audacieux, italique ou gras italique<br />- Utilisation pour le texte du corps<br />- Utilisation dans les fenêtres d’outils|**Apparaît comme:** 34 pt Segoe UI Light<br /><br /> **Exemple visuel :**<br /><br /> *Actuellement non utilisé. Peut être utilisé dans la page de démarrage Visual Studio 2017.*|

#### <a name="310-environment-font--light"></a>310% Police de l’environnement - Lumière

::: moniker range="vs-2017"

|||
|-|-|
|**Utilisation:**<br /><br /> - Plus grand cap dans les dialogues signature<br />- Direction du rapport principal<br /><br /> **faire:**<br /><br /> - Utiliser l’affaire de la peine<br />- Utilisez toujours le poids léger<br /><br /> **Ne pas:**<br /><br /> - Utilisation de l’interface utilisateur autre que l’interface utilisateur signature telle que La page De démarrage<br />- Audacieux, italique ou gras italique<br />- Utilisation pour le texte du corps<br />- Utilisation dans les fenêtres d’outils|**Apparaît comme:** 28 pt Segoe UI Light<br /><br /> **Exemple visuel :**<br /><br /> ![Exemple de police 310% Environnement &#43; tête de lumière](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

::: moniker range=">=vs-2019"

|||
|-|-|
|**Utilisation:**<br /><br /> - Plus grand cap dans les dialogues signature<br />- Direction du rapport principal<br /><br /> **faire:**<br /><br /> - Utiliser l’affaire de la peine<br />- Utilisez toujours le poids léger<br /><br /> **Ne pas:**<br /><br /> - Utilisation de l’interface utilisateur autre que l’interface utilisateur signature<br />- Audacieux, italique ou gras italique<br />- Utilisation pour le texte du corps<br />- Utilisation dans les fenêtres d’outils|**Apparaît comme:** 28 pt Segoe UI Light<br /><br /> **Exemple visuel :**<br /><br /> ![Exemple de police 310% Environnement &#43; tête de lumière](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

#### <a name="200-environment-font--semilight"></a>200% Police de l’environnement - Semilight

|||
|-|-|
|**Utilisation:**<br /><br /> - Sous-titrages<br />- Titres en petits et moyens dialogues<br /><br /> **faire:**<br /><br /> - Utiliser l’affaire de la peine<br />- Utilisez toujours le poids Semilight<br /><br /> **Ne pas:**<br /><br /> - Audacieux, italique ou gras italique<br />- Utilisation pour le texte du corps<br />- Utilisation dans les fenêtres d’outils|**Apparaît comme:** 18 pt Segoe UI Semillight<br /><br /> **Exemple visuel :**<br /><br /> ![Exemple de police 200% Environnement &#43; Semilight](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202-b_EF200")|

#### <a name="155-environment-font"></a>155% Police de l’environnement

|||
|-|-|
|**Utilisation:**<br /><br /> - Section des rubriques dans le document bien l’interface utilisateur<br />- Rapports<br /><br /> **Faire:** Utiliser le cas de phrase<br /><br /> **Ne pas:**<br /><br /> - Audacieux, italique ou gras italique<br />- Utilisation pour le texte du corps<br />- Utilisation dans les commandes standard visual Studio<br />- Utilisation dans les fenêtres d’outils|**Apparaît comme:** 14 pt Segoe UI<br /><br /> **Exemple visuel :**<br /><br /> ![Exemple de titre de police d'environnement 155 %](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202-c_EF155")|

#### <a name="133-environment-font"></a>133% Police de l’environnement

|||
|-|-|
|**Utilisation:**<br /><br /> - Sous-titrages plus petits dans les dialogues signature<br />- Sous-titrages plus petits dans le document bien l’interface utilisateur<br /><br /> **Faire:** Utiliser le cas de phrase<br /><br /> **Ne pas:**<br /><br /> - Audacieux, italique ou gras italique<br />- Utilisation pour le texte du corps<br />- Utilisation dans les commandes standard visual Studio<br />- Utilisation dans les fenêtres d’outils|**Apparaît comme:** 12 pt Segoe UI<br /><br /> **Exemple visuel :**<br /><br /> ![Exemple de titre de police d'environnement 133 %](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202-d_EF133")|

#### <a name="122-environment-font"></a>122% Police de l’environnement

|||
|-|-|
|**Utilisation:**<br /><br /> - Titres de section dans les dialogues signature<br />- Top nœuds dans la vue d’arbre<br />- Navigation verticale de l’onglet<br /><br /> **Faire:** Utiliser le cas de phrase<br /><br /> **Ne pas:**<br /><br /> - Audacieux, italique ou gras italique<br />- Utilisation pour le texte du corps<br />- Utilisation dans les commandes standard visual Studio<br />- Utilisation dans les fenêtres d’outils|**Apparaît comme:** 11 pt Segoe UI<br /><br /> **Exemple visuel :**<br /><br /> ![Exemple de titre de police d'environnement 122 %](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202-e_EF122")|

#### <a name="environment-font--bold"></a>Police de l’environnement et gras

|||
|-|-|
|**Utilisation:**<br /><br /> - Étiquettes et sous-têtes dans les dialogues signature<br />- Étiquettes et sous-têtes dans les rapports<br />- Étiquettes et sous-têtes dans le document bien l’interface utilisateur<br /><br /> **faire:**<br /><br /> - Utiliser l’affaire de la peine<br />- Utiliser un poids gras<br /><br /> **Ne pas:**<br /><br /> - Italique ou gras italique<br />- Utilisation pour le texte du corps<br />- Utilisation dans les commandes standard visual Studio<br />- Utilisation dans les fenêtres d’outils|**Apparaît comme:** audacieux 9 pt Segoe UI<br /><br /> **Exemple visuel :**<br /><br /> ![Exemple de police de l’environnement &#43; tête audacieuse](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202-f_EFB")|

#### <a name="environment-font"></a>Police de l’environnement

|||
|-|-|
|**Utilisation:** Tous les autres textes<br /><br /> **Faire:** Utiliser le cas de phrase<br /><br /> **Ne pas:** Italique ou audacieux italique|**Apparaît comme:** 9 pt Segoe UI<br /><br /> **Exemple visuel :**<br /><br /> ![Exemple de police d'environnement](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202-g_EF")|

### <a name="padding-and-spacing"></a>Padding et espacement
 Les rubriques ont besoin d’espace autour d’eux pour leur donner l’accent approprié. Cet espace varie en fonction de la taille du point et de ce qui se trouve près du cap, comme une règle horizontale ou une ligne de texte dans la police de l’environnement.

- Le rembourrage idéal pour un cap par lui-même devrait être 90% de l’espace de hauteur de caractère de capital. Par exemple, un cap Segoe UI Light de 28 pt a une hauteur de capuchon de 26 pt, et le rembourrage doit être d’environ 23 pt, soit environ 31 pixels.

- L’espace minimum autour d’un titre devrait être de 50% de la hauteur de caractère de la capitale. Moins d’espace peut être utilisé lorsqu’un titre est accompagné d’une règle ou d’un autre élément moulant.

- Le texte de police d’environnement audacieux devrait suivre l’espacement et le rembourrage par défaut de la hauteur de la ligne.

## <a name="see-also"></a>Voir aussi

- [MSDN: Fonts (Windows)](/windows/desktop/uxguide/vis-fonts)
- [MSDN: Texte d’interface utilisateur (Windows)](/windows/desktop/uxguide/text-ui)
