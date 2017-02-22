---
title: "Mise en forme pour Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# Mise en forme pour Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

##  <a name="BKMK_TheEnvironmentFont"></a> La police d'environnement  
 Toutes les polices dans Visual Studio doivent être exposés à l'utilisateur pour la personnalisation. Cela s'effectue principalement via le **polices et couleurs** page dans le **Outils \> Options** boîte de dialogue. Les trois principales catégories de paramètres de police sont :  
  
-   **Police d'environnement** — la police principale pour l'IDE \(environnement de développement intégré\), utilisée pour tous les éléments d'interface, y compris les boîtes de dialogue, les menus, les fenêtres Outil et les fenêtres de document. Par défaut, la police d'environnement est liée à une police système qui apparaît sous la forme 9 pt Segoe UI dans les versions actuelles de Windows. À l'aide d'une police pour tous les éléments d'interface permet de garantir une apparence cohérente police tout au long de l'IDE.  
  
-   **Éditeur de texte** — page éléments que surface dans le code et d'autres éditeurs de texte peuvent être personnalisés dans l'éditeur de texte **Outils \> Options**.  
  
-   **Des regroupements spécifiques** — apparaître les fenêtres du concepteur qui offrent la personnalisation de leurs éléments de l'interface de l'utilisateur peut exposer des polices spécifiques à leur conception dans leur propre page Paramètres **Outils \> Options**.  
  
### Personnalisation de police de l'éditeur et le redimensionnement  
 Les utilisateurs souvent agrandir ou effectuer un zoom de la taille et\/ou la couleur du texte dans l'éditeur en fonction de leurs préférences, indépendamment de l'interface utilisateur. Étant donné que la police d'environnement est utilisée sur des éléments qui peuvent apparaître au sein ou en tant que partie d'un éditeur\/concepteur, il est important de noter le comportement attendu lorsque l'une de ces classifications de police est modifiée.  
  
 Lors de la création des éléments d'interface utilisateur qui s'affichent dans l'éditeur mais sont ne fait pas partie de la *contenu*, il est important d'utiliser la police d'environnement et pas la police du texte afin que le redimensionnement des éléments de manière prévisible.  
  
1.  Texte du code dans l'éditeur, redimensionner avec le paramètre de police du texte code et répondre au niveau de zoom du texte de l'éditeur.  
  
2.  Tous les autres éléments de l'interface doivent être liées pour le paramètre de police d'environnement et répondent aux modifications éventuelles globales dans l'environnement. Cela inclut \(mais n'est pas limité à\) :  
  
    -   Texte dans les menus contextuels  
  
    -   Texte dans un ornement de l'éditeur, telles que du texte de menu ampoule, rapide éditeur volet de recherche, puis accédez au volet  
  
    -   Texte d'étiquette dans les boîtes de dialogue telles que rechercher dans les fichiers ou de Refactor \!  
  
### L'accès à la police d'environnement  
 Dans le code natif ou WinForms, la police d'environnement sont accessibles en appelant la méthode **IUIHostLocale::GetDialogFont** après interrogation de l'interface du service SID\_SUIHostLocale.  
  
 Pour Windows Presentation Foundation \(WPF\), dérivez votre classe de fenêtre de boîte de dialogue à partir du shell **DialogWindow** classe au lieu de WPF **fenêtre** classe.  
  
 En XAML, le code ressemble à ceci :  
  
```  
<ui:DialogWindow x:Class"MyNameSpace.MyWindow" xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" xmlns:s="http://schemas.microsoft.com/winfx/2006/xaml" xmlns:ui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0" ShowInTaskbar="False" WindowStartupLocation="CenterOwner" Title="My Dialog"> </ui:DialogWindow> code behind: internal partial class WebConfigModificationWindow : DialogWindow { }  
  
```  
  
 \(Remplacez `Microsoft.VisualStudio.Shell.11.0` avec la version actuelle de la dll MPF.\)  
  
 Pour afficher la boîte de dialogue, appelez «**ShowModal\(\)**» sur la classe sur **OpenFileDialog**.**ShowModal\(\)** définit l'état modal approprié dans l'interpréteur de commandes, garantit la boîte de dialogue est centrée dans la fenêtre parente et ainsi de suite.  
  
 Le code est comme suit :  
  
