---
title: Polices et mise en forme pour Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4b68e103edcd3162b72bc5fddd4d1401b2430df3
ms.sourcegitcommit: b6dfa1bdf4c23c2e341754454bbd4758db2218e0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48863996"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Polices et mise en forme pour Visual Studio
##  <a name="BKMK_TheEnvironmentFont"></a> La police d’environnement
 Toutes les polices dans Visual Studio doivent être exposés à l’utilisateur pour la personnalisation. Cela s’effectue principalement via le **polices et couleurs** page dans le **Outils > Options** boîte de dialogue. Les trois principales catégories de paramètres de police sont :  
  
-   **Police d’environnement** -la police principale pour l’IDE (environnement de développement intégré), utilisée pour tous les éléments d’interface, y compris les boîtes de dialogue, les menus, les fenêtres Outil et les fenêtres de document. Par défaut, la police d’environnement est liée à une police système qui s’affiche en tant que 9 pt Segoe UI dans les versions actuelles de Windows. À l’aide d’une police pour tous les éléments d’interface permet de garantir une apparence de la police cohérente tout au long de l’IDE.  
  
-   **Éditeur de texte** -page d’éléments que surface dans le code et d’autres éditeurs de texte peuvent être personnalisés dans l’éditeur de texte dans **Outils > Options**.  
  
-   **Des regroupements spécifiques** -fenêtres du concepteur qui offrent la personnalisation de l’utilisateur de leurs éléments d’interface peut exposer des polices spécifiques à leur conception surface dans leur propre page Paramètres **Outils > Options**.  
  
### <a name="editor-font-customization-and-resizing"></a>Personnalisation de police de l’éditeur et le redimensionnement  
 Les utilisateurs souvent agrandir ou effectuer un zoom de la taille et/ou la couleur du texte dans l’éditeur en fonction de leurs préférences, indépendant de l’interface utilisateur général. Étant donné que la police d’environnement est utilisée sur les éléments qui peuvent apparaître au sein ou en tant que partie d’un éditeur/concepteur, il est important de noter le comportement attendu lorsqu’un de ces classifications de police est modifié.  
  
 Lors de la création des éléments d’interface utilisateur qui s’affichent dans l’éditeur, mais sont ne fait pas partie de la *contenu*, il est important d’utiliser la police d’environnement et pas la police du texte afin que redimensionnent des éléments de manière prévisible.  
  
1.  Texte du code dans l’éditeur, redimensionnez avec le paramètre de police de texte de code et répondre au niveau de zoom du texte de l’éditeur.  
  
2.  Tous les autres éléments de l’interface doivent être liées pour le paramètre de police d’environnement et répondent à toutes les modifications dans l’environnement globales. Cela inclut (mais n’est pas limité à) :  
  
    -   Texte dans les menus contextuels  
  
    -   Texte dans un ornement de l’éditeur, telles que le texte du menu ampoule, volet Recherche rapide de l’éditeur et accédez au volet  
  
    -   L’étiquette de texte dans les boîtes de dialogue, telles que **rechercher dans les fichiers** ou **refactoriser**  
  
### <a name="accessing-the-environment-font"></a>L’accès à la police d’environnement  
 Dans le code natif ou WinForms, la police d’environnement sont accessibles en appelant la méthode `IUIHostLocale::GetDialogFont` après l’analyse de l’interface à partir de la `SID_SUIHostLocale` service.  
  
 Pour Windows Presentation Foundation (WPF), dérivez votre classe de fenêtre de boîte de dialogue de l’interpréteur de commandes `DialogWindow` classe au lieu de WPF `Window` classe.  
  
 Dans XAML, le code ressemble à ceci :
  
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

code-behind :

```csharp
internal partial class WebConfigModificationWindow : DialogWindow  
{  
}  
```
  
 (Remplacez `Microsoft.VisualStudio.Shell.11.0` avec la version actuelle de la dll MPF.)  
  
 Pour afficher la boîte de dialogue, appelez «`ShowModal()`» sur la classe sur `ShowDialog()`. `ShowModal()` définit l’état modal correct dans l’interpréteur de commandes, garantit que la boîte de dialogue est centrée dans la fenêtre parente et ainsi de suite.  
  
 Le code est comme suit :  
  
