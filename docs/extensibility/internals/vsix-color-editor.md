---
title: "Éditeur de couleurs VSIX | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70879c5d-e0f0-4845-993c-2f4229869706
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7987d2b6d22893e82893755ed76fa5253aeb600c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="vsix-color-editor"></a>Éditeur de couleurs VSIX
L’outil Éditeur de couleurs Extension Visual Studio peut créer et modifier des couleurs personnalisées pour Visual Studio. L’outil peut également générer des clés de ressources de thème afin que les couleurs peuvent être utilisées dans le code. Cet outil est utile pour effectuer des couleurs pour une extension Visual Studio qui prend en charge les thèmes. Cet outil peut ouvrir des fichiers .pkgdef et .xml. Les thèmes Visual Studio (fichiers .vstheme) peuvent être utilisés avec l’éditeur de couleurs Extension Visual Studio en remplaçant l’extension de fichier .xml. En outre, les fichiers .vstheme peuvent être importées dans un fichier .xml en cours.  
  
 ![Héros d’éditeur de couleurs VSIX](../../extensibility/internals/media/vsix-color-editor-hero.png "héros d’éditeur de couleurs VSIX")  
  
 **Fichiers de définition de package**  
  
 Les fichiers de définition (.pkgdef) de package sont les fichiers qui définissent les thèmes. Les couleurs eux-mêmes sont stockés dans les fichiers .xml couleur de thème qui sont compilés dans un fichier .pkgdef. Les fichiers .pkgdef sont déployés sur les emplacements de recherche de Visual Studio, traités lors de l’exécution et fusionnées pour définir des thèmes.  
  
 **Jetons de couleur**  
  
 Un jeton de couleur se compose de quatre éléments :  
  
-   **Nom de la catégorie :** un regroupement logique pour un jeu de couleurs. Utiliser un nom de catégorie existant s’il existe déjà des couleurs qui sont spécifiques à l’élément souhaité de l’interface utilisateur, ou le groupe d’éléments d’interface utilisateur.  
  
-   **Nom du jeton :** un nom descriptif pour le jeton de couleur et les jeux de jeton. Jeux incluent en arrière-plan et les noms de jeton de premier plan (texte), ainsi que tous les États de leurs et ceux-ci doivent être nommés afin qu’il soit facile d’identifier les paires et les États auxquels ils s’appliquent à.  
  
-   **Couleur des valeurs (ou teintes) :** nécessaire pour chaque thème de couleur. Toujours créer en arrière-plan et le texte des valeurs de couleur par paires. Couleurs sont associés pour l’arrière-plan/premier plan afin que la couleur du texte (premier plan) est toujours accessible en lecture par rapport à la couleur d’arrière-plan sur lequel elle est dessinée. Ces couleurs sont liés et seront utilisés ensemble dans l’interface utilisateur. Si l’arrière-plan n’est pas destinée à être utilisé avec le texte, ne définissez pas une couleur de premier plan.  
  
-   **Nom de couleur système :** pour une utilisation dans les affichages de contraste élevé.  
  
## <a name="how-to-use-the-tool"></a>Comment utiliser l’outil  
 Autant que possible, et le cas échéant, des couleurs de Visual Studio existants doivent être réutilisés au lieu d’effectuer de nouvelles. Toutefois, pour les cas où aucun couleurs appropriées ne sont définies, les couleurs personnalisées doivent être créés pour conserver une thèmes extension compatible.  
  
 **Création de nouveaux jetons de couleur**  
  
 Pour créer des couleurs personnalisées à l’aide de l’éditeur de couleurs Extension Visual Studio, procédez comme suit :  
  
1.  Déterminez les noms de catégorie et le jeton pour les nouveaux jetons de couleur.  
  
2.  Choisissez les teintes que l’élément d’interface utilisateur utilisera pour chaque thème et de la couleur système pour le contraste élevé.  
  
3.  Utilisez l’éditeur de couleurs pour créer de nouveaux jetons de couleur.  
  
4.  Utiliser les couleurs dans une extension Visual Studio.  
  
