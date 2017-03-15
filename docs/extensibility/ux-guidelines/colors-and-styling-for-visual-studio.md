---
title: "Couleurs et styles pour Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# Couleurs et styles pour Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

## À l'aide de couleurs dans Visual Studio  
 Dans Visual Studio, la couleur est utilisée principalement comme outil de communication, pas comme décoration. Utiliser la couleur au minimum et réserver aux situations où vous souhaitez :  
  
-   Communiquer la signification ou l'affiliation \(par exemple, les modificateurs de plateforme ou langue\)  
  
-   Attirer votre attention \(par exemple, en indiquant un changement d'état\)  
  
-   Améliorer la lisibilité et de fournir des points de repère pour naviguer dans l'interface utilisateur  
  
-   Opportunité d'augmentation  
  
 Il existe plusieurs options pour attribuer des couleurs aux éléments d'interface utilisateur dans Visual Studio. Il peut parfois être difficile de figure en option que vous êtes censé pour utiliser, ou comment l'utiliser correctement. Cette rubrique vous aidera à :  
  
1.  Comprendre les différents services et les systèmes utilisés pour définir des couleurs dans Visual Studio.  
  
2.  Sélectionnez l'option appropriée pour un élément donné.  
  
3.  Utiliser correctement l'option que vous avez choisi.  
  
 **IMPORTANT :** jamais coder en dur hex, RVB ou les couleurs système à vos éléments d'interface utilisateur. L'utilisation des services permet de souplesse dans le réglage Teinte. En outre, vous sans que le service, seront pas en mesure de tirer parti des fonctionnalités de commutation de thème de le [Le Service VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).  
  
### Méthodes d'attribution de couleurs à des éléments d'interface de Visual Studio  
 Choisissez la méthode mieux adaptée à vos éléments d'interface utilisateur.  
  
|Votre interface utilisateur|Méthode|Quelles sont\-elles ?|  
|---------------------------------|-------------|---------------------------|  
|Vous avez incorporé ou boîtes de dialogue autonome.|**Couleurs système**|Noms de système qui permettent au système d'exploitation définir la couleur et l'apparence des éléments de l'interface utilisateur, tels que des contrôles de boîte de dialogue commune.|  
|Vous disposez d'interface utilisateur personnalisée que vous souhaitez être cohérente de l'environnement Visual Studio et les éléments d'interface utilisateur qui correspondent à la catégorie et la signification sémantique des jetons partagés.|**Couleurs courantes partagés**|Noms de jeton de couleurs prédéfinies existant pour les éléments d'interface utilisateur spécifiques|  
|Vous disposez d'une fonctionnalité ou un groupe de fonctionnalités et il n'existe aucune couleur partagé pour les éléments similaires.|**Couleurs personnalisées**|Noms de jeton de couleurs qui sont spécifiques à une zone et pas destiné à être partagé avec une autre interface utilisateur|  
|Vous souhaitez autoriser l'utilisateur final de personnaliser l'interface utilisateur ou du contenu \(par exemple, pour les éditeurs de texte ou les fenêtres du concepteur spécialisés\).|**Personnalisation de l'utilisateur final**<br /><br /> **\(Outils \> boîte de dialogue Options\)**|Les paramètres définis dans la page « Polices et couleurs » de la **Outils \> Options** boîte de dialogue ou une page spécialisée spécifique à une fonction de l'interface utilisateur.|  
|Vous disposez de l'interface utilisateur qui est créé au format HTML.|**Daytona**|Permet à l'interface utilisateur créé dans le code HTML pour accéder au service de couleur et la police.|  
  
### Thèmes Visual Studio  
 Visual Studio propose trois thèmes de couleurs différentes : bleu, sombre et clair. Il détecte également le mode de contraste élevé est un thème de couleur du système conçu pour l'accessibilité.  
  
 Les utilisateurs sont invités à sélectionner un thème lors de leur première utilisation de Visual Studio et sont en mesure de changer de thème ultérieurement en accédant à **Outils \> Options \> environnement \> Général** et en choisissant un thème dans le menu déroulant « thème ».  
  
 Utilisateurs peuvent également utiliser le panneau de configuration pour changer leurs systèmes ensemble dans une de plusieurs thèmes à contraste élevé. Si un utilisateur sélectionne un thème à contraste élevé, puis le sélecteur de thème de couleur Visual Studio n'affecte plus les couleurs dans Visual Studio, bien que toutes les modifications de thème sont enregistrées au cas où l'utilisateur quitte le mode de contraste élevé. Pour plus d'informations sur le mode de contraste élevé, consultez [Choix de couleurs à contraste élevé](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).  
  
### Le service VSColor  
 Visual Studio fournit un service de couleur d'environnement, appelé service VSColor, ce qui vous permet de lier les valeurs de couleur de vos éléments d'interface utilisateur à une entrée nommée contenant les valeurs de couleur pour chaque thème de Visual Studio. Cela garantit que vos couleurs change automatiquement pour refléter l'actuel sélectionné par l'utilisateur système ou thème mode de contraste élevé. Utilisation du service signifie que l'implémentation de toutes les modifications de couleur de thème liées est gérée dans un seul emplacement, et si vous utilisez des couleurs courantes partagés à partir du service, votre interface utilisateur reflètent automatiquement les nouveaux thèmes dans les futures versions de Visual Studio.  
  
### Implémentation  
 Le code source de Visual Studio inclut plusieurs fichiers de définition de package qui contiennent des listes de noms de jeton et les valeurs de couleur respectifs pour chaque thème. Le service de couleur lit le VSColors définis dans ces fichiers de définition de package. Ces couleurs sont référencés dans le balisage XAML ou dans le code et ensuite chargés par le biais du **IVsUIShell5.GetThemedColor** méthode ou un mappage DynamicResource.  
  
### Couleurs système  
 Contrôles communs pour référencer les couleurs système par défaut. Si vous souhaitez que votre interface utilisateur à utiliser des couleurs système, tels que lorsque vous créez une boîte de dialogue intégré ou autonome, vous n'avez rien à faire.  
  
### Couleurs courantes partagés dans le service VSColor  
 Vos éléments d'interface doivent refléter l'environnement global de Visual Studio. En réutilisant les couleurs partagées communes qui sont appropriés pour le composant de l'interface utilisateur que vous concevez, vous assurer que votre interface est compatible avec d'autres interfaces de Visual Studio, et que vos couleurs met automatiquement à jour lorsque les thèmes sont ajoutés ou mis à jour.  
  
 Avant d'utiliser des couleurs courantes partagés, assurez\-vous que vous comprenez comment les utiliser correctement. Utilisation incorrecte de couleurs partagées communes peut entraîner une expérience confuse, frustrante ou incohérente pour vos utilisateurs.  
  
### Couleurs personnalisables par l'utilisateur  
 Voir : [Exposition des couleurs pour les utilisateurs finaux](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)  
  
 Parfois, vous souhaiterez autoriser l'utilisateur final de personnaliser l'interface utilisateur, tels que lorsque vous créez un éditeur de code ou l'aire de conception. Composants d'interface utilisateur personnalisables sont trouvent dans le **polices et couleurs** section de la **Outils \> Options** boîte de dialogue, où les utilisateurs peuvent choisir de modifier la couleur de premier plan, couleur d'arrière\-plan ou les deux.  
  
 ![Tools &#62; Options dialog in Visual Studio](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301\-a\_ToolsOptionsDialog")  
  
 **Outils \> boîte de dialogue Options**  
  
### Couleurs de l'interface utilisateur Web  
 Il est plus commun pour créer des composants de l'interface utilisateur à l'aide de HTML afin qu'ils peuvent être utilisés dans Visual Studio Online et dans Visual Studio. L'interface utilisateur écrite en langage HTML doit toujours utiliser le service VSColor lors de l'exécution à l'intérieur de l'environnement Visual Studio. Pour plus d'informations sur Daytona et comment l'utiliser, consultez [Daytona et l'interface utilisateur web](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_DaytonaAndWebUI).  
  
##  <a name="BKMK_TheVSColorService"></a> Le Service VSColor  
 Visual Studio fournit un service de couleur d'environnement, également appelé le service VSColor ou le service de couleur du shell. Ce service vous permet de lier les valeurs de couleur de vos éléments d'interface utilisateur à un jeu contenant des couleurs pour chaque thème de couleurs de nom\-valeur. Le service de VSColor doit être utilisé pour tous les éléments d'interface utilisateur, afin que les couleurs changent pour refléter le thème sélectionné par l'utilisateur actuel et automatiquement afin que l'interface utilisateur liée au service environnement couleur seront intègrent nouveaux thèmes dans les futures versions de Visual Studio.  
  
### Comment fonctionne le service  
 Le service de couleur environnement lit que vscolors défini dans le .pkgdef pour le composant de l'interface utilisateur. Ces VSColors puis référencés dans le balisage XAML ou de code et sont chargés par le biais du **IVsUIShell5.GetThemedColor** ou un mappage DynamicResource.  
  
 ![Environment color service architecture](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302\-a\_EnvironmentColorServiceArchitecture")  
  
 **Architecture de service de couleur d'environnement**  
  
### L'accès au service  
 Il existe différentes méthodes pour le service VSColor, selon le type de couleur jetons vous utilisez l'accès et le type de code que vous avez.  
  
#### Couleurs de l'environnement prédéfinis  
  
##### À partir du code natif  
 Le shell fournit un service qui permet d'accéder à la COLORREF des couleurs. L'interface de service\/est :  
  
```  
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)  
```  
  
 Dans le fichier VSShell80.idl, l'énumération **\_\_VSSYSCOLOREX** a des constantes de couleur de shell. Utilisation, réussissent et que la valeur de l'index de l'une des valeurs de la \_\_VSSYSCOLOREX enum documentées dans MSDN ou un index normal numéro que le système Windows API, **GetSysColor**, accepte. Cette opération récupère la valeur RVB de la couleur qui doit être utilisée dans le deuxième paramètre.  
  
 Si vous stockez un stylet ou un pinceau avec une couleur, vous devez AdviseBroadcastMessages \(sur l'interpréteur de commandes de Visual Studio\) et écoutez les messages WM\_SYSCOLORCHANGE et WM\_THEMECHANGED.  
  
```  
// To access the color service in native code, you'll make a call that resembles this: pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);  
  
```  
  
 **Remarque :** valeurs COLORREF le retournées par **GetVSSysColorEx\(\)** contiennent simplement R, G, composants B d'une couleur de thème. Si une entrée de thème utilise la transparence, la valeur du canal alpha est ignorée avant de retourner. Par conséquent, si la couleur de l'environnement d'intérêt doit être utilisée dans un endroit où le canal de transparence est importante, vous devez utiliser IVsUIShell5.GetThemedColor plutôt que IVsUIShell2::GetVSSysColorEx, comme décrit plus loin dans cette rubrique.  
  
##### À partir de code managé  
 Accès au service de VSColor le code natif est assez simple. Si vous travaillez dans le code managé, toutefois, déterminer comment utiliser le service peut être difficile. Dans cette optique, Voici un extrait de code c\# illustrant ce processus :  
  
```  
private void VSColorPaint(object sender, System.Windows.Forms.PaintEventArgs e) { //getIVSUIShell2 IVsUIShell2 uiShell2 = Package.GetService(typeof(SVsUIShell)) as IVsUIShell2; Debug.Assert (uiShell2 != null, "failed to get IVsUIShell2"); if (uiShell2 != null) { //get the COLORREF structure uint win32Color; uiShell.GetVSSysColorEx(VSSYSCOLOREX.VSCOLOR_SMARTTAG_HOVER_FILL, out win32Color); //translate it to a managed Color structure Color myColor = ColorTranslator.FromWin32((int)win32Color); //use it e.Graphics.FillRectangle(new SolidBrush(myColor), 0, 0, 100, 100); } }  
```  
  
 Si vous travaillez dans Visual Basic, utilisez :  
  
```  
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)  
```  
  
##### À partir de l'interface utilisateur WPF  
 Vous pouvez lier aux couleurs de Visual Studio via des valeurs exportées dans un ResourceDictionary de l'Application. Voici un exemple d'utilisation des ressources à partir de la table des couleurs, ainsi que la liaison aux données de police d'environnement en XAML.  
  
```  
<Style TargetType="{x:Type Button}"> <Setter Property="TextBlock.FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" /> <Setter Property="TextBlock.FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" /> <Setter Property="Background" Value="{DynamicResource VsBrush.EnvironmentBackgroundGradient}" /> </Style>  
```  
  
#### Classes d'assistance et des méthodes pour le code managé  
 Pour le code managé, bibliothèque de Managed Package Framework du shell \(Microsoft.VisualStudio.Shell.12.0.dll\) contient deux classes d'assistance facilitant l'utilisation des couleurs de thème.  
  
 Les méthodes d'assistance dans le **Microsoft.VisualStudio.Shell.VsColors** dans MPF inclure **GetThemedGDIColor\(\)** et **GetThemedWPFColor\(\)**. Ces méthodes d'assistance retournent la valeur de couleur d'une entrée de thème System.Drawing.Color ou System.Windows.Media.Color, utilisable dans WinForms ou WPF UI.  
  
```  
IVsUIShell5 shell5; Button button = new Button(); button.BackColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemBrushKey); button.ForeColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemTextBrushKey); /// <summary> /// Gets a System.Drawing.Color value from the current theme for the given color key. /// </summary> /// <param name="vsUIShell">The IVsUIShell5 service, used to get the color's value.</param> /// <param name="themeResourceKey">The key to find the color for.</param> /// <returns>The current theme's value of the named color.</returns> public static System.Drawing.Color GetThemedGDIColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey) { Validate.IsNotNull(vsUIShell, "vsUIShell"); Validate.IsNotNull(themeResourceKey, "themeResourceKey"); byte[] colorComponents = GetThemedColorRgba(vsUIShell, themeResourceKey); // Note: The Win32 color we get back from IVsUIShell5.GetThemedColor is ABGR return System.Drawing.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]); } private static byte[] GetThemedColorRgba(IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey) { Guid category = themeResourceKey.Category; __THEMEDCOLORTYPE colorType = __THEMEDCOLORTYPE.TCT_Foreground if (themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundColor || themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundBrush) { colorType = __THEMEDCOLORTYPE.TCT_Background; } // This call will throw an exception if the color is not found uint rgbaColor = vsUIShell.GetThemedColor(ref category, themeResourceKey.Name, (uint)colorType); return BitConverter.GetBytes(rgbaColor); } public static System.Windows.Media.Color GetThemedWPFColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey) { Validate.IsNotNull(vsUIShell, "vsUIShell"); Validate.IsNotNull(themeResourceKey, "themeResourceKey"); byte[] colorComponents = GetThemedColorComponents(vsUIShell, themeResourceKey); return System.Windows.Media.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]); }  
  
```  
  
 La classe peut également être utilisée pour obtenir une clé de ressource de couleur WPF donnée, identificateurs VSCOLOR ou vice versa.  
  
```  
public static string GetColorBaseKey(int vsSysColor); public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);  
```  
  
 Les méthodes de **VsColors** classe interroger le service de VSColor pour renvoyer la valeur de couleur à chaque fois qu'ils sont appelés. Pour obtenir une valeur de couleur en tant que **System.Drawing.Color**, une alternative avec de meilleures performances consiste à utiliser à la place les méthodes de la **Microsoft.VisualStudio.PlatformUI.VSThemeColor** \(classe\), qui met en cache les valeurs de couleur obtenues auprès du service VSColor. La classe s'abonne en interne à des événements de messages de diffusion de shell et ignore la valeur mise en cache lorsque survient un événement de modification du thème. En outre, la classe fournit un. Événement NET conviviale pour s'abonner aux modifications de thème. Utiliser le **ThemeChanged** événement pour ajouter un nouveau gestionnaire et utiliser le **GetThemedColor\(\)** méthode pour obtenir la couleur de valeurs pour le **ThemeResourceKeys** d'intérêt. Un exemple de code pourrait ressembler à ceci :  
  
```  
public MyWindowPanel() { InitializeComponent(); // Subscribe to theme changes events so we can refresh the colors VSColorTheme.ThemeChanged += VSColorTheme_ThemeChanged; RefreshColors(); } private void VSColorTheme_ThemeChanged(ThemeChangedEventArgs e) { RefreshColors(); // Also post a message to all the children so they can apply the current theme appropriately foreach (System.Windows.Forms.Control child in this.Controls) { NativeMethods.SendMessage(child.Handle, e.Message, IntPtr.Zero, IntPtr.Zero); } } private void RefreshColors() { this.BackColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowBackgroundColorKey); this.ForeColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowTextColorKey); } protected override void Dispose(bool disposing) { if (disposing) { VSColorTheme.ThemeChanged -= this.VSColorTheme_ThemeChanged; base.Dispose(disposing);} }  
```  
  
##  <a name="BKMK_ChoosingHighContrastColors"></a> Choix de couleurs à contraste élevé  
  
### Vue d'ensemble  
 Windows utilise plusieurs thèmes au niveau du système à contraste élevé qui augmentent le contraste des couleurs du texte, les arrière\-plans et les images, rendre les éléments apparaissent plus distincte à l'écran. Pour des raisons d'accessibilité, il est important que les éléments de l'interface Visual Studio répondent correctement lorsque les utilisateurs basculent vers un thème à contraste élevé.  
  
 Seule une poignée des couleurs système peut servir de thèmes à contraste élevé. Lorsque vous choisissez votre système de noms de couleurs, n'oubliez pas les conseils suivants :  
  
1.  **Choisir les couleurs système qui ont la même signification sémantique** que l'élément qui vous sont coloration. Par exemple, si vous choisissez une couleur de contraste élevé pour le texte dans une fenêtre, utilisez WindowText et ControlText pas.  
  
2.  **Choisir des paires de premier plan\/arrière\-plan** ensemble ou vous ne serez pas certain que votre choix de couleurs fonctionne dans tous les thèmes de contraste élevé.  
  
3.  **Déterminer quelles parties de l'interface utilisateur sont les plus importants et assurez\-vous que les zones de contenu ressortent.** Vous allez perdre beaucoup de détails qui seraient normalement distinguer des différences subtiles dans la teinte de la couleur, par conséquent, l'utilisation des couleurs de bordure fort est courant de définir des zones de contenu, étant donné qu'aucun des variantes de couleur pour les différentes zones de contenu.  
  
### Jeu de couleurs système  
 La table de [Blog de l'équipe WPF : SystemColors référence](http://blogs.msdn.com/b/wpf/archive/2010/11/30/systemcolors-reference.aspx) indique l'ensemble complet des noms de couleurs système et les teintes correspondants affichés dans chaque thème.  
  
 Lorsque cette application d'un jeu de couleurs à votre interface utilisateur, limité *il est probable que vous perdrez détails subtils qui étaient présents dans les thèmes « normales »*. Voici un exemple d'interface utilisateur avec des couleurs gris subtiles qui sont utilisés pour distinguer les domaines au sein d'une fenêtre outil. Lorsqu'elle est combinée avec la même fenêtre affichée en mode de contraste élevé, vous pouvez voir que tous les arrière\-plans sont la même teinte et les bordures de ces zones sont indiquées par un seul bordure :  
  
 ![Properties window](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303\-a\_PropertiesWindow")  
  
 **Exemple de détails comment subtiles sont perdues en contraste élevé**  
  
#### Choix de couleurs de texte dans un éditeur  
 Couleur de texte est utilisé dans un éditeur ou sur une aire de conception pour indiquer le sens, par exemple pour autoriser pour faciliter l'identification des groupes d'éléments similaires. Toutefois, dans un thème à contraste élevé, vous n'avez pas la possibilité de faire la distinction entre plus de trois couleurs de texte. WindowText, GrayText et HotTrackText sont des couleurs uniquement disponibles sur les surfaces WindowBackground. Étant donné que vous ne pouvez pas utiliser plus de trois couleurs, choisissez soigneusement les différences les plus importantes que vous souhaitez afficher en mode de contraste élevé.  
  
 Teintes pour chacun des noms de jeton autorisées sur une surface de l'éditeur, telles qu'elles apparaissent dans chaque thème à contraste élevé :  
  
 ![High Contrast editor comparison](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303\-b\_HCEditorComparison")  
  
 **Comparaison de l'éditeur de contraste élevé**  
  
 Exemples de la surface de l'éditeur dans le thème bleu :  
  
 ![Editor in Blue theme](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303\-c\_EditorBlue")  
  
 **Éditeur dans le thème bleu**  
  
 ![Editor in High Contrast theme](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303\-d\_EditorHC1")  
  
 **Éditeur dans le thème à contraste élevé n ° 1**  
  
### Modèles d'utilisation  
 Plusieurs éléments d'interface utilisateur courants ont déjà définis des couleurs à contraste élevé. Vous pouvez référencer ces modèles d'utilisation lors du choix de votre propre système de noms de couleurs, afin que vos éléments d'interface utilisateur sont cohérents avec les composants similaires.  
  
|Couleur du système|Utilisation|  
|------------------------|-----------------|  
|ActiveCaption|-   IDE active et les glyphes de bouton de fenêtre rafted sur pointage et appuyez sur<br />-   Arrière\-plan de barre de titre pour IDE et rafted windows<br />-   Arrière\-plan de barre d'état par défaut|  
|ActiveCaptionText|-   IDE active et rafted fenêtres au premier plan barre de titre \(texte et des glyphes\)<br />-   Arrière\-plan et bordure des boutons de la fenêtre active de survol et appuyez sur|  
|Contrôle|-   Contrôlent de zone de liste déroulante, liste déroulante, puis recherchez par défaut et arrière\-plan désactivé, y compris le bouton de liste déroulante<br />-   Ancrer l'arrière\-plan du bouton cible<br />-   Arrière\-plan de barre de commandes<br />-   Arrière\-plan de la fenêtre outil|  
|ControlDark|-   Arrière\-plan de l'IDE<br />-   Séparateurs de barre de menus et de commandes<br />-   Bordure barre de commandes<br />-   Ombres de menu<br />-   Séparateur et fenêtre outil onglet par défaut et pointer bordure<br />-   Arrière\-plan de bouton de dépassement de capacité et de documents<br />-   Bordure de glyphe Dock cible|  
|ControlDarkDark|-   Fenêtre de l'onglet document sélectionné inactif|  
|ControlLight|-   Masquer automatiquement l'onglet Bordure<br />-   Zone de liste déroulante et de la bordure de la liste déroulante<br />-   Ancrage cible arrière\-plan et bordure|  
|ControlLightLight|-   Bordure provisoire sélectionné actif|  
|ControlText|-   Glyphe de la liste déroulante et de zone de liste déroulante<br />-   Texte de l'onglet outil fenêtre désactivée|  
|GrayText|-   Zone de liste déroulante et bordure désactivé liste déroulante, liste déroulante glyphe, texte et texte d'élément de menu<br />-   Texte du menu désactivé<br />-   Texte de l'en\-tête « options de recherche » contrôle recherche<br />-   Séparateur de section de contrôle de recherche|  
|Mettez en surbrillance|-   Tous les pointez et enfoncé arrière\-plans et des bordures, à l'exception de liste déroulante de zone de liste déroulante document et l'arrière\-plan du bouton et de dépassement de capacité bordure du bouton<br />-   Arrière\-plan de l'élément sélectionné|  
|HighlightText|-   Tous les survol et enfoncé colorier \(texte et des glyphes\)<br />-   Outil fenêtre et document onglet fenêtre contrôle au premier plan<br />-   Bordure de barre de titre de fenêtre outil<br />-   Premier plan sélectionné, focalisé, onglet provisoire<br />-   Bordure de bouton de dépassement de capacité et de document sur pointage et appuyez sur<br />-   Bordure de l'icône sélectionnée|  
|HotTrack|-   Arrière\-plan de curseur de barre de défilement et appuyez sur la bordure<br />-   Glyphe de flèche de barre de défilement sur Presse|  
|InactiveCaption|-   IDE inactive et les glyphes de bouton de fenêtre rafted pointage<br />-   Arrière\-plan de barre de titre pour IDE et rafted windows<br />-   Arrière\-plan de contrôle de recherche désactivé|  
|InactiveCaptionText|-   IDE inactif et au premier plan de barre de titre windows rafted \(texte et des glyphes\)<br />-   Arrière\-plan des boutons de fenêtre inactive et bordure pointage<br />-   Bordure et arrière\-plan de bouton de fenêtre outil inactif<br />-   Au premier plan du contrôle de recherche désactivé|  
|Menu|-   Arrière\-plan du menu déroulant<br />-   Arrière\-plan de coche activés et désactivés|  
|MenuText|-   Bordure du menu déroulant<br />-   Vérification de coche<br />-   Glyphes de menu<br />-   Texte du menu déroulant<br />-   Bordure de l'icône sélectionnée|  
|Barre de défilement|-   Barre de défilement et la barre de défilement flèche en arrière\-plan, tous les États|  
|Fenêtre|-   Masquer automatiquement l'arrière\-plan de l'onglet<br />-   Menu barre et de commandes en arrière\-plan de l'étagère<br />-   Inactif ou non sélectionné fenêtre onglet arrière\-plan et bordure d'un document, des onglets ouverts et provisoires<br />-   Arrière\-plan de barre de titre de fenêtre outil inactif<br />-   Fenêtre outil onglet arrière\-plan, à la fois sélectionnés et|  
|Cadre de fenêtre|-   Bordure de l'IDE|  
|WindowText|-   Premier plan d'onglet Masquer automatiquement<br />-   Premier plan onglet de fenêtre outil sélectionné<br />-   Onglet de fenêtre de document inactif et premier plan inactif ou désélectionné onglet provisoire<br />-   Premier plan de la vue arborescence et passez la souris sur le glyphe non sélectionné<br />-   Onglet sélectionné fenêtre outil bordure<br />-   Glyphe, la bordure et arrière\-plan de curseur de barre de défilement|  
  
##  <a name="BKMK_ExposingColorsForEndUsers"></a> Exposition des couleurs pour les utilisateurs finaux  
  
### Vue d'ensemble  
 Parfois, vous pouvez autoriser l'utilisateur final de personnaliser l'interface utilisateur, tels que lorsque vous créez un éditeur de code ou l'aire de conception. La méthode la plus courante pour ce faire consiste à utiliser le **Outils \> Options** boîte de dialogue. Sauf si vous avez extrêmement spécialisé qui requiert des contrôles spéciaux, le moyen le plus simple pour présenter la personnalisation consiste à utiliser le **polices et couleurs** page dans le **environnement** section de la boîte de dialogue. Pour chaque élément que vous exposez pour la personnalisation, l'utilisateur peut choisir de modifier la couleur de premier plan, couleur d'arrière\-plan ou les deux.  
  
### Création d'un VSPackage pour vos couleurs personnalisables  
 Un VSPackage peut contrôler les polices et couleurs grâce à des catégories personnalisées et d'afficher des éléments sur la page de propriétés de polices et couleurs. Lorsque vous utilisez ce mécanisme, VSPackages doit implémenter le [IVsFontAndColorDefaultsProvider](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.aspx) interface et ses interfaces associées.  
  
 En principe, ce mécanisme peut être utilisé pour modifier tous les éléments d'affichage existants et les catégories qui les contiennent. Toutefois, il ne doit pas utilisé pour modifier la catégorie de l'éditeur de texte ou de ses éléments d'affichage. Pour plus d'informations sur la catégorie de l'éditeur de texte, consultez [vue d'ensemble de la couleur et de police](https://msdn.microsoft.com/en-us/library/bb165065.aspx).  
  
 Pour implémenter des catégories personnalisées ou afficher les éléments, un VSPackage doit :  
  
-   **Créez ou identifiez les catégories dans le Registre.** Implémentation de l'IDE de le **polices et couleurs** page de propriétés utilise ces informations pour interroger correctement pour le service de prise en charge d'une catégorie donnée.  
  
-   **Créez ou identifiez les groupes dans le Registre \(facultatif\).** Il peut être utile de définir un groupe qui représente l'union de deux ou plusieurs catégories. Si un groupe est défini, l'IDE fusionne les sous\-catégories automatiquement et distribue les éléments affichés dans le groupe.  
  
-   **Implémenter la prise en charge de l'IDE.**  
  
-   **Gérer les modifications de police et la couleur.**  
  
#### Pour créer ou identifier des catégories  
 Créer un type spécial d'entrée de Registre de catégorie sous \[HKLM\\SOFTWARE\\Microsoft \\Visual Studio\\ \< version de Visual Studio \> \\FontAndColors\\ \< catégorie \>\]. \< catégorie \> est le nom non localisé de la catégorie.  
  
 Remplir le Registre avec deux valeurs :  
  
|Nom|Type|Données|Description|  
|---------|----------|-------------|-----------------|  
|Catégorie|REG\_SZ|GUID|Un GUID est créé pour identifier la catégorie|  
|Package|REG\_SZ|GUID|Le GUID du service VSPackage qui prend en charge de la catégorie|  
  
 Le service spécifié dans le Registre doit fournir une implémentation de [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) pour la catégorie correspondante.  
  
#### Pour créer ou identifier des groupes  
 Créer un type spécial d'entrée de Registre de catégorie sous \[HKLM\\SOFTWARE\\Microsoft \\Visual Studio\\ \< version de Visual Studio \> \\FontAndColors\\ \< groupe \>\]. \< groupe \> est le nom non localisé du groupe.  
  
 Remplir le Registre avec deux valeurs :  
  
|Nom|Type|Données|Description|  
|---------|----------|-------------|-----------------|  
|Catégorie|REG\_SZ|GUID|Un GUID est créé pour identifier la catégorie|  
|Package|REG\_SZ|GUID|Le GUID du service VSPackage qui prend en charge de la catégorie|  
  
 Le service spécifié dans le Registre doit fournir une implémentation de **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** pour le groupe correspondant.  
  
 ![IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304\-a\_FontAndColorGroup")  
  
### Pour implémenter la prise en charge IDE  
 Implémentez [GetObject](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject.aspx), qui retourne un [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) interface ou un **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** de l'interface de l'IDE pour chaque catégorie ou le groupe GUID fourni.  
  
 Pour chaque catégorie, il prend en charge, un VSPackage implémente une instance distincte de la [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) interface.  
  
 Les méthodes implémentées via [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) doit fournir l'environnement de développement intégré :  
  
-   Listes d'éléments affichés dans la catégorie  
  
-   Noms localisables pour afficher les éléments  
  
-   Afficher des informations pour chaque membre de la catégorie  
  
 **Remarque :** chaque catégorie doit contenir au moins un élément d'affichage.  
  
 L'IDE utilise le **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** interface pour définir une union de plusieurs catégories.  
  
 Son implémentation fournit l'environnement de développement intégré :  
  
-   Une liste des catégories qui composent un groupe donné  
  
-   Accès aux instances de [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) prise en charge de chaque catégorie dans le groupe  
  
-   Noms de groupe localisable  
  
#### Mise à jour de l'IDE  
 L'IDE met en cache les informations sur les paramètres de police et la couleur. Par conséquent, après toute modification de la configuration de couleurs et de polices de l'IDE, garantissant que le cache est à jour est une meilleure pratique.  
  
 Mise à jour du cache s'effectue via la [IvsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) de l'interface et peut être effectuées seulement ou globalement sélectionnées.  
  
### Gestion des modifications de police et couleur  
 Pour correctement prendre en charge la colorisation de texte qui affiche un VSPackage, le service de colorisation prenant en charge le VSPackage doit répondre aux modifications initiées par l'utilisateur via la page de propriétés de polices et couleurs.  
  
 Pour ce faire, un VSPackage doit :  
  
-   **Gérer les événements générés par l'IDE** en implémentant le [IVsFontAndColorEvents](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.aspx) interface. L'IDE appelle la méthode appropriée après les modifications de l'utilisateur de la page polices et couleurs. Par exemple, il appelle le [OnFontChanged](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged.aspx) méthode si une nouvelle police est sélectionnée.  
  
 **OU**  
  
-   **interroger l'IDE pour modifications**. Cela est possible via le système implémenté [IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) interface. Bien que principalement pour la prise en charge de la persistance, la [GetItem](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem.aspx) méthode permettre obtenir des informations de police et la couleur pour afficher les éléments. Pour plus d'informations sur les paramètres de police et couleur, consultez l'article MSDN [l'accès à stockées paramètres de police et couleur](https://msdn.microsoft.com/en-us/library/bb166382.aspx).  
  
 **Remarque :** pour vous assurer que les résultats de l'interrogation sont correctes, utilisez les [IVsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) interface pour déterminer si un vidage du cache et la mise à jour sont nécessaires avant d'appeler les méthodes d'extraction de la [IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) interface.  
  
#### L'enregistrement de catégorie de couleur et de police personnalisée sans avoir à implémenter des interfaces  
 L'exemple de code suivant montre comment inscrire la police et la couleur de catégorie sans avoir à implémenter les interfaces :  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window] "Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}" "Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}" "ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}" "NameID"=dword:00000064  
```  
  
 **REMARQUE :**  
  
-   « NameID » \= l'ID de ressource de la catégorie localisée dans votre package.  
  
-   « ToolWindowPackage » \= GUID du Package  
  
-   « Catégorie » \= « {9FF46859\-A47E\-47bf\-8AC5\-EC3DBE69D1FE} » est juste un exemple et la valeur réelle peut être un nouveau GUID fourni par l'implémenteur.  
  
### Définir la police et la couleur propriété GUID de catégorie  
 L'exemple de code ci\-dessous montre comment définir des GUID de catégorie.  
  
```  
// m_pView is your IVsTextView IVsTextEditorPropertyCategoryContainer spPropCatContainer = (IVsTextEditorPropertyCategoryContainer)m_pView; if (spPropCatContainer != null) { IVsTextEditorPropertyContainer spPropContainer; Guid GUID_EditPropCategory_View_MasterSettings = new Guid("{D1756E7C-B7FD-49a8-B48E-87B14A55655A}"); hr = spPropCatContainer.GetPropertyCategory( ref GUID_EditPropCategory_View_MasterSettings, out spPropContainer); if(hr == 0) { hr = spPropContainer.SetProperty( VSEDITPROPID.VSEDITPROPID_ViewGeneral_FontCategory, catGUID); hr = spPropContainer.SetProperty( VSEDITPROPID.VSEDITPROPID_ViewGeneral_ColorCategory, catGUID); } }  
```  
  
##  <a name="BKMK_DaytonaAndWebUI"></a> Daytona et l'interface utilisateur web  
  
### Vue d'ensemble  
 « Daytona » est un ensemble d'API, outils et services qui permettent aux utilisateurs de créer des plug\-ins avec HTML, CSS et JavaScript qui peut être utilisé de plusieurs hôtes, tels que Visual Studio ou F12. Plug\-ins sont composées d'un portable, qui est écrit en HTML, CSS et JavaScript, et les composants spécifiques à l'hôte facultatif. Chaque hôte Daytona peut avoir son propre ensemble de conventions de l'interface utilisateur, implicites ou explicites, qu'un plug\-in doit respecter pour apparaître de son environnement natif. Certains hôtes, tels que Visual Studio, permettent aux utilisateurs finaux de modifier le thème « par défaut » afin que les aspects visuels de l'ordinateur hôte ne peut pas être ciblés statiquement lors de la création d'une feuille de style. Cela pose un défi pour les développeurs créant des plug\-ins portables. Cette rubrique explique comment créer une interface utilisateur dans Visual Studio à l'aide de l'hôte Daytona d'une façon qui prend en charge correctement les thèmes et contraste élevé.  
  
### Mécanisme de thèmes Daytona  
 Le runtime Daytona fournit un ensemble de services qui résume les conventions de l'interface utilisateur et les fonctionnalités de thèmes de l'ordinateur hôte. Ces services garantissent que les plug\-ins sont automatiquement conformes aux attentes de l'utilisateur en fonction de l'environnement, dans qu'ils sont hébergés visual. Ce comportement est fourni par trois fonctionnalités principales :  
  
1.  Une feuille de style injectées par le runtime \(plugin.css\) qui applique un ensemble de règles CSS à l'interface utilisateur du plug\-in en toute transparence et de styles de l'ensemble de contrôles HTML \(par exemple, HTMLInputElement et HTMLButtonElement  
  
2.  Un ensemble de jetons fourni par l'hôte qui peut être utilisé pour les éléments d'interface utilisateur de style à l'aide des valeurs qui sont basés sur le thème au lieu de codé en dur  
  
    1.  une syntaxe déclarative pour l'accès à ces jetons avec CSS  
  
    2.  une API pour accéder par programme aux jetons de thème à partir de JavaScript  
  
3.  Notification des modifications de thème  
  
#### Feuille de style injectées par le runtime  
 Les coordonnées de runtime Daytona avec l'hôte pour injecter un style de feuille automatiquement les éléments de l'interface utilisateur standard d'un plug\-in de thèmes. Cela inclut les styles pour les concepts suivants :  
  
-   Police d'environnement  
  
-   Couleurs d'arrière\-plan  
  
-   Liens hypertexte  
  
-   Contrôles de formulaire \(par exemple : \< Sélectionner \>, \< Entrée \>, \< bouton \>  
  
-   Tables  
  
-   En\-têtes  
  
-   Barres de défilement  
  
 Cela signifie que si votre interface utilisateur est entièrement composée de contrôles d'interface utilisateur HTML standard, alors aucun travail supplémentaire ne doit être requis pour répondre correctement aux modifications de thème et de prendre en charge le contraste élevé.  
  
#### Une interface utilisateur personnalisée  
 Dans presque tous les cas non triviale, contrôle de l'interface utilisateur HTML standard peut ne pas suffire pour fournir une expérience complète pour un plug\-in et l'interface utilisateur personnalisé doit être introduite. Pour prendre en charge d'utilisation de choix et la couleur de police appropriée, **les jetons de thème** doit être utilisé par déclaration dans CSS ou impérative via l'API JavaScript décrites ci\-dessous. Le runtime Daytona se chargera de mettre à jour les feuilles de style qui utilisent ces jetons lors du chargement du plug\-in et sur les modifications de thème.  
  
##### Jetons de thème  
 Les deux jetons thème standard et spécifiques à l'hôte sont disponibles. Les jetons standard sont injectées par l'hôte et toujours disponibles. Il est préférable d'utiliser les jetons standards lorsque cela est possible. Les jetons standard sont garantis être fournies par tous les hôtes Daytona et leur utilisation rend votre plug\-in par nature plus portable. Le jeu de jetons standards est susceptible de changer, bien que seuls les nouveaux jetons doivent être ajoutés et none doit être supprimé. La version de Visual Studio 2013 est décrit ci\-dessous :  
  
|Nom du jeton|Description|  
|------------------|-----------------|  
|couleur d'arrière\-plan du plug\-in|La couleur d'arrière\-plan par défaut pour le plug\-in|  
|couleur de plug\-in|La couleur de premier plan par défaut pour le plug\-in|  
|plug\-in\-contextmenu\-active\-couleur|La couleur de sélection de premier plan par défaut pour les menus contextuels lorsqu'elles sont actives \(a le focus\)|  
|plug\-in\-contextmenu\-couleur d'arrière\-plan|La couleur d'arrière\-plan par défaut des menus contextuels|  
|plug\-in\-contextmenu\-couleur de bordure|La couleur de bordure par défaut pour les menus contextuels|  
|couleur de plug\-in contextmenu|La couleur de premier plan par défaut des menus contextuels|  
|plug\-in\-contextmenu\-pointage|La couleur d'arrière\-plan par défaut pointage des menus contextuels|  
|couleur du texte pointage Plug\-in contextmenu|La couleur de premier plan par défaut pointage des menus contextuels|  
|plug\-in\-contextmenu\-icône de case à cocher|Couleur de l'icône de case à cocher par défaut pour les menus contextuels|  
|plug\-in\-contextmenu\-inactive\-couleur de texte|La couleur de sélection de premier plan par défaut pour les menus contextuels lorsqu'elles sont inactives|  
|plug\-in contextmenu\-séparateur de couleurs|La couleur du séparateur par défaut pour les menus contextuels|  
|famille de polices de plug\-in|La famille de polices par défaut à utiliser pour le plug\-in|  
  
 Dans Visual Studio, les jetons du plug\-in de police suivants sont basés sur les paramètres de police d'environnement :  
  
-   taille de police de plug\-in  
  
-   épaisseur de police de plug\-in  
  
-   plug\-in\-mise en surbrillance en couleur d'arrière\-plan  
  
-   couleur de surbrillance plug\-in  
  
-   plug\-in inactif couleur  
  
 Les jetons de liaison de plug\-in suivants sont utilisés pour appliquer un style HTMLElements \(liens\) :  
  
-   couleur de lien de plug\-in  
  
-   plug\-in\-\-active\-couleur de lien  
  
-   plug\-in\-lien\-pointage  
  
 Plugin.CSS styles des barres de défilement par défaut en utilisant les jetons suivants pour mieux prendre en charge les thèmes dans les différents hôtes \(en particulier, Visual Studio\) :  
  
-   plug\-in scrollbar flèche de couleur  
  
-   plug\-in\-barre de défilement en couleur d'arrière\-plan  
  
-   barre de défilement plug\-in\-couleur face  
  
 Les jetons de sélection du plug\-in suivants sont utilisés pour définir le style du HTMLSelectElement \(zone de liste modifiable déroulante\) :  
  
-   plug\-in\-sélectionnez\-option\-couleur d'arrière\-plan  
  
-   plug\-in sélectionnez option couleurs  
  
-   plugin\-SELECT\-option\-checked\-Background\-Color  
  
-   plugin\-SELECT\-option\-checked\-Border\-Color  
  
-   plugin\-SELECT\-option\-checked\-Foreground\-Color  
  
-   plugin\-SELECT\-option\-Hover\-Background\-Color  
  
-   plugin\-SELECT\-option\-Hover\-Border\-Color  
  
-   plugin\-SELECT\-option\-Hover\-Foreground\-Color  
  
-   plug\-in\-sélectionnez\-couleur de bordure  
  
-   plug\-in\-sélectionnez\-couleur d'arrière\-plan  
  
-   plug\-in\-sélectionnez\-\-couleur de premier plan  
  
-   plug\-in\-sélectionnez\-pointage\-couleur d'arrière\-plan  
  
-   plug\-in\-sélectionnez\-pointage\-couleur de bordure  
  
-   couleur du premier plan pointage Plug\-in select  
  
-   plug\-in\-table\-couleur de bordure  
  
-   plug\-in\-table\-en\-tête\-couleur d'arrière\-plan  
  
-   plug\-in\-table\-en\-tête\-couleur  
  
-   plug\-in\-zone de texte en couleur de bordure  
  
-   plug\-in\-zone de texte\-couleur d'arrière\-plan  
  
-   couleur de zone de texte de plug\-in  
  
-   plug\-in\-zone de texte\-disabled\-couleur d'arrière\-plan  
  
-   plug\-in\-zone de texte\-disabled\-couleur de bordure  
  
-   plug\-in\-zone de texte\-disabled\-couleur  
  
 Ces jetons doivent être utilisés pour *tous les* tables et les vues d'arborescence parce qu'ils ont les valeurs par défaut appropriés définis dans les différents hôtes pour prendre en charge des thèmes et contraste élevé :  
  
-   plug\-in\-treeview\-contenu\-couleur d'arrière\-plan  
  
-   plug\-in treeview contenu couleurs  
  
-   plugin\-TreeView\-Content\-inactive\-Selected\-Color  
  
-   plugin\-TreeView\-Content\-MouseOver\-Background\-Color  
  
-   couleur du mouseover contenu plug\-in treeview  
  
-   plugin\-TreeView\-Content\-inactive\-Selected\-Color  
  
-   plugin\-TreeView\-Content\-Selected\-Background\-Color  
  
-   plugin\-TreeView\-Content\-Selected\-Border\-Color  
  
-   plug\-in treeview\-contenu\-sélectionné\-couleur  
  
##### Jetons spécifiques à l'hôte  
 Prise en charge de l'ensemble standard de jetons, les hôtes peuvent également fournir des jetons non standard. Pour cela, l'hôte Visual Studio permettant le plug\-in spécifier les alias de jeton de thème dans une section spécifique de Visual Studio du manifeste. Exemple :  
  
```  
"vs": { "theme_token_aliases": { "diagnostics-host-border": { "category": "f8a8b2a5-dd35-43f6-a382-fd6a61325c22", "key_type": "BackgroundColor", "name": "Border" }, ... } }  
  
```  
  
 Cet exemple présente un jeton thème, nommé « diagnostics\-hôte\-bordure », qui peut être référencé identique pour les jetons standards mentionnés ci\-dessus. La catégorie, le key\_type et le nom sont utilisés pour résoudre la couleur par le biais du **IVsFontAndColorStorage** interface. Dans de nombreux cas, il est possible de trouver des couleurs \(ainsi que les informations de catégorie, key\_type et nom\) dans les fichiers XML situés dans vscommon\\themes. Ce mécanisme est utilisé si votre package introduit de nouvelles couleurs configurables : correspondent à la catégorie, key\_type et le nom de la couleur que vous souhaitez utiliser. Les auteurs de plug\-in doivent tentent d'utiliser autant que possible les jetons standard et utiliser uniquement des jetons spécifiques à l'hôte lorsque cela est absolument nécessaire.  
  
##### Utilisation de jetons de thème dans CSS  
 Les jetons de thème sont appelés via une syntaxe de commentaire spécialement mise en forme. Les règles pour l'analyse du jeton :  
  
1.  L'expression de commentaire doit être placée entre crochets \(**\[\]**\).  
  
2.  Tous les espaces blancs dans un commentaire, mais en dehors de l'expression sont ignorée.  
  
3.  L'expression de commentaire doit suivre directement la propriété qu'il remplace.  
  
4.  Aucun espace de début ou de fin dans l'expression est supprimé.  
  
5.  Chaque nom de jeton dans l'expression doit être placé entre accolades \(par exemple, **{famille de polices}** et **{couleur de survol bouton}**\). Dans le cas contraire, il est considéré comme une valeur littérale.  
  
 Voici des exemples de la façon dont l'Analyseur de jeton remplacent les valeurs CSS, en supposant que le **couleur d'arrière\-plan du plug\-in** jeton a la valeur \#000 et **plug\-in\-font\-family** jeton a la valeur « Verdana ».  
  
|CSS créés|CSS analysée|Notes|  
|---------------|------------------|-----------|  
|`background-color: #fff; /*[{plugin-background-color}]*/`|`background-color: #000;`|La valeur par défaut est remplacée par la valeur spécifique à l'hôte dynamique.|  
|`background-color: #fff; /*   [{plugin-background-color}]   */`|`background-color: #000;`|L'espace blanc en dehors de l'expression est ignorée.|  
|`background-color: #fff; /*[   {plugin-background-color}   ]*/`|`background-color: #000;`|Les espaces de début et de fin dans l'expression sont supprimés.|  
|`background-color: #fff; /*{plugin-background-color}*/`|`background-color: #fff;`|L'expression n'est pas placée entre crochets, et par conséquent, le commentaire est ignoré.|  
|`background-color: #fff; /*[plugin-background-color]*/`|`background-color: plugin-background-color;`|Le jeton n'est pas placé entre accolades et est donc traité comme une valeur littérale.|  
|`/*[{plugin-background-color}]*/ background-color: #fff;`|`background-color: #fff;`|Le commentaire ne suit pas la valeur de propriété et est donc ignoré.|  
|`background-color: #fff; /*[{plugin-background-color}]*/`|`background-color: #fff;`|*Comme ci\-dessus*|  
|`/*[{plugin-background-color}]*/ background-color: #fff;`|`background-color: #fff;`|*Comme ci\-dessus*|  
|`font-family: Arial, sans-serif; /*[{plugin-font-family}, sans-serif]*/`|`font-family: Verdana, sans-serif;`|Le jeton est remplacé et le contenu littéral est conservé.|  
|`background-image: linear-gradient(0% #000, 100% #ccc); /*[linear-gradient(0% #000, 100% {plugin-background-color})]*/`|`background-image: linear-gradient(0% #000, 100% #000);`|*Comme ci\-dessus*|  
  
 Si un fichier CSS inclut les jetons de thème, il doit être marqué par l'attribut de thème de plug\-in de données sur l'élément de liaison dans le fichier HTML. Exemple :  
  
```  
<link href="default.css" rel="stylesheet" data-plugin-theme="true" />  
```  
  
##### L'utilisation de jetons de thème à partir de JavaScript  
 Alors que l'interface utilisateur personnalisée doit être à thème par CSS lorsque cela est possible, il existe des scénarios lorsque la valeur d'un thème de jeton doivent être accessibles par programme. Par exemple, si l'interface utilisateur personnalisée est dessinée sur un CanvasElement qui n'hérite pas le style de CSS, ou si un élément d'interface utilisateur est en cours de manière dynamique créé par opposition à faisant référence à des feuilles de style. Les scénarios sont activés à l'aide de l'API Daytona **Plugin.Theme.getValue**. Cette fonction retourne une valeur de thème fourni par l'hôte en fonction d'un nom de jeton.  
  
|Pas de thème|À thème|  
|------------------|-------------|  
|`var surface = document.getElementById("surface").getContext("2d"); surface.fillStyle = "#ccc"; surface.fillRect(0, 0, 200, 200);`|`var surface = document.getElementById("surface").getContext("2d"); surface.fillStyle = ("plugin-background-color"); surface.fillRect(0, 0, 200, 200);`|  
|`var el = document.createElement("div"); el.style.backgroundColor = "#ccc";`|`var el = document.createElement("div"); el.style.backgroundColor = Plugin.Theme.getValue("plugin-background-color");`|  
  
 Si les jetons sont utilisés à partir de JavaScript**, l'événement de changement de thème doit être gérée pour répondre aux mises à jour**. Cela n'est pas nécessaire pour les jetons de thème utilisées de façon déclarative dans le CSS, comme le runtime Daytona s'en charge pour le plug\-in. L'événement thème peut être géré de la façon suivante :  
  
|Membre \(gestionnaire unique\)|Événement DOM \(plusieurs gestionnaires\)|  
|------------------------------------|-----------------------------------------------|  
|`Plugin.Theme.onchange = function () { // re-draw dynamic UI here }`|`Plugin.Theme.addEventListener("change", function () { // re-draw dynamic UI here });`|  
  
 Dans ce cas, il est très courant d'appeler de nouveau **Plugin.Theme.getValue** dans ces gestionnaires, comme la valeur des jetons thème probables modifié lorsque le thème modifié.  
  
##### Mappage de jeton standard  
 Les jetons standards sont mappés aux couleurs de Shell et d'environnement. La liste ci\-dessous donne une idée de ce que sont ces mappages.  
  
|Nom du jeton|Mappage de Visual Studio \(EnvironmentColors\)|  
|------------------|----------------------------------------------------|  
|couleur de plug\-in|ToolWindowTextColorKey|  
|couleur d'arrière\-plan du plug\-in|ToolWindowBackgroundColorKey|  
|couleur de lien de plug\-in|ControlLinkTextColorKey|  
|plug\-in\-lien\-pointage|ControlLinkTextHoverColorKey|  
|plug\-in\-\-active\-couleur de lien|ControlLinkTextPressedColorKey|  
|couleur de surbrillance plug\-in|HighlightTextColorKey|  
|plug\-in\-mise en surbrillance en couleur d'arrière\-plan|HighlightColorKey|  
|plug\-in\-table\-en\-tête\-couleur d'arrière\-plan|GridHeadingBackgroundColorKey|  
|plug\-in\-table\-en\-tête\-couleur|GridHeadingTextColorKey|  
|plug\-in\-table\-couleur de bordure|GridLineColorKey|  
|plug\-in\-bouton\-couleur d'arrière\-plan|ButtonFaceColorKey|  
|plug\-in\-bouton\-pointage\-couleur d'arrière\-plan|ButtonHighlightColorKey|  
|couleur de bouton de plug\-in|ButtonTextColorKey|  
|plug\-in\-bouton\-couleur de bordure|ButtonBorderColorKey|  
  
##### Modifications de thème  
 Visual Studio hôte déclencheurs plug\-in thème change lorsqu'un utilisateur final apporte des modifications aux paramètres suivants :  
  
 **Thème de couleur :**  
  
 ![Color theme changes](../../extensibility/ux-guidelines/media/0305-a_colortheme.png "0305\-a\_ColorTheme")  
  
 **Thème d'environnement :**  
  
 ![Environment theme changes](../../extensibility/ux-guidelines/media/0305-b_environmenttheme.png "0305\-b\_EnvironmentTheme")  
  
 **Thème du système d'exploitation** \(uniquement en cas de modification vers et à partir de contraste élevé\) :  
  
 ![OS theme changes](../../extensibility/ux-guidelines/media/0305-c_ostheme.png "0305\-c\_OSTheme")