```csharp
MyWindow window = new MyWindow();  
window.ShowModal()  
```
  
 `ShowModal` Retourne une valeur bool ? (valeur booléenne nullable) avec le `DialogResult`, qui peut être utilisé si nécessaire. La valeur renvoyée est true si la boîte de dialogue a été fermée avec **OK**.  
  
 Si vous avez besoin afficher certains UI WPF qui n’est pas une boîte de dialogue et qui est hébergé dans son propre `HwndSource`, comme une fenêtre contextuelle ou une fenêtre enfant WPF d’une fenêtre de fenêtre Win32/WinForms parent, vous devez définir le `FontFamily` et `FontSize` sur l’élément racine du e WPF élément. (L’interpréteur de commandes définit les propriétés de la fenêtre principale, mais ils ne seront pas héritées après un `HWND`). L’interpréteur de commandes fournit des ressources dans lequel les propriétés peuvent être liées, comme suit :  
  
```xaml
<Setter Property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />  
<Setter Property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />  
```
  
###  <a name="BKMK_Formatting"></a> Mise en forme (mise à l’échelle/mise en gras) référence  
 Certaines boîtes de dialogue requièrent un texte spécifique pour être en gras ou une taille différente de la police d’environnement. Auparavant, les polices supérieure à la police d’environnement étaient codées en tant que «`environment font +2`» ou similaire. À l’aide d’extraits de code fourni pour prendre en charge des moniteurs haute résolution et vérifiez que texte d’affichage apparaît toujours à la taille et le poids (comme Light ou Semilight).  
  
> **Remarque : Avant d’appliquer la mise en forme, assurez-vous que vous suivez les instructions figurant dans [style de texte](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).**  
  
 Pour mettre à l’échelle de la police d’environnement, définissez le style du TextBlock ou Label, comme indiqué. Chacune de ces extraits de code, elle est utilisées correctement, génère la police correcte, y compris les variations de taille et le poids appropriées.  
  
 Où «`vsui`» est une référence à l’espace de noms `Microsoft.VisualStudio.Shell`:  

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0" 
```
  
#### <a name="375-environment-font--light"></a>Police d’environnement 375 % + clair  
 **Apparaît sous la forme :** pt 34 Segoe UI Light  
 **Utilisation pour :** (rare) unique de marque l’interface utilisateur, comme dans la Page de démarrage

 **Code procédural :** où `textBlock` est un TextBlock précédemment défini et `label` est une étiquette définie précédemment :  
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);  
```
  
 **XAML :** définir le style du TextBlock ou Label comme indiqué.  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>  
```
  
#### <a name="310-environment-font--light"></a>Police d’environnement 310 % + clair  
 **Apparaît sous la forme :** pt 28 Segoe UI Light   
 **Utilisation pour :** signature grande boîte de dialogue, hormis principales titre dans les rapports  
  
 **Code procédural :** où `textBlock` est un TextBlock précédemment défini et `label` est une étiquette définie précédemment :  
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);    
```
  
 **XAML :** définir le style du TextBlock ou Label comme indiqué.  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>     
```
  
#### <a name="200-environment-font--semilight"></a>Police d’environnement 200 % + Semilight  
 **Apparaît sous la forme :** 18 pt Segoe UI Semilight    
 **Utilisation pour :** sous-titres, les titres des petites et moyennes des boîtes de dialogue  
  
 **Code procédural :** où `textBlock` est un TextBlock précédemment défini et `label` est une étiquette définie précédemment : 
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);    
```
  
 **XAML :** définir le style du TextBlock ou Label comme indiqué :  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>    
