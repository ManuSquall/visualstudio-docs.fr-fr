---
title: Polices et mise en forme pour Visual Studio | Microsoft Docs
description: En savoir plus sur les polices et la mise en forme pour les nouvelles fonctionnalités que vous concevez pour Visual Studio, notamment l’utilisation de la police d’environnement.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e6e26b18c838fc240d7fab398f8626890eed0d31
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901680"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Polices et mise en forme pour Visual Studio
## <a name="the-environment-font"></a><a name="BKMK_TheEnvironmentFont"></a> Police de l’environnement
 Toutes les polices dans Visual Studio doivent être exposées à l’utilisateur pour la personnalisation. Cela s’effectue principalement via la page **polices et couleurs** de la boîte de dialogue **Outils > options** . Les trois principales catégories de paramètres de police sont les suivantes :

- **Police** de l’environnement-la police principale de l’IDE (environnement de développement intégré), utilisée pour tous les éléments d’interface, y compris les boîtes de dialogue, les menus, les fenêtres outil et les fenêtres de document. Par défaut, la police d’environnement est liée à une police système qui s’affiche sous la forme 9 PT Segoe UI dans les versions actuelles de Windows. L’utilisation d’une police pour tous les éléments d’interface permet de garantir un aspect cohérent des polices dans l’IDE.

- **Éditeur de texte** -les éléments qui se trouvent dans le code et d’autres éditeurs textuels peuvent être personnalisés dans la page éditeur de texte dans **Outils > options**.

- **Regroupements spécifiques** -les fenêtres du concepteur qui permettent la personnalisation par l’utilisateur de leurs éléments d’interface peuvent exposer des polices spécifiques à leur aire de conception dans leur propre page de paramètres dans **Outils > options**.

### <a name="editor-font-customization-and-resizing"></a>Personnalisation et redimensionnement des polices de l’éditeur
 Les utilisateurs vont souvent agrandir ou zoomer la taille et/ou la couleur du texte dans l’éditeur en fonction de leurs préférences, indépendamment de l’interface utilisateur générale. Étant donné que la police d’environnement est utilisée sur les éléments qui peuvent apparaître dans ou dans le cadre d’un éditeur/concepteur, il est important de noter le comportement attendu quand l’une de ces classifications de police est modifiée.

 Lorsque vous créez des éléments d’interface utilisateur qui s’affichent dans l’éditeur, mais qui ne font pas partie du *contenu*, il est important d’utiliser la police de l’environnement et non la police du texte afin que les éléments se redimensionnent de manière prévisible.

1. Pour le texte de code dans l’éditeur, redimensionnez avec le paramètre de police de texte du code et répondez au niveau de zoom du texte de l’éditeur.

2. Tous les autres éléments de l’interface doivent être liés au paramètre de police d’environnement et répondre à toutes les modifications globales dans l’environnement. Ce sont notamment les suivantes :

    - Texte dans les menus contextuels

    - Texte dans un ornement d’éditeur, comme le texte de menu de l’ampoule, le volet de recherche rapide et le volet naviguer vers

    - Texte de l’étiquette dans les boîtes de dialogue, par exemple **Rechercher dans les fichiers** ou **Refactoriser**

### <a name="accessing-the-environment-font"></a>Accès à la police de l’environnement
 Dans le code natif ou WinForms, la police d’environnement est accessible en appelant la méthode `IUIHostLocale::GetDialogFont` après l’interrogation de l’interface à partir du `SID_SUIHostLocale` service.

 Par Windows Presentation Foundation (WPF), dérivez votre classe de fenêtre de boîte de dialogue à partir de la classe de l’interpréteur de commandes `DialogWindow` au lieu de la classe de WPF `Window` .

 En XAML, le code ressemble à ceci :

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

Code-behind :

```csharp
internal partial class WebConfigModificationWindow : DialogWindow
{
}
```

 (Remplacez `Microsoft.VisualStudio.Shell.11.0` par la version actuelle de la dll MPF.)

 Pour afficher la boîte de dialogue, appelez « `ShowModal()` » sur la classe `ShowDialog()` . `ShowModal()` définit l’État modal correct dans l’interpréteur de commandes, garantit que la boîte de dialogue est centrée dans la fenêtre parente, et ainsi de suite.

 Le code se présente comme suit :