```  
MyWindow window = new MyWindow(); window.ShowModal()  
  
```  
  
 **ShowModal pour rendre** retourne une valeur bool ? \(valeur booléenne nullable\) avec le **DialogResult**, qui peut être utilisé si nécessaire. La valeur de retour est true si la boîte de dialogue a été fermée avec **OK**.  
  
 Si vous avez besoin afficher une UI WPF qui n'est pas une boîte de dialogue et est hébergé dans son propre **HwndSource**, comme une fenêtre contextuelle ou la fenêtre WPF enfant d'une fenêtre parent de Win32\/WinForms, vous devez définir le **FontFamily** et **FontSize** sur l'élément racine de l'élément WPF. \(L'interface définit les propriétés de la fenêtre principale, mais ils ne seront pas héritées après un HWND\). L'interpréteur de commandes fournit des ressources dans lequel les propriétés peuvent être liées, comme suit :  
  
```  
<Setter property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" /> <Setter property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />  
  
```  
  
###  <a name="BKMK_Formatting"></a> Mise en forme \(mise à l'échelle\/mise en gras\) référence  
 Certaines boîtes de dialogue requièrent le texte en gras ou une taille de la police d'environnement. Auparavant, les polices plus de la police d'environnement étaient codés en tant que « police d'environnement \+ 2 » ou similaire. À l'aide d'extraits de code fournis pour prennent en charge les moniteurs haute résolution et vérifiez que texte d'affichage apparaît toujours à la taille et le poids \(par exemple, la lumière ou Semilight\).  
  
> **Remarque : Avant d'appliquer la mise en forme, vérifiez que vous suivez les conseils figurant dans [Style de texte](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).**  
  
 Pour mettre à l'échelle de la police d'environnement, définissez le style du TextBlock ou Label, comme indiqué. Chacun de ces extraits de code, elle est utilisées correctement, génère la police correcte, y compris les variations de taille et poids appropriées.  
  
 Où « vsui » est une référence à l'espace de noms Microsoft.VisualStudio.Shell :  
  
```  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
```  
  
#### Police d'environnement 375 % \+ clair  
 **Apparaît sous la forme :** pt 34 Segoe UI Light  
  
 **Utiliser pour :** \(rare\) unique marque l'interface utilisateur, comme dans la Page de démarrage  
  
 **Code procédural :** où « textBlock » est un TextBlock précédemment défini et « label » est une étiquette définie précédemment.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);  
  
```  
  
 **XAML :** définir le style de l'étiquette ou TextBlock comme indiqué.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>  
  
```  
  
#### Police d'environnement 310 % \+ clair  
 **Apparaît sous la forme :** pt 28 Segoe UI Light  
  
 **Utiliser pour :** signature grande boîte de dialogue, hormis principales en\-tête dans les rapports  
  
 **Code procédural :** où « textBlock » est un TextBlock précédemment défini et « label » est une étiquette définie précédemment.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);  
  
```  
  
 **XAML :** définir le style de l'étiquette ou TextBlock comme indiqué.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>  
  
```  
  
#### Police d'environnement 200 % \+ Semilight  
 **Apparaît sous la forme :** 18 pt Segoe UI Semilight  
  
 **Utiliser pour :** sous\-titres, des titres dans les petites et moyennes des boîtes de dialogue  
  
 **Code procédural :** où « textBlock » est un TextBlock précédemment défini et « label » est une étiquette définie précédemment.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);  
  
```  
  
 **XAML :** définir le style de l'étiquette ou TextBlock comme indiqué.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>  
  
```  
  
#### Police d'environnement 155 %  
 **Apparaît sous la forme :** 14 pt Segoe UI  
  
 **Utiliser pour :** des en\-têtes de section dans le document et l'interface utilisateur ou des rapports  
  
 **Code procédural :** où « textBlock » est un TextBlock précédemment défini et « label » est une étiquette définie précédemment.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);  
  