```
  
#### <a name="155-environment-font"></a>Police d’environnement 155 %  
 **Apparaît sous la forme :** 14 pt Segoe UI    
 **Utilisation pour :** des titres de section de document et l’interface utilisateur ou des rapports  
  
 **Code procédural :** où `textBlock` est un TextBlock précédemment défini et `label` est une étiquette définie précédemment :  
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);    
```
  
 **XAML :** définir le style du TextBlock ou Label comme indiqué :  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>  
```
  
#### <a name="133-environment-font"></a>Police d’environnement 133 %  
 **Apparaît sous la forme :** 12 pt Segoe UI    
 **Utilisation pour :** sous-titres plus petits dans les boîtes de dialogue de signature et de document et l’interface utilisateur  
  
 **Code procédural :** où `textBlock` est un TextBlock précédemment défini et `label` est une étiquette définie précédemment :  
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);    
```
  
 **XAML :** définir le style du TextBlock ou Label comme indiqué :  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>    
```
  
#### <a name="122-environment-font"></a>Police d’environnement 122 %  
 **Apparaît sous la forme :** 11 pt Segoe UI    
 **Utilisation pour :** section des en-têtes dans les boîtes de dialogue de signature, les nœuds dans l’arborescence, navigation par onglets vertical de haut  
  
 **Code procédural :** où `textBlock` est un TextBlock précédemment défini et `label` est une étiquette définie précédemment :  
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);    
```
  
 **XAML :** définir le style du TextBlock ou Label comme indiqué :  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>    
```
  
#### <a name="environment-font--bold"></a>Police d’environnement + gras  
 **Apparaît sous la forme :** en gras 9 pt Segoe UI    
 **Utilisation pour :** étiquettes et des sous-titres dans les boîtes de dialogue de signature, des rapports et des documents bien l’interface utilisateur  
  
 **Code procédural :** où `textBlock` est un TextBlock précédemment défini et `label` est une étiquette définie précédemment :  
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironmentBoldStyleKey);    
```
  
 **XAML :** définir le style du TextBlock ou Label comme indiqué :  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>    
