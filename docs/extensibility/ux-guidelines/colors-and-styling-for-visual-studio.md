---
title: Couleurs et styles pour Visual Studio | Documents Microsoft
ms.custom: 
ms.date: 07/31/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ff1f5d9c7c28c63e2f1f1c0783f1032888e3c645
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="colors-and-styling-for-visual-studio"></a>Couleurs et styles pour Visual Studio
## <a name="using-color-in-visual-studio"></a>À l’aide de la couleur dans Visual Studio  
Dans Visual Studio, la couleur est utilisée principalement comme outil de communication, pas comme décoration. Utiliser une couleur au minimum et réserver aux situations où vous souhaitez :  
  
-   Communiquer la signification ou l’affiliation (par exemple, les modificateurs de plateforme ou la langue)  
  
-   Attirer l’attention (par exemple, en indiquant un changement d’état)  
  
-   Améliorer la lisibilité et fournir des points de repère pour naviguer dans l’interface utilisateur  
  
-   Augmenter l’opportunité  
  
Plusieurs options existent pour attribuer des couleurs aux éléments d’interface utilisateur dans Visual Studio. Il peut parfois être difficile à figure out option que vous êtes censé pour utiliser, ou comment l’utiliser correctement. Cette rubrique vous aideront à :  
  
1.  Comprendre les différents services et les systèmes qui permet de définir des couleurs dans Visual Studio.  
  
2.  Sélectionnez l’option appropriée pour un élément donné.  
  
3.  Utiliser correctement l’option que vous avez choisi.  
  
> **Remarque :** jamais coder en dur hex, RVB ou les couleurs système à vos éléments de l’interface utilisateur. L’utilisation des services permet de flexibilité teinte de paramétrage. En outre, vous sans le service, seront pas en mesure de tirer parti des fonctionnalités de commutation de thème [le service VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).
  
### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Méthodes pour l’affectation de couleur pour les éléments d’interface de Visual Studio  
Choisissez la méthode mieux adaptée à vos éléments d’interface utilisateur.  
  
| Votre interface utilisateur | Méthode | Quelles sont-elles ? |  
| --- | --- | --- |  
| Vous avez incorporé ou des boîtes de dialogue autonome. | **Couleurs système** | Les noms système que le système d’exploitation définir la couleur et l’apparence des éléments de l’interface utilisateur, tels que les contrôles de boîte de dialogue commune. |
| Vous avez l’interface utilisateur personnalisée que vous souhaitez être cohérent avec l’environnement Visual Studio global et éléments d’interface utilisateur qui correspondent à la catégorie et la sémantique des jetons partagés. | **Couleurs partagées communes** | Noms de jeton de couleur prédéfinis existants pour les éléments d’interface utilisateur spécifiques |
| Vous disposez d’une fonctionnalité individuelle ou un groupe de fonctionnalités et il n’existe aucune couleur partagé pour les éléments similaires. | **Couleurs personnalisées** | Noms de jeton de couleur qui sont spécifiques à une zone et pas destiné à être partagé avec toute autre interface utilisateur |
| Vous souhaitez autoriser l’utilisateur final de personnaliser l’interface utilisateur ou du contenu (par exemple, pour les éditeurs de texte ou les fenêtres du concepteur spécialisés). | **Personnalisation de l’utilisateur final**<br /><br />**(Outils &gt; boîte de dialogue Options)** | Les paramètres définis dans la page « Polices et couleurs » de la **outils &gt; Options** boîte de dialogue ou une page spécialisée spécifique à une fonction de l’interface utilisateur. |
  
### <a name="visual-studio-themes"></a>Thèmes Visual Studio  
Visual Studio propose trois thèmes de couleurs différentes : clair, sombre ou bleu. Il détecte également le mode de contraste élevé, ce qui constitue un thème de couleur de l’échelle du système conçu pour l’accessibilité.  
  