```  
  
 **XAML :** définir le style de l'étiquette ou TextBlock comme indiqué.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>  
  
```  
  
#### Police d'environnement 133 %  
 **Apparaît sous la forme :** 12 pt Segoe UI  
  
 **Utiliser pour :** plus petits sous\-titres dans les boîtes de dialogue de signature et de document ainsi l'interface utilisateur  
  
 **Code procédural :** où « textBlock » est un TextBlock précédemment défini et « label » est une étiquette définie précédemment.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);  
  
```  
  
 **XAML :** définir le style de l'étiquette ou TextBlock comme indiqué.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>  
  
```  
  
#### Police d'environnement 122 %  
 **Apparaît sous la forme :** 11 pt Segoe UI  
  
 **Utiliser pour :** section en\-têtes dans les boîtes de dialogue de signature, premiers nœuds d'arborescence, navigation de tabulation verticale  
  
 **Code procédural :** où « textBlock » est un TextBlock précédemment défini et « label » est une étiquette définie précédemment.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);  
  
```  
  
 **XAML :** définir le style de l'étiquette ou TextBlock comme indiqué.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>  
  
```  
  
#### Police d'environnement \+ gras  
 **Apparaît sous la forme :** en gras 9 pt Segoe UI  
  
 **Utiliser pour :** étiquettes et des sous\-titres dans les boîtes de dialogue de signature, les rapports et les documents et l'interface utilisateur  
  
 **Code procédural :** où « textBlock » est un TextBlock précédemment défini et « label » est une étiquette définie précédemment.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironmentBoldStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironmentBoldStyleKey);  
  
```  
  
 **XAML :** définir le style de l'étiquette ou TextBlock comme indiqué.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>  
  
```  
  
### Styles localisables  
 Dans certains cas, les localisateurs devez modifier les styles de police pour différents paramètres régionaux, telles que la suppression en gras du texte pour les langues d'Extrême\-Orient. Pour permettre la localisation des styles de police, les styles doivent se trouver dans le fichier .resx. La meilleure façon d'effectuer cette opération et toujours modifier les styles de police dans le Concepteur de formulaires de Visual Studio consiste à définir explicitement les styles de police au moment du design. Bien que cela crée un objet police complète et peut sembler l'héritage des polices de parent, seule la propriété FontStyle est utilisée pour définir la police.  
  
 La solution consiste à raccorder le formulaire de boîte de dialogue **FontChanged** événement. Dans le **FontChanged** événement parcourir tous les contrôles et vérifier si leur format de police est défini. S'il est défini, remplacez\-le par une nouvelle police en fonction de la police du formulaire et le style de police du contrôle précédent. Un exemple de code est :  
  
```  
private void Form1_FontChanged(object sender, System.EventArgs e) { SetFontStyles(); } /// <summary> /// SetFontStyles - This function will iterate all controls on a page /// and recreate their font with the desired fontstyle. /// It should be called in the OnFontChanged handler (and also in the constructor /// in case the IUIService is not available so OnFontChange doesn't fire). /// This way, when the VS shell font is given to us the controls that have /// a different style for the font (bolded for example) will recreate their font /// and use the VS shell font but with a style variation (bolded ...). /// </summary> protected void SetFontStyles() { SetFontStyles(this, this, this.Font); } protected static void SetFontStyles(Control topControl, Control parent, Font referenceFont) { foreach(Control c in parent.Controls) { if (c.Controls != null && c.Controls.Count > 0) { SetFontStyles(topControl, c, referenceFont); } if (c.Font != topControl.Font) { c.Font = new Font(referenceFont, c.Font.Style); } } }  
```  
  
 À l'aide de ce code garantit que lorsque la police du formulaire est mis à jour, les polices des contrôles met à jour également. Cette méthode doit également être appelée à partir du constructeur du formulaire, car la boîte de dialogue peut ne pas obtenir une instance de **IUIService** et **FontChanged** événement ne se déclenche jamais. Raccordement **FontChanged** permettra de boîtes de dialogue Sélectionner dynamiquement la nouvelle police même si la boîte de dialogue est déjà ouverte.  
  
