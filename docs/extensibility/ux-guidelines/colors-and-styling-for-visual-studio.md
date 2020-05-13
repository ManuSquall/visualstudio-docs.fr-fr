---
title: Couleurs et style pour Visual Studio (fr) Microsoft Docs
ms.date: 07/31/2017
ms.topic: conceptual
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2c7d8a02de9331f268cd06ad35e19faab6494fe0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699854"
---
# <a name="colors-and-styling-for-visual-studio"></a>Couleurs et styles pour Visual Studio

## <a name="use-color-in-visual-studio"></a>Utiliser la couleur dans Visual Studio

Dans Visual Studio, la couleur est principalement utilisée comme un outil de communication, pas seulement comme décoration. Utilisez la couleur au minimum et réservez-la pour les situations où vous voulez :

- Communiquer le sens ou l’affiliation (par exemple, plateforme ou modificateurs linguistiques)

- Attirer l’attention (par exemple, indiquer un changement de statut)

- Améliorer la lisibilité et fournir des repères pour la navigation de l’interface utilisateur

- Augmenter l’opportunité

Plusieurs options existent pour attribuer des couleurs aux éléments d’interface utilisateur dans Visual Studio. Parfois, il peut être difficile de comprendre quelle option vous êtes censé utiliser, ou comment l’utiliser correctement. Ce sujet vous aidera :

- Comprendre les différents services et systèmes utilisés pour définir les couleurs dans Visual Studio.

- Sélectionnez la bonne option pour un élément donné.

- Utilisez correctement l’option que vous avez choisie.