Les utilisateurs sont invités pour sélectionner un thème lors de leur première utilisation de Visual Studio et sont en mesure de basculer les thèmes ultérieurement en accédant à **outils &gt; Options &gt; environnement &gt; général** et en choisissant un nouveau thème à partir de le menu déroulant « thème ».  
  
Utilisateurs peuvent également utiliser le panneau de configuration pour basculer de leurs systèmes entières dans une de plusieurs thèmes à contraste élevé. Si un utilisateur sélectionne un thème à contraste élevé, puis le sélecteur de thème de couleur Visual Studio n’affecte plus les couleurs dans Visual Studio, bien que les modifications de thème sont enregistrées pour lorsque l’utilisateur quitte le mode de contraste élevé. Pour plus d’informations sur le mode de contraste élevé, consultez [couleurs contrastées de choix](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).
  
### <a name="the-vscolor-service"></a>Le service VSColor  
Visual Studio fournit un service de couleur d’environnement, connu en tant que le service de VSColor, ce qui vous permet de lier les valeurs de couleur de vos éléments de l’interface utilisateur à une entrée nommée contenant les valeurs de couleur pour chaque thème Visual Studio. Cela garantit que vos couleurs change automatiquement pour refléter l’actuel sélectionnés par l’utilisateur système ou thème mode contraste élevé. Utilisation du service signifie que l’implémentation de toutes les modifications liées au thème de couleur est gérée dans un seul emplacement, et si vous utilisez des couleurs partagées communes à partir du service, votre interface utilisateur reflètent automatiquement les nouveaux thèmes dans les futures versions de Visual Studio.  
  
### <a name="implementation"></a>Implémentation  
Le code source Visual Studio inclut plusieurs fichiers de définition de package qui contiennent des listes de noms de jeton et les valeurs de couleur respectives pour chaque thème. Le service de couleur lit le VSColors définis dans ces fichiers de définition de package. Ces couleurs sont référencés dans le balisage XAML ou dans le code et puis chargés par le biais du `IVsUIShell5.GetThemedColor` méthode ou un mappage DynamicResource.  
  
### <a name="system-colors"></a>Couleurs système  
Contrôles communs référencent les couleurs système par défaut. Si vous souhaitez que votre interface utilisateur à utiliser des couleurs système, comme lors de la création d’une boîte de dialogue intégré ou autonome, vous n’avez pas besoin de faire quoi que ce soit.  
  
### <a name="common-shared-colors-in-the-vscolor-service"></a>Couleurs partagées communes dans le service VSColor  
Éléments de l’interface doivent refléter l’environnement Visual Studio global. En réutilisant les couleurs partagées communes qui sont appropriées pour le composant de l’interface utilisateur que vous concevez, vous assurer que votre interface est compatible avec d’autres interfaces de Visual Studio, et que vos couleurs met à jour automatiquement lorsque les thèmes sont ajoutés ou mis à jour.  
  
Avant d’utiliser les couleurs partagées communes, assurez-vous que vous comprenez comment les utiliser correctement. Utilisation incorrecte de couleurs partagées communes peut entraîner une expérience incohérente, confuse ou frustrante pour vos utilisateurs.  
  
### <a name="user-customizable-colors"></a>Couleurs personnalisables par l’utilisateur  
Voir : [exposant des couleurs pour les utilisateurs finaux](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)  
  
Dans certains cas, vous devez autoriser l’utilisateur final de personnaliser votre interface utilisateur, comme lorsque vous créez un éditeur de code ou l’aire de conception. Composants d’interface utilisateur personnalisables sont trouvent dans le **polices et couleurs** section de la **outils &gt; Options** boîte de dialogue, où les utilisateurs peuvent choisir de modifier la couleur de premier plan, couleur d’arrière-plan ou les deux.  
  