5.  Tester les modifications dans Visual Studio.  
  
 **Étape 1 : Déterminer les noms de jeton pour les nouveaux jetons de couleur.**  
  
 Schéma de l’attribution de noms par défaut pour un VSColor est **[catégorie] [type d’interface utilisateur] [État]**. N’utilisez pas le mot « couleur » dans les noms de VSColor, car il est redondant.  
  
 Noms de catégorie fournissent des regroupements logiques et doivent être définies comme précisément que possible. Par exemple, le nom d’une fenêtre outil unique peut être un nom de catégorie, mais n’est pas le nom d’une équipe unité ou un projet d’entreprise dans sa totalité. Regroupement des entrées en catégories permet d’éviter toute confusion entre les couleurs portant le même nom.  
  
 Un nom de jeton doit clairement indiquer le type d’élément et les situations ou « état », pour lequel la couleur sera appliquée. Par exemple, un actif info-bulle **[type d’interface utilisateur]** peut être nommé «**DataTip**» et le **[State]** peut être nommé «**Active**, » résultant dans un nom de «**DataTipActive**. » Étant donné que les conseils de données texte, un premier plan et une couleur d’arrière-plan doivent être définies. À l’aide de combinaison arrière-plan/premier plan, l’éditeur de couleurs crée automatiquement les couleurs «**DataTipActive**» pour l’arrière-plan et «**DataTipActiveText**» pour le premier plan.  
  
 Si la partie de l’interface utilisateur a uniquement un seul état, le **[State]** partie du nom peut être omis. Par exemple, si une zone de recherche a une bordure, et il n’existe aucun changement d’état susceptible d’affecter les couleurs de la bordure, puis le nom de jeton de couleur de la bordure peut simplement être appelé «**SearchBoxBorder**. »  
  
 Certains noms d’état courantes sont les suivantes :  
  
-   Actif  
  
-   Inactif  
  
-   MouseOver  
  
-   MouseDown  
  
-   Selected  
  
-   Avec focus  
  
 Exemples de certains noms de jeton pour les parties d’un contrôle d’élément de liste :  
  
-   ListItem  
  
-   ListItemBorder  
  
-   ListItemMouseOver  
  
-   ListItemMouseOverBorder  
  
-   ListItemSelected  
  
-   ListItemSelectedBorder  
  
-   ListItemDisabled  
  
-   ListItemDisabledBorder  
  
 **Étape 2 : Choisissez les teintes que l’élément d’interface utilisateur utilisera pour chaque thème et de la couleur système pour le contraste élevé.**  
  
 Lors du choix des couleurs personnalisées pour l’interface utilisateur, sélectionnez un élément d’interface utilisateur similaires existant et utiliser ses couleurs comme base. Les couleurs des éléments d’interface utilisateur de l’emploi ont subi révision et le test, afin qu’ils fonctionnent correctement dans tous les thèmes et rechercher appropriées.  
  
 **Étape 3 : Utiliser l’éditeur de couleurs pour créer de nouveaux jetons de couleur.**  
  
 Lancer l’éditeur de couleurs et ouvrez ou créez un fichier .xml couleurs thème personnalisé. Sélectionnez **Modifier > nouvelle couleur** à partir du menu. Cette action ouvre une boîte de dialogue pour spécifier la catégorie et un ou plusieurs noms pour les entrées de couleur de cette catégorie :  
  
 ![Couleurs VSIX-nouvelle couleur](../../extensibility/internals/media/vsix-color-editor-new-color.png "couleurs VSIX-nouvelle couleur")  
  
 Sélectionnez une catégorie existante ou **nouvelle catégorie** pour créer une nouvelle catégorie. Une autre boîte de dialogue s’ouvre, créez un nouveau nom de catégorie :  
  
 ![Nouvelle catégorie de l’éditeur de couleurs VSIX](../../extensibility/internals/media/vsix-color-editor-new-category.png "nouvelle catégorie de l’éditeur de couleurs VSIX")  
  
 La nouvelle catégorie sera ensuite disponible dans le **nouvelle couleur** menu déroulant de catégorie. Après avoir choisi une catégorie, entrez un nom par ligne pour chaque nouveau jeton de couleur et sélectionnez « Créer » une fois :  
  
 ![Couleurs VSIX-nouvelle couleur rempli](../../extensibility/internals/media/vsix-color-editor-new-color-filled.png "couleurs VSIX-nouvelle couleur rempli")  
  
 Les valeurs de couleur sont affichées par paires d’arrière-plan/premier plan, avec « None », indiquant que la couleur n’a pas été définie. Remarque : si une couleur ne dispose pas d’un texte de couleur/paire de couleurs d’arrière-plan, puis que l’arrière-plan doit être défini.  
  
 ![Valeurs de couleur de l’éditeur de couleurs VSIX](../../extensibility/internals/media/vsix-color-editor-color-values.png "valeurs de couleur de l’éditeur de couleurs VSIX")  
  
 Pour modifier un jeton de couleur, sélectionnez une couleur pour le thème (colonne) de ce jeton. Ajouter la valeur de couleur en tapant une valeur de couleur hexadécimale sur 8 chiffres ARVB format, entrez un nom de couleur système dans la cellule ou à l’aide de la liste déroulante pour sélectionner la couleur souhaitée via un jeu de curseurs de couleur ou une liste des couleurs système.  
  
 ![Couleurs VSIX-modifier couleur](../../extensibility/internals/media/vsix-color-editor-edit-color.png "couleurs VSIX-modifier couleur")  
  
 ![Couleurs VSIX-arrière-plan](../../extensibility/internals/media/vsix-color-editor-background.png "couleurs VSIX-arrière-plan")  
  
 Pour les composants que vous n’avez pas besoin pour afficher le texte, entrez la valeur qu’une seule couleur : la couleur d’arrière-plan. Dans le cas contraire, entrez des valeurs pour la couleur d’arrière-plan et de texte, séparée par une barre oblique.  
  
 Lorsque vous entrez des valeurs pour le contraste élevé, entrez les noms de couleur système Windows valides. N’entrez pas de valeurs d’ARVB codées en dur. Vous pouvez afficher une liste des noms de couleurs système valide en sélectionnant « En arrière-plan : système » ou « premier plan : » dans les menus de liste déroulante de valeur de couleur. Lorsque vous créez des éléments qui ont des composants de texte, utilisez la paire de couleurs système en arrière-plan/texte correct ou le texte peut être illisible.  
  
 Lorsque vous avez terminé la création, la définition et modification les jetons de couleur, enregistrez-les dans le .xml souhaitée ou .pkgdef format. Les jetons de couleur fond ni, ni un ensemble de premier plan sera enregistré sous la forme des couleurs vides au format .xml, mais ignoré dans le format de .pkgdef. Une boîte de dialogue vous avertit de perte potentielle de couleur si vous tentez d’enregistrer des couleurs vides dans un fichier .pkgdef.  
  
 **Étape 4 : Utiliser les couleurs dans une extension Visual Studio.**  
  
 Après avoir défini la nouvelle couleur jetons, incluent le .pkgdef dans le fichier projet avec « Action de génération » la valeur « Contenu » et « Inclure dans VSIX » la valeur « True ».  
  
 ![Éditeur de couleurs VSIX pkgdef](../../extensibility/internals/media/vsix-color-editor-pkgdef.png "pkgdef de couleurs VSIX")  
  
 Dans l’éditeur Visual Studio Extension couleur, choisissez Fichier > Afficher le Code de ressource pour afficher le code qui est utilisé pour accéder aux personnalisé des couleurs dans l’interface utilisateur WPF.  
  
 ![Visionneuse de Code de ressources de l’éditeur de couleurs VSIX](../../extensibility/internals/media/vsix-color-editor-resource-code-viewer.png "visionneuse de Code de ressources de l’éditeur de couleurs VSIX")  
  
 Inclure ce code dans une classe statique dans le projet. Une référence à **Microsoft.VisualStudio.Shell.\< VSVersion >.0.dll** doit être ajouté au projet pour utiliser le **ThemeResourceKey** type.  
  