```csharp
MyWindow window = new MyWindow();
window.ShowModal()
```

 `ShowModal` retourne une valeur booléenne ? (valeur booléenne Nullable) avec `DialogResult` , qui peut être utilisé si nécessaire. La valeur de retour est true si la boîte de dialogue a été fermée avec la valeur **OK**.

 Si vous avez besoin d’afficher une interface utilisateur WPF qui n’est pas une boîte de dialogue et qui est hébergée dans sa propre fenêtre `HwndSource` , telle qu’une fenêtre contextuelle ou une fenêtre enfant WPF d’une fenêtre parente Win32/WinForms, vous devez définir les `FontFamily` et `FontSize` sur l’élément racine de l’élément WPF. (L’interpréteur de commandes définit les propriétés dans la fenêtre principale, mais elles ne seront pas héritées après un `HWND` ). L’interpréteur de commandes fournit des ressources auxquelles les propriétés peuvent être liées, comme suit :

```xaml
<Setter Property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
<Setter Property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />
```

### <a name="formatting-scalingbolding-reference"></a><a name="BKMK_Formatting"></a> Référence de mise en forme (mise à l’échelle/mise en gras)
 Certaines boîtes de dialogue nécessitent un texte en gras ou une taille différente de la police de l’environnement. Auparavant, les polices plus volumineuses que la police de l’environnement étaient codées comme « `environment font +2` » ou similaires. L’utilisation des extraits de code fournis prend en charge les moniteurs haute résolution et garantit que le texte affiché apparaît toujours à la taille et au poids corrects (par exemple, Light ou Semilight).

> [!NOTE]
> Avant d’appliquer la mise en forme, vérifiez que vous suivez les instructions fournies dans [style du texte](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle). * *

 Pour mettre à l’échelle la police de l’environnement, définissez le style de TextBlock ou de l’étiquette comme indiqué. Chacun de ces extraits de code, correctement utilisé, génère la police correcte, y compris les variations de taille et de poids appropriées.

 Où « `vsui` » est une référence à l’espace de noms `Microsoft.VisualStudio.Shell` :

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

#### <a name="375-environment-font--light"></a>police d’environnement 375% + clair

**Apparaît comme suit :** 34 PT Segoe UI clair

::: moniker range="vs-2017"

**À utiliser pour :** (rare) une interface utilisateur de personnalisation unique, comme dans la page de démarrage

::: moniker-end

::: moniker range=">=vs-2019"

**À utiliser pour :** (rare) interface utilisateur de personnalisation unique

::: moniker-end

**Code procédural :** Où `textBlock` est un TextBlock précédemment défini et `label` est une étiquette précédemment définie :

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);
```

**Code XAML :** Définissez le style de TextBlock ou de l’étiquette comme indiqué.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>
```

#### <a name="310-environment-font--light"></a>police d’environnement 310% + clair
 **S’affiche sous la forme :** 28 PT Segoe UI légère **utilisation pour :** titres de boîte de dialogue de signature volumineux, en-tête principal dans les rapports

 **Code procédural :** Où `textBlock` est un TextBlock précédemment défini et `label` est une étiquette précédemment définie :

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);
```

 **Code XAML :** Définissez le style de TextBlock ou de l’étiquette comme indiqué.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>
```

#### <a name="200-environment-font--semilight"></a>200% police d’environnement + Semilight
 **Apparaît comme suit :** 18 PT Segoe UI Semilight **utiliser pour :** sous-titres, titres dans les boîtes de dialogue petites et moyennes

 **Code procédural :** Où `textBlock` est un TextBlock précédemment défini et `label` est une étiquette précédemment définie :

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);
```

 **Code XAML :** Définissez le style de TextBlock ou de l’étiquette comme indiqué ci-dessous :

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>
```