```
  
### <a name="localizable-styles"></a>Styles localisables  
 Dans certains cas, les localisateurs doivent modifier les styles de police pour différents paramètres régionaux, tels que la suppression en gras à partir du texte pour les langues d’Extrême-Orient. Pour permettre la localisation des styles de police, ces styles doivent se trouver dans le fichier .resx. La meilleure façon d’effectuer cette opération et toujours modifier les styles de police dans le Concepteur de formulaires de Visual Studio consiste à définir explicitement les styles de police au moment du design. Bien que cela crée un objet police complète et peut sembler l’héritage des polices de parent, seule la propriété FontStyle sert à définir la police.  
  
 La solution consiste à raccorder le formulaire de boîte de dialogue `FontChanged` événement. Dans le `FontChanged` événement parcourir tous les contrôles et vérifier si leur format de police est définie. S’il est défini, remplacez-le par une nouvelle police en fonction de la police du formulaire et le style de police du contrôle précédent. Est un exemple de ce code :  
  
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
  
 À l’aide de ce code garantit que lorsque la police du formulaire est mis à jour, les polices des contrôles met à jour également. Cette méthode doit également être appelée depuis le constructeur du formulaire, car la boîte de dialogue peut échouer obtenir une instance de `IUIService` et `FontChanged` événement ne se déclenchera jamais. Raccordement `FontChanged` permettra de boîtes de dialogue à assimiler dynamiquement la nouvelle police même si la boîte de dialogue est déjà ouverte.  
  
### <a name="testing-the-environment-font"></a>La police d’environnement de test  
 Pour vous assurer que votre interface utilisateur à l’aide de la police d’environnement et qu’il respecte les paramètres de taille, ouvrez **Outils > Options > environnement > polices et couleurs** et sélectionnez « Police environnement » sous le « afficher les paramètres de : « menu déroulant.  
  
 ![Paramètres de polices et couleurs dans les outils &gt; boîte de dialogue Options](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "a_OptionsFonts-0201")<br />Paramètres de polices et couleurs dans les outils &gt; boîte de dialogue Options
  
 Définir la police à quelque chose de très différent de la valeur par défaut. Pour le rendre évidente qui ne met pas à jour l’interface utilisateur, choisissez une police avec empattements (par exemple « Times New Roman ») et définir une très grande taille. Ensuite, testez votre interface utilisateur pour vous assurer qu’il respecte l’environnement. Voici un exemple à l’aide de la boîte de dialogue licence :  
  
 ![Exemple de texte de l’interface utilisateur qui ne respecte pas la police d’environnement](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "b_WrongFontDialog-0201")<br />Exemple de texte de l’interface utilisateur qui ne respecte pas la police d’environnement
  
 Dans ce cas, « Informations utilisateur » et « Informations de produit » ne sont pas en respectant la police. Dans certains cas, cela peut être un choix de conception explicite, mais il peut être un bogue si la police explicite n’est pas spécifiée dans le cadre de la ligne rouge de spécifications.  
  
 Pour réinitialiser la police, cliquez sur « Par défaut » sous **Outils > Options > environnement > polices et couleurs**.  
  
##  <a name="BKMK_TextStyle"></a> Style de texte  
 Style de texte fait référence à la casse, le poids et la taille de police. Pour obtenir des conseils d’implémentation, consultez [la police d’environnement](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
### <a name="text-casing"></a>Casse du texte  
  
#### <a name="all-caps"></a>Tout en majuscules  
 N’utilisez pas tout en majuscules de titres ou des étiquettes dans Visual Studio.  
  
#### <a name="all-lowercase"></a>Tout en minuscules  
 N’utilisez pas tout en minuscules pour les titres ou des étiquettes dans Visual Studio.  
  
#### <a name="sentence-and-title-case"></a>Cas de phrase et le titre  
 Texte dans Visual Studio doit utiliser majuscule ou majuscule, selon la situation.  
  
|Cas d’utilisation du titre pour :|Utilisez la casse de la phrase pour :|  
|-------------------------|----------------------------|  
|Titres de la boîte de dialogue|Étiquettes|  
|Zones de groupe|Cases à cocher|  
|Éléments de menu|Cases d’option|  
|Éléments de menu contextuel|Éléments de liste|  
|Boutons|Barres d’état|  
|Étiquettes de table||  
|En-têtes de colonnes||  
|Info-bulles||  
  
##### <a name="title-case"></a>Première lettre en majuscule  
 Première lettre en majuscule est un style dans lequel les premières lettres de la plupart ou tous les mots dans une expression sont en majuscules. Dans Visual Studio, majuscule est utilisé pour le nombre d’éléments, y compris :  
  
-   **Info-bulles.** Exemple : « aperçu les éléments sélectionnés »  
  
-   **En-têtes de colonne.** Exemple : « réponse système »  
  
-   **Éléments de menu.** Exemple : « enregistrer tout »  
  
 Lorsque vous utilisez la première lettre en majuscule, voici les instructions pour mettre en majuscule de mots et de les laisser en minuscules :  
  
|Majuscules|Commentaires et des exemples|  
|---------------|---------------------------|  
|Tous les noms||  
|Tous les verbes|Y compris « Est » et autres formes de « pour être »|  
|Tous les adverbes|Y compris « À » et « When »|  
|Tous les adjectifs|Y compris « This » et « That »|  
|Tous les pronoms|Y compris le possessif « Sa » et «, » une contraction du pronom « it » et le verbe « est »|  
|Premiers et derniers mots, quelle que soit grammaticales||  
|Prépositions qui font partie d’une phrase verbale|« Closing Out tous les Windows » ou « Arrêt du système »|  
|Toutes les lettres d’un acronyme|HTML, XML, URL, IDE, RVB|  
|Le deuxième mot du mot composé, s’il s’agit d’un nom ou un adjectif d’approprié, ou si les mots ont le même poids|Accès en lecture/écriture de références croisées, des logiciels Microsoft avant, exécution|  
  
|Minuscules|Exemples|  
|---------------|--------------|  
|Le deuxième mot dans un mot composé, s’il s’agit d’une autre partie du message ou une expression verbale modifiant le premier mot|Procédures, décollage|  
|Articles, sauf si un est le premier mot dans le titre|un, une, le|  
|Coordonner les conjonctions|et, mais, pour, nor, ou|  
|Prépositions avec des mots de moins de quatre lettres en dehors d’une phrase verbale|dans, vers, en tant que pour hors, en haut de|  
|« Vers » lorsqu’il est utilisé dans une expression infinitive|« Comment mettre en forme votre disque dur »|  
  
##### <a name="sentence-case"></a>Début de phrase  
 Casse de la phrase est la méthode de mise en majuscules standard pour l’écriture dans lequel seul le premier mot de la phrase est en majuscules, ainsi que les noms propres et du pronom « I ». En règle générale, la casse de la phrase est plus facile pour une audience internationale pour la lecture, en particulier lorsque le contenu sera traduit par un ordinateur. Utilisez la casse de la phrase pour :  
  
1.  **Messages de barre d’état.** Ceux-ci sont simples, bref et fournissent uniquement les informations d’état. Exemple : « le chargement de fichier projet »  
  
2.  **Tous les autres éléments d’interface utilisateur**, y compris les étiquettes, les cases à cocher, cases d’option et les éléments de zone de liste. Exemple : « sélectionner tous les éléments dans la liste »  
  
### <a name="text-formatting"></a>Mise en forme de texte  
 Texte par défaut de mise en forme dans Visual Studio 2013 est contrôlé par [la police d’environnement](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont). Ce service permet de s’assurer une apparence de la police cohérente tout au long de l’IDE (environnement de développement intégré), et vous devez l’utiliser pour garantir une expérience cohérente pour vos utilisateurs.  
  
 La taille par défaut utilisée par le service de police de Visual Studio est fourni à partir de Windows et apparaît sous la forme 9 pt.  
  
 Vous pouvez mettre en forme la police d’environnement. Cette rubrique décrit comment et où utiliser des styles. Pour plus d’informations, reportez-vous à [la police d’environnement](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
#### <a name="bold-text"></a>Texte en gras  
 Texte en gras est utilisé avec parcimonie dans Visual Studio et doit être réservé pour :  
  
-   étiquettes de question dans les Assistants  
  
-   désignant le projet actif dans l’Explorateur de solutions  
  
-   substitution des valeurs dans la fenêtre d’outil Propriétés  
  
-   certains événements dans les listes déroulantes de l’éditeur Visual Basic  
  
-   contenu généré par le serveur dans la structure du document pour les pages web  
  
-   en-têtes de section dans la boîte de dialogue complexe ou d’interface utilisateur du Concepteur  
  
#### <a name="italics"></a>Italique  
 Visual Studio n’utilise pas de texte en italique Italique ou en gras.  
  
#### <a name="color"></a>Color  
  
-   Bleu est réservé pour les liens hypertexte (navigation et exécution des commandes) et ne doit jamais être utilisée pour l’orientation.  
  
-   En-têtes supérieure (police d’environnement x 155 % ou version supérieure) peuvent être en couleur à ces fins :  
  
    -   Pour fournir l’aspect visuel de la signature de l’interface utilisateur de Visual Studio  
  
    -   Pour attirer l’attention sur une zone spécifique  
  
    -   Pour offrir de relief à partir de la couleur du texte standard environnement/noir gris foncé  
  
-   Couleur dans les en-têtes doit tirer parti de Visual Studio marque couleurs existantes, principalement le principal violet, #FF68217A.  
  
-   Lorsque vous utilisez des couleurs dans les en-têtes, vous devez respecter les [les instructions de couleurs Windows](/windows/desktop/uxguide/vis-color), y compris le niveau de contraste et autres considérations d’accessibilité.  
  
### <a name="font-size"></a>Taille de police  
 Conception visuelle de l’interface utilisateur Studio propose une apparence plus claire avec davantage d’espace blanc. Si possible, les barres de titre et de chrome ont été réduites ou supprimés. Bien que la densité des informations est une exigence dans Visual Studio, typographie continue d’être important, en mettant l’accent sur Interligne plus ouvert et une variante de tailles de police et les poids.  
  
 Les tableaux ci-dessous inclut des détails de la conception et des exemples visuels pour les polices d’affichage utilisées dans Visual Studio. Certaines variantes de police d’affichage ont la taille et le poids, tels que Semilight ou Light, de manière irréversible dans leur apparence.  
  
 Extraits de code d’implémentation pour toutes les polices d’affichage se trouve dans [mise en forme (mise à l’échelle/mise en gras) référence](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting).  
  
#### <a name="375-environment-font--light"></a>Police d’environnement 375 % + clair  
  
|||  
|-|-|  
|**Utilisation :** rares. Unique interface uniquement.<br /><br /> **Procédez comme :**<br /><br /> -Utilisez la casse de la phrase<br />-Toujours utiliser léger<br /><br /> **Ne pas :**<br /><br /> -Utilisation de l’interface utilisateur autre que de la signature de l’interface utilisateur comme Page de démarrage<br />-En gras, italique ou gras italique<br />-Utilisation de corps de texte<br />-Utiliser dans les fenêtres Outil|**Apparaît sous la forme :** pt 34 Segoe UI Light<br /><br /> **Exemple visuel :**<br /><br /> *Pas utilisé actuellement. Peut être utilisé dans la Page de démarrage.*|  
  
#### <a name="310-environment-font--light"></a>Police d’environnement 310 % + clair  
  
|||  
|-|-|  
|**Utilisation :**<br /><br /> -Titre plus grande dans les boîtes de dialogue de signature<br />-Titre de rapport principal<br /><br /> **Procédez comme :**<br /><br /> -Utilisez la casse de la phrase<br />-Toujours utiliser léger<br /><br /> **Ne pas :**<br /><br /> -Utilisation de l’interface utilisateur autre que de la signature de l’interface utilisateur comme Page de démarrage<br />-En gras, italique ou gras italique<br />-Utilisation de corps de texte<br />-Utiliser dans les fenêtres Outil|**Apparaît sous la forme :** pt 28 Segoe UI Light<br /><br /> **Exemple visuel :**<br /><br /> ![Exemple de police d’environnement 310 % &#43; titre clair](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|  
  
#### <a name="200-environment-font--semilight"></a>Police d’environnement 200 % + Semilight  
  
|||  
|-|-|  
|**Utilisation :**<br /><br /> -Les sous-titres<br />-Titres des petites et moyennes des boîtes de dialogue<br /><br /> **Procédez comme :**<br /><br /> -Utilisez la casse de la phrase<br />-Toujours utiliser le poids de Semilight<br /><br /> **Ne pas :**<br /><br /> -En gras, italique ou gras italique<br />-Utilisation de corps de texte<br />-Utiliser dans les fenêtres Outil|**Apparaît sous la forme :** 18 pt Segoe UI Semillight<br /><br /> **Exemple visuel :**<br /><br /> ![Exemple de police d’environnement 200 % &#43; Semilight](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202-b_EF200")|  
  
#### <a name="155-environment-font"></a>Police d’environnement 155 %  
  
|||  
|-|-|  
|**Utilisation :**<br /><br /> -Les titres de section document bien l’interface utilisateur<br />-Rapports<br /><br /> **:** Majuscule<br /><br /> **Ne pas :**<br /><br /> -En gras, italique ou gras italique<br />-Utilisation de corps de texte<br />-Utiliser dans les contrôles standards de Visual Studio<br />-Utiliser dans les fenêtres Outil|**Apparaît sous la forme :** 14 pt Segoe UI<br /><br /> **Exemple visuel :**<br /><br /> ![Exemple de titre de police d’environnement 155 %](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202-c_EF155")|  
  
#### <a name="133-environment-font"></a>Police d’environnement 133 %  
  
|||  
|-|-|  
|**Utilisation :**<br /><br /> -Sous-titres plus petits dans les boîtes de dialogue de signature<br />-Sous-titres plus petits dans le document et l’interface utilisateur<br /><br /> **:** Majuscule<br /><br /> **Ne pas :**<br /><br /> -En gras, italique ou gras italique<br />-Utilisation de corps de texte<br />-Utiliser dans les contrôles standards de Visual Studio<br />-Utiliser dans les fenêtres Outil|**Apparaît sous la forme :** 12 pt Segoe UI<br /><br /> **Exemple visuel :**<br /><br /> ![Exemple de titre de police d’environnement 133 %](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202-d_EF133")|  
  
#### <a name="122-environment-font"></a>Police d’environnement 122 %  
  
|||  
|-|-|  
|**Utilisation :**<br /><br /> -En-têtes de section dans les boîtes de dialogue de signature<br />-Nœuds du plus haut dans l’arborescence<br />-Navigation par onglets vertical<br /><br /> **:** Majuscule<br /><br /> **Ne pas :**<br /><br /> -En gras, italique ou gras italique<br />-Utilisation de corps de texte<br />-Utiliser dans les contrôles standards de Visual Studio<br />-Utiliser dans les fenêtres Outil|**Apparaît sous la forme :** 11 pt Segoe UI<br /><br /> **Exemple visuel :**<br /><br /> ![Exemple de titre de police d’environnement 122 %](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202-e_EF122")|  
  
#### <a name="environment-font--bold"></a>Police d’environnement + gras  
  
|||  
|-|-|  
|**Utilisation :**<br /><br /> -Étiquettes et les sous-titres dans les boîtes de dialogue de signature<br />-Étiquettes et les sous-titres dans les rapports<br />-Étiquettes et les sous-titres dans le document et l’interface utilisateur<br /><br /> **Procédez comme :**<br /><br /> -Utilisez la casse de la phrase<br />-Utiliser le poids en gras<br /><br /> **Ne pas :**<br /><br /> -En italique ou gras italique<br />-Utilisation de corps de texte<br />-Utiliser dans les contrôles standards de Visual Studio<br />-Utiliser dans les fenêtres Outil|**Apparaît sous la forme :** en gras 9 pt Segoe UI<br /><br /> **Exemple visuel :**<br /><br /> ![Exemple de police d’environnement &#43; titre gras](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202-f_EFB")|  
  
#### <a name="environment-font"></a>Police d’environnement  
  
|||  
|-|-|  
|**Utilisation :** tous les autres textes<br /><br /> **:** Majuscule<br /><br /> **Ne :** italique ou gras italique|**Apparaît sous la forme :** 9 pt Segoe UI<br /><br /> **Exemple visuel :**<br /><br /> ![Exemple de police d’environnement](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202-g_EF")|  
  
### <a name="padding-and-spacing"></a>Marge intérieure et l’espacement  
 En-têtes nécessitent d’espace autour d’elles afin de leur donner l’importance approprié. Cet espace varie en fonction de la taille en points et les autres sont proche de l’en-tête, par exemple une barre horizontale ou une ligne de texte dans la police d’environnement.  
  
-   La marge intérieure idéale pour un en-tête par lui-même doit être 90 % de l’espace de hauteur des caractères majuscules. Par exemple, un titre de Segoe UI Light pt 28 a une hauteur de la limite de 26 pt, et la marge intérieure doit être environ 23 pt, ou environ 31 pixels.  
  
-   L’espace minimal autour d’un en-tête doit être 50 % de la hauteur des caractères majuscules. Moins d’espace peut servir quand un en-tête est accompagné d’une règle ou un autre élément étroite ajustement.  
  
-   Texte de police d’environnement en gras doit suivre la marge intérieure et l’espacement de hauteur de ligne par défaut.  
  
## <a name="see-also"></a>Voir aussi  
 [MSDN : Polices (Windows)](/windows/desktop/uxguide/vis-fonts)   
 [MSDN : Texte de l’Interface utilisateur (Windows)](/windows/desktop/uxguide/text-ui)