```csharp  
namespace MyCustomColors  
{  
    public static class MyCategory  
    {  
        #region Autogenerated resource keys  
        // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category.  
        public static readonly Guid Category = new Guid("faf7f3f9-9fe5-4dd3-9350-59679617dfbe");  
  
        private static ThemeResourceKey _MyColor1ColorKey;  
        private static ThemeResourceKey _MyColor1BrushKey;  
        private static ThemeResourceKey _MyColor1TextColorKey;  
        private static ThemeResourceKey _MyColor1TextBrushKey;  
        public static ThemeResourceKey MyColor1ColorKey { get { return _MyColor1ColorKey ?? (_MyColor1ColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundColor)); } }  
        public static ThemeResourceKey MyColor1BrushKey { get { return _MyColor1BrushKey ?? (_MyColor1BrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundBrush)); } }  
        public static ThemeResourceKey MyColor1TextColorKey { get { return _MyColor1TextColorKey ?? (_MyColor1TextColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundColor)); } }  
        public static ThemeResourceKey MyColor1TextBrushKey { get { return _MyColor1TextBrushKey ?? (_MyColor1TextBrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundBrush)); } }  
        #endregion  
    }  
}  
```  
  
 Cela permet d’accéder aux couleurs dans le code XAML et l’interface utilisateur répondre aux modifications de thème.  
  
```xaml  
<UserControl x:Class="NewTestProject.TestPackageControl" Name="MyToolWindow"  
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
             xmlns:ns="clr-namespace:MyCustomColors">  
  <Grid>  
    <TextBlock Background="{DynamicResource {x:Static ns:MyCategory.MyColor1BrushKey}}"  
               Foreground="{DynamicResource {x:Static ns:MyCategory.MyColor1TextBrushKey}}"  
      >Sample Text</TextBlock>  
  
  </Grid>  
</UserControl>  
```  
  
 **Étape 5 : Tester les modifications dans Visual Studio.**  
  
 L’éditeur de couleurs peut appliquer temporairement les jetons de couleur pour les instances en cours d’exécution de Visual Studio pour afficher les modifications en direct aux couleurs sans reconstruire le package d’extension. Pour ce faire, cliquez sur le bouton « Appliquer ce thème windows de Visual Studio en cours d’exécution » dans l’en-tête de chaque colonne de thème. Ce thème temporaire disparaîtra lorsque l’éditeur de couleurs VSIX est fermé.  
  
 ![Éditeur de couleurs VSIX appliquer](../../extensibility/internals/media/vsix-color-editor-apply.png "de couleurs VSIX s’appliquent.")  
  
 Pour rendre les modifications définitives, régénérer et redéployer de l’extension Visual Studio après l’ajout de nouvelles couleurs dans le fichier .pkgdef et l’écriture du code qui utilise ces couleurs. La reconstruction de l’extension Visual Studio fusionne les valeurs de Registre pour les nouvelles couleurs dans le reste des thèmes. Redémarrez Visual Studio, afficher l’interface utilisateur et vérifier que les nouvelles couleurs apparaissent comme prévu.  
  