![Outils &gt; boîte de dialogue Options](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")<br />Outils &gt; boîte de dialogue Options
  
##  <a name="BKMK_TheVSColorService"></a>Le Service VSColor  
Visual Studio fournit un service de couleur d’environnement, également appelé le service VSColor ou le service de couleur du shell. Ce service vous permet de lier les valeurs de couleur de vos éléments de l’interface utilisateur à un jeu contenant des couleurs pour chaque thème de couleurs de nom-valeur. Le service de VSColor doit être utilisé pour tous les éléments d’interface utilisateur, afin que les couleurs changent pour refléter le thème sélectionné par l’utilisateur actuel et automatiquement afin que l’interface utilisateur liée au service de couleur d’environnement seront intègre avec les nouveaux thèmes dans les futures versions de Visual Studio.  
  
### <a name="how-the-service-works"></a>Comment fonctionne le service  
Le service de couleur d’environnement lit que vscolors défini dans le .pkgdef pour le composant d’interface utilisateur. Ces VSColors sont ensuite référencés dans le balisage XAML ou du code et sont chargés par le biais du `IVsUIShell5.GetThemedColor` ou un `DynamicResource` mappage.  
  
![Architecture du service de couleur environnement](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")<br />Architecture de service de couleur d'environnement
  
### <a name="accessing-the-service"></a>L’accès au service
Il existe plusieurs façons différentes pour le service VSColor, selon le type de couleur jetons vous utilisez l’accès et le type de code que vous avez.  

#### <a name="predefined-environment-colors"></a>Couleurs de l’environnement prédéfinis  
  
##### <a name="from-native-code"></a>À partir du code natif  
L’interpréteur de commandes fournit un service qui fournit l’accès à la `COLORREF` des couleurs. / L’interface de service est la suivante :  
  
```  
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)  
```  
  
Dans le fichier VSShell80.idl, l’énumération `__VSSYSCOLOREX` a des constantes de couleur de shell. Pour l’utiliser, transmettre en tant que la valeur d’index l’une des valeurs de la `enum __VSSYSCOLOREX` documentées dans MSDN ou un index normal numéro que le système Windows API, `GetSysColor`, accepte. Cette opération récupère la valeur RVB de la couleur qui doit être utilisée dans le deuxième paramètre.  
  
Si vous stockez un stylet ou un pinceau avec une nouvelle couleur, vous devez `AdviseBroadcastMessages` (hors de l’interpréteur de commandes de Visual Studio) et écouter les `WM_SYSCOLORCHANGE` et `WM_THEMECHANGED` messages.  
  
  
Pour accéder au service de couleur dans le code natif, vous devez effectuer un appel qui ressemble à ceci : 

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);    
```  

> **Remarque :** le `COLORREF` valeurs retournées par `GetVSSysColorEx()` contiennent simplement R, G, les composants B d’une couleur de thème. Si une entrée de thème utilise la transparence, la valeur de canal alpha est ignorée avant de retourner. Par conséquent, si la couleur de l’environnement d’intérêt doit être utilisé dans un endroit où le canal de transparence est importante, vous devez utiliser `IVsUIShell5.GetThemedColor` au lieu de `IVsUIShell2::GetVSSysColorEx`, comme décrit plus loin dans cette rubrique.  
  
##### <a name="from-managed-code"></a>À partir du code managé  
Il est assez simple d’accéder au service VSColor le code natif. Si vous travaillez dans le code managé, toutefois, déterminer comment utiliser le service peut être compliquée. Dans cette optique, Voici un extrait de code c# illustrant ce processus :  
  
```  
private void VSColorPaint(object sender, System.Windows.Forms.PaintEventArgs e)  
{  
    //getIVSUIShell2  
    IVsUIShell2 uiShell2 = Package.GetService(typeof(SVsUIShell)) as IVsUIShell2;  
    Debug.Assert (uiShell2 != null, "failed to get IVsUIShell2");  
  
    if (uiShell2 != null)  
    {  
        //get the COLORREF structure  
        uint win32Color;  
        uiShell.GetVSSysColorEx(VSSYSCOLOREX.VSCOLOR_SMARTTAG_HOVER_FILL, out win32Color);  
  
        //translate it to a managed Color structure  
        Color myColor = ColorTranslator.FromWin32((int)win32Color);  
        //use it  
        e.Graphics.FillRectangle(new SolidBrush(myColor), 0, 0, 100, 100);  
    }  
}  
```  
  
Si vous travaillez dans Visual Basic, utilisez :  
  
```  
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)  
```  
  
##### <a name="from-wpf-ui"></a>À partir de l’interface utilisateur WPF  
Vous pouvez lier aux couleurs de Visual Studio via des valeurs exportées dans l’Application `ResourceDictionary`. Voici un exemple d’utilisation des ressources à partir de la table des couleurs, ainsi que la liaison aux données de police d’environnement en XAML.  
  
```  
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
Pour le code managé, bibliothèque de Managed Package Framework de l’interpréteur de commandes (`Microsoft.VisualStudio.Shell.12.0.dll`) contient deux classes d’assistance facilitant l’utilisation de couleurs de thème.  
  
Les méthodes d’assistance dans le `Microsoft.VisualStudio.Shell.VsColors` classe MPF incluent `GetThemedGDIColor()` et `GetThemedWPFColor()`. Ces méthodes d’assistance retournent la valeur de couleur d’une entrée de thème en tant que `System.Drawing.Color` ou `System.Windows.Media.Color`, à utiliser dans les Windows Forms ou WPF UI.  
  
```  
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
  
La classe peut également être utilisée pour obtenir les identificateurs VSCOLOR d’une clé de ressource de couleur WPF spécifique, ou vice versa.  
  
```  
public static string GetColorBaseKey(int vsSysColor);  
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);  
```  
  
Les méthodes de `VsColors` classe interroger le service de VSColor pour retourner la valeur de couleur à chaque fois qu’ils sont appelés. Pour obtenir une valeur de couleur en tant que `System.Drawing.Color`, une alternative avec de meilleures performances est au lieu d’utiliser les méthodes de la `Microsoft.VisualStudio.PlatformUI.VSThemeColor` (classe), qui met en cache les valeurs de couleur obtenues auprès du service VSColor. La classe s’abonne en interne aux événements de messages de diffusion de shell et ignore la valeur mise en cache lorsque survient un événement de changement de thème. En outre, la classe fournit un. Nom convivial de la NET l’événement pour s’abonner aux modifications de thème. Utiliser le `ThemeChanged` événement pour ajouter un nouveau gestionnaire et utiliser le `GetThemedColor()` méthode pour obtenir les couleurs des valeurs pour le `ThemeResourceKeys` d’intérêt. Un exemple de code pourrait ressembler à ceci :  
  
```  
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
  
##  <a name="BKMK_ChoosingHighContrastColors"></a>Choix de couleurs à contraste élevé  
  
### <a name="overview"></a>Vue d'ensemble  
Windows utilise plusieurs thèmes au niveau du système à contraste élevé qui augmentent le contraste de couleur du texte, les arrière-plans et les images, rendre les éléments apparaissent plus distincte à l’écran. Pour des raisons d’accessibilité, il est important que les éléments d’interface de Visual Studio répondent correctement quand les utilisateurs basculent vers un thème à contraste élevé.  
  
Seule une poignée des couleurs système peut servir de thèmes de contraste élevé. Lorsque vous choisissez votre système de noms de couleurs, n’oubliez pas les conseils suivants :  
  
1.  **Choisissez les couleurs système qui ont la même signification sémantique** que l’élément qui vous sont coloration. Par exemple, si vous choisissez une couleur de contraste élevé pour le texte dans une fenêtre, utilisez WindowText et ControlText pas.  
  
2.  **Choisissez les paires de premier plan/arrière-plan** ensemble ou vous ne serez pas certain que votre choix de couleurs fonctionne dans tous les thèmes de contraste élevé.  
  
