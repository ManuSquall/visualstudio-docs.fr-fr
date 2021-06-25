---
title: Couleurs et styles pour Visual Studio | Microsoft Docs
description: Découvrez comment l’expérience utilisateur de Visual Studio utilise la couleur comme un outil de communication, plutôt que pour des raisons purement esthétiques.
ms.custom: SEO-VS-2020
ms.date: 07/31/2017
ms.topic: reference
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 307a4013c06258524c60619c6eff40e4d64740b6
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904485"
---
# <a name="colors-and-styling-for-visual-studio"></a>Couleurs et styles pour Visual Studio

## <a name="use-color-in-visual-studio"></a>Utiliser la couleur dans Visual Studio

Dans Visual Studio, la couleur est principalement utilisée comme un outil de communication, et pas simplement comme décoration. Utilisez la couleur au minimum et réservez-la dans les situations où vous souhaitez :

- Communiquer la signification ou l’affiliation (par exemple, modificateurs de plateforme ou de langage)

- Attirer l’attention (par exemple, en indiquant un changement d’État)

- Améliorez la lisibilité et fournissez des points de repère pour naviguer dans l’interface utilisateur

- Améliorez l’opportunité

Il existe plusieurs options pour assigner des couleurs aux éléments d’interface utilisateur dans Visual Studio. Parfois, il peut être difficile de déterminer l’option que vous êtes censé utiliser ou la manière de l’utiliser correctement. Cette rubrique vous aidera à :

- Comprenez les différents services et systèmes utilisés pour définir des couleurs dans Visual Studio.

- Sélectionnez l’option appropriée pour un élément donné.

- Utilisez correctement l’option que vous avez choisie.