## <a name="notes"></a>Remarques  
 Cet outil est destiné à être utilisé pour créer des couleurs personnalisées pour les thèmes Visual Studio préexistants, ou pour modifier les couleurs d’un thème personnalisé de Visual Studio. Pour créer des thèmes personnalisés Visual Studio terminées, téléchargez le [extension de l’éditeur de thème de couleur Visual Studio](http://visualstudiogallery.msdn.microsoft.com/6f4b51b6-5c6b-4a81-9cb5-f2daa560430b) à partir de la galerie d’Extensions Visual Studio.  
  
## <a name="sample-output"></a>Résultat de l'exemple  
 **Sortie de couleur XML**  
  
 Le fichier .xml généré par l’outil sera similaire à ceci :  
  
```xml  
<Themes>  
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">  
    <Category Name="CategoryName" GUID="{eee9d521-dac2-48d9-9a5e-5c625ba2040c}">  
      <Color Name="ColorName1">  
        <Background Type="CT_RAW" Source="FFFFFFFF" />  
      </Color>  
      <Color Name="ColorName2">  
        <Background Type="CT_RAW" Source="FFFFFFFF" />  
        <Foreground Type="CT_RAW" Source="FF000000" />  
      </Color>  
      <Color Name="ColorName3">  
        <Background Type="CT_RAW" Source="FFFF0000" />  
      </Color>  
      <Color Name="ColorName4">  
        <Background Type="CT_RAW" Source="FF000088" />  
        <Foreground Type="CT_RAW" Source="FFFFFFFF" />  
      </Color>  
    </Category>  
  </Theme>  
  <Theme Name="Dark" GUID="{1ded0138-47ce-435e-84ef-9ec1f439b749}">...</Theme>  
  <Theme Name="Blue" GUID="{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}">...</Theme>  
  <Theme Name="HighContrast" GUID="{a5c004b4-2d4b-494e-bf01-45fc492522c7}">...</Theme>  
</Themes>  
  
```  
  
 **Sortie de couleur PKGDEF**  
  
 Le fichier .pkgdef généré par l’outil sera similaire à ceci :  
  
```  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\CategoryName]  
"Data"=hex:78,00,00,00,0b,00,00,00,01,00,00,00,21,d5,e9,ee,c2,da,d9,48,9a,5e,5c,62,5b,a2,04,0c,04,00,00,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,31,01,ff,ff,ff,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,32,01,ff,ff,ff,ff,01,00,00,00,ff,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,33,01,ff,00,00,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,34,01,00,00,88,ff,01,ff,ff,ff,ff  
[$RootKey$\Themes\{1ded0138-47ce-435e-84ef-9ec1f439b749}\CategoryName]  
"Data"=hex:...  
[$RootKey$\Themes\{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}\CategoryName]  
"Data"=hex:...  
[$RootKey$\Themes\{a5c004b4-2d4b-494e-bf01-45fc492522c7}\CategoryName]  
"Data"=hex:...  
  
```  
  
 **Wrapper de clés de ressources c#**  
  
 Les clés de ressource de couleur générés par l’outil sera similaires à ceci :  
  
```csharp  
namespace MyNamespace  
{  
    public static class MyColors  
    {  
        #region Autogenerated resource keys  
        // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category.  
  
        public static string ColorName1ColorKey { get { return "ColorName1ColorKey"; } }  
        public static string ColorName1BrushKey { get { return "ColorName1BrushKey"; } }  
  
        public static string ColorName2ColorKey { get { return "ColorName2ColorKey"; } }  
        public static string ColorName2BrushKey { get { return "ColorName2BrushKey"; } }  
        public static string ColorName2TextColorKey { get { return "ColorName2TextColorKey"; } }  
        public static string ColorName2TextBrushKey { get { return "ColorName2TextBrushKey"; } }  
  
        public static string ColorName3ColorKey { get { return "ColorName4ColorKey"; } }  
        public static string ColorName3BrushKey { get { return "ColorName4BrushKey"; } }  
        public static string ColorName3TextColorKey { get { return "ColorName4TextColorKey"; } }  
        public static string ColorName3TextBrushKey { get { return "ColorName4TextBrushKey"; } }  
        #endregion  
    }  
}  
```  
  
 **Wrapper de dictionnaire de ressources WPF**  
  
 La couleur **ResourceDictionary** clés générées par l’outil sera similaires à ceci :  
  
```xaml  
<ResourceDictionary xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:colors="clr-namespace:MyNamespace">  
  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName1BrushKey}" Color="#FFFFFFFF" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName1ColorKey}" A="255" R="255" G="255" B="255" />  
  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2BrushKey}" Color="#FFFFFFFF" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName2ColorKey}" A="255" R="255" G="255" B="255" />  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2TextBrushKey}" Color="#FF000000" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName2TextColorKey}" A="255" R="0" G="0" B="0" />  
  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName3BrushKey}" Color="#FFFF0000" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName3ColorKey}" A="255" R="255" G="0" B="0" />  
  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4BrushKey}" Color="#FF000088" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName4ColorKey}" A="255" R="0" G="0" B="136" />  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4TextBrushKey}" Color="#FFFFFFFF" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName4TextColorKey}" A="255" R="255" G="255" B="255" />  
</ResourceDictionary>  
```