3.  **Déterminer quelles parties de votre interface utilisateur sont les plus importants et assurez-vous que des zones de contenu ressortent.** Vous allez perdre beaucoup de détail des différences subtiles en teinte de couleur normalement établit une distinction, donc l’utilisation de couleurs de bordure fort est courant de définir des zones de contenu, car il n’existe des variantes d’aucune couleur pour les différentes zones de contenu.  
  
### <a name="system-color-set"></a>Jeu de couleurs système  
La table de [Blog de l’équipe WPF : SystemColors référence](http://blogs.msdn.com/b/wpf/archive/2010/11/30/systemcolors-reference.aspx) indique l’ensemble complet des noms de couleurs système et les teintes correspondantes affichées dans chaque thème.  
  
Lorsque cette application d’un jeu de couleurs à votre interface utilisateur, limité *il est probable que vous allez perdre les détails subtiles qui étaient présents dans les thèmes « normales »*. Voici un exemple d’interface utilisateur avec des couleurs gris subtiles qui sont utilisés pour distinguer les zones dans une fenêtre outil. Associées à la même fenêtre affichée en mode de contraste élevé, vous pouvez voir que tous les arrières-plans sont la même teinte et les bordures de ces zones sont indiquées par bordure uniquement :  
  
![Exemple de détails comment subtiles sont perdues en contraste élevé](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303-a_PropertiesWindow")<br />Exemple de détails comment subtiles sont perdues en contraste élevé
  
#### <a name="choosing-text-colors-in-an-editor"></a>Choix de couleurs de texte dans un éditeur  
Couleur de texte est utilisé dans un éditeur ou sur une aire de conception pour indiquer le sens, comme autoriser pour faciliter l’identification des groupes d’éléments similaires. Toutefois, dans un thème à contraste élevé, vous n’avez pas la possibilité de faire la distinction entre plus de trois couleurs de texte. WindowText, GrayText et HotTrackText sont disponibles sur les surfaces WindowBackground de couleurs uniquement. Étant donné que vous ne pouvez pas utiliser plus de trois couleurs, choisissez soigneusement les différences les plus importantes que vous souhaitez afficher en mode de contraste élevé.  
  
Teintes pour chacun des noms de jeton autorisés sur une surface de l’éditeur, telles qu’elles apparaissent dans chaque thème à contraste élevé :  
  
![Comparaison de l’éditeur de contraste élevé](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303-b_HCEditorComparison")<br />Comparaison de l'éditeur de contraste élevé
  
Exemples de la surface de l’éditeur dans le thème bleu :  
  
![Éditeur dans le thème bleu](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303-c_EditorBlue")<br />Éditeur dans le thème bleu
  
![Éditeur dans le thème à contraste élevé, #1](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303-d_EditorHC1")<br />Éditeur dans le thème à contraste élevé, #1
  
### <a name="usage-patterns"></a>Modèles d’utilisation
Plusieurs éléments d’interface utilisateur communes ont déjà des couleurs à contraste élevé définis. Vous pouvez référencer ces modèles d’utilisation lors du choix de votre propre système de noms de couleur, afin que vos éléments d’interface utilisateur sont cohérents avec des composants similaires.  
  
| Couleur du système | Utilisation |
| --- | --- |
| LégendeActive | -Active IDE et les glyphes de bouton de fenêtre rafted sur pointage et appuyez sur<br />-Arrière-plan de la barre de titre pour l’IDE et rafted windows<br />-Arrière-plan de la barre par défaut état |
| TexteLégendeActive | -Active IDE et rafted fenêtres au premier plan barre de titre (texte et des glyphes)<br />-En arrière-plan et de la bordure des boutons de la fenêtre active de pointage et appuyez sur |
| Contrôle | -Zone de liste déroulante, liste déroulante, puis recherchez contrôlent par défaut et désactivé en arrière-plan, y compris le bouton de liste déroulante<br />-Ancrer l’arrière-plan du bouton cible<br />: Arrière-plan de la barre de commandes<br />-Arrière-plan de la fenêtre outil |
| ControlDark | -Arrière-plan de IDE<br />-Les séparateurs de barre menu et commande<br />: Bordure de la barre de commandes<br />-Menu occulte<br />-Outil d’onglet par défaut et pointage de bordure de la fenêtre et séparateur<br />-Document bien en arrière-plan de bouton de dépassement de capacité<br />-Bordure de glyphe dock cible |
| ContrôleFoncéFoncé |-Fenêtre de l’onglet document sélectionné inactif |
| ContrôleClair |-Bordure d’onglet masquage automatique<br />-Bordure de liste de zone et de liste déroulante liste déroulante<br />-Ancrer en arrière-plan de la cible et la bordure |
| ControlLightLight | -Bordure de provisoire sélectionné, avec focus |
| ControlText | -Glyphe de liste de zone et de liste déroulante liste déroulante<br />-Texte de l’onglet outil fenêtre désactivée |
| GrayText |-Zone de liste déroulante et de liste déroulante désactivée bordure, le glyphe de la liste déroulante, le texte et le texte d’élément de menu<br />-Texte du menu désactivé<br />-Texte d’en-tête 'options de recherche' recherche contrôle<br />-Séparateur de section de contrôle de recherche |
| Surligner | -Toutes les pointage et appuyés arrière-plans et les bordures, à l’exception de liste déroulante bouton déroulant documents et arrière-plan et de dépassement de capacité bouton bordure de la zone<br />-Arrière-plans de l’élément sélectionné |
| HighlightText | -Toutes les pointage et premiers de plans enfoncés (texte et des glyphes)<br />-Outil focus fenêtre et document onglet fenêtre contrôle au premier plan<br />-Bordure de barre de titre de fenêtre outil ayant le focus<br />-Au premier plan de l’onglet provisoire ciblé et sélectionné<br />-Bordure de bouton de dépassement de capacité bien document sur pointage et appuyez sur<br />-Bordure d’icône sélectionné|
| HotTrack | -Défilement de la barre d’arrière-plan du curseur de défilement et appuyez sur la bordure<br />-Barre de défilement glyphe de flèche sur Presse |
| InactiveCaption | -Inactive IDE et les glyphes de bouton de fenêtre rafted pointage<br />-Arrière-plan de la barre de titre pour l’IDE et rafted windows<br />-Arrière-plan de contrôle de recherche désactivé |
| InactiveCaptionText | -Inactive IDE et au premier plan de barre de titre windows rafted (texte et des glyphes)<br />-Arrière-plan des boutons de fenêtre inactive et de bordure pointage<br />-Bordure et arrière-plan de bouton de fenêtre outil inactif<br />-Au premier plan du contrôle de recherche désactivé |
| Menu | -Arrière-plan du menu liste déroulante<br />-Arrière-plan de case à cocher activés et désactivés |
| MenuText | -Bordure du menu liste déroulante<br />-Coches<br />-Les glyphes menu<br />-Texte du menu liste déroulante<br />-Bordure d’icône sélectionné |  
| Scrollbar | -Faire défiler barre et arrière-plan de la flèche, tous les États de la barre de défilement |
| Fenêtre | Masquage automatique en arrière-plan d’onglet<br />-Menu barre et d’arrière-plan de l’interface de commande<br />-Arrière-plan de la fenêtre du document inactif ou désélectionné onglet et la bordure de document, pour les onglets ouverts et provisoires<br />-Arrière-plan de barre de titre de fenêtre outil inactif<br />-Outil fenêtre onglet en arrière-plan, à la fois sélectionnés et |
| Cadre de fenêtre | -Bordure de IDE |
| WindowText | -Premier plan d’onglet masquage automatique<br />-Premier plan onglet de fenêtre outil sélectionné<br />-Onglet de fenêtre de document inactif et au premier plan inactif ou désélectionné onglet provisoire<br />-Arborescence de premier plan par défaut de vue et du curseur sur le glyphe non sélectionnée<br />-Fenêtre outil sélectionné onglet Bordure<br />-Barre de défilement en arrière-plan de curseur de défilement, de bordure et de glyphe |
  
##  <a name="BKMK_ExposingColorsForEndUsers"></a>Exposition de couleurs pour les utilisateurs finaux  
  
### <a name="overview"></a>Vue d'ensemble  
Parfois, que vous souhaitez autoriser l’utilisateur final de personnaliser votre interface utilisateur, comme lorsque vous créez un éditeur de code ou l’aire de conception. La plus courante pour ce faire consiste à l’aide de la **outils &gt; Options** boîte de dialogue. Sauf si vous avez hautement spécialisé l’interface utilisateur qui nécessite des contrôles spéciaux, le moyen le plus simple pour présenter la personnalisation s’effectue via le **polices et couleurs** page au sein de la **environnement** section de la boîte de dialogue. Pour chaque élément que vous exposez pour la personnalisation, l’utilisateur peut choisir de modifier la couleur de premier plan, couleur d’arrière-plan ou les deux.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Création d’un VSPackage pour vos couleurs personnalisables  
Un VSPackage peut contrôler les polices et couleurs via des catégories personnalisées et afficher les éléments sur la page de propriétés de polices et couleurs. Lorsque vous utilisez ce mécanisme, VSPackages doivent implémenter le [IVsFontAndColorDefaultsProvider](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.aspx) interface et ses interfaces associées.  
  
En principe, ce mécanisme peut être utilisé pour modifier tous les éléments d’affichage existants et les catégories qui les contiennent. Toutefois, ne doit pas être utilisé pour modifier la catégorie de l’éditeur de texte ou de ses éléments d’affichage. Pour plus d’informations sur la catégorie de l’éditeur de texte, consultez [vue d’ensemble de la couleur et de police](https://msdn.microsoft.com/en-us/library/bb165065.aspx).  
  
Pour implémenter des catégories personnalisées ou afficher les éléments, un VSPackage doit :  
  
-   **Créez ou identifiez les catégories dans le Registre.** Implémentation de l’IDE de le **polices et couleurs** page de propriétés utilise ces informations pour interroger correctement pour le service de prise en charge d’une catégorie donnée.  
  
-   **Créez ou identifiez les groupes dans le Registre (facultatif).** Il peut être utile de définir un groupe, qui représente l’union de deux ou plusieurs catégories. Si un groupe est défini, l’IDE fusionne les sous-catégories automatiquement et distribue les éléments affichés dans le groupe.  
  
-   **Implémenter la prise en charge de l’IDE.**  
  
-   **Gérer les modifications de police et la couleur.**  
  
#### <a name="to-create-or-identify-categories"></a>Pour créer ou identifier des catégories  
Construire un type spécial de l’entrée de Registre de catégorie sous `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` où `<Category>` est le nom non localisé de la catégorie.
  
Remplir le Registre avec deux valeurs :  

| Nom | Type | Données | Description |
| --- | --- | --- | --- |
| Catégorie | REG_SZ | GUID | Un GUID est créé pour identifier la catégorie |
| Package | REG_SZ | GUID | Le GUID du service VSPackage qui prend en charge de la catégorie |
  
 Le service spécifié dans le Registre doit fournir une implémentation de [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) pour la catégorie correspondante.  
  
#### <a name="to-create-or-identify-groups"></a>Pour créer ou d’identifier les groupes  
Construire un type spécial de l’entrée de Registre de catégorie sous `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` où `<group>` est le nom non localisé du groupe.  
  
Remplir le Registre avec deux valeurs :

| Nom | Type | Données | Description |
|--- | --- | --- | --- |
| Catégorie | REG_SZ | GUID | Un GUID est créé pour identifier la catégorie |
| Package | REG_SZ | GUID | Le GUID du service VSPackage qui prend en charge de la catégorie |
  
Le service spécifié dans le Registre doit fournir une implémentation de `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` pour le groupe correspondant.

![Implémentation de l’interface IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "a_FontAndColorGroup-0304")<br />Implémentation de`IVsFontAndColorGroup`
  
### <a name="to-implement-ide-support"></a>Pour implémenter la prise en charge IDE  
Implémentez [GetObject](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject.aspx), qui retourne un [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) interface ou un `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` à l’IDE pour chaque catégorie de l’interface ou le groupe de GUID fourni.  
  
Pour chaque catégorie, il prend en charge, un VSPackage implémente une instance distincte de la [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) interface.  
  
Les méthodes implémentées via [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) doit fournir l’IDE avec :  
  
-   Listes d’éléments affichés dans la catégorie  
  
-   Noms localisables pour les éléments d’affichage  
  
-   Afficher des informations pour chaque membre de la catégorie  
  
 > **Remarque :** chaque catégorie doit contenir au moins un élément d’affichage.
  
L’IDE utilise le `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` interface pour définir une union de plusieurs catégories.

Son implémentation fournit l’IDE avec :

-   Une liste des catégories qui composent un groupe donné  
  
-   Accès aux instances du [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) prise en charge de chaque catégorie dans le groupe  
  
-   Noms de groupe localisable  
  
#### <a name="updating-the-ide"></a>Mise à jour de l’IDE  
L’IDE met en cache les informations sur les paramètres de police et la couleur. Par conséquent, après toute modification de la configuration de la police de l’IDE et la couleur, s’assurer que le cache est à jour est une meilleure pratique.  
  
Mise à jour le cache s’effectue via le [IvsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) interface et peut être effectuées globalement ou seulement sur sélectionnées.  
  
### <a name="handling-font-and-color-changes"></a>Gestion des modifications de police et de couleur  
Pour prendre en charge correctement la colorisation de texte affichant un VSPackage, le service de colorisation prenant en charge le VSPackage doit répondre aux modifications initiée par l’utilisateur via la page de propriétés de polices et couleurs.  
  
Pour ce faire, un VSPackage doit :  
  
-   **gérer les événements générés par l’IDE** en implémentant la [IVsFontAndColorEvents](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.aspx) interface. L’IDE appelle la méthode appropriée après les modifications des utilisateurs de la page polices et couleurs. Par exemple, il appelle la [OnFontChanged](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged.aspx) méthode si une nouvelle police est sélectionnée.  
  
 **OR**  
  
-   **interroger l’IDE pour les modifications**. Cela est possible via l’objet implémentés par le système [IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) interface. Bien que principalement pour la prise en charge de la persistance, la [GetItem](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem.aspx) méthode permettre obtenir des informations de police et la couleur pour afficher les éléments. Pour plus d’informations sur les paramètres de police et couleur, consultez l’article MSDN [l’accès à stockées paramètres de police et couleur](https://msdn.microsoft.com/en-us/library/bb166382.aspx).  
  
> **Remarque :** pour vous assurer que les résultats d’interrogation sont corrects, utilisez le [IVsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) interface pour déterminer si un vidage du cache et la mise à jour sont nécessaires avant d’appeler les méthodes de récupération de la [ IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) interface.
  
#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>L’inscription de la police et couleur catégorie sans avoir à implémenter des interfaces  
L’exemple de code suivant montre comment inscrire la police personnalisée et la catégorie de couleur sans avoir à implémenter des interfaces :  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]  
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"  
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"  
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"  
  
    "NameID"=dword:00000064  
```  

Pour cet exemple de code :   
-   `"NameID"`= l’ID de ressource du nom de catégorie localisée dans votre package.
-   `"ToolWindowPackage"`= GUID du package
-   `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"`est juste un exemple et la valeur réelle peut être un GUID fourni par l’implémenteur.  
  
### <a name="set-the-font-and-color-property-category-guid"></a>Définir la police et couleur propriété GUID de catégorie  
L’exemple de code ci-dessous montre comment définir des GUID de catégorie.  
  
```  
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