> [!NOTE]
> Ne vous contentez pas de coder en dur les couleurs hexadécimales, RVB ou système pour vos éléments d’interface utilisateur. L’utilisation des services permet de bénéficier d’une certaine flexibilité dans le paramétrage de la teinte. En outre, sans le service, vous ne pourrez pas tirer parti des fonctionnalités de changement de thème du [service VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Méthodes pour assigner des couleurs aux éléments de l’interface Visual Studio

Choisissez la méthode la mieux adaptée à vos éléments d’interface utilisateur.

| Votre interface utilisateur | Méthode | Quelles sont-elles ? |
| --- | --- | --- |
| Vous avez des boîtes de dialogue incorporées ou autonomes. | **Couleurs système** | Les noms système qui permettent au système d’exploitation de définir la couleur et l’apparence des éléments d’interface utilisateur, comme les contrôles de boîte de dialogue courants. |
| Vous disposez d’une interface utilisateur personnalisée qui doit être cohérente avec l’environnement Visual Studio global et où vous avez des éléments d’interface utilisateur qui correspondent à la signification sémantique et de catégorie des jetons partagés. | **Couleurs partagées communes** | Noms de jeton de couleur prédéfinis existants pour des éléments d’interface utilisateur spécifiques |
| Vous disposez d’une fonctionnalité individuelle ou d’un groupe de fonctionnalités, et il n’existe pas de couleur partagée pour les éléments similaires. | **Couleurs personnalisées** | Les noms des jetons de couleur qui sont spécifiques à une zone et qui ne sont pas destinés à être partagés avec d’autres interfaces utilisateur |
| Vous souhaitez autoriser l’utilisateur final à personnaliser l’interface utilisateur ou le contenu (par exemple, pour les éditeurs de texte ou les fenêtres de concepteur spécialisées). | **Personnalisation par l’utilisateur final**<br /><br />**(Outils &gt; Boîte de dialogue Options)** | Paramètres définis dans la page « polices et couleurs » de la boîte de dialogue **&gt; Options des outils** ou une page spécialisée spécifique à une fonctionnalité de l’interface utilisateur. |

### <a name="visual-studio-themes"></a>Thèmes Visual Studio

Visual Studio propose trois thèmes de couleur différents : clair, foncé et bleu. Il détecte également le mode contraste élevé, qui est un thème de couleurs à l’ensemble du système conçu pour l’accessibilité.

Les utilisateurs sont invités à sélectionner un thème lors de leur première utilisation de Visual Studio et peuvent changer les thèmes ultérieurement en accédant à **outils &gt; options &gt; environnement &gt; général** et en choisissant un nouveau thème dans le menu déroulant « thème de couleur ».

Les utilisateurs peuvent également utiliser le panneau de configuration pour basculer l’ensemble de leurs systèmes dans l’un des nombreux contraste élevé thèmes. Si un utilisateur sélectionne un thème de contraste élevé, le sélecteur de thème de couleur Visual Studio n’affecte plus les couleurs dans Visual Studio, bien que toutes les modifications de thème soient enregistrées lorsque l’utilisateur quitte le mode contraste élevé. Pour plus d’informations sur le mode de contraste élevé, consultez [choix des couleurs de contraste élevé](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).

### <a name="the-vscolor-service"></a>Service VSColor

Visual Studio fournit un service de couleur d’environnement, connu sous le nom de service VSColor, qui vous permet de lier les valeurs de couleur de vos éléments d’interface utilisateur à une entrée nommée contenant des valeurs de couleur pour chaque thème Visual Studio. Cela permet de s’assurer que vos couleurs seront automatiquement modifiées pour refléter le mode de contraste élevé du thème ou du système actuellement sélectionné par l’utilisateur. L’utilisation du service signifie que l’implémentation de toutes les modifications de couleur liées au thème est gérée dans un même emplacement et que si vous utilisez des couleurs partagées communes du service, votre interface utilisateur reflète automatiquement les nouveaux thèmes dans les futures versions de Visual Studio.

### <a name="implementation"></a>Implémentation

Le code source Visual Studio comprend plusieurs fichiers de définition de package qui contiennent des listes de noms de jetons et les valeurs de couleur respectives pour chaque thème. Le service de couleur lit les VSColors définis dans ces fichiers de définition de package. Ces couleurs sont référencées dans le balisage XAML ou dans le code, puis chargées par le biais de la `IVsUIShell5.GetThemedColor` méthode ou d’un mappage DynamicResource.

### <a name="system-colors"></a>Couleurs système

Les contrôles communs font référence aux couleurs système par défaut. Si vous souhaitez que votre interface utilisateur utilise les couleurs système, comme lorsque vous créez une boîte de dialogue incorporée ou autonome, vous n’avez rien à faire.

### <a name="common-shared-colors-in-the-vscolor-service"></a>Couleurs partagées communes dans le service VSColor

Vos éléments d’interface doivent refléter l’environnement Visual Studio global. En réutilisant les couleurs partagées communes qui sont appropriées pour le composant d’interface utilisateur que vous concevez, vous vous assurez que votre interface est cohérente avec les autres interfaces Visual Studio et que vos couleurs seront mises à jour automatiquement lorsque des thèmes sont ajoutés ou mis à jour.

Avant d’utiliser les couleurs partagées courantes, assurez-vous que vous comprenez comment les utiliser correctement. Une utilisation incorrecte des couleurs partagées communes peut entraîner une expérience incohérente, frustrante ou confuse pour vos utilisateurs.

### <a name="user-customizable-colors"></a>Couleurs personnalisables par l’utilisateur

Voir : [exposition des couleurs pour les utilisateurs finaux](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

Parfois, vous pouvez autoriser l’utilisateur final à personnaliser votre interface utilisateur, comme lorsque vous créez un éditeur de code ou une aire de conception. Les composants d’interface utilisateur personnalisables se trouvent dans la section **polices et couleurs** de la boîte de dialogue **&gt; Options des outils** , où les utilisateurs peuvent choisir de modifier la couleur de premier plan, la couleur d’arrière-plan ou les deux.

![&gt;Boîte de dialogue Options des outils](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")<br />&gt;Boîte de dialogue Options des outils

## <a name="the-vscolor-service"></a><a name="BKMK_TheVSColorService"></a> Service VSColor

Visual Studio fournit un service de couleur d’environnement, également appelé service VSColor ou le service de couleurs de l’interpréteur de commandes. Ce service vous permet de lier les valeurs de couleur de vos éléments d’interface utilisateur à un jeu de couleurs de valeur de nom contenant des couleurs pour chaque thème. Le service VSColor doit être utilisé pour tous les éléments d’interface utilisateur, de sorte que les couleurs changent automatiquement pour refléter le thème sélectionné par l’utilisateur actuel, de sorte que l’interface utilisateur liée au service de couleur de l’environnement s’intègre aux nouveaux thèmes dans les futures versions de Visual Studio.

### <a name="how-the-service-works"></a>Fonctionnement du service

Le service de couleur de l’environnement lit les VSColors définis dans le fichier. pkgdef du composant d’interface utilisateur. Ces VSColors sont ensuite référencés dans le balisage ou le code XAML et sont chargés via le `IVsUIShell5.GetThemedColor` ou un `DynamicResource` mappage.

![Architecture de service de couleur d'environnement](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")<br />Architecture de service de couleur d'environnement

### <a name="accessing-the-service"></a>Accès au service

Il existe plusieurs façons d’accéder au service VSColor, selon le type de jetons de couleur que vous utilisez et le type de code que vous utilisez.

#### <a name="predefined-environment-colors"></a>Couleurs d’environnement prédéfinies

##### <a name="from-native-code"></a>À partir du code natif

L’interpréteur de commandes fournit un service qui donne accès à la `COLORREF` des couleurs. Le service/l’interface est :

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

Dans le fichier VSShell80. idl, l’énumération `__VSSYSCOLOREX` a des constantes de couleur de Shell. Pour l’utiliser, transmettez en tant que valeur d’index l’une des valeurs du `enum __VSSYSCOLOREX` document documenté dans MSDN ou un numéro d’index standard que l’API système Windows `GetSysColor` accepte. Cette action permet d’obtenir la valeur RVB de la couleur à utiliser dans le deuxième paramètre.

Si vous stockez un stylet ou un pinceau avec une nouvelle couleur, vous devez `AdviseBroadcastMessages` (à partir de l’interpréteur de commandes Visual Studio) et écouter les `WM_SYSCOLORCHANGE` `WM_THEMECHANGED` messages et.

Pour accéder au service de couleurs en code natif, vous allez effectuer un appel qui ressemble à ceci :

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> [!NOTE]
> Les `COLORREF` valeurs retournées par `GetVSSysColorEx()` contiennent uniquement les composants R, v, B d’une couleur de thème. Si une entrée de thème utilise la transparence, la valeur du canal alpha est ignorée avant de retourner. Par conséquent, si la couleur d’environnement d’intérêt doit être utilisée à un endroit où le canal de transparence est important, vous devez utiliser `IVsUIShell5.GetThemedColor` au lieu de `IVsUIShell2::GetVSSysColorEx` , comme décrit plus loin dans cette rubrique.

##### <a name="from-managed-code"></a>À partir du code managé

L’accès au service VSColor via du code natif est relativement simple. Toutefois, si vous utilisez du code managé, il peut être difficile de déterminer comment utiliser le service. À l’esprit, voici un extrait de code C# qui illustre ce processus :

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

Si vous travaillez dans Visual Basic, utilisez :

```vb
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)
```

##### <a name="from-wpf-ui"></a>À partir de l’interface utilisateur WPF

Vous pouvez lier les couleurs de Visual Studio à des valeurs exportées dans le de l’application `ResourceDictionary` . Vous trouverez ci-dessous un exemple d’utilisation de ressources à partir de la table des couleurs, ainsi que d’une liaison aux données de police de l’environnement en XAML.

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

#### <a name="helper-classes-and-methods-for-managed-code"></a>Classes et méthodes d’assistance pour le code managé

Pour le code managé, la bibliothèque de l’infrastructure de package managé () de l’interpréteur de `Microsoft.VisualStudio.Shell.12.0.dll` commandes contient deux classes d’assistance facilitant l’utilisation des couleurs à thème.

Les méthodes d’assistance de la `Microsoft.VisualStudio.Shell.VsColors` classe dans MPF incluent `GetThemedGDIColor()` et `GetThemedWPFColor()` . Ces méthodes d’assistance retournent la valeur de couleur d’une entrée de thème comme `System.Drawing.Color` ou `System.Windows.Media.Color` , à utiliser dans WinForms ou l’interface utilisateur WPF.

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

La classe peut également être utilisée pour obtenir des identificateurs VSCOLOR pour une clé de ressource de couleur WPF donnée, ou vice versa.

```csharp
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

Les méthodes de la `VsColors` classe interrogent le service VSColor pour retourner la valeur de couleur à chaque fois qu’elles sont appelées. Pour obtenir une valeur de couleur en tant que `System.Drawing.Color` , une alternative avec de meilleures performances consiste à utiliser à la place les méthodes de la `Microsoft.VisualStudio.PlatformUI.VSThemeColor` classe, qui met en cache les valeurs de couleur obtenues à partir du service VSColor. La classe s’abonne aux événements de messages de diffusion de Shell en interne et ignore la valeur mise en cache lorsqu’un événement de modification de thème se produit. En outre, la classe fournit un. Événement NET-friendly pour s’abonner aux modifications du thème. Utilisez l' `ThemeChanged` événement pour ajouter un nouveau gestionnaire et utilisez la `GetThemedColor()` méthode pour obtenir les valeurs `ThemeResourceKeys` de couleur du qui vous intéressent. Un exemple de code peut se présenter comme suit :

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

## <a name="choosing-high-contrast-colors"></a><a name="BKMK_ChoosingHighContrastColors"></a> Choix des couleurs de contraste élevé

### <a name="overview"></a>Vue d’ensemble

Windows utilise plusieurs thèmes de niveau système à contraste élevé qui augmentent le contraste des couleurs du texte, des arrière-plans et des images, ce qui rend les éléments plus distincts à l’écran. Pour des raisons d’accessibilité, il est important que les éléments de l’interface Visual Studio répondent correctement quand les utilisateurs basculent vers un thème de contraste élevé.

Seules quelques couleurs système peuvent être utilisées pour contraste élevé thèmes. Lorsque vous choisissez vos noms de couleurs système, gardez à l’esprit les conseils suivants :

- **Choisissez des couleurs système dont la signification sémantique est identique** à celle de l’élément que vous colorez. Par exemple, si vous choisissez une couleur de contraste élevé pour le texte dans une fenêtre, utilisez WindowText et non ControlText.

- **Choisissez les paires premier plan/arrière-plan** ou vous n’êtes pas certain que votre choix de couleurs fonctionnera dans tous les thèmes de contraste élevé.

- **Déterminez les parties de votre interface utilisateur qui sont les plus importantes et assurez-vous que les zones de contenu se présentent.** Vous perdrez beaucoup de détails, car les légères différences de teinte de couleur se distinguent normalement. l’utilisation de couleurs de bordure fortes est donc courante pour définir des zones de contenu, car il n’existe aucune variante de couleur pour les différentes zones de contenu.

### <a name="system-color-set"></a>Jeu de couleurs système

Le tableau sur le blog de l' [équipe WPF : la référence SystemColors](/archive/blogs/wpf/systemcolors-reference) indique l’ensemble complet des noms de couleurs système et les teintes correspondantes affichées dans chaque thème.

Lors de l’application de ce jeu limité de couleurs à votre interface utilisateur, *il est prévu que vous perdiez des détails subtils qui étaient présents dans les thèmes « normaux »*. Voici un exemple d’interface utilisateur avec des couleurs grises subtiles utilisées pour distinguer les zones dans une fenêtre outil. Lorsqu’ils sont associés à la même fenêtre affichée en mode contraste élevé, vous pouvez voir que tous les arrière-plans sont identiques et que les bordures de ces zones sont indiquées par la bordure seule :

![Exemple de la façon dont les détails subtils sont perdus dans contraste élevé](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303-a_PropertiesWindow")<br />Exemple de la façon dont les détails subtils sont perdus dans contraste élevé

#### <a name="choosing-text-colors-in-an-editor"></a>Choix des couleurs de texte dans un éditeur

Le texte en couleur est utilisé dans un éditeur ou sur une aire de conception pour indiquer la signification, par exemple pour permettre une identification simple des groupes d’éléments similaires. Toutefois, dans un thème contraste élevé, vous n’avez pas la possibilité de faire la différence entre plus de trois couleurs de texte. WindowText, GrayText et HotTrackText sont les seules couleurs disponibles sur les surfaces WindowBackground. Étant donné que vous ne pouvez pas utiliser plus de trois couleurs, choisissez avec précaution les différences les plus importantes que vous souhaitez afficher en mode contraste élevé.

Teintes pour chacun des noms de jeton autorisés sur une surface d’éditeur, tels qu’ils apparaissent dans chaque contraste élevé thème :

![Comparaison de l'éditeur de contraste élevé](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303-b_HCEditorComparison")<br />Comparaison de l'éditeur de contraste élevé

Exemples de la surface de l’éditeur dans le thème bleu :

![Éditeur dans le thème bleu](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303-c_EditorBlue")<br />Éditeur dans le thème bleu

![Éditeur dans contraste élevé thème #1](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303-d_EditorHC1")<br />Éditeur dans contraste élevé thème #1

### <a name="usage-patterns"></a>Modèles d’usage

De nombreux éléments d’interface utilisateur communs ont déjà des couleurs de contraste élevé définies. Vous pouvez référencer ces modèles d’utilisation lorsque vous choisissez vos propres noms de couleurs système, afin que vos éléments d’interface utilisateur soient cohérents avec des composants similaires.

| Couleur système | Utilisation |
| --- | --- |
| LégendeActive | -L’IDE actif et les glyphes de boutons de fenêtre volés au survol et à la pression<br />-Arrière-plan de la barre de titre pour les fenêtres de l’IDE et les fenêtres à Raft<br />-Arrière-plan de la barre d’État par défaut |
| TexteLégendeActive | -IDE actif et fenêtres avec des rafts pour le premier plan de la barre de titre (texte et glyphes)<br />-Arrière-plan et bordure des boutons de la fenêtre active au pointage et appuyez sur |
| Contrôler | -Zone de liste déroulante, liste déroulante et arrière-plan par défaut et désactivés du contrôle de recherche, y compris le bouton de liste déroulante<br />-Arrière-plan du bouton de cible d’ancrage<br />-Arrière-plan de barre de commandes<br />-Arrière-plan de fenêtre outil |
| ControlDark | -Arrière-plan IDE<br />-Menus et séparateurs de barre de commandes<br />-Bordure de barre de commandes<br />-Shadows de menu<br />-Onglet de fenêtre outil bordure et séparateur par défaut<br />-Arrière-plan du bouton de dépassement de capacité de document<br />: Bordure du glyphe cible de l’ancrage |
| ContrôleFoncéFoncé |-Inactif, fenêtre d’onglet de document sélectionnée |
| ContrôleClair |-Masquer automatiquement la bordure de l’onglet<br />-Zone de liste déroulante et bordure de liste déroulante<br />-Arrière-plan et bordure de la cible d’ancrage |
| ControlLightLight | -Bordure provisoire sélectionnée |
| ControlText | -Zone de liste déroulante et glyphe de liste déroulante<br />-Texte de l’onglet non sélectionné dans la fenêtre outil |
| GrayText |-Zone de liste déroulante et liste déroulante de bordure désactivée, glyphe de liste déroulante, texte et texte d’élément de menu<br />-Texte de menu désactivé<br />-Texte d’en-tête des options de recherche du contrôle de recherche<br />-Séparateur de section de contrôle de recherche |
| Surlignage | -Tous les arrière-plans et bordures avec pointage et enfoncé, à l’exception de la bordure du bouton de liste déroulante zone de liste déroulante<br />-Arrière-plan des éléments sélectionnés |
| HighlightText | -Tous les points de suspension et de pointage appuyés (texte et glyphes)<br />-Fenêtre outil ciblée et contrôle de fenêtre d’onglet de document premier plan<br />-Bordure de barre de titre de fenêtre outil ciblée<br />-Premier plan de l’onglet provisoire sélectionné<br />-Bouton de dépassement de capacité de document bordure sur pointage et pression<br />-Icône sélectionnée|
| HotTrack | -Arrière-plan et bordure du curseur de la barre de défilement sur la pression<br />-Flèche de barre de défilement glyphe sur pression |
| InactiveCaption | -L’IDE inactif et les glyphes de bouton de fenêtre volés au survol<br />-Arrière-plan de la barre de titre pour les fenêtres de l’IDE et les fenêtres à Raft<br />-Arrière-plan du contrôle de recherche désactivé |
| InactiveCaptionText | -L’IDE inactif et le premier plan de barre de titre Windows (texte et glyphes)<br />-L’arrière-plan et la bordure des boutons de la fenêtre inactives au survol<br />-Arrière-plan et bordure du bouton de la fenêtre outil sans focus<br />-Premier plan du contrôle de recherche désactivé |
| Menu | -Arrière-plan du menu déroulant<br />-Coche cochée et désactivée en arrière-plan |
| MenuText | -Menu déroulant bordure<br />-Coches<br />-Les glyphes de menu<br />-Texte du menu déroulant<br />-Icône sélectionnée |
| Scrollbar | -Arrière-plan de la barre de défilement et de la barre de défilement, tous les États |
| Fenêtre | -Masquer automatiquement l’arrière-plan de tabulation<br />-Arrière-plan de la barre de menus et de l’étagère de commande<br />-Arrière-plan ou non sélectionné onglet de la fenêtre de document arrière-plan et bordure du document, pour les onglets ouvert et provisoire<br />-Arrière-plan de la barre de titre de la fenêtre outil inactif<br />-Arrière-plan de l’onglet de la fenêtre outil, sélectionné et non sélectionné |
| WindowFrame | -Bordure IDE |
| WindowText | -Masquer automatiquement le premier plan de tabulation<br />-Premier plan de l’onglet de la fenêtre outil sélectionnée<br />-Onglet de fenêtre de document sans focus et onglet provisoire sans focus ou non sélectionné<br />-Arborescence par défaut du premier plan et pointage sur le glyphe non sélectionné<br />-Fenêtre outil bordure de l’onglet sélectionnée<br />-Arrière-plan du curseur de la barre de défilement, bordure et glyphe |

## <a name="exposing-colors-for-end-users"></a><a name="BKMK_ExposingColorsForEndUsers"></a> Exposition des couleurs pour les utilisateurs finaux

### <a name="overview"></a>Vue d’ensemble

Il peut arriver que vous souhaitiez autoriser l’utilisateur final à personnaliser votre interface utilisateur, par exemple lorsque vous créez un éditeur de code ou une aire de conception. Pour ce faire, la méthode la plus courante consiste à utiliser la boîte de dialogue **&gt; Options des outils** . À moins que vous n’ayez une interface utilisateur hautement spécialisée nécessitant des contrôles spéciaux, le moyen le plus simple de présenter la personnalisation consiste à utiliser la page **polices et couleurs** dans la section **environnement** de la boîte de dialogue. Pour chaque élément que vous exposez pour la personnalisation, l’utilisateur peut choisir de modifier la couleur de premier plan, la couleur d’arrière-plan ou les deux.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Création d’un VSPackage pour vos couleurs personnalisables

Un VSPackage peut contrôler les polices et les couleurs via des catégories personnalisées et afficher des éléments dans la page de propriétés polices et couleurs. Lors de l’utilisation de ce mécanisme, les VSPackages doivent implémenter l’interface [IVsFontAndColorDefaultsProvider](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider) et ses interfaces associées.

En principe, ce mécanisme peut être utilisé pour modifier tous les éléments d’affichage existants et les catégories qui les contiennent. Toutefois, il ne doit pas être utilisé pour modifier la catégorie éditeur de texte ou ses éléments d’affichage. Pour plus d’informations sur la catégorie éditeur de texte, consultez [vue d’ensemble des polices et des couleurs](/previous-versions/visualstudio/visual-studio-2015/extensibility/font-and-color-overview?preserve-view=true&view=vs-2015).

Pour implémenter des catégories personnalisées ou des éléments d’affichage, un VSPackage doit :

- **Créez ou identifiez des catégories dans le registre.** L’implémentation de l’IDE de la page de propriétés **polices et couleurs** utilise ces informations pour interroger correctement le service qui prend en charge une catégorie donnée.

- **Créez ou identifiez des groupes dans le registre (facultatif).** Il peut être utile de définir un groupe, qui représente l’Union de deux catégories ou plus. Si un groupe est défini, l’IDE fusionne automatiquement les sous-catégories et distribue les éléments affichés au sein du groupe.

- **Implémenter la prise en charge de l’IDE.**

- **Gérer les modifications de police et de couleur.**

#### <a name="to-create-or-identify-categories"></a>Pour créer ou identifier des catégories

Construisez un type spécial d’entrée de Registre Category sous `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` où `<Category>` est le nom non localisé de la catégorie.

Remplissez le Registre avec deux valeurs :

| Nom | Type | Données | Description |
| --- | --- | --- | --- |
| Category | REG_SZ | GUID | GUID créé pour identifier la catégorie |
| Paquet | REG_SZ | GUID | GUID du service VSPackage qui prend en charge la catégorie |

 Le service spécifié dans le registre doit fournir une implémentation de [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) pour la catégorie correspondante.

#### <a name="to-create-or-identify-groups"></a>Pour créer ou identifier des groupes

Construisez un type spécial d’entrée de Registre Category sous `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` où `<group>` est le nom non localisé du groupe.

Remplissez le Registre avec deux valeurs :

| Nom | Type | Données | Description |
|--- | --- | --- | --- |
| Category | REG_SZ | GUID | GUID créé pour identifier la catégorie |
| Paquet | REG_SZ | GUID | GUID du service VSPackage qui prend en charge la catégorie |

Le service spécifié dans le registre doit fournir une implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> pour le groupe correspondant.

![Implémentation de IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304-a_FontAndColorGroup")<br />Implémentation de `IVsFontAndColorGroup`

### <a name="to-implement-ide-support"></a>Pour implémenter la prise en charge IDE

Implémentez [GetObject](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject), qui retourne soit une interface [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) , soit une <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interface à l’IDE pour chaque catégorie ou GUID de groupe fourni.

Pour chaque catégorie qu’il prend en charge, un VSPackage implémente une instance distincte de l’interface [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) .

Les méthodes implémentées via [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) doivent fournir l’IDE avec :

- Listes d’éléments affichés dans la catégorie

- Noms localisables pour les éléments affichés

- Afficher des informations pour chaque membre de la catégorie

> [!NOTE]
> Chaque catégorie doit contenir au moins un élément d’affichage.

L’IDE utilise l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interface pour définir une Union de plusieurs catégories.

Son implémentation fournit l’IDE avec :

- Liste des catégories qui composent un groupe donné

- Accès aux instances de [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) prenant en charge chaque catégorie au sein du groupe

- Noms de groupes localisables

#### <a name="updating-the-ide"></a>Mise à jour de l’IDE

L’IDE met en cache les informations sur les paramètres de police et de couleur. Par conséquent, après toute modification de la configuration de la police et de la couleur de l’IDE, il est recommandé de s’assurer que le cache est à jour.

La mise à jour du cache s’effectue par le biais de l’interface [IvsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) et peut être exécutée globalement ou uniquement sur des éléments sélectionnés.

### <a name="handling-font-and-color-changes"></a>Gestion des modifications des polices et des couleurs

Pour prendre en charge correctement la coloration du texte affiché par le VSPackage, le service de colorisation qui le prend en charge doit répondre aux modifications effectuées par l’utilisateur via la page de propriétés polices et couleurs.

Pour ce faire, un VSPackage doit :

- **Gérez les événements générés** par l’IDE en implémentant l’interface [IVsFontAndColorEvents](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents) . L’IDE appelle la méthode appropriée après les modifications de l’utilisateur de la page polices et couleurs. Par exemple, il appelle la méthode [OnFontChanged](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged) si une nouvelle police est sélectionnée.

  **OR**

- **interroger l’IDE pour les modifications**. Cela peut être effectué par le biais de l’interface [IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) implémentée par le système. Bien qu’principalement pour la prise en charge de la persistance, la méthode [GetItem](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem) peut obtenir des informations sur la police et la couleur pour les éléments affichés. Pour plus d’informations sur les paramètres de police et de couleur, consultez l’article MSDN [accès aux paramètres de police et de couleur stockés](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-stored-font-and-color-settings?preserve-view=true&view=vs-2015).

> [!NOTE]
> Pour vous assurer que les résultats de l’interrogation sont corrects, utilisez l’interface [IVsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) pour déterminer si un vidage et une mise à jour du cache sont nécessaires avant d’appeler les méthodes de récupération de l’interface [IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) .

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Inscription de la catégorie de couleur et de police personnalisée sans implémenter d’interfaces

L’exemple de code suivant montre comment inscrire la catégorie de couleur et de police personnalisée sans implémenter les interfaces :

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

Pour cet exemple de code :

- `"NameID"` = ID de ressource du nom de la catégorie localisée dans votre package
- `"ToolWindowPackage"` = GUID du package
- `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"` est juste un exemple et la valeur réelle peut être un nouveau GUID fourni par l’implémenteur.

### <a name="set-the-font-and-color-property-category-guid"></a>Définir le GUID de la catégorie de propriété de la police et de la couleur

L’exemple de code ci-dessous illustre la définition de GUID de catégorie.

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
