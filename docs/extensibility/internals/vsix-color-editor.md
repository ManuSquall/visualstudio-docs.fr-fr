---
title: VSIX Color Editor ( fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 70879c5d-e0f0-4845-993c-2f4229869706
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa3ed1f1a2a761a6602ac891eb78b5a5436abf92
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704040"
---
# <a name="vsix-color-editor"></a>Éditeur de couleur VSIX
L’outil Visual Studio Extension Color Editor peut créer et modifier des couleurs personnalisées pour Visual Studio. L’outil peut également générer des clés de ressources thématiques afin que les couleurs puissent être utilisées dans le code. Cet outil est utile pour faire des couleurs pour une extension Visual Studio qui prend en charge le thème. Cet outil peut ouvrir .pkgdef et .xml fichiers. Les thèmes Visual Studio (.vstheme fichiers) peuvent être utilisés avec le Visual Studio Extension Color Editor en changeant l’extension de fichier à .xml. En outre, les fichiers .vstheme peuvent être importés dans un fichier .xml en cours.

 ![Sélecteur de couleurs VSIX - Hero](../../extensibility/internals/media/vsix-color-editor-hero.png "Sélecteur de couleurs VSIX - Hero")

 **Fichiers de définition du package**

 Les fichiers de définition de paquet (.pkgdef) sont les fichiers qui définissent les thèmes. Les couleurs elles-mêmes sont stockées dans des fichiers de couleur thème .xml, qui sont compilés dans un fichier .pkgdef. Les fichiers .pkgdef sont déployés dans des endroits consultables Visual Studio, traités à l’heure de l’exécution et fusionnés pour définir des thèmes.

 **Jetons de couleur**

 Un jeton de couleur est composé de quatre éléments :

- **Nom de catégorie:** Un regroupement logique pour un ensemble de couleurs. Utilisez un nom de catégorie existant s’il existe déjà des couleurs spécifiques à l’élément d’interface utilisateur souhaité, ou un groupe d’éléments d’interface utilisateur.

- **Nom symbolique:** Un nom descriptif pour les ensembles de jetons de couleur et de jeton. Les ensembles comprennent des noms de jetons de fond et de premier plan (texte) ainsi que tous leurs états, et ceux-ci doivent être nommés de sorte qu’il soit facile d’identifier les paires et les états auxquels ils s’appliquent.

- **Valeurs de couleur (ou teintes) :** Nécessaire pour chaque thème coloré. Toujours créer des valeurs de couleur de fond et de texte par paires. Les couleurs sont appariées pour le fond/au premier plan de sorte que le texte (au premier plan) couleur est toujours lisible sur la couleur de fond sur laquelle il est dessiné. Ces couleurs sont liées et seront utilisées ensemble dans l’interface utilisateur. Si l’arrière-plan n’est pas destiné à une utilisation avec le texte, ne définissez pas une couleur de premier plan.

- **Nom de couleur du système:** Pour une utilisation dans les écrans à contraste élevé.

## <a name="how-to-use-the-tool"></a>Comment utiliser l’outil
 Dans la mesure du possible, et le cas échéant, les couleurs existantes visual Studio devraient être réutilisées au lieu d’en faire de nouvelles. Cependant, pour les cas où aucune couleur appropriée n’est définie, les couleurs personnalisées doivent être créées pour garder une extension de thème compatible.

 **Création de nouveaux jetons de couleur**

 Pour créer des couleurs personnalisées à l’aide de l’éditeur visual Studio Extension Color Editor, suivez ces étapes :

1. Déterminez la catégorie et les noms symboliques pour les nouveaux jetons de couleur.

2. Choisissez les teintes que l’élément d’interface utilisateur utilisera pour chaque thème et la couleur du système pour High Contrast.

3. Utilisez l’éditeur de couleurs pour créer de nouveaux jetons de couleur.

4. Utilisez les couleurs dans une extension Visual Studio.

5. Testez les changements dans Visual Studio.

   **Étape 1 : Déterminez la catégorie et les noms symboliques pour les nouveaux jetons de couleur.**

   Le système de nommage préféré d’un VSColor est **[catégorie] [type d’assurance-chômage] [État]**. N’utilisez pas le mot "couleur" dans les noms VSColor, car il est redondant.

   Les noms de catégorie fournissent des regroupements logiques et doivent être définis aussi étroitement que possible. Par exemple, le nom d’une fenêtre d’outil unique peut être un nom de catégorie, mais le nom de toute une unité d’affaires ou d’une équipe de projet ne l’est pas. Regrouper les entrées en catégories permet d’éviter la confusion entre les couleurs du même nom.

   Un nom symbolique doit indiquer clairement le type d’élément et les situations, ou « état », pour lesquels la couleur sera appliquée. Par exemple, un conseil de données active **[type d’interface utilisateur]** pourrait être nommé "**DataTip**" et le **[État]** pourrait être nommé "**Actif**", ce qui donne un nom couleur de "**DataTipActive**". Étant donné que les conseils de données ont du texte, une couleur de premier plan et une couleur de fond doivent être définies. En utilisant un fond /avant-plan d’appariement, l’éditeur de couleur va automatiquement créer les couleurs "**DataTipActive**" pour l’arrière-plan et "**DataTipActiveText**" pour le premier plan.

   Si le morceau de l’interface utilisateur n’a qu’un seul état, la partie **[de l’État]** du nom peut être omise. Par exemple, si une boîte de recherche a une bordure et qu’il n’y a pas de changement d’état qui affecterait la couleur de la frontière, alors le nom du jeton couleur de la frontière peut simplement être appelé «**SearchBoxBorder**».

   Voici quelques noms d’État courants :

- Actif

- Inactif

- MouseOver

- Mousedown

- Volumes sélectionnés

- Avec focus

  Exemples de quelques noms symboliques pour les parties d’un contrôle d’élément de liste :

- ListItem

- ListItemBorder (listitemBorder)

- ListItemMouseOver (en)

- ListItemMouseOverBorder

- ListItemSelected ListItemSelected ListItemSelected ListIte

- ListeItemSelectedBorder

- ListItemDisabled ListItemDisabled

- ListeItemDisabledBorder

  **Étape 2 : Choisissez les teintes que l’élément d’interface utilisateur utilisera pour chaque thème et la couleur du système pour High Contrast.**

  Lors du choix des couleurs personnalisées pour l’interface utilisateur, sélectionnez un élément d’interface utilisateur existant similaire, et utilisez ses couleurs comme base. Les couleurs pour les éléments d’interface utilisateur dans la boîte ont subi l’examen et les tests, de sorte qu’ils auront l’air approprié et se comportent correctement dans tous les thèmes.

  **Étape 3 : Utilisez l’éditeur de couleurs pour créer de nouveaux jetons de couleur.**

  Lancez l’éditeur de couleurs et ouvrez ou créez un nouveau fichier personnalisé couleurs thème .xml. Sélectionnez **Modifier > Nouvelle Couleur** dans le menu. Cela ouvre un dialogue pour spécifier la catégorie et un ou plusieurs noms pour les entrées de couleur dans cette catégorie:

  ![Sélecteur de couleurs VSIX - Nouvelle couleur](../../extensibility/internals/media/vsix-color-editor-new-color.png "Sélecteur de couleurs VSIX - Nouvelle couleur")

  Sélectionnez une catégorie existante ou sélectionnez **une nouvelle catégorie** pour créer une nouvelle catégorie. Un autre dialogue s’ouvrira, créant un nouveau nom de catégorie :

  ![Sélecteur de couleurs VSIX - Nouvelle catégorie](../../extensibility/internals/media/vsix-color-editor-new-category.png "Sélecteur de couleurs VSIX - Nouvelle catégorie")

  La nouvelle catégorie sera ensuite disponible dans le menu drop-down de la catégorie **Nouvelle Couleur.** Après avoir choisi une catégorie, entrez un nom par ligne pour chaque nouveau jeton de couleur et sélectionnez « Créer » une fois terminé :

  ![Sélecteur de couleurs VSIX - Remplissage par une nouvelle couleur](../../extensibility/internals/media/vsix-color-editor-new-color-filled.png "Sélecteur de couleurs VSIX - Remplissage par une nouvelle couleur")

  Les valeurs de couleur sont affichées dans les paires de fond/premier plan, avec "Aucun" indiquant que la couleur n’a pas été définie. Remarque : si une couleur n’a pas de couleur de texte/paire de couleurs de fond, alors seul l’arrière-plan doit être défini.

  ![Sélecteur de couleurs VSIX - Valeurs de couleur](../../extensibility/internals/media/vsix-color-editor-color-values.png "Sélecteur de couleurs VSIX - Valeurs de couleur")

  Pour modifier un jeton de couleur, sélectionnez une entrée de couleur pour le thème (colonne) de ce jeton. Ajoutez la valeur de couleur en tapant une valeur de couleur hex dans le format ARGB à 8 chiffres, en entrant un nom de couleur du système dans la cellule, ou en utilisant le menu de décrochage pour sélectionner la couleur désirée via un ensemble de curseurs de couleur ou une liste de couleurs du système.

  ![Sélecteur de couleurs VSIX - Modifier une couleur](../../extensibility/internals/media/vsix-color-editor-edit-color.png "Sélecteur de couleurs VSIX - Modifier une couleur")

  ![Sélecteur de couleurs VSIX - Arrière-plan](../../extensibility/internals/media/vsix-color-editor-background.png "Sélecteur de couleurs VSIX - Arrière-plan")

  Pour les composants qui n’ont pas besoin d’afficher du texte, entrez une seule valeur de couleur : la couleur de fond. Sinon, entrez les valeurs pour la couleur de fond et de texte, séparée par une barre oblique vers l’avant.

  Lors de l’entrée des valeurs pour High Contrast, entrez les noms de couleur valides du système Windows. N’entrez pas les valeurs ARGB codées en dur. Vous pouvez consulter une liste de noms de couleur système valides en sélectionnant "Background: System" ou "Foreground: System" à partir des menus de baisse de la valeur des couleurs. Lors de la création d’éléments qui ont des composants de texte, utilisez la paire de couleur de fond/système de texte correcte ou le texte peut être illisible.

  Lorsque vous avez terminé la création, le réglage et l’édition des jetons de couleur, enregistrez-les dans le format .xml ou .pkgdef souhaité. Les jetons de couleur sans arrière-plan ni un ensemble de premier plan seront enregistrés comme des couleurs vides en format .xml, mais jetés en format .pkgdef. Un dialogue vous avertira de la perte de couleur potentielle si vous essayez d’enregistrer les couleurs vides à un fichier .pkgdef.

  **Étape 4 : Utilisez les couleurs dans une extension Visual Studio.**

  Après avoir défini les nouveaux jetons de couleur, inclure le .pkgdef dans le fichier du projet avec "Build Action" réglé à "Contenu," et "Inclure dans VSIX" mis à "Vrai."

  ![Sélecteur de couleurs VSIX - pkgdef](../../extensibility/internals/media/vsix-color-editor-pkgdef.png "Sélecteur de couleurs VSIX - pkgdef")

  Dans l’éditeur visual Studio Extension Color Editor, choisissez File > View Resource Code pour afficher le code qui est utilisé pour accéder aux couleurs personnalisées dans l’interface utilisateur basée sur le WPF.

  ![Sélecteur de couleurs VSIX - Visionneuse du code de la ressource](../../extensibility/internals/media/vsix-color-editor-resource-code-viewer.png "Sélecteur de couleurs VSIX - Visionneuse du code de la ressource")

  Inclure ce code dans une classe statique dans le projet. Une référence à **Microsoft.VisualStudio.Shell.\< VSVersion>.0.dll** doit être ajouté au projet pour utiliser le type **ThemeResourceKey.**

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

 Cela permet d’accéder aux couleurs dans le code XAML et permet à l’interface utilisateur de répondre aux changements de thème.

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

 **Étape 5 : Testez les changements dans Visual Studio.**

 L’éditeur de couleur peut temporairement appliquer des jetons de couleur aux instances en cours d’exécution de Visual Studio pour voir les changements en direct aux couleurs sans reconstruire le paquet d’extension. Pour ce faire, cliquez sur le bouton " Appliquer ce thème aux fenêtres Visual Studio en cours d’exécution" situé sur l’en-tête de chaque colonne thème. Ce thème temporaire disparaîtra lorsque l’éditeur de couleurs VSIX sera fermé.

 ![Sélecteur de couleurs VSIX - Appliquer](../../extensibility/internals/media/vsix-color-editor-apply.png "Sélecteur de couleurs VSIX - Appliquer")

 Pour rendre les modifications permanentes, reconstruire et redéployer l’extension Visual Studio après avoir ajouté les nouvelles couleurs au fichier .pkgdef et l’écriture du code qui utilisera ces couleurs. La reconstruction de l’extension Visual Studio fusionnera les valeurs de registre des nouvelles couleurs dans le reste des thèmes. Ensuite, relancez Visual Studio, regardez l’interface utilisateur, et vérifiez que les nouvelles couleurs apparaissent comme prévu.

## <a name="notes"></a>Notes
 Cet outil est destiné à être utilisé pour créer des couleurs personnalisées pour les thèmes préexistants Visual Studio, ou pour l’édition des couleurs d’un thème Visual Studio personnalisé. Pour créer des thèmes Visual Studio personnalisés complets, téléchargez [l’extension Visual Studio Color Theme Editor](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.VisualStudio2015ColorThemeEditor) de la Visual Studio Extensions Gallery.

## <a name="sample-output"></a>Exemple de sortie
 **Sortie de couleur XML**

 Le fichier .xml généré par l’outil sera similaire à ceci :

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

 **Sortie couleur PKGDEF**

 Le fichier .pkgdef généré par l’outil sera similaire à ceci :

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

 **Emballage de clés de ressources CMD**

 Les clés de ressources en couleur générées par l’outil seront similaires à ceci :

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

 **Emballage de dictionnaire de ressource de WPF**

 Les touches **de couleur ResourceDictionary** générées par l’outil seront similaires à ceci :

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