#### <a name="155-environment-font"></a>police d’environnement 155%
 **S’affiche sous la forme :** 14 PT Segoe UI **utiliser pour :** en-têtes de section dans l’interface utilisateur ou les rapports du document

 **Code procédural :** Où `textBlock` est un TextBlock précédemment défini et `label` est une étiquette précédemment définie :

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);
```

 **Code XAML :** Définissez le style de TextBlock ou de l’étiquette comme indiqué ci-dessous :

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>
```

#### <a name="133-environment-font"></a>police d’environnement 133%
 **S’affiche sous la forme :** 12 pt Segoe UI **utilisez pour :** sous-titres plus petits dans les boîtes de dialogue de signature et interface utilisateur de document

 **Code procédural :** Où `textBlock` est un TextBlock précédemment défini et `label` est une étiquette précédemment définie :

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);
```

 **Code XAML :** Définissez le style de TextBlock ou de l’étiquette comme indiqué ci-dessous :

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>
```

#### <a name="122-environment-font"></a>police d’environnement 122%
 **S’affiche sous la forme :** 11 PT Segoe UI **utilisez pour :** les en-têtes de section dans les boîtes de dialogue de signature, les nœuds supérieurs dans l’arborescence, la navigation verticale avec onglets

 **Code procédural :** Où `textBlock` est un TextBlock précédemment défini et `label` est une étiquette précédemment définie :

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);
```

 **Code XAML :** Définissez le style de TextBlock ou de l’étiquette comme indiqué ci-dessous :

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>
```

#### <a name="environment-font--bold"></a>Police d’environnement + gras
 **S’affiche sous la forme :** 9 PT en gras Segoe UI **utiliser pour :** étiquettes et sous-titres dans les boîtes de dialogue de signature, les rapports et l’interface utilisateur du document

 **Code procédural :** Où `textBlock` est un TextBlock précédemment défini et `label` est une étiquette précédemment définie :

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironmentBoldStyleKey);
```

 **Code XAML :** Définissez le style de TextBlock ou de l’étiquette comme indiqué ci-dessous :

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>
```

### <a name="localizable-styles"></a>Styles localisables
 Dans certains cas, les localisateurs doivent modifier les styles de police pour des paramètres régionaux différents, par exemple en supprimant le gras du texte pour les langues d’Extrême-Orient. Pour rendre possible la localisation des styles de police, ces styles doivent se trouver dans le fichier. resx. La meilleure façon de procéder et de modifier les styles de police dans le concepteur de formulaires de Visual Studio consiste à définir explicitement les styles de police au moment du Design. Bien que cela crée un objet de police complète et peut sembler rompre l’héritage des polices parentes, seule la propriété FontStyle est utilisée pour définir la police.

 La solution consiste à raccorder l’événement du formulaire de boîte de dialogue `FontChanged` . Dans l' `FontChanged` événement, Parcourez tous les contrôles et vérifiez si leur police est définie. S’il est défini, remplacez-le par une nouvelle police en fonction de la police du formulaire et du style de police précédent du contrôle. Voici un exemple de ce code :

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

 L’utilisation de ce code garantit que lorsque la police du formulaire est mise à jour, les polices des contrôles sont également mises à jour. Cette méthode doit également être appelée à partir du constructeur du formulaire, car la boîte de dialogue peut ne pas parvenir à recevoir une instance de `IUIService` et l' `FontChanged` événement ne se déclenchera jamais. Le raccordement `FontChanged` permet aux boîtes de dialogue de sélectionner dynamiquement la nouvelle police, même si la boîte de dialogue est déjà ouverte.

### <a name="testing-the-environment-font"></a>Test de la police de l’environnement
 Pour vous assurer que votre interface utilisateur utilise la police d’environnement et respecte les paramètres de taille, ouvrez **outils > Options > environnement > polices et couleurs** , puis sélectionnez « police d’environnement » dans le menu déroulant « Afficher les paramètres de : ».

 ![Paramètres des polices et des couleurs dans la &gt; boîte de dialogue Options des outils](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201-a_OptionsFonts")<br />Paramètres des polices et des couleurs dans la &gt; boîte de dialogue Options des outils

 Définissez la police sur une valeur très différente de celle par défaut. Pour que l’interface utilisateur ne soit pas mise à jour, choisissez une police avec empattements (comme « Times New Roman ») et définissez une très grande taille. Testez ensuite votre interface utilisateur pour vous assurer qu’elle respecte l’environnement. Voici un exemple d’utilisation de la boîte de dialogue de licence :

 ![Exemple de texte d’interface utilisateur qui ne respecte pas la police de l’environnement](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201-b_WrongFontDialog")<br />Exemple de texte d’interface utilisateur qui ne respecte pas la police de l’environnement

 Dans ce cas, les informations « utilisateur » et « informations sur le produit » ne respectent pas la police. Dans certains cas, il peut s’agir d’un choix de conception explicite, mais il peut s’agir d’un bogue si la police explicite n’est pas spécifiée dans les spécifications de ligne rouge.

 Pour réinitialiser la police, cliquez sur « utiliser les valeurs par défaut » sous **outils > Options > environnement > polices et couleurs**.

## <a name="text-style"></a><a name="BKMK_TextStyle"></a> Style de texte
 Le style texte fait référence à la taille de police, au poids et à la casse. Pour obtenir des conseils d’implémentation, consultez [la police de l’environnement](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

### <a name="text-casing"></a>Casse du texte

#### <a name="all-caps"></a>Tout en majuscules
 N’utilisez pas toutes les majuscules pour les titres ou les étiquettes dans Visual Studio.

#### <a name="all-lowercase"></a>Tout en minuscules
 N’utilisez pas tout en minuscules pour les titres ou les étiquettes dans Visual Studio.

#### <a name="sentence-and-title-case"></a>Casse des phrases et du titre
 Le texte dans Visual Studio doit utiliser la casse du titre ou le cas de phrase, en fonction de la situation.

|Utiliser la casse du titre pour :|Utiliser la casse en phrases pour :|
|-------------------------|----------------------------|
|Titres de boîtes de dialogue|Étiquettes|
|Zones de groupe|Cases à cocher|
|Éléments de menu|Cases d’option|
|Éléments de menu contextuel|Éléments de zone de liste|
|Boutons|Barres d'état|
|Étiquettes de table||
|En-têtes de colonne||
|Info-bulles||

##### <a name="title-case"></a>Première lettre des mots en majuscule
 Le titre est un style dans lequel les premières lettres de la plupart ou de la totalité des mots d’une expression sont en majuscules. Dans Visual Studio, le titre de la casse est utilisé pour de nombreux éléments, notamment :

- **Info-bulles.** Exemple : « aperçu des éléments sélectionnés »

- **En-têtes de colonne.** Exemple : « réponse du système »

- **Éléments de menu.** Exemple : « enregistrer tout »

  Lors de l’utilisation de la casse du titre, il s’agit des indications pour mettre en majuscules les mots et quand les mettre en minuscules :

|Majuscules|Commentaires et exemples|
|---------------|---------------------------|
|Tous les noms||
|All verbs|Y compris « is » et d’autres formes de « à faire »|
|Toutes les adverbes|Y compris « de » et « When »|
|Tous les adjectifs|Y compris « this » et « This »|
|Tous les pronoms|Y compris la possession « son », ainsi que « c’est », une pronom « it » et le verbe « is »|
|Premier et dernier mots, indépendamment des parties de la parole||
|Prépositions qui font partie d’une expression verbale|« Fermeture de toutes les fenêtres » ou « arrêt du système »|
|Toutes les lettres d’un acronyme|HTML, XML, URL, IDE, RVB|
|Le deuxième mot d’un mot composé s’il s’agit d’un nom ou d’un adjectif approprié, ou si les mots ont le même poids|Références croisées, logiciels pré-Microsoft, accès en lecture/écriture, Run-Time|

|Minuscules|Exemples|
|---------------|--------------|
|Le deuxième mot d’un mot composé s’il s’agit d’une autre partie de la parole ou d’un participe modifiant le premier mot|Procédure, prise en charge|
|Articles, sauf s’il s’agit du premier mot du titre|a, an, the|
|Conjonctions de coordonnées|et, mais, pour, ou|
|Prépositions avec des mots de quatre lettres ou moins en dehors d’une expression verbale|into, to, As pour, out of, en plus de|
|« To » lorsqu’il est utilisé dans une expression infinitive|« Comment formater votre disque dur »|

##### <a name="sentence-case"></a>Casse de la phrase
 La casse en phrases est la méthode de mise en majuscules standard pour l’écriture dans laquelle seul le premier mot de la phrase est capitalisé, avec les noms appropriés et le pronom « I ». En général, la lecture des phrases est plus facile pour un public mondial, en particulier lorsque le contenu est traduit par une machine. Utiliser la casse en phrases pour :

1. **Messages de la barre d’État.** Ils sont simples, courts et fournissent uniquement des informations d’État. Exemple : « chargement du fichier projet »

2. **Tous les autres éléments d’interface utilisateur**, y compris les étiquettes, les cases à cocher, les cases d’option et les éléments de zone de liste. Exemple : « sélectionner tous les éléments dans la liste »

### <a name="text-formatting"></a>Mise en forme de texte
 La mise en forme du texte par défaut dans Visual Studio 2013 est contrôlée par [la police de l’environnement](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont). Ce service permet de garantir un aspect cohérent des polices dans l’environnement de développement intégré (IDE), et vous devez l’utiliser pour garantir une expérience cohérente pour vos utilisateurs.

 La taille par défaut utilisée par le service de police de Visual Studio provient de Windows et apparaît sous la forme 9 PT.

 Vous pouvez appliquer une mise en forme à la police de l’environnement. Cette rubrique explique comment et où utiliser les styles. Pour plus d’informations sur l’implémentation, reportez-vous à [la police de l’environnement](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

#### <a name="bold-text"></a>Texte en gras
 Le texte en gras est utilisé avec modération dans Visual Studio et doit être réservé pour :

- étiquettes de question dans les assistants

- désignation du projet actif dans Explorateur de solutions

- valeurs remplacées dans la fenêtre de l’outil Propriétés

- certains événements dans les listes déroulantes de l’éditeur de Visual Basic

- contenu généré par le serveur dans la structure du document pour les pages Web

- en-têtes de section dans une interface utilisateur de concepteur ou de boîte de dialogue complexe

#### <a name="italics"></a>Italique
 Visual Studio n’utilise pas de texte en italique ou en gras.

#### <a name="color"></a>Couleur

- Le bleu est réservé aux liens hypertexte (navigation et commande) et ne doit jamais être utilisé pour l’orientation.

- Les en-têtes plus grands (police d’environnement x 155% ou plus) peuvent être colorés dans les cas suivants :

  - Pour fournir un attrait visuel à la signature de l’interface utilisateur de Visual Studio

  - Pour attirer l’attention sur une zone spécifique

  - Pour offrir une déchirure de la couleur de texte de l’environnement gris foncé standard/noir

- Les couleurs des en-têtes doivent tirer parti des couleurs existantes de la personnalisation de Visual Studio, principalement la #FF68217A principale violette.

- Lorsque vous utilisez des couleurs dans les en-têtes, vous devez respecter les [instructions de couleurs Windows](/windows/desktop/uxguide/vis-color), notamment le taux de contraste et d’autres considérations relatives à l’accessibilité.

### <a name="font-size"></a>Taille de police
 La conception de l’interface utilisateur de Visual Studio offre une apparence plus claire avec davantage d’espace blanc. Lorsque cela est possible, les barres de chrome et de titre ont été réduites ou supprimées. Alors que la densité des informations est une exigence dans Visual Studio, la typographie continue d’être importante, en mettant l’accent sur davantage d’espacement entre les lignes ouvertes et sur une variation des tailles et des poids des polices.

 Les tableaux ci-dessous incluent des détails de conception et des exemples visuels pour les polices d’affichage utilisées dans Visual Studio. Certaines variations de police d’affichage ont à la fois la taille et le poids, par exemple Semilight ou Light, codées dans leur apparence.

 Les extraits de code d’implémentation pour toutes les polices d’affichage se trouvent dans la [référence de mise en forme (mise à l’échelle/mise en gras)](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting).

#### <a name="375-environment-font--light"></a>police d’environnement 375% + clair

|Utilisation|Apparence|
|-|-|
|**Utilisation :** Rares. Interface utilisateur personnalisée uniquement.<br /><br /> **Ne**<br /><br /> -Utiliser la casse en majuscules<br />-Toujours utiliser l’épaisseur légère<br /><br /> **Ne pas:**<br /><br /> -À utiliser pour l’interface utilisateur autre que la signature (page de démarrage)<br />-Gras, italique ou italique gras<br />-À utiliser pour le corps du texte<br />-À utiliser dans les fenêtres outil|**Apparaît comme suit :** 34 PT Segoe UI clair<br /><br /> **Exemple visuel :**<br /><br /> *Actuellement non utilisé. Peut être utilisé dans la page de démarrage de Visual Studio 2017.*|

#### <a name="310-environment-font--light"></a>police d’environnement 310% + clair

::: moniker range="vs-2017"

|Utilisation|Apparence|
|-|-|
|**Utilisation :**<br /><br /> -Plus grand en-tête dans les boîtes de dialogue de signature<br />-Titre du rapport principal<br /><br /> **Ne**<br /><br /> -Utiliser la casse en majuscules<br />-Toujours utiliser l’épaisseur légère<br /><br /> **Ne pas:**<br /><br /> -À utiliser pour l’interface utilisateur autre que la signature (page de démarrage)<br />-Gras, italique ou italique gras<br />-À utiliser pour le corps du texte<br />-À utiliser dans les fenêtres outil|**Apparaît comme :** 28 PT Segoe UI clair<br /><br /> **Exemple visuel :**<br /><br /> ![Exemple de police d’environnement de 310% &#43; en-tête clair](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

::: moniker range=">=vs-2019"

|Utilisation|Apparence|
|-|-|
|**Utilisation :**<br /><br /> -Plus grand en-tête dans les boîtes de dialogue de signature<br />-Titre du rapport principal<br /><br /> **Ne**<br /><br /> -Utiliser la casse en majuscules<br />-Toujours utiliser l’épaisseur légère<br /><br /> **Ne pas:**<br /><br /> -À utiliser pour l’interface utilisateur autre que la signature<br />-Gras, italique ou italique gras<br />-À utiliser pour le corps du texte<br />-À utiliser dans les fenêtres outil|**Apparaît comme :** 28 PT Segoe UI clair<br /><br /> **Exemple visuel :**<br /><br /> ![Exemple de police d’environnement de 310% &#43; en-tête clair](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

#### <a name="200-environment-font--semilight"></a>200% police d’environnement + Semilight

|Utilisation|Apparence|
|-|-|
|**Utilisation :**<br /><br /> -En-têtes<br />-Titres dans les boîtes de dialogue petites et moyennes<br /><br /> **Ne**<br /><br /> -Utiliser la casse en majuscules<br />-Toujours utiliser le poids de Semilight<br /><br /> **Ne pas:**<br /><br /> -Gras, italique ou italique gras<br />-À utiliser pour le corps du texte<br />-À utiliser dans les fenêtres outil|**S’affiche sous la forme :** 18 PT Segoe UI Semillight<br /><br /> **Exemple visuel :**<br /><br /> ![Exemple de police d’environnement 200% &#43; Semilight](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202-b_EF200")|

#### <a name="155-environment-font"></a>police d’environnement 155%

|Utilisation|Apparence|
|-|-|
|**Utilisation :**<br /><br /> -En-têtes de section dans l’interface utilisateur du document<br />-Rapports<br /><br /> **Procédez comme suit :** Utiliser la casse des phrases<br /><br /> **Ne pas:**<br /><br /> -Gras, italique ou italique gras<br />-À utiliser pour le corps du texte<br />-À utiliser dans les contrôles Visual Studio standard<br />-À utiliser dans les fenêtres outil|**S’affiche sous la forme :** 14 PT Segoe UI<br /><br /> **Exemple visuel :**<br /><br /> ![Exemple de titre de police d'environnement 155 %](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202-c_EF155")|

#### <a name="133-environment-font"></a>police d’environnement 133%

|Utilisation|Apparence|
|-|-|
|**Utilisation :**<br /><br /> -Sous-titres plus petits dans les boîtes de dialogue de signature<br />-Sous-titres plus petits dans l’interface utilisateur du document<br /><br /> **Procédez comme suit :** Utiliser la casse des phrases<br /><br /> **Ne pas:**<br /><br /> -Gras, italique ou italique gras<br />-À utiliser pour le corps du texte<br />-À utiliser dans les contrôles Visual Studio standard<br />-À utiliser dans les fenêtres outil|**S’affiche sous la forme :** 12 pt Segoe UI<br /><br /> **Exemple visuel :**<br /><br /> ![Exemple de titre de police d'environnement 133 %](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202-d_EF133")|

#### <a name="122-environment-font"></a>police d’environnement 122%

|Utilisation|Apparence|
|-|-|
|**Utilisation :**<br /><br /> -En-têtes de section dans les boîtes de dialogue de signature<br />-Nœuds supérieurs en mode arborescence<br />-Navigation de tabulation verticale<br /><br /> **Procédez comme suit :** Utiliser la casse des phrases<br /><br /> **Ne pas:**<br /><br /> -Gras, italique ou italique gras<br />-À utiliser pour le corps du texte<br />-À utiliser dans les contrôles Visual Studio standard<br />-À utiliser dans les fenêtres outil|**S’affiche sous la forme :** 11 PT Segoe UI<br /><br /> **Exemple visuel :**<br /><br /> ![Exemple de titre de police d'environnement 122 %](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202-e_EF122")|

#### <a name="environment-font--bold"></a>Police d’environnement + gras

|Utilisation|Apparence|
|-|-|
|**Utilisation :**<br /><br /> -Étiquettes et sous-titres dans les boîtes de dialogue de signature<br />-Étiquettes et sous-titres dans les rapports<br />-Étiquettes et sous-titres dans l’interface utilisateur du document<br /><br /> **Ne**<br /><br /> -Utiliser la casse en majuscules<br />-Utiliser le poids gras<br /><br /> **Ne pas:**<br /><br /> -Italique ou italique gras<br />-À utiliser pour le corps du texte<br />-À utiliser dans les contrôles Visual Studio standard<br />-À utiliser dans les fenêtres outil|**S’affiche sous la forme :** 9 PT en gras Segoe UI<br /><br /> **Exemple visuel :**<br /><br /> ![Exemple de police d’environnement &#43; en-tête en gras](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202-f_EFB")|

#### <a name="environment-font"></a>Police d’environnement

|Utilisation|Apparence|
|-|-|
|**Utilisation :** Tout le reste du texte<br /><br /> **Procédez comme suit :** Utiliser la casse des phrases<br /><br /> **Ne pas :** Italique ou italique gras|**S’affiche sous la forme :** 9 PT Segoe UI<br /><br /> **Exemple visuel :**<br /><br /> ![Exemple de police d'environnement](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202-g_EF")|

### <a name="padding-and-spacing"></a>Remplissage et espacement
 Les en-têtes nécessitent de l’espace pour leur apporter l’accent approprié. Cet espace varie en fonction de la taille du point et de ce qui se trouve à proximité de l’en-tête, par exemple une règle horizontale ou une ligne de texte dans la police de l’environnement.

- Le remplissage idéal pour un en-tête en lui-même doit être de 90% de l’espace de hauteur de caractère majuscule. Par exemple, une en-tête 28 PT Segoe UI clair a une hauteur de l’extrémité de 26 PT, et la marge intérieure doit être d’environ 23 PT, ou environ 31 pixels.

- L’espace minimal autour d’une en-tête doit être de 50% de la hauteur du caractère majuscule. Moins d’espace peut être utilisé lorsqu’un en-tête est accompagné d’une règle ou d’un autre élément d’ajustement étroit.

- Le texte de police d’environnement en gras doit suivre l’espacement et le remplissage de la hauteur de ligne par défaut.

## <a name="see-also"></a>Voir aussi

- [Polices (Windows)](/windows/desktop/uxguide/vis-fonts)
- [Texte de l’interface utilisateur (Windows)](/windows/desktop/uxguide/text-ui)