> [!NOTE]
> Jamais de couleur hex, RGB ou système hardcode à vos éléments d’interface utilisateur. L’utilisation des services permet une flexibilité dans l’accordage de la teinte. En outre, sans le service, vous ne serez pas en mesure de profiter des capacités de changement de thème [du service VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Méthodes d’attribution de la couleur aux éléments d’interface Visual Studio

Choisissez la méthode la mieux adaptée à vos éléments d’interface utilisateur.

| Votre interface utilisateur | Méthode | Qu’est-ce que c’est ? |
| --- | --- | --- |
| Vous avez des boîtes de dialogue intégrées ou autonomes. | **Couleurs du système** | Noms système qui permettent au système d’exploitation de définir la couleur et l’apparence des éléments d’interface utilisateur, comme les contrôles de dialogue communs. |
| Vous avez l’interface utilisateur personnalisée que vous voulez être compatible avec l’environnement VS global et vous avez des éléments d’interface utilisateur qui correspondent à la catégorie et la signification sémantique des jetons partagés. | **Couleurs communes partagées** | Noms de jetons de couleur prédéfinis existants pour des éléments spécifiques de l’interface utilisateur |
| Vous avez une fonctionnalité individuelle ou un groupe de fonctionnalités et il n’y a pas de couleur partagée pour des éléments similaires. | **Couleurs personnalisées** | Noms de jetons de couleur qui sont spécifiques à une zone et non destinés à être partagés avec d’autres interfaces utilisateur |
| Vous souhaitez permettre à l’utilisateur final de personnaliser l’interface utilisateur ou le contenu (par exemple, pour les éditeurs de texte ou les fenêtres spécialisées de concepteur). | **Personnalisation de l’utilisateur final**<br /><br />**(Outils &gt; Options dialogue)** | Paramètres définis dans la page "Fonts and Colors" du dialogue **Tools &gt; Options** ou une page spécialisée spécifique à une fonction d’interface utilisateur. |

### <a name="visual-studio-themes"></a>Thèmes Visual Studio

Visual Studio présente trois thèmes de couleurs différents : la lumière, l’obscurité et le bleu. Il détecte également le mode High Contrast, qui est un thème couleur à l’échelle du système conçu pour l’accessibilité.

Les utilisateurs sont invités à choisir un thème lors de leur première utilisation de Visual Studio et sont en mesure de changer de thèmes plus tard en allant à **Tools &gt; Options &gt; Environnement &gt; Général** et en choisissant un nouveau thème à partir du menu "thème couleur" drop-down.

Les utilisateurs peuvent également utiliser Le panneau de contrôle pour transformer l’ensemble de leurs systèmes en l’un des nombreux thèmes De contraste élevé. Si un utilisateur sélectionne un thème High Contrast, le sélectionneur de thème de couleur Visual Studio n’affecte plus les couleurs dans Visual Studio, bien que tous les changements de thème soient enregistrés pour quand l’utilisateur quitte le mode contraste élevé. Pour plus d’informations sur le mode High Contrast, voir [Choisir les couleurs de contraste élevé](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).

### <a name="the-vscolor-service"></a>Le service VSColor

Visual Studio fournit un service de couleur de l’environnement, connu sous le nom de service VSColor, qui vous permet de lier les valeurs de couleur de vos éléments d’interface utilisateur à une entrée nommée contenant des valeurs de couleur pour chaque thème Visual Studio. Cela garantit que vos couleurs changeront automatiquement pour refléter le thème ou le mode High Contrast sélectionné par l’utilisateur actuel. L’utilisation du service signifie que la mise en œuvre de tous les changements de couleur liés au thème est gérée en un seul endroit, et si vous utilisez les couleurs communes partagées du service, votre interface utilisateur reflétera automatiquement de nouveaux thèmes dans les futures versions de Visual Studio.

### <a name="implementation"></a>Implémentation

Le code source Visual Studio comprend plusieurs fichiers de définition de paquet qui contiennent des listes de noms de jetons et les valeurs de couleur respectives pour chaque thème. Le service de couleur lit les VSColors définis dans ces fichiers de définition de paquet. Ces couleurs sont référencées dans le balisage XAML ou dans le code, puis chargées par la `IVsUIShell5.GetThemedColor` méthode ou une cartographie DynamicResource.

### <a name="system-colors"></a>Couleurs du système

Les contrôles courants font référence aux couleurs du système par défaut. Si vous voulez que votre interface utilisateur utilise les couleurs du système, comme lorsque vous créez un dialogue intégré ou autonome, vous n’avez pas besoin de faire quoi que ce soit.

### <a name="common-shared-colors-in-the-vscolor-service"></a>Couleurs communes partagées dans le service VSColor

Vos éléments d’interface doivent refléter l’environnement global visual Studio. En réutilisant les couleurs communes partagées qui conviennent au composant d’interface utilisateur que vous concevez, vous vous assurez que votre interface est compatible avec d’autres interfaces Visual Studio, et que vos couleurs se mettront à jour automatiquement lorsque des thèmes sont ajoutés ou mis à jour.

Avant d’utiliser les couleurs communes partagées, assurez-vous que vous comprenez comment les utiliser correctement. L’utilisation incorrecte des couleurs communes partagées peut entraîner une expérience incohérente, frustrante ou déroutante pour vos utilisateurs.

### <a name="user-customizable-colors"></a>Couleurs personnalisables par l’utilisateur

Voir : [Exposer les couleurs pour les utilisateurs finaux](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

Parfois, vous voudrez permettre à l’utilisateur final de personnaliser votre interface utilisateur, comme lorsque vous créez un éditeur de code ou une surface de conception. Des composants d’interface utilisateur personnalisables se trouvent dans la section **Fonts et Couleurs** du dialogue ** &gt; Tools Options,** où les utilisateurs peuvent choisir de changer la couleur du premier plan, la couleur de fond, ou les deux.

![Outils &gt; Options dialogue](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")<br />Outils &gt; Options dialogue

## <a name="the-vscolor-service"></a><a name="BKMK_TheVSColorService"></a>Le service VSColor

Visual Studio fournit un service de couleur de l’environnement, également appelé le service VSColor ou le service de couleur shell. Ce service vous permet de lier les valeurs de couleur de vos éléments d’interface utilisateur à un ensemble de couleurs de valeur nominale contenant des couleurs pour chaque thème. Le service VSColor doit être utilisé pour tous les éléments d’interface utilisateur, de sorte que les couleurs changent automatiquement pour refléter le thème actuel sélectionné par l’utilisateur, et de sorte que l’interface utilisateur lié au service de couleur de l’environnement s’intégrera avec de nouveaux thèmes dans les futures versions de Visual Studio.

### <a name="how-the-service-works"></a>Fonctionnement du service

Le service de couleur de l’environnement lit VSColors définis dans le .pkgdef pour le composant d’interface utilisateur. Ces VSColors sont ensuite référencés dans le balisage `IVsUIShell5.GetThemedColor` ou `DynamicResource` le code XAML et sont chargés par le ou une cartographie.

![Architecture de service de couleur d'environnement](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")<br />Architecture de service de couleur d'environnement

### <a name="accessing-the-service"></a>Accès au service

Il existe plusieurs façons d’accéder au service VSColor, en fonction du type de jetons de couleur que vous utilisez et du type de code que vous avez.

#### <a name="predefined-environment-colors"></a>Couleurs prédéfinises de l’environnement

##### <a name="from-native-code"></a>Du code natif

La coque fournit un service `COLORREF` qui donne accès aux couleurs. Le service/interface est :

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

Dans le fichier VSShell80.idl, `__VSSYSCOLOREX` l’énumération a des constantes de couleur de coquille. Pour l’utiliser, passez comme la valeur de l’index soit l’une des valeurs de la `enum __VSSYSCOLOREX` `GetSysColor`documentée dans MSDN ou un numéro d’index régulier que le système Windows API, accepte. Faire cela récupère la valeur RGB de la couleur qui doit être utilisé dans le deuxième paramètre.

Si vous stockez un stylo ou `AdviseBroadcastMessages` un pinceau avec une nouvelle couleur, `WM_THEMECHANGED` vous devez (hors de la coque Visual Studio) et écouter et les `WM_SYSCOLORCHANGE` messages.

Pour accéder au service de couleur dans le code natif, vous ferez un appel qui ressemble à ceci:

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> [!NOTE]
> Les `COLORREF` valeurs `GetVSSysColorEx()` retournées par contiennent juste R,G,B composants d’une couleur de thème. Si une entrée de thème utilise la transparence, la valeur alpha-canal est jetée avant de revenir. Par conséquent, si la couleur de l’environnement d’intérêt doit être `IVsUIShell5.GetThemedColor` utilisé `IVsUIShell2::GetVSSysColorEx`dans un endroit où le canal de transparence est important, vous devriez utiliser au lieu de , comme décrit plus tard dans ce sujet.

##### <a name="from-managed-code"></a>Du code géré

L’accès au service VSColor par le code natif est assez simple. Toutefois, si vous travaillez sur le code géré, il peut être difficile de déterminer comment utiliser le service. Dans cet esprit, voici un extrait de code Cmd démontrant ce processus :

```csharp
private void VSColorPaint(object sender, System.Windows.Forms.PaintEventArgs e)
{
    //getIVSUIShell2
    IVsUIShell2 uiShell2 = Package.GetService(typeof(SVsUIShell)) as IVsUIShell2;
    Debug.Assert (uiShell2 != null, "failed to get IVsUIShell2");

    if (uiShell2 != null)
    {
        //get the COLORREF structure
        uint win32Color;
        uiShell2.GetVSSysColorEx((int)__VSSYSCOLOREX.VSCOLOR_SMARTTAG_HOVER_FILL, out win32Color);

        //translate it to a managed Color structure
        Color myColor = ColorTranslator.FromWin32((int)win32Color);
        //use it
        e.Graphics.FillRectangle(new SolidBrush(myColor), 0, 0, 100, 100);
    }
}
```

Si vous travaillez dans Visual Basic, utilisez :

```vb
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)
```

##### <a name="from-wpf-ui"></a>De WPF UI

Vous pouvez vous lier aux couleurs Visual `ResourceDictionary`Studio grâce à des valeurs exportées dans l’application. Voici un exemple d’utilisation des ressources de la table couleur ainsi que la liaison aux données de police de l’environnement dans XAML.

```xml
<Style TargetType="{x:Type Button}">
    <Setter Property="TextBlock.FontFamily"
            Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
    <Setter Property="TextBlock.FontSize"
            Value="{DynamicResource VsFont.EnvironmentFontSize}" />
    <Setter Property="Background"
            Value="{DynamicResource VsBrush.EnvironmentBackgroundGradient}" />
</Style>
```

#### <a name="helper-classes-and-methods-for-managed-code"></a>Classes d’aide et méthodes pour le code géré

Pour le code géré, la bibliothèque`Microsoft.VisualStudio.Shell.12.0.dll`de cadre de paquet géré de la coquille ( ) contient quelques classes d’aide facilitant l’utilisation de couleurs thématiques.

Les méthodes d’aide dans `Microsoft.VisualStudio.Shell.VsColors` la `GetThemedGDIColor()` `GetThemedWPFColor()`classe dans MPF comprennent et . Ces méthodes d’aide retournent la `System.Drawing.Color` valeur `System.Windows.Media.Color`de couleur d’une entrée de thème comme ou, pour être utilisé dans WinForms ou WPF UI.

```csharp
IVsUIShell5 shell5;
Button button = new Button();
button.BackColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemBrushKey);
button.ForeColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemTextBrushKey);

/// <summary>
/// Gets a System.Drawing.Color value from the current theme for the given color key.
/// </summary>
/// <param name="vsUIShell">The IVsUIShell5 service, used to get the color's value.</param>
/// <param name="themeResourceKey">The key to find the color for.</param>
/// <returns>The current theme's value of the named color.</returns>
public static System.Drawing.Color GetThemedGDIColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Validate.IsNotNull(vsUIShell, "vsUIShell");
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");

   byte[] colorComponents = GetThemedColorRgba(vsUIShell, themeResourceKey);

   // Note: The Win32 color we get back from IVsUIShell5.GetThemedColor is ABGR
   return System.Drawing.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);
}

private static byte[] GetThemedColorRgba(IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Guid category = themeResourceKey.Category;
   __THEMEDCOLORTYPE colorType = __THEMEDCOLORTYPE.TCT_Foreground
   if (themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundColor || themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundBrush)
   {
      colorType = __THEMEDCOLORTYPE.TCT_Background;
   }

   // This call will throw an exception if the color is not found
   uint rgbaColor = vsUIShell.GetThemedColor(ref category, themeResourceKey.Name, (uint)colorType);
   return BitConverter.GetBytes(rgbaColor);
}
public static System.Windows.Media.Color GetThemedWPFColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Validate.IsNotNull(vsUIShell, "vsUIShell");
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");

   byte[] colorComponents = GetThemedColorComponents(vsUIShell, themeResourceKey);

    return System.Windows.Media.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);
}
```

La classe peut également être utilisée pour obtenir des identifiants VSCOLOR pour une clé de ressources couleur WPF donnée, ou vice versa.

```csharp
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

Les méthodes `VsColors` de la classe requêtent le service VSColor pour retourner la valeur de couleur chaque fois qu’ils sont invoqués. Pour obtenir une `System.Drawing.Color`valeur de couleur comme , une alternative `Microsoft.VisualStudio.PlatformUI.VSThemeColor` avec de meilleures performances est d’utiliser à la place les méthodes de la classe, qui cache les valeurs de couleur obtenues à partir du service VSColor. La classe s’abonner en interne aux événements de messages de diffusion de coquille, et rejette la valeur mise en cache quand un événement changeant de thème se produit. En outre, la classe fournit un . ÉVÉNEMENT NET-friendly pour s’abonner aux changements de thème. Utilisez `ThemeChanged` l’événement pour ajouter un `GetThemedColor()` nouveau gestionnaire, et `ThemeResourceKeys` utilisez la méthode pour obtenir des valeurs de couleur pour l’intérêt. Un code d’échantillon pourrait ressembler à ceci :

```csharp
public MyWindowPanel()
{
    InitializeComponent();

    // Subscribe to theme changes events so we can refresh the colors
    VSColorTheme.ThemeChanged += VSColorTheme_ThemeChanged;

    RefreshColors();
}

private void VSColorTheme_ThemeChanged(ThemeChangedEventArgs e)
{
    RefreshColors();

    // Also post a message to all the children so they can apply the current theme appropriately
    foreach (System.Windows.Forms.Control child in this.Controls)
    {
        NativeMethods.SendMessage(child.Handle, e.Message, IntPtr.Zero, IntPtr.Zero);
    }
}

private void RefreshColors()
{
    this.BackColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowBackgroundColorKey);
    this.ForeColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowTextColorKey);
}

protected override void Dispose(bool disposing)
{
    if (disposing)
    {
        VSColorTheme.ThemeChanged -= this.VSColorTheme_ThemeChanged;
        base.Dispose(disposing);}
}
```

## <a name="choosing-high-contrast-colors"></a><a name="BKMK_ChoosingHighContrastColors"></a>Choisir des couleurs High Contrast

### <a name="overview"></a>Vue d'ensemble

Windows utilise plusieurs thèmes à haut contraste au niveau du système qui augmentent le contraste de couleur du texte, des arrière-plans et des images, ce qui rend les éléments semblent plus distincts sur l’écran. Pour des raisons d’accessibilité, il est important que les éléments de l’interface Visual Studio répondent correctement lorsque les utilisateurs passent à un thème High Contrast.

Seule une poignée de couleurs système peut être utilisée pour les thèmes De contraste élevé. Lorsque vous choisissez les noms de couleur de votre système, n’oubliez pas les conseils suivants :

- **Choisissez des couleurs système qui ont la même signification sémantique** que l’élément que vous colorez. Par exemple, si vous choisissez une couleur à contraste élevé pour le texte dans une fenêtre, utilisez WindowText et non ControlText.

- **Choisissez des paires de premier plan/ arrière-plan** ensemble ou vous ne serez pas sûr que votre choix de couleur fonctionnera dans tous les thèmes de contraste élevé.

- **Déterminez quelles parties de votre interface utilisateur sont les plus importantes et assurez-vous que les zones de contenu se démarqueront.** Vous perdrez beaucoup de détails que les différences subtiles dans la teinte de couleur distinguerait normalement, ainsi l’utilisation des couleurs de frontière fortes est commune pour définir des secteurs de contenu, parce qu’il n’y a aucune variante de couleur pour différentes zones de contenu.

### <a name="system-color-set"></a>Ensemble de couleur de système

La table du [blog de l’équipe WPF : SystemColors Reference](https://blogs.msdn.microsoft.com/wpf/2010/11/30/systemcolors-reference/) indique l’ensemble complet des noms de couleur du système et les teintes correspondantes affichées dans chaque thème.

Lors de l’application de cet ensemble limité de couleurs à votre interface utilisateur, *il est prévu que vous perdrez des détails subtils qui étaient présents dans les thèmes «normaux».* Voici un exemple d’interface utilisateur avec des couleurs grises subtiles qui sont utilisés pour distinguer les zones dans une fenêtre d’outil. Lorsqu’il est jumelé avec la même fenêtre affichée en mode Contraste élevé, vous pouvez voir que tous les arrière-plans sont de la même teinte et les frontières de ces zones sont indiquées par la frontière seule:

![Exemple de la façon dont les détails subtils sont perdus dans High Contrast](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303-a_PropertiesWindow")<br />Exemple de la façon dont les détails subtils sont perdus dans High Contrast

#### <a name="choosing-text-colors-in-an-editor"></a>Choisir des couleurs de texte dans un éditeur

Le texte colorisé est utilisé dans un éditeur ou sur une surface de conception pour indiquer le sens, comme permettant l’identification facile des groupes d’éléments similaires. Dans un thème De contraste élevé, cependant, vous n’avez pas la capacité de différencier entre plus de trois couleurs de texte. WindowText, GrayText et HotTrackText sont les seules couleurs disponibles sur les surfaces De WindowBackground. Puisque vous ne pouvez pas utiliser plus de trois couleurs, choisissez soigneusement les différences les plus importantes que vous souhaitez afficher en mode contraste élevé.

Teintes pour chacun des noms symboliques autorisés sur une surface d’éditeur, comme ils apparaissent dans chaque thème High Contrast:

![Comparaison de l'éditeur de contraste élevé](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303-b_HCEditorComparison")<br />Comparaison de l'éditeur de contraste élevé

Exemples de la surface de l’éditeur dans le thème bleu :

![Éditeur dans le thème bleu](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303-c_EditorBlue")<br />Éditeur dans le thème bleu

![Rédacteur en chef dans High Contrast #1 thème](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303-d_EditorHC1")<br />Rédacteur en chef dans High Contrast #1 thème

### <a name="usage-patterns"></a>Modèles d’usage

Beaucoup d’éléments d’interface utilisateur communs ont déjà des couleurs de contraste élevé définies. Vous pouvez faire référence à ces modèles d’utilisation lors du choix de vos propres noms de couleur du système, de sorte que vos éléments d’interface utilisateur sont compatibles avec des composants similaires.

| Couleur du système | Usage |
| --- | --- |
| LégendeActive | - IDE actif et glyphes de bouton de fenêtre rafted sur le plan stationnaire et appuyez<br />- Fond de barre de titre pour IDE et fenêtres rafted<br />- Fond de barre d’état par défaut |
| TexteLégendeActive | - IDE actif et fenêtres en radeau pour le premier plan de barre de titre (texte et glyphes)<br />- Contexte et bordure des boutons de fenêtre actifs sur le vol stationnaire et appuyez sur |
| Control | - Boîte combo, liste d’abandon, et contrôle de recherche par défaut et arrière-plan désactivé, y compris le bouton de baisse<br />- Dock fond de bouton cible<br />- Fond de barre de commande<br />- Fond de fenêtre d’outil |
| ControlDark | - Fond IDE<br />- Menu et séparateurs de barres de commande<br />- Bordure de barre de commandement<br />- Ombres de menu<br />- Défaut de l’onglet de fenêtre d’outil et bordure et séparateur de planer<br />- Documentez bien le fond du bouton de débordement<br />- Frontière de glyphe cible de quai |
| ContrôleFoncéFoncé |- Fenêtre d’onglet de document non ciblée et sélectionnée |
| ContrôleClair |- Bordure d’onglet de cache automatique<br />- Boîte combo et bordure de liste d’abandon<br />- Dock cible arrière-plan et la frontière |
| ControlLightLight | - Frontière provisoire sélectionnée et ciblée |
| ContrôleTexte | - Boîte combo et glyph liste d’abandon<br />- Texte d’onglet non sélectionné de fenêtre d’outil |
| GrayText (en) |- Boîte combo et liste déroulante bordure désactivée, glyph de chute, texte, et texte d’élément de menu<br />- Texte du menu désactivé<br />- Contrôle de recherche 'options de recherche' texte d’en-tête<br />- Séparateur de section de contrôle de recherche |
| Surligner | - Tous les arrière-plans et les bordures planés et pressés, à l’exception de l’arrière-plan du bouton de décrochage de la boîte combo et documentent la bordure du bouton de débordement de puits<br />- Contextes d’objets sélectionnés |
| HighlightText | - Tous les plans stationnaires et pressés au premier plan (texte et glyphes)<br />- Fenêtre d’outil ciblée et contrôle de fenêtre d’onglet de document au premier plan<br />- Bordure ciblée de barre de titre de fenêtre d’outil<br />- Au premier plan de l’onglet provisoire ciblé et sélectionné<br />- Documentez bien la bordure de bouton de débordement sur le vol stationnaire et appuyez<br />- Bordure d’icône sélectionnée|
| HotTrack (en) | - Faire défiler le fond du pouce de barre et la bordure sur la presse<br />- Faire défiler le glyph de flèche de barre sur la presse |
| InactiveCaption | - IDE inactif et glyphes bouton de fenêtre rafted sur le plan stationnaire<br />- Fond de barre de titre pour IDE et fenêtres rafted<br />- Contexte de contrôle de recherche désactivé |
| InactiveCaptionText | - Inactive IDE et fenêtres en radeau barre de titre au premier plan (texte et glyphes)<br />- Fond et bordure de boutons de fenêtre inactifs sur le plan stationnaire<br />- Fond et bordure de bouton de fenêtre d’outil non focalisé<br />- Contrôle de recherche désactivé au premier plan |
| Menu | - Fond de menu de dépôt<br />- Contexte de la marque de contrôle vérifiée et désactivé |
| MenuTexte | - Bordure du menu de dépôt<br />- Vérifier les marques<br />- Glyphs de menu<br />- Texte du menu de dépôt<br />- Bordure d’icône sélectionnée |
| Scrollbar | - Faire défiler la barre et défiler le fond de flèche de barre, tous les états |
| Fenêtre | - Fond d’onglet de cache automatique<br />- Barre de menu et fond d’étagère de commande<br />- Fond d’onglet de fenêtre de document non focalisé ou non sélectionné et bordure de document, pour les onglets ouverts et provisoires<br />- Fond de barre de titre de fenêtre d’outil non focalisé<br />- Fond d’onglet de fenêtre d’outil, sélectionné et non sélectionné |
| WindowFrame (en) | - Frontière IDE |
| WindowText (en) | - Au premier plan de l’onglet Auto-cacher<br />- Ame de fenêtre d’outil sélectionné<br />- Onglet de fenêtre de document non focalisé et avant-plan provisoire non focalisé ou non sélectionné<br />- Vue d’arbre avant-plan par défaut et planer au-dessus du glyph non sélectionné<br />- Fenêtre d’outil sélectionnée bordure d’onglet<br />- Faire défiler le fond du pouce de barre, la bordure et le glyphe |

## <a name="exposing-colors-for-end-users"></a><a name="BKMK_ExposingColorsForEndUsers"></a>Exposer les couleurs pour les utilisateurs finaux

### <a name="overview"></a>Vue d'ensemble

Parfois, vous souhaitez permettre à l’utilisateur final de personnaliser votre interface utilisateur, comme lorsque vous créez un éditeur de code ou une surface de conception. La façon la plus courante de le faire est d’utiliser le dialogue ** &gt; Tools Options.** Sauf si vous avez une interface utilisateur hautement spécialisée qui nécessite des contrôles spéciaux, la façon la plus simple de présenter la personnalisation est à travers la page **Fonts et Couleurs** dans la section **Environnement** du dialogue. Pour chaque élément que vous exposez pour la personnalisation, l’utilisateur peut choisir de changer la couleur du premier plan, la couleur de fond, ou les deux.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Construire un VSPackage pour vos couleurs personnalisables

Un VSPackage peut contrôler les polices et les couleurs à travers des catégories personnalisées et afficher des éléments sur la page de propriété Fonts and Colors. Lors de l’utilisation de ce mécanisme, VSPackages doit implémenter [l’interface IVsFontAndColorDefaultsProvider](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider) et ses interfaces associées.

En principe, ce mécanisme peut être utilisé pour modifier tous les éléments d’affichage existants et les catégories qui les contiennent. Toutefois, il ne doit pas être utilisé pour modifier la catégorie De l’éditeur de texte ou ses éléments d’affichage. Pour plus d’informations sur la catégorie Éditeur de Texte, voir [Font et Color Overview](/visualstudio/extensibility/font-and-color-overview?view=vs-2015).

Pour implémenter des catégories personnalisées ou afficher des éléments, un VSPackage doit :

- **Créer ou identifier des catégories dans le registre.** La mise en œuvre de la page de propriété **Fonts and Colors** par l’IDE utilise ces informations pour interroger correctement le service à l’appui d’une catégorie donnée.

- **Créer ou identifier des groupes dans le registre (facultatif).** Il pourrait être utile de définir un groupe, qui représente l’union de deux catégories ou plus. Si un groupe est défini, l’IDE fusionne automatiquement les sous-catégories et distribue des éléments d’affichage au sein du groupe.

- **Implémentez le support IDE.**

- **Poignée de police et de changements de couleur.**

#### <a name="to-create-or-identify-categories"></a>Créer ou identifier des catégories

Construire un type spécial d’inscription au registre de catégories sous `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` l’endroit où `<Category>` se trouve le nom non localisé de la catégorie.

Remplissez le registre avec deux valeurs :

| Nom | Type | Données | Description |
| --- | --- | --- | --- |
| Category | REG_SZ | GUID | Un GUID créé pour identifier la catégorie |
| Package | REG_SZ | GUID | Le GUID du service VSPackage qui prend en charge la catégorie |

 Le service spécifié dans le registre doit fournir une mise en œuvre de [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) pour la catégorie correspondante.

#### <a name="to-create-or-identify-groups"></a>Créer ou identifier des groupes

Construire un type spécial d’inscription au registre de catégories sous `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` l’endroit où `<group>` se trouve le nom non localisé du groupe.

Remplissez le registre avec deux valeurs :

| Nom | Type | Données | Description |
|--- | --- | --- | --- |
| Category | REG_SZ | GUID | Un GUID créé pour identifier la catégorie |
| Package | REG_SZ | GUID | Le GUID du service VSPackage qui prend en charge la catégorie |

Le service spécifié dans le registre <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> doit fournir une mise en œuvre pour le groupe correspondant.

![Mise en œuvre de IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304-a_FontAndColorGroup")<br />Implémentation de `IVsFontAndColorGroup`

### <a name="to-implement-ide-support"></a>Mettre en œuvre le support IDE

Implémentez [GetObject](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject), qui renvoie soit une interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> [IVsFontAndColorDefaults,](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) soit une interface à l’IDE pour chaque catégorie ou groupe GUID fourni.

Pour chaque catégorie qu’il prend en charge, un VSPackage met en œuvre une instance distincte de l’interface [IVsFontAndColorDefaults.](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults)

Les méthodes mises en œuvre par [iVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) doivent fournir à l’IDE :

- Listes d’éléments d’affichage dans la catégorie

- Noms localisables pour les articles d’affichage

- Afficher les informations pour chaque membre de la catégorie

> [!NOTE]
> Chaque catégorie doit contenir au moins un élément d’affichage.

L’IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> utilise l’interface pour définir une union de plusieurs catégories.

Sa mise en œuvre fournit à l’IDE :

- Une liste des catégories qui composent un groupe donné

- Accès aux instances [d’IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) soutenant chaque catégorie au sein du groupe

- Noms de groupe localisables

#### <a name="updating-the-ide"></a>Mise à jour de l’IDE

L’IDE cache des informations sur les paramètres Font et Couleur. Par conséquent, après toute modification de la configuration IDE Font et Color, s’assurer que le cache est à jour est une pratique exemplaire.

La mise à jour du cache se fait par l’intermédiaire de l’interface [IvsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) et peut être effectuée globalement ou simplement sur certains éléments.

### <a name="handling-font-and-color-changes"></a>Manipulation des polices et des changements de couleur

Pour soutenir correctement la colorisation du texte qu’un VSPackage affiche, le service de colorisation supportant le VSPackage doit répondre aux modifications initiées par l’utilisateur effectuées par le biais de la page des propriétés Fonts et Couleurs.

Pour ce faire, un VSPackage doit :

- **gérer les événements générés par l’IDE** en implémentant l’interface [IVsFontAndColorEvents.](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents) L’IDE appelle la méthode appropriée suite aux modifications de l’utilisateur de la page Fonts et Couleurs. Par exemple, il appelle la méthode [OnFontChanged](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged) si une nouvelle police est sélectionnée.

  **Ou**

- **sondage de l’IDE pour les changements**. Cela peut se faire grâce à l’interface [IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) mise en œuvre par le système. Bien que principalement pour le soutien de la persistance, la méthode [GetItem](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem) peut obtenir des informations de police et de couleur pour les éléments d’affichage. Pour plus d’informations sur les paramètres de police et de couleur, consultez l’article MSDN [Accessing Stored Font et Color Settings](/visualstudio/extensibility/accessing-stored-font-and-color-settings?view=vs-2015).

> [!NOTE]
> Pour vous assurer que les résultats des sondages sont corrects, utilisez [l’interface IVsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) pour déterminer si une couleur de cache et une mise à jour sont nécessaires avant d’appeler les méthodes de récupération de [l’interface IVsFontAndColorStorage.](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage)

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Enregistrement des polices personnalisées et de la catégorie de couleur sans implémenter les interfaces

L’exemple de code suivant montre comment enregistrer la police personnalisée et la catégorie de couleur sans implémenter les interfaces :

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

Pour cet exemple de code :

- `"NameID"`l’ID de ressource du nom de la catégorie localisée dans votre forfait
- `"ToolWindowPackage"`Paquet GUID
- `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"`n’est qu’un exemple et la valeur réelle peut être un nouveau GUID fourni par l’implémentateur.

### <a name="set-the-font-and-color-property-category-guid"></a>Définir la catégorie de propriété Font et Couleur GUID

L’exemple de code ci-dessous montre les GUIDs de catégorie de réglage.

```csharp
// m_pView is your IVsTextView
IVsTextEditorPropertyCategoryContainer spPropCatContainer =
(IVsTextEditorPropertyCategoryContainer)m_pView;
if (spPropCatContainer != null)
{
IVsTextEditorPropertyContainer spPropContainer;
Guid GUID_EditPropCategory_View_MasterSettings =
new Guid("{D1756E7C-B7FD-49a8-B48E-87B14A55655A}");
hr = spPropCatContainer.GetPropertyCategory(
ref GUID_EditPropCategory_View_MasterSettings,
out spPropContainer);
if(hr == 0)
{
hr =
spPropContainer.SetProperty(
VSEDITPROPID.VSEDITPROPID_ViewGeneral_FontCategory,
catGUID);
hr =
spPropContainer.SetProperty(
VSEDITPROPID.VSEDITPROPID_ViewGeneral_ColorCategory,
catGUID);
}
}
```
