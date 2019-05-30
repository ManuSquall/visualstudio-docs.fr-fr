---
title: Couleurs et styles pour Visual Studio | Microsoft Docs
ms.date: 07/31/2017
ms.topic: conceptual
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: faded3e4a541ad899306e40bf9d46bf96a6b8ace
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338348"
---
# <a name="colors-and-styling-for-visual-studio"></a>Couleurs et styles pour Visual Studio

## <a name="use-color-in-visual-studio"></a>Utiliser une couleur dans Visual Studio

Dans Visual Studio, la couleur est utilisée principalement comme outil de communication, pas seulement en tant que de décoration. Utiliser une couleur au minimum et réserver aux situations où vous souhaitez :

- Communiquer la signification ou l’affiliation (par exemple, les modificateurs de plateforme ou langage)

- Attirer votre attention (par exemple, en indiquant un changement d’état)

- Améliorer la lisibilité et de fournir des points de repère pour naviguer dans l’interface utilisateur

- Augmenter l’opportunité

Il existe plusieurs options pour l’attribution de couleurs aux éléments d’interface utilisateur dans Visual Studio. Parfois, il peut être difficile à figure out option que vous êtes censé pour utiliser, ou comment l’utiliser correctement. Cette rubrique vous aideront à :

- Comprendre les différents services et les systèmes utilisés pour définir des couleurs dans Visual Studio.

- Sélectionnez l’option appropriée pour un élément donné.

- Utiliser correctement l’option que vous avez choisi.

> [!NOTE]
> Jamais coder en dur hex, RVB ou des couleurs système à vos éléments d’interface utilisateur. L’utilisation des services permet de souplesse de réglage hue. En outre, sans que le service, pas pouvoir tirer parti des fonctionnalités de changement de thème de [le VSColor service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Méthodes d’affectation de couleur aux éléments d’interface de Visual Studio

Choisissez la méthode mieux adaptée à vos éléments d’interface utilisateur.

| Votre interface utilisateur | Méthode | Quelles sont-elles ? |
| --- | --- | --- |
| Vous avez incorporé ou boîtes de dialogue autonome. | **Couleurs système** | Les noms de système qui permettent au système d’exploitation définir la couleur et l’apparence des éléments d’interface utilisateur, tels que les contrôles de boîte de dialogue commune. |
| Vous disposez d’interface utilisateur personnalisée que vous souhaitez être cohérent avec l’environnement Visual Studio global et vous disposez des éléments d’interface utilisateur qui correspondent à la catégorie et la signification sémantique des jetons partagés. | **Couleurs partagées communes** | Noms de jeton de couleur prédéfinis existants des éléments d’interface spécifiques |
| Vous avez une fonctionnalité individuelle ou un groupe de fonctionnalités, et il n’existe aucune couleur partagé pour les éléments similaires. | **Couleurs personnalisées** | Noms de jeton de couleur qui sont spécifiques à une zone et pas destiné à être partagé avec toute autre interface utilisateur |
| Voulez-vous autoriser l’utilisateur final de personnaliser l’interface utilisateur ou du contenu (par exemple, pour les éditeurs de texte ou les fenêtres du concepteur spécialisés). | **Personnalisation de l’utilisateur final**<br /><br />**(Outils &gt; boîte de dialogue Options)** | Paramètres définis dans la page « Polices et couleurs » de la **outils &gt; Options** boîte de dialogue ou une page spécialisée spécifique à une fonction de l’interface utilisateur. |

### <a name="visual-studio-themes"></a>Thèmes Visual Studio

Visual Studio propose trois thèmes de couleur différente : clair, sombre ou bleu. Il détecte également le mode de contraste élevé, ce qui est un thème de couleur de l’échelle du système conçu pour l’accessibilité.

Les utilisateurs sont invités à sélectionner un thème lors de leur première utilisation de Visual Studio et sont en mesure de basculer entre les thèmes ultérieurement en accédant à **outils &gt; Options &gt; environnement &gt; général** et en choisissant un nouveau thème à partir de le menu déroulant « thème de couleur ».

Utilisateurs peuvent également utiliser le panneau de configuration pour changer leurs systèmes ensemble dans une de plusieurs thèmes à contraste élevé. Si un utilisateur sélectionne un thème à contraste élevé, puis le sélecteur de thème de couleur Visual Studio n’affecte plus les couleurs dans Visual Studio, bien que les modifications de thème sont enregistrées pour lorsque l’utilisateur quitte le mode de contraste élevé. Pour plus d’informations sur le mode de contraste élevé, consultez [couleurs contrastées en choisissant](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).

### <a name="the-vscolor-service"></a>Le service VSColor

Visual Studio fournit un service de couleur d’environnement, appelé VSColor service, qui permet de lier les valeurs de couleur de vos éléments d’interface utilisateur à une entrée nommée contenant les valeurs de couleur pour chaque thème de Visual Studio. Cela garantit que vos couleurs change automatiquement pour refléter l’actuel sélectionné par l’utilisateur système ou thème mode contraste élevé. Utilisation du service signifie que l’implémentation de toutes les modifications liées au thème de couleur est gérée au même endroit, et si vous utilisez des couleurs partagées communes à partir du service, votre interface utilisateur reflète automatiquement les nouveaux thèmes dans les futures versions de Visual Studio.

### <a name="implementation"></a>Implémentation

Le code source de Visual Studio inclut plusieurs fichiers de définition de package qui contiennent des listes de noms de jeton et les valeurs de couleur respectifs pour chaque thème. Le service de couleur lit le VSColors définis dans ces fichiers de définition de package. Ces couleurs sont référencés dans le balisage XAML ou dans le code et ensuite chargées à l’aide du `IVsUIShell5.GetThemedColor` méthode ou un mappage DynamicResource.

### <a name="system-colors"></a>Couleurs système

Contrôles communs référencent les couleurs système par défaut. Si vous souhaitez que votre interface utilisateur à utiliser des couleurs système, comme lors de la création d’une boîte de dialogue intégré ou autonome, vous n’avez pas besoin de faire quoi que ce soit.

### <a name="common-shared-colors-in-the-vscolor-service"></a>Couleurs partagées communes dans le service VSColor

Vos éléments d’interface doivent refléter l’environnement global de Visual Studio. En réutilisant les couleurs partagées communes qui sont appropriés pour le composant d’interface utilisateur que vous concevez, vous vous assurer que votre interface est cohérente avec d’autres interfaces de Visual Studio, et que vos couleurs mettra à jour automatiquement lorsque les thèmes sont ajoutés ou mis à jour.

Avant d’utiliser les couleurs partagées communes, assurez-vous que vous comprenez comment les utiliser correctement. Utilisation incorrecte de couleurs partagées communes peut entraîner une expérience incohérente, frustrante ou déroutante pour vos utilisateurs.

### <a name="user-customizable-colors"></a>Couleurs personnalisables par l’utilisateur

Consultez : [Exposition des couleurs pour les utilisateurs finaux](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

Parfois, vous devez autoriser l’utilisateur final à personnaliser votre interface utilisateur, comme lorsque vous créez un éditeur de code ou l’aire de conception. Composants d’interface utilisateur personnalisables sont trouvent dans le **polices et couleurs** section de la **outils &gt; Options** boîte de dialogue, où les utilisateurs peuvent choisir de modifier la couleur de premier plan, couleur d’arrière-plan ou les deux.

![Outils &gt; boîte de dialogue Options](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "a_ToolsOptionsDialog-0301")<br />Outils &gt; boîte de dialogue Options

## <a name="BKMK_TheVSColorService"></a> Le Service VSColor

Visual Studio fournit un service de couleur d’environnement, également appelé le service VSColor ou le service de couleur du shell. Ce service vous permet de lier les valeurs de couleur de vos éléments d’interface utilisateur à un jeu contenant des couleurs pour chaque thème de couleurs de nom-valeur. Le service de VSColor doit être utilisé pour tous les éléments d’interface utilisateur, afin que les couleurs changent pour refléter le thème sélectionné par l’utilisateur actuel et automatiquement afin que l’interface utilisateur liée au service de couleur d’environnement seront intègre avec les nouveaux thèmes dans les futures versions de Visual Studio.

### <a name="how-the-service-works"></a>Fonctionnement du service

Le service de couleur d’environnement lit que vscolors défini dans le .pkgdef pour le composant d’interface utilisateur. Ces VSColors sont ensuite référencés dans le balisage XAML ou de code et sont chargés à l’aide du `IVsUIShell5.GetThemedColor` ou un `DynamicResource` mappage.

![Architecture de service de couleur environnement](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")<br />Architecture de service de couleur d'environnement

### <a name="accessing-the-service"></a>L’accès au service

Il existe différentes façons de l’accès à l’aide de VSColor service, selon le type de couleur jetons vous et quel type de code que vous avez.

#### <a name="predefined-environment-colors"></a>Couleurs de l’environnement prédéfinis

##### <a name="from-native-code"></a>À partir du code natif

L’interpréteur de commandes fournit un service qui permet d’accéder à la `COLORREF` des couleurs. L’interface/de service est :

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

Dans le fichier vsshell80.idl, dans l’énumération `__VSSYSCOLOREX` a des constantes de couleur de shell. Pour l’utiliser, passez en tant que la valeur d’index l’une des valeurs à partir de la `enum __VSSYSCOLOREX` documentées dans MSDN ou un index normal numéro que le système Windows API, `GetSysColor`, accepte. Cette opération récupère la valeur RVB de la couleur qui doit être utilisée dans le deuxième paramètre.

Si vous stockez un stylet ou un pinceau avec une nouvelle couleur, vous devez `AdviseBroadcastMessages` (sur le shell Visual Studio) et écouter `WM_SYSCOLORCHANGE` et `WM_THEMECHANGED` messages.

Pour accéder au service de couleur en code natif, vous allez effectuer un appel qui ressemble à ceci :

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> [!NOTE]
> Le `COLORREF` valeurs retournées par `GetVSSysColorEx()` contiennent simplement R, G, composants B d’une couleur de thème. Si une entrée de thème utilise la transparence, la valeur de canal alpha est ignorée avant de retourner. Par conséquent, si la couleur de l’environnement d’intérêt doit être utilisée dans un emplacement où le canal de transparence est importante, vous devez utiliser `IVsUIShell5.GetThemedColor` au lieu de `IVsUIShell2::GetVSSysColorEx`, comme décrit plus loin dans cette rubrique.

##### <a name="from-managed-code"></a>À partir du code managé

Il est assez simple d’accéder au service VSColor dans le code natif. Si vous travaillez via du code managé, toutefois, déterminer comment utiliser le service peut être difficile. Dans cette optique, Voici un extrait de code c# illustrant ce processus :

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

Vous pouvez lier aux couleurs de Visual Studio via des valeurs exportées dans l’Application `ResourceDictionary`. Voici un exemple d’utilisation des ressources à partir de la table des couleurs, ainsi que la liaison aux données de police d’environnement dans XAML.

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

#### <a name="helper-classes-and-methods-for-managed-code"></a>Classes d’assistance et des méthodes pour le code managé

Pour le code managé, bibliothèque de Managed Package Framework de l’interpréteur de commandes (`Microsoft.VisualStudio.Shell.12.0.dll`) contient deux classes d’assistance facilitant l’utilisation de couleurs à thème.

Les méthodes d’assistance dans le `Microsoft.VisualStudio.Shell.VsColors` classe dans MPF inclure `GetThemedGDIColor()` et `GetThemedWPFColor()`. Ces méthodes d’assistance retournent la valeur de couleur d’une entrée de thème en tant que `System.Drawing.Color` ou `System.Windows.Media.Color`, utilisable dans WinForms ou WPF UI.

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

La classe peut également être utilisée pour obtenir les identificateurs VSCOLOR pour une clé de ressource de couleur WPF spécifique, ou vice versa.

```csharp
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

Les méthodes de `VsColors` classe interroger le service de VSColor pour retourner la valeur de couleur à chaque fois qu’ils sont appelés. Pour obtenir une valeur de couleur en tant que `System.Drawing.Color`, une alternative avec de meilleures performances consiste à utiliser à la place les méthodes de la `Microsoft.VisualStudio.PlatformUI.VSThemeColor` (classe), qui met en cache les valeurs de couleur obtenues à partir du service VSColor. La classe s’abonne en interne aux événements de messages de diffusion de shell et ignore la valeur mise en cache lorsqu’un événement de changement de thème. En outre, la classe fournit un. Événement NET conviviale pour vous abonner aux modifications de thème. Utiliser le `ThemeChanged` événement à ajouter un nouveau gestionnaire, utilisez le `GetThemedColor()` méthode pour obtenir la couleur des valeurs pour le `ThemeResourceKeys` d’intérêt. Un exemple de code pourrait ressembler à ceci :

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

## <a name="BKMK_ChoosingHighContrastColors"></a> Choix de couleurs à contraste élevé

### <a name="overview"></a>Vue d'ensemble

Windows utilise plusieurs thèmes à contraste élevé au niveau du système qui augmentent le contraste des couleurs de texte, les arrière-plans et les images, de rendre les éléments apparaissent plus distincte sur l’écran. Pour des raisons d’accessibilité, il est important que les éléments d’interface Visual Studio répondent correctement lorsque les utilisateurs basculer vers un thème à contraste élevé.

Seule une poignée de couleurs système peut servir pour les thèmes à contraste élevé. Lorsque vous choisissez votre système de noms de couleur, n’oubliez pas les conseils suivants :

- **Choisissez des couleurs système qui ont la même signification sémantique** que l’élément qui sont de couleurs. Par exemple, si vous choisissez une couleur de contraste élevé pour du texte dans une fenêtre, utilisez WindowText et ControlText pas.

- **Choisissez des paires de premier plan/arrière-plan** ensemble ou vous ne serez pas certain que votre choix de couleurs fonctionnent dans tous les thèmes à contraste élevé.

- **Déterminer quelles parties de votre interface utilisateur sont les plus importants et assurez-vous que les zones de contenu seront ressortir.** Vous allez perdre beaucoup de détails des différences subtiles dans teinte de couleur seraient normalement faire la distinction, l’utilisation de couleurs de bordure fort est donc courant pour définir les zones de contenu, car il n’existe aucune variantes de couleur pour les différentes zones de contenu.

### <a name="system-color-set"></a>Jeu de couleurs système

La table sur [Blog de l’équipe WPF : Référence de SystemColors](https://blogs.msdn.microsoft.com/wpf/2010/11/30/systemcolors-reference/) indique l’ensemble complet des noms de couleurs système et les teintes correspondantes affichées dans chaque thème.

Lorsque cette application d’un jeu de couleurs à votre interface utilisateur, limité *il est probable que vous allez perdre les détails subtils qui étaient présents dans les thèmes « normales »* . Voici un exemple d’interface utilisateur avec des couleurs gris subtiles qui sont utilisés pour distinguer les domaines au sein d’une fenêtre outil. Associé à la même fenêtre affichée en mode de contraste élevé, vous pouvez voir que tous les horizons sont la même teinte et les bordures de ces zones sont indiquées par bordure autonome :

![Exemple de détails comment subtiles sont perdues en contraste élevé](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303-a_PropertiesWindow")<br />Exemple de détails comment subtiles sont perdues en contraste élevé

#### <a name="choosing-text-colors-in-an-editor"></a>Choix de couleurs de texte dans un éditeur

Texte en couleurs s’est utilisé dans un éditeur ou sur une aire de conception pour indiquer la signification, que ce qui permet de faciliter l’identification des groupes d’éléments similaires. Toutefois, dans un thème à contraste élevé, vous n’avez pas la possibilité de faire la distinction entre plus de trois couleurs de texte. WindowText, GrayText et HotTrackText sont les couleurs uniquement disponibles sur les surfaces WindowBackground. Étant donné que vous ne pouvez pas utiliser plus de trois couleurs, choisissez soigneusement les différences les plus importantes que vous souhaitez afficher en mode de contraste élevé.

Teintes pour chacun des noms de jeton autorisées sur une surface de l’éditeur, telles qu’elles apparaissent dans chaque thème à contraste élevé :

![Comparaison de l’éditeur de contraste élevé](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303-b_HCEditorComparison")<br />Comparaison de l'éditeur de contraste élevé

Exemples de la surface de l’éditeur dans le thème bleu :

![Éditeur dans le thème bleu](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303-c_EditorBlue")<br />Éditeur dans le thème bleu

![Éditeur dans le thème à contraste élevé, #1](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303-d_EditorHC1")<br />Éditeur dans le thème à contraste élevé, #1

### <a name="usage-patterns"></a>Modèles d’utilisation

Nombreux éléments d’interface utilisateur courants ont déjà des couleurs à contraste élevé définis. Vous pouvez référencer ces modèles d’utilisation lors du choix de votre propre système de noms de couleurs, afin que vos éléments d’interface utilisateur sont cohérents avec des composants similaires.

| Couleur système | Utilisation |
| --- | --- |
| LégendeActive | -Active IDE et les glyphes de bouton de fenêtre rafted sur pointage et appuyez sur<br />-Arrière-plan de la barre de titre pour IDE et rafted windows<br />-Arrière-plan de barre d’état par défaut |
| TexteLégendeActive | -Active IDE et rafted windows pour l’avant-plan de barre de titre (texte et des glyphes)<br />-En arrière-plan et de bordure des boutons de la fenêtre active de pointage, puis appuyez sur |
| Contrôle | -Zone de liste déroulante, liste déroulante et recherche contrôlent par défaut et désactivé en arrière-plan, y compris le bouton de liste déroulante<br />-Arrière-plan du bouton de cible d’ancrage<br />-Arrière-plan de la barre de commande<br />-Arrière-plan de la fenêtre outil |
| ControlDark | -En arrière-plan IDE<br />-Séparateurs de barre menu et commande<br />: Bordure barre de commandes<br />-Les ombres menu<br />-Outil d’onglet par défaut et le pointage de bordure de la fenêtre et le séparateur<br />-De documents et d’arrière-plan de bouton de dépassement de capacité<br />-Bordure de glyphe de cible dock |
| ContrôleFoncéFoncé |-Fenêtre de l’onglet documents sélectionné inactif |
| ContrôleClair |-Bordure de l’onglet masquage automatique<br />-Bordure de liste de zone et de liste déroulante liste déroulante<br />-Ancrer en arrière-plan de la cible et la bordure |
| ControlLightLight | -Bordure provisoire sélectionné, avec focus |
| ControlText | -Glyphe de liste de zone et de liste déroulante liste déroulante<br />-Onglet fenêtre désélectionné outil texte |
| GrayText |-Zone de liste déroulante et de liste déroulante désactivée bordure, le glyphe de liste déroulante, le texte et le texte de l’élément menu<br />-Texte de menu désactivé<br />-Recherche texte d’en-tête de contrôle 'options de recherche'<br />-Séparateur de section de contrôle de recherche |
| Surligner | -Toutes les pointage et appuyés arrière-plans et bordures, à l’exception de liste déroulante zone bouton de liste déroulante d’arrière-plan et de document dépassement de capacité bien bordure du bouton<br />-Arrière-plans de l’élément sélectionné |
| HighlightText | -Toutes les pointage et colorier appuyé (texte et des glyphes)<br />-Outil fenêtre et document onglet fenêtre contrôle au premier plan<br />-Bordure de barre de titre de fenêtre outil ayant le focus<br />-Premier plan onglet provisoire ciblé et sélectionné<br />-Bordure du bouton de dépassement de capacité bien document sur pointage et appuyez sur<br />-Bordure d’icône sélectionné|
| HotTrack | -Défilement barre d’arrière-plan du curseur et appuyez sur la bordure<br />-Barre de défilement glyphe de flèche sur la presse |
| InactiveCaption | -IDE inactive et fenêtre rafted des glyphes de bouton au pointage<br />-Arrière-plan de la barre de titre pour IDE et rafted windows<br />-Arrière-plan de contrôle de recherche désactivé |
| InactiveCaptionText | -IDE inactive et au premier plan de barre de titre windows rafted (texte et des glyphes)<br />-Arrière-plan des boutons de fenêtre inactive et la bordure au pointage<br />-Bordure et arrière-plan de bouton de fenêtre outil inactif<br />-Premier plan de contrôle de recherche désactivé |
| Menu | -Arrière-plan de menu liste déroulante<br />-Arrière-plan de case à cocher activé et désactivé |
| MenuText | -Bordure du menu liste déroulante<br />-Coches<br />-Les glyphes menu<br />-Texte de menu liste déroulante<br />-Bordure d’icône sélectionné |
| Scrollbar | -Faire défiler barre et arrière-plan de flèche, tous les États de la barre de défilement |
| Fenêtre | -Arrière-plan de l’onglet masquage automatique<br />-Menu barre et d’arrière-plan de conservation de commande<br />-Onglet d’arrière-plan de la fenêtre document inactif ou non sélectionnés et bordure de document, pour les onglets ouverts et provisoires<br />-Arrière-plan de barre de titre de fenêtre outil inactif<br />-Fenêtre outil onglet arrière-plan, à la fois sélectionnés et |
| WindowFrame | : Bordure de l’IDE |
| WindowText | -Premier plan d’onglet masquage automatique<br />-Premier plan onglet de fenêtre outil sélectionné<br />-Onglet de fenêtre de document inactif et premier plan inactif ou désélectionné onglet provisoire<br />-Premier plan par défaut de vue et arborescence pointage sur glyphe non sélectionné<br />-Bordure onglet sélectionné de la fenêtre outil<br />-Barre de défilement thumb arrière-plan, la bordure et glyphe |

## <a name="BKMK_ExposingColorsForEndUsers"></a> Exposition des couleurs pour les utilisateurs finaux

### <a name="overview"></a>Vue d'ensemble

Parfois vous souhaitez autoriser l’utilisateur final à personnaliser votre interface utilisateur, comme lorsque vous créez un éditeur de code ou l’aire de conception. La plus courante pour ce faire consiste à l’aide de la **outils &gt; Options** boîte de dialogue. À moins que vous avez hautement spécialisées l’interface utilisateur qui nécessite des contrôles spéciaux, le moyen le plus simple pour présenter la personnalisation consiste à utiliser le **polices et couleurs** page au sein de la **environnement** section de la boîte de dialogue. Pour chaque élément que vous exposez pour la personnalisation, l’utilisateur peut choisir de modifier la couleur de premier plan, couleur d’arrière-plan ou les deux.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Création d’un VSPackage pour vos couleurs personnalisables

Un VSPackage peut contrôler les polices et couleurs par le biais des catégories personnalisées et d’afficher des éléments sur la page de propriétés de polices et couleurs. Lorsque vous utilisez ce mécanisme, les VSPackages doivent implémenter le [IVsFontAndColorDefaultsProvider](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider) interface et ses interfaces associées.

En principe, ce mécanisme peut être utilisé pour modifier tous les éléments d’affichage existants et les catégories qui les contiennent. Toutefois, il ne doit pas servir à modifier la catégorie de l’éditeur de texte ou de ses éléments d’affichage. Pour plus d’informations sur la catégorie de l’éditeur de texte, consultez [vue d’ensemble de la couleur et de police](../font-and-color-overview.md).

Pour implémenter des catégories personnalisées ou afficher les éléments, un VSPackage doit :

- **Créez ou identifiez des catégories dans le Registre.** Implémentation de l’IDE de le **polices et couleurs** page de propriétés utilise ces informations pour interroger correctement pour le service prenant en charge d’une catégorie donnée.

- **Créez ou identifiez les groupes dans le Registre (facultatif).** Il peut être utile de définir un groupe, qui représente l’union de deux ou plusieurs catégories. Si un groupe est défini, l’IDE fusionne les sous-catégories automatiquement et distribue les éléments affichés dans le groupe.

- **Implémenter la prise en charge de l’IDE.**

- **Gérer les modifications de police et de couleur.**

#### <a name="to-create-or-identify-categories"></a>Pour créer ou identifier des catégories

Construire un type spécial de l’entrée de Registre de catégorie sous `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` où `<Category>` est le nom non localisé de la catégorie.

Remplir le Registre avec deux valeurs :

| Name | Type | Données | Description |
| --- | --- | --- | --- |
| Category | REG_SZ | GUID | Un GUID est créé pour identifier la catégorie |
| Package | REG_SZ | GUID | Le GUID du service VSPackage qui prend en charge de la catégorie |

 Le service spécifié dans le Registre doit fournir une implémentation de [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) pour la catégorie correspondante.

#### <a name="to-create-or-identify-groups"></a>Pour créer ou identifier des groupes

Construire un type spécial de l’entrée de Registre de catégorie sous `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` où `<group>` est le nom non localisé du groupe.

Remplir le Registre avec deux valeurs :

| Name | Type | Données | Description |
|--- | --- | --- | --- |
| Category | REG_SZ | GUID | Un GUID est créé pour identifier la catégorie |
| Package | REG_SZ | GUID | Le GUID du service VSPackage qui prend en charge de la catégorie |

Le service spécifié dans le Registre doit fournir une implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> pour le groupe correspondant.

![Implémentation d’interface IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304-a_FontAndColorGroup")<br />Implémentation de `IVsFontAndColorGroup`

### <a name="to-implement-ide-support"></a>Pour implémenter la prise en charge de l’IDE

Implémentez [GetObject](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject), qui retourne soit une [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) interface ou un <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> de l’interface à l’IDE pour chaque catégorie ou le groupe GUID fourni.

Pour chaque catégorie, il prend en charge, un VSPackage implémente une instance distincte de la [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) interface.

Les méthodes implémentées par le biais [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) doit fournir l’IDE avec :

- Listes d’éléments affichés dans la catégorie

- Noms localisables pour les éléments d’affichage

- Afficher des informations pour chaque membre de la catégorie

> [!NOTE]
> Chaque catégorie doit contenir au moins un élément d’affichage.

L’IDE utilise le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interface pour définir une union de plusieurs catégories.

Son implémentation fournit l’IDE avec :

- Une liste des catégories qui composent un groupe donné

- Accès aux instances du [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) prise en charge de chaque catégorie au sein du groupe

- Noms de groupe localisable

#### <a name="updating-the-ide"></a>La mise à jour de l’IDE

L’IDE met en cache les informations sur les paramètres de police et de couleur. Par conséquent, après toute modification de la configuration de la couleur et de police de l’IDE, en garantissant que le cache est à jour est une bonne pratique.

La mise à jour le cache s’effectue via le [IvsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) interface et peut être effectuée dans le monde entier ou seulement sélectionnées.

### <a name="handling-font-and-color-changes"></a>Gestion des modifications de police et de couleur

Pour correctement prendre en charge la colorisation de texte qui affiche un VSPackage, le service de colorisation prenant en charge le VSPackage doit répondre aux modifications initiée par l’utilisateur apportées via la page de propriétés de polices et couleurs.

Pour ce faire, un VSPackage doit :

- **gérer les événements générés par l’IDE** en implémentant la [IVsFontAndColorEvents](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents) interface. L’IDE appelle la méthode appropriée suivant les modifications de l’utilisateur de la page polices et couleurs. Par exemple, il appelle le [OnFontChanged](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged) méthode si une nouvelle police est sélectionnée.

  **OU**

- **interroger l’IDE pour les modifications**. Cela est possible via l’implémenté par le système [IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) interface. Bien que principalement pour la prise en charge de la persistance, le [GetItem](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem) méthode peut obtenir des informations de police et de couleur pour afficher les éléments. Pour plus d’informations sur les paramètres de police et couleur, consultez l’article MSDN [l’accès à stockées paramètres de police et couleur](../accessing-stored-font-and-color-settings.md).

> [!NOTE]
> Pour vous assurer que les résultats d’interrogation sont corrects, utilisez le [IVsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) interface pour déterminer si un vidage du cache et la mise à jour sont nécessaires avant d’appeler les méthodes de récupération de la [IVsFontAndColorStorage ](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) interface.

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>L’inscription de la catégorie de couleur et de police personnalisée sans avoir à implémenter des interfaces

L’exemple de code suivant montre comment inscrire la police personnalisée et la catégorie de couleur sans avoir à implémenter les interfaces :

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

Pour cet exemple de code :

- `"NameID"` = l’ID de ressource du nom de catégorie localisée dans votre package.
- `"ToolWindowPackage"` = Package GUID
- `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"` est juste un exemple et la valeur réelle peut être un nouveau GUID fourni par l’implémenteur.

### <a name="set-the-font-and-color-property-category-guid"></a>Définir la police et couleur propriété GUID de catégorie

L’exemple de code ci-dessous montre comment définir des GUID de catégorie.

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