### La police d'environnement de test  
 Pour vous assurer que votre interface utilisateur à l'aide de la police d'environnement et qu'il respecte les paramètres de taille, ouvrez **Outils \> Options \> environnement \> polices et couleurs** et sélectionnez « Police d'environnement » sous la « afficher les paramètres de: « menu déroulant.  
  
 ![Fonts and Colors page in Tools &#62; Options dialog](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201\-a\_OptionsFonts")  
  
 **Paramètres de polices et couleurs dans les outils \> boîte de dialogue Options**  
  
 Définir la police à quelque chose de très différente de la valeur par défaut. Pour bien qui ne met pas à jour l'interface utilisateur, choisissez une police avec empattements \(par exemple « Times New Roman »\) et définissez une taille très importante. Testez ensuite votre interface utilisateur pour vous assurer qu'il respecte l'environnement. Voici un exemple d'utilisation de la boîte de dialogue licence :  
  
 ![Example of dialog not using the environment font](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201\-b\_WrongFontDialog")  
  
 **Exemple de texte de l'interface utilisateur qui ne respecte pas la police d'environnement**  
  
 Dans ce cas, « Informations utilisateur » et « Informations sur le produit » sont respectant pas la police. Dans certains cas, cela peut être un choix de conception explicite, mais il peut être un bogue si la police explicite n'est pas spécifiée dans le cadre des ligne rouge de spécifications.  
  
 Pour rétablir la police, cliquez sur « Par défaut » sous **Outils \> Options \> environnement \> polices et couleurs**.  
  
##  <a name="BKMK_TextStyle"></a> Style de texte  
 Style de texte fait référence à la casse, le poids et la taille de police. Pour des instructions d'implémentation, consultez la page [La police d'environnement](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
### Casse du texte  
  
#### Tout en majuscules  
 N'utilisez pas les majuscules pour des titres ou des étiquettes dans Visual Studio.  
  
#### Toutes les minuscules  
 Ne pas utiliser des minuscules pour les titres ou des étiquettes dans Visual Studio.  
  
#### Cas de phrase et titre  
 Texte dans Visual Studio doit utiliser majuscule ou casse de la phrase, selon la situation.  
  
|Cas d'utilisation du titre pour :|Utilisez la casse de la phrase pour :|  
|---------------------------------------|-------------------------------------------|  
|Titres de boîte de dialogue|Étiquettes|  
|Zones de groupe|Cases à cocher|  
|Éléments de menu|Cases d'option|  
|Éléments de menu contextuel|Éléments de liste|  
|Boutons|Barres d'état|  
|Étiquettes de table||  
|En\-têtes de colonne||  
|Info\-bulles||  
  
##### Casse du titre  
 Casse du titre est un style dans lequel sont écrits en majuscules les lettres de tout ou partie des mots dans une phrase. Dans Visual Studio, majuscule est utilisé pour de nombreux éléments, y compris :  
  
-   **Info\-bulles.** Exemple: « aperçu les éléments sélectionnés »  
  
-   **En\-têtes de colonne.** Exemple: « réponse système »  
  
-   **Éléments de menu.** Exemple: « enregistrer tout »  
  
 Lorsque vous utilisez la casse, voici les instructions de mise en majuscule de mots et les laisser en minuscules :  
  
|Majuscules|Commentaires et exemples|  
|----------------|------------------------------|  
|Tous les noms||  
|Tous les verbes|Y compris « Est » et autres formes de « être »|  
|Tous les adverbes|Y compris « À » et « When »|  
|Tous les adjectifs|Y compris « This » et « Qui »|  
|Tous les pronoms|Y compris le short « Sa » et «, » une contraction du pronom « it » et le verbe « est »|  
|Premiers et derniers mots, indépendamment des parties de la voix||  
|Prépositions qui font partie d'une expression verbale|« Fermer tous les Windows » ou « Arrêt du système »|  
|Toutes les lettres d'un acronyme.|HTML, XML, URL, IDE, RVB|  
|Le deuxième mot dans un mot composé s'il s'agit d'un nom ou un adjectif d'approprié, ou si les mots ont le même poids|Référence croisée, les logiciels Microsoft avant, l'accès en lecture\/écriture, exécution|  
  
|Minuscules|Exemples|  
|----------------|--------------|  
|Le deuxième mot dans un mot composé s'il s'agit d'une autre voix ou un participe modifier le premier mot|Procédures, décollage|  
|Articles, sauf si un est le premier mot du titre|un fichier, un objet, le|  
|Coordonner les conjonctions|et bien, mais, ni, ou|  
|Prépositions avec des mots de moins de quatre lettres en dehors d'une expression verbale|dans, comme pour hors, en haut de|  
|« À » lorsqu'il est utilisé dans une expression infinitive|« Comment formater votre disque dur »|  
  
##### Casse de la phrase  
 Casse de la phrase est la méthode standard de mise en majuscules pour l'écriture dans lequel seul le premier mot de la phrase est en majuscule, ainsi que des noms propres et le pronom « I ». En général, la casse de la phrase est plus facile pour une audience internationale à lire, particulièrement lorsque le contenu est converti par un ordinateur. Utilisez la casse de la phrase pour :  
  
1.  **Messages de barre d'état.** Ces sont simples, bref et fournissent uniquement les informations d'état. Exemple: « chargement du fichier projet »  
  
2.  **Tous les autres éléments d'interface utilisateur**, y compris les étiquettes, les cases à cocher, les cases d'option et les éléments de zone de liste. Exemple: « sélectionner tous les éléments dans la liste »  
  
### Mise en forme  
 Texte par défaut de mise en forme dans Visual Studio 2013 est contrôlé par un [La police d'environnement](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont). Ce service permet de garantir une apparence cohérente police tout au long de l'IDE \(environnement de développement intégré\), et vous devez l'utiliser afin de garantir une expérience cohérente pour vos utilisateurs.  
  
 La taille par défaut utilisée par le service de police de Visual Studio est fournie par Windows et apparaît sous la forme 9 pt.  
  
 Vous pouvez mettre en forme la police d'environnement. Cette rubrique décrit comment et où utiliser des styles. Pour plus d'informations d'implémentation, reportez\-vous à [La police d'environnement](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
#### Texte en gras  
 Texte en gras est utilisé avec modération dans Visual Studio et doit être réservé pour :  
  
-   étiquettes de question dans les Assistants  
  
-   désignation du projet actif dans l'Explorateur de solutions  
  
-   les valeurs dans la fenêtre d'outil propriétés substituées  
  
-   certains événements dans les listes déroulantes de l'éditeur Visual Basic  
  
-   contenu généré par le serveur dans la structure du document pour les pages web  
  
-   en\-têtes de section dans la boîte de dialogue complexe ou d'interface utilisateur du Concepteur  
  
#### Italique  
 Visual Studio n'utilise pas le texte en italique ou en gras italique.  
  
#### Couleur  
  
-   Bleu est réservé pour les liens hypertexte \(navigation et exécution des commandes\) et ne doit jamais être utilisé pour l'orientation.  
  
-   Plus grands titres \(police d'environnement x 155 % ou supérieure\) peuvent être en couleur à ces fins :  
  
    -   Pour fournir l'aspect visuel de la signature de l'interface utilisateur de Visual Studio  
  
    -   Pour attirer l'attention sur une zone spécifique  
  
    -   Pour offrir la franchise de la couleur du texte standard environnement gris\/noir foncé  
  
-   Couleur dans les en\-têtes doit tirer parti de Visual Studio marque couleurs existantes, principalement le principal violet, \#FF68217A.  
  
-   Lorsque vous utilisez des couleurs dans les en\-têtes, vous devez respecter les [les instructions de couleurs Windows](https://msdn.microsoft.com/en-us/library/dn742482.aspx), y compris de contraste et autres considérations d'accessibilité.  
  
### Taille de police  
 Conception visuelle de l'interface utilisateur Studio propose un aspect plus clair avec davantage d'espace blanc. Si possible, barres de chrome et le titre ont été réduits ou supprimés. Densité des informations est une exigence dans Visual Studio, typographie reste important, en mettant l'accent sur Interligne plus ouvert et une variation de poids et de tailles de police.  
  
 Les tableaux ci\-dessous inclut les détails de la conception et des exemples visuels pour les polices d'affichage utilisés dans Visual Studio. Des variantes de police d'affichage ont la taille et le poids, tels que Semilight ou de lumière, de manière irréversible dans leur apparence.  
  
 Extraits de code d'implémentation pour l'affichage de toutes les polices se trouve dans [Mise en forme (mise à l'échelle/mise en gras) référence](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting).  
  
#### Police d'environnement 375 % \+ clair  
  
|||  
|-|-|  
|**Utilisation :** rares. Unique marque uniquement l'interface utilisateur.<br /><br /> **Faire :**<br /><br /> -   Utilisez la casse de la phrase<br />-   Utilisez toujours légère<br /><br /> **Ne pas faire :**<br /><br /> -   Utiliser pour l'interface utilisateur autre que la signature de l'interface utilisateur comme Page de démarrage<br />-   Gras, italique ou gras italique<br />-   Utilisation de corps de texte<br />-   Utiliser dans les fenêtres Outil|**Apparaît sous la forme :** pt 34 Segoe UI Light<br /><br /> **Exemple visuel :**<br /><br /> *Pas utilisé pour l'instant. Peut être utilisé dans la Page de démarrage.*|  
  
#### Police d'environnement 310 % \+ clair  
  
|||  
|-|-|  
|**Utilisation :**<br /><br /> -   Position supérieure dans les boîtes de dialogue de signature<br />-   Titre du rapport principal<br /><br /> **Faire :**<br /><br /> -   Utilisez la casse de la phrase<br />-   Utilisez toujours légère<br /><br /> **Ne pas faire :**<br /><br /> -   Utiliser pour l'interface utilisateur autre que la signature de l'interface utilisateur comme Page de démarrage<br />-   Gras, italique ou gras italique<br />-   Utilisation de corps de texte<br />-   Utiliser dans les fenêtres Outil|**Apparaît sous la forme :** pt 28 Segoe UI Light<br /><br /> **Exemple visuel :**<br /><br /> ![Example of 310% Environment font &#43; Light heading](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202\-a\_EF310")|  
  
#### Police d'environnement 200 % \+ Semilight  
  
|||  
|-|-|  
|**Utilisation :**<br /><br /> -   Sous\-titres<br />-   Titres dans les petites et moyennes des boîtes de dialogue<br /><br /> **Faire :**<br /><br /> -   Utilisez la casse de la phrase<br />-   Utilisez toujours des poids de Semilight<br /><br /> **Ne pas faire :**<br /><br /> -   Gras, italique ou gras italique<br />-   Utilisation de corps de texte<br />-   Utiliser dans les fenêtres Outil|**Apparaît sous la forme :** 18 pt Segoe UI Semillight<br /><br /> **Exemple visuel :**<br /><br /> ![Example of 200% Environment font &#43; Semilight](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202\-b\_EF200")|  
  
#### Police d'environnement 155 %  
  
|||  
|-|-|  
|**Utilisation :**<br /><br /> -   En\-têtes de section dans le document et l'interface utilisateur<br />-   Rapports<br /><br /> **Faire :** utiliser la casse de la phrase<br /><br /> **Ne pas faire :**<br /><br /> -   Gras, italique ou gras italique<br />-   Utilisation de corps de texte<br />-   Utiliser dans la norme que contrôle Visual Studio<br />-   Utiliser dans les fenêtres Outil|**Apparaît sous la forme :** 14 pt Segoe UI<br /><br /> **Exemple visuel :**<br /><br /> ![Example of 155% Environment font heading](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202\-c\_EF155")|  
  
#### Police d'environnement 133 %  
  
|||  
|-|-|  
|**Utilisation :**<br /><br /> -   Sous\-titres plus petits dans les boîtes de dialogue de signature<br />-   Plus petits sous\-titres dans le document et l'interface utilisateur<br /><br /> **Faire :** utiliser la casse de la phrase<br /><br /> **Ne pas faire :**<br /><br /> -   Gras, italique ou gras italique<br />-   Utilisation de corps de texte<br />-   Utiliser dans la norme que contrôle Visual Studio<br />-   Utiliser dans les fenêtres Outil|**Apparaît sous la forme :** 12 pt Segoe UI<br /><br /> **Exemple visuel :**<br /><br /> ![Example of 133% Environment font heading](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202\-d\_EF133")|  
  
#### Police d'environnement 122 %  
  
|||  
|-|-|  
|**Utilisation :**<br /><br /> -   En\-têtes de section dans les boîtes de dialogue de signature<br />-   Nœuds principaux dans l'arborescence<br />-   Navigation de tabulation verticale<br /><br /> **Faire :** utiliser la casse de la phrase<br /><br /> **Ne pas faire :**<br /><br /> -   Gras, italique ou gras italique<br />-   Utilisation de corps de texte<br />-   Utiliser dans la norme que contrôle Visual Studio<br />-   Utiliser dans les fenêtres Outil|**Apparaît sous la forme :** 11 pt Segoe UI<br /><br /> **Exemple visuel :**<br /><br /> ![Example of 122% Environment font heading](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202\-e\_EF122")|  
  
#### Police d'environnement \+ gras  
  
|||  
|-|-|  
|**Utilisation :**<br /><br /> -   Étiquettes et des sous\-titres dans les boîtes de dialogue de signature<br />-   Étiquettes et des sous\-titres dans les rapports<br />-   Étiquettes et des sous\-titres dans le document et l'interface utilisateur<br /><br /> **Faire :**<br /><br /> -   Utilisez la casse de la phrase<br />-   Utiliser le poids en gras<br /><br /> **Ne pas faire :**<br /><br /> -   Italique ou gras italique<br />-   Utilisation de corps de texte<br />-   Utiliser dans la norme que contrôle Visual Studio<br />-   Utiliser dans les fenêtres Outil|**Apparaît sous la forme :** en gras 9 pt Segoe UI<br /><br /> **Exemple visuel :**<br /><br /> ![Example of Environment font &#43; Bold heading](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202\-f\_EFB")|  
  
#### Police d'environnement  
  
|||  
|-|-|  
|**Utilisation :** tous les autres types de texte<br /><br /> **Faire :** utiliser la casse de la phrase<br /><br /> **Pas :** italique ou gras italique|**Apparaît sous la forme :** 9 pt Segoe UI<br /><br /> **Exemple visuel :**<br /><br /> ![Example of Environment font](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202\-g\_EF")|  
  
### Marge intérieure et l'espacement  
 En\-têtes nécessitent d'espace autour d'elles pour leur donner l'accent appropriée. Cet espace varie selon la taille du point et ce qui est proche de l'en\-tête, par exemple une règle horizontale ou une ligne de texte dans la police d'environnement.  
  
-   La marge intérieure idéale pour un titre par lui\-même doit être 90 % de l'espace de hauteur de caractère majuscule. Par exemple, titre pt 28 Segoe UI Light a une hauteur de 26 pt, et la marge intérieure doit être environ 23 pt ou environ 31 pixels.  
  
-   Le moins d'espace autour d'un en\-tête doit être de 50 % de la hauteur de caractère majuscule. Moins d'espace peut être utilisé lorsqu'un titre est accompagné d'une règle ou un autre élément ajustement étroite.  
  
-   Texte gras police d'environnement doit respecter la marge intérieure et l'espacement de hauteur de ligne par défaut.  
  
## Voir aussi  
 [MSDN : Polices \(Windows\)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742483\(v=vs.85\).aspx)   
 [MSDN : Texte de l'Interface utilisateur \(Windows\)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx)