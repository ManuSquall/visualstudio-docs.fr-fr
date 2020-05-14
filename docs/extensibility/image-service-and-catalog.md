---
title: Service d’image et catalogue Microsoft Docs
ms.date: 04/01/2019
ms.topic: conceptual
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 79e1ccfad2a678656bcf09e37852532a8b28eb0e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710391"
---
# <a name="image-service-and-catalog"></a>Service d’image et catalogue
Ce livre de cuisine contient des conseils et des meilleures pratiques pour l’adoption du Visual Studio Image Service and Image Catalog introduit dans Visual Studio 2015.

 Le service d’image introduit dans Visual Studio 2015 permet aux développeurs d’obtenir les meilleures images pour l’appareil et le thème choisi par l’utilisateur pour afficher l’image, y compris le thème correct pour le contexte dans lequel ils sont affichés. L’adoption du service d’image aidera à éliminer les principaux points de douleur liés à la maintenance de l’actif, à la mise à l’échelle HDPI et au thème.

|||
|-|-|
|**Problèmes aujourd’hui**|**Solutions**|
|Mélange de couleur de fond|Mélange alpha intégré|
|Images thématiques (certaines)|Métadonnées thématiques|
|Mode contraste élevé|Ressources alternatives à contraste élevé|
|Besoin de ressources multiples pour différents modes DPI|Ressources sélectionnables avec repli vectoriel|
|Images en double|Un identifiant par concept d’image|

 Pourquoi adopter le service d’image?

- Toujours obtenir la dernière "pixel-parfait" image de Visual Studio

- Vous pouvez soumettre et utiliser vos propres images

- Pas besoin de tester vos images lorsque Windows ajoute une nouvelle mise à l’échelle DPI

- Résoudre les anciens obstacles architecturaux dans vos mises en œuvre

  La barre d’outils de la coque Visual Studio avant et après l’utilisation du service d’image :

  ![Service d’images avant et après](../extensibility/media/image-service-before-and-after.png "Service d’images avant et après")

## <a name="how-it-works"></a>Fonctionnement
 Le service d’image peut fournir une image bitmapped adaptée à n’importe quel cadre d’interface utilisateur pris en charge :

- WPF: BitmapSource

- WinForms: System.Drawing.Bitmap

- Win32: HBITMAP

  Diagramme de flux de service d’image

  ![Diagramme de flux du service d’images](../extensibility/media/image-service-flow-diagram.png "Diagramme de flux du service d’images")

  **Surnoms d’image**

  Un surnom d’image (ou surnom pour faire court) est une paire GUID/ID qui identifie de façon unique un actif d’image ou un actif de liste d’images dans la bibliothèque d’images.

  **Surnoms connus**

  L’ensemble de monikers d’image contenu dans le visual Studio Image Catalog et publiquement consommable par n’importe quel composant ou extension Visual Studio.

  **Fichiers de manifeste d’image**

  Les fichiers d’image manifeste (*.imagemanifest*) sont des fichiers XML qui définissent un ensemble d’actifs d’image, les surnoms qui représentent ces actifs, et l’image réelle ou des images qui représentent chaque actif. Les manifestes d’image peuvent définir des images autonomes ou des listes d’images pour le support d’interface utilisateur hérité. En outre, il existe des attributs qui peuvent être définis soit sur l’actif ou sur les images individuelles derrière chaque actif pour changer quand et comment ces actifs sont affichés.

  **Schéma manifeste d’image**

  Un manifeste d’image complet ressemble à ceci :

```xml
<ImageManifest>
      <!-- zero or one Symbols elements -->
      <Symbols>
        <!-- zero or more Import, Guid, ID, or String elements -->
      </Symbols>
      <!-- zero or one Images elements -->
      <Images>
        <!-- zero or more Image elements -->
      </Images>
      <!-- zero or one ImageLists elements -->
      <ImageLists>
        <!-- zero or more ImageList elements -->
      </ImageLists>
</ImageManifest>
```

 **Symboles**

 En tant qu’aide à la lisibilité et à l’entretien, le manifeste de l’image peut utiliser des symboles pour les valeurs d’attribut. Les symboles sont définis comme ceci :

```xml
<Symbols>
      <Import Manifest="manifest" />
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />
      <ID Name="cmdidSaveAll" Value="1000" />
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />
</Symbols>
```

|||
|-|-|
|**Sous-élément**|**Définition**|
|Importer|Importations les symboles du fichier manifeste donné pour utilisation dans le manifeste actuel|
|Guid|Le symbole représente un GUID et doit correspondre au formatage GUID|
|id|Le symbole représente une pièce d’identité et doit être un intégrateur non natif|
|String|Le symbole représente une valeur de chaîne arbitraire|

 Les symboles sont sensibles aux cas et référencés à l’aide d’une syntaxe de $(symbol-name) :

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 Certains symboles sont prédéfinis pour tous les manifestes. Ceux-ci peuvent être utilisés dans \<l’attribut Uri de la Source> ou \<Import> élément de référence sur la machine locale.

|||
|-|-|
|**Symbole**|**Description**|
|CommonProgramFiles|La valeur de la variable de l’environnement %CommonProgramFiles%|
|LocalAppData (localAppData)|La valeur de la variable de l’environnement %LocalAppData%|
|ManifesteFolder|Le dossier contenant le fichier manifeste|
|MyDocuments (en)|Le chemin complet du dossier Mes Documents de l’utilisateur actuel|
|ProgramFiles|La valeur de la variable de l’environnement % ProgramFiles %|
|Système|Le dossier *Windows-System32*|
|WinDir (WinDir)|La valeur de la variable de l’environnement %WinDir%|

 **Image**

 L’élément \<Image> définit une image qui peut être référencée par un surnom. Le GUID et l’ID pris ensemble forment le surnom d’image. Le surnom de l’image doit être unique dans toute la bibliothèque d’images. Si plus d’une image a un surnom donné, la première rencontrée lors de la construction de la bibliothèque est celle qui est conservée.

 Il doit contenir au moins une source. Les sources neutres en taille donneront les meilleurs résultats dans un large éventail de tailles, mais elles ne sont pas nécessaires. Si le service est demandé pour une image \<d’une taille non définie dans l’élément Image> et qu’il n’y a pas de source neutre sur mesure, le service choisira la meilleure source spécifique à la taille et l’échelle à la taille demandée.

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|||
|-|-|
|**Attribut**|**Définition**|
|Guid|[Requis] La partie GUID du surnom d’image|
|id|[Requis] La partie ID du surnom d’image|
|AutoriserColorInversion|[Optionnel, par défaut vrai] Indique si l’image peut avoir ses couleurs programmatiquement inversées lorsqu’elles sont utilisées sur un fond sombre.|

 **Source**

 L’élément \<Source> définit un actif unique de source d’image (XAML et PNG).

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|||
|-|-|
|**Attribut**|**Définition**|
|Uri|[Requis] Un URI qui définit d’où l’image peut être chargée. Les valeurs possibles sont les suivantes :<br /><br /> - Un [pack URI](/dotnet/framework/wpf/app-development/pack-uris-in-wpf) utilisant l’autorité application:///<br />- Une référence absolue des ressources composant<br />- Un chemin vers un fichier contenant une ressource autochtone|
|Arrière-plan|[Facultatif] Indique ce que sur le type de fond de la source est destinée à être utilisé.<br /><br /> Les valeurs possibles sont les suivantes :<br /><br /> *Lumière:* La source peut être utilisée sur un fond lumineux.<br /><br /> *Sombre:* La source peut être utilisée sur un fond sombre.<br /><br /> *HighContrast:* La source peut être utilisée sur n’importe quel fond en mode Contraste élevé.<br /><br /> *HighContrastLight:* La source peut être utilisée sur un fond lumineux en mode contraste élevé.<br /><br /> *HighContrastDark:* La source peut être utilisée sur un fond sombre en mode Contraste élevé.<br /><br /> Si l’attribut d’arrière-plan est omis, la source peut être utilisée sur n’importe quel fond.<br /><br /> Si Background is *Light*, *Dark*, *HighContrastLight*, ou *HighContrastDark*, les couleurs de la source ne sont jamais inversées. Si Background est omis ou réglé à *HighContrast*, l’inversion des couleurs de la source est contrôlée par l’attribut **AllowColorInversion** de l’image.|

Un \<élément source> peut avoir exactement l’un des sous-ensembles optionnels suivants :

||||
|-|-|-|
|**Élément**|**Attributs (tous requis)**|**Définition**|
|\<Taille>|Valeur|La source sera utilisée pour des images de la taille donnée (dans les unités de périphérique). L’image sera carrée.|
|\<SizeRange>|MinSize, MaxSize|La source sera utilisée pour les images de MinSize à MaxSize (en unités d’appareils) inclusivement. L’image sera carrée.|
|\<Dimensions>|Width, Height|La source sera utilisée pour des images de la largeur et de la hauteur données (dans les unités de périphérique).|
|\<DimensionRange>|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|La source sera utilisée pour les images de la largeur/hauteur minimale à la largeur/hauteur maximale (dans les unités de périphérique) inclusivement.|

 Un \<élément source> peut également \<avoir un sous-ensemble de> NativeResource en option, qui définit un \<> source qui est chargé à partir d’une assemblée autochtone plutôt qu’un assemblage géré.

```xml
<NativeResource Type="type" ID="int" />
```

|||
|-|-|
|**Attribut**|**Définition**|
|Type|[Requis] Le type de ressource indigène, soit XAML ou PNG|
|id|[Requis] La partie ID integer de la ressource autochtone|

 **Imagelist**

 L’élément \<ImageList> définit une collection d’images qui peuvent être retournées en une seule bande. La bande est construite sur demande, au besoin.

```xml
<ImageList>
      <ContainedImage Guid="guid" ID="int" External="true/false" />
      <!-- optional additional ContainedImage elements -->
 </ImageList>
```

|||
|-|-|
|**Attribut**|**Définition**|
|Guid|[Requis] La partie GUID du surnom d’image|
|id|[Requis] La partie ID du surnom d’image|
|Externe|[Optionnel, faux par défaut] Indique si le surnom d’image fait référence à une image dans le manifeste actuel.|

 Le surnom de l’image contenue n’a pas à référencer une image définie dans le manifeste actuel. Si l’image contenue ne peut pas être trouvée dans la bibliothèque d’images, une image blanche de placeholder sera utilisée à sa place.

## <a name="using-the-image-service"></a>Utilisation du service d’image

### <a name="first-steps-managed"></a>Premiers pas (gérés)
 Pour utiliser le service d’image, vous devez ajouter des références à certaines ou la totalité des assemblages suivants à votre projet :

- *Microsoft.VisualStudio.ImageCatalog.dll*

  - Nécessaire si vous utilisez le catalogue d’images **intégré KnownMonikers**.

- *Microsoft.VisualStudio.Imaging.dll*

  - Nécessaire si vous utilisez **CrispImage** et **ImageThemingUtilities** dans votre interface utilisateur WPF.

- *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll*

  - Nécessaire si vous utilisez les types **ImageMoniker** et **ImageAttributes.**

  - **EmbedInteropTypes** devrait être mis à vrai.

- *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime (en anglais seulement)*

  - Nécessaire si vous utilisez le type **IVsImageService2.**

  - **EmbedInteropTypes** devrait être mis à vrai.

- *Microsoft.VisualStudio.Utilities.dll*

  - Nécessaire si vous utilisez le **BrushToColorConverter** pour **l’ImageThemingUtilities.ImageBackgroundColor** dans votre interface utilisateur WPF.

- *Microsoft.VisualStudio.Shell. \<VSVersion>.0*

  - Nécessaire si vous utilisez le type **IVsUIObject.**

- *Microsoft.VisualStudio.Shell.Interop.10.0.dll*

  - Nécessaire si vous utilisez les aides à l’interface utilisateur liées à WinForms.

  - **EmbedInteropTypes** devrait être mis à vrai

### <a name="first-steps-native"></a>Premiers pas (natif)
 Pour utiliser le service d’image, vous devez inclure une partie ou la totalité des en-têtes suivants à votre projet :

- **ConnuImageIds.h**

  - Exigé si vous utilisez le catalogue d’images **intégré KnownMonikers**, mais ne peut pas utiliser le type **ImageMoniker,** comme lors du retour des valeurs d’IVsHierarchy **GetGuidProperty** ou **GetProperty** appels.

- **ConnuMonikers.h**

  - Nécessaire si vous utilisez le catalogue d’images **intégré KnownMonikers**.

- **ImageParameters140.h**

  - Nécessaire si vous utilisez les types **ImageMoniker** et **ImageAttributes.**

- **VSShell140.h**

  - Nécessaire si vous utilisez le type **IVsImageService2.**

- **ImageLesutilities.h**

  - Nécessaire si vous n’êtes pas en mesure de laisser le service d’image gérer le thème pour vous.

  - N’utilisez pas cet en-tête si le service d’image peut gérer votre thème d’image.

::: moniker range="vs-2017"
- **VSUIDPIHelper.h**

  - Nécessaire si vous utilisez les aides DPI pour obtenir le DPI actuel.

::: moniker-end

::: moniker range=">=vs-2019"
- **VsDpiAwareness.h**

  - Nécessaire si vous utilisez les aides de sensibilisation DPI pour obtenir le DPI actuel.

::: moniker-end

## <a name="how-do-i-write-new-wpf-ui"></a>Comment puis-je écrire une nouvelle interface utilisateur WPF ?

1. Commencez par ajouter les références d’assemblage requises dans la section des premières étapes ci-dessus de votre projet. Vous n’avez pas besoin de les ajouter tous, alors ajoutez juste les références dont vous avez besoin. (Remarque: si vous utilisez ou avez accès à **des couleurs** au lieu de **brosses**, alors vous pouvez sauter la référence aux **services publics**, puisque vous n’aurez pas besoin du convertisseur.)

2. Sélectionnez l’image désirée et obtenez son surnom. Utilisez un **KnownMoniker**, ou utilisez votre propre si vous avez vos propres images personnalisées et surnoms.

3. Ajoutez **CrispImages** à votre XAML. (Voir l’exemple ci-dessous.)

4. Définissez la propriété **ImageThemingUtilities.ImageBackgroundColor** dans votre hiérarchie d’interface utilisateur. (Cela doit être réglé à l’endroit où la couleur de fond est connue, pas nécessairement sur le **CrispImage**.) (Voir l’exemple ci-dessous.)

```xaml
<Window
  x:Class="WpfApplication.MainWindow"
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  xmlns:imaging="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"
  xmlns:theming="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Imaging"
  xmlns:utilities="clr-namespace:Microsoft.Internal.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"
  xmlns:catalog="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.ImageCatalog"
  Title="MainWindow" Height="350" Width="525" UseLayoutRounding="True">
  <Window.Resources>
    <utilities:BrushToColorConverter x:Key="BrushToColorConverter"/>
  </Window.Resources>
  <StackPanel Background="White" VerticalAlignment="Center"
    theming:ImageThemingUtilities.ImageBackgroundColor="{Binding Background, RelativeSource={RelativeSource Self}, Converter={StaticResource BrushToColorConverter}}">
    <imaging:CrispImage Width="16" Height="16" Moniker="{x:Static catalog:KnownMonikers.MoveUp}" />
  </StackPanel>
</Window>
```

 **Comment mettre à jour l’interface utilisateur WPF existante ?**

 La mise à jour de l’interface utilisateur WPF existante est un processus relativement simple qui se compose de trois étapes de base :

1. Remplacez \<tous les éléments de> \<d’image dans votre interface utilisateur par des éléments> CrispImage.

2. Modifier tous les attributs Source aux attributs Moniker.

    - Si l’image ne change jamais et que vous utilisez **KnownMonikers**, puis statiquement lier cette propriété à la **KnownMoniker**. (Voir l’exemple ci-dessus.)

    - Si l’image ne change jamais et que vous utilisez votre propre image personnalisée, alors vous liez statiquement à votre propre surnom.

    - Si l’image peut changer, liez l’attribut Moniker à une propriété de code qui informe sur les modifications de propriété.

3. Quelque part dans la hiérarchie de l’interface utilisateur, définissez **ImageThemingUtilities.ImageBackgroundColor** pour vous assurer que l’inversion de couleur fonctionne correctement.

    - Cela pourrait nécessiter l’utilisation de la classe **BrushToColorConverter.** (Voir l’exemple ci-dessus.)

## <a name="how-do-i-update-win32-ui"></a>Comment mettre à jour l’interface utilisateur Win32 ?
 Ajoutez ce qui suit à votre code le cas échéant pour remplacer le chargement brut des images. Changez de valeur pour le retour des HBITMAP par rapport aux HICONs par rapport à HIMAGELIST au besoin.

 **Obtenez le service d’image**

```cpp
CComPtr<IVsImageService2> spImgSvc;
CGlobalServiceProvider::HrQueryService(SID_SVsImageService, &spImgSvc);
```

 **Demande de l’image**

::: moniker range="vs-2017"

```cpp
ImageAttributes attr = { 0 };
attr.StructSize      = sizeof(attributes);
attr.Format          = DF_Win32;
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST
attr.ImageType       = IT_Bitmap;
attr.LogicalWidth    = 16;
attr.LogicalHeight   = 16;
attr.Dpi             = VsUI::DpiHelper::GetDeviceDpiX();
// Desired RGBA color, if you don't use this, don't set IAF_Background below
attr.Background      = 0xFFFFFFFF;
attr.Flags           = IAF_RequiredFlags | IAF_Background;

CComPtr<IVsUIObject> spImg;
// Replace this KnownMoniker with your desired ImageMoniker
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);
```

::: moniker-end

::: moniker range=">=vs-2019"

```cpp
UINT dpiX, dpiY;
HWND hwnd = // get the HWND where the image will be displayed
VsUI::CDpiAwareness::GetDpiForWindow(hwnd, &dpiX, &dpiY);

ImageAttributes attr = { 0 };
attr.StructSize      = sizeof(attributes);
attr.Format          = DF_Win32;
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST
attr.ImageType       = IT_Bitmap;
attr.LogicalWidth    = 16;
attr.LogicalHeight   = 16;
attr.Dpi             = dpiX;
// Desired RGBA color, if you don't use this, don't set IAF_Background below
attr.Background      = 0xFFFFFFFF;
attr.Flags           = IAF_RequiredFlags | IAF_Background;

CComPtr<IVsUIObject> spImg;
// Replace this KnownMoniker with your desired ImageMoniker
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);
```

::: moniker-end

## <a name="how-do-i-update-winforms-ui"></a>Comment mettre à jour l’interface utilisateur WinForms ?
 Ajoutez ce qui suit à votre code le cas échéant pour remplacer le chargement brut des images. Changez de valeur pour le retour de Bitmaps par rapport aux icônes au besoin.

 **Utile à l’aide de l’instruction**

```csharp
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;
```

 **Obtenez le service d’image**

```csharp
// This or your preferred way of querying for Visual Studio services
IVsImageService2 imageService = (IVsImageService2)Package.GetGlobalService(typeof(SVsImageService));

```

 **Demander l’image**

::: moniker range="vs-2017"

```csharp
ImageAttributes attributes = new ImageAttributes
{
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),
    // IT_Bitmap for Bitmap, IT_Icon for Icon, IT_ImageList for ImageList
    ImageType     = (uint)_UIImageType.IT_Bitmap,
    Format        = (uint)_UIDataFormat.DF_WinForms,
    LogicalWidth  = 16,
    LogicalHeight = 16,
    Dpi           = (int)DpiHelper.DeviceDpiX;
    // Desired RGBA color, if you don't use this, don't set IAF_Background below
    Background    = 0xFFFFFFFF,
    Flags         = unchecked((uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background),
};

// Replace this KnownMoniker with your desired ImageMoniker
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);

Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj);    // Use this if you need an icon
```

::: moniker-end

::: moniker range=">=vs-2019"

```csharp
Control control = // get the control where the image will be displayed

ImageAttributes attributes = new ImageAttributes
{
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),
    // IT_Bitmap for Bitmap, IT_Icon for Icon, IT_ImageList for ImageList
    ImageType     = (uint)_UIImageType.IT_Bitmap,
    Format        = (uint)_UIDataFormat.DF_WinForms,
    LogicalWidth  = 16,
    LogicalHeight = 16,
    Dpi           = (int)DpiAwareness.GetWindowDpi(control.Handle);
    // Desired RGBA color, if you don't use this, don't set IAF_Background below
    Background    = 0xFFFFFFFF,
    Flags         = unchecked((uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background),
};

// Replace this KnownMoniker with your desired ImageMoniker
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);

Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj);    // Use this if you need an icon
```

::: moniker-end

## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>Comment puis-je utiliser des surnoms d’image dans une nouvelle fenêtre d’outil ?
 Le modèle de projet de paquet VSIX a été mis à jour pour Visual Studio 2015. Pour créer une nouvelle fenêtre d’outil, cliquez à droite sur le projet VSIX et **sélectionnez Ajouter** > **un nouvel article** (**Ctrl**+**Shift**+**A**). Sous le nœud Extensibility pour la langue du projet, sélectionnez **Custom Tool Window,** donnez un nom à la fenêtre d’outil et appuyez sur le bouton **Ajouter.**

 Ce sont les endroits clés pour utiliser des surnoms dans une fenêtre d’outils. Suivez les instructions pour chacun :

1. L’onglet fenêtre d’outil lorsque les onglets deviennent assez petits (également utilisés dans le commutateur de fenêtre **Ctrl**+**Tab).**

    Ajoutez cette ligne au constructeur pour la classe qui dérive du type **ToolWindowPane** :

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   this.BitmapImageMoniker = KnownMonikers.Blank;
   ```

2. La commande d’ouvrir la fenêtre d’outil.

    Dans le fichier *.vsct* pour le paquet, modifiez le bouton de commande de la fenêtre d’outil :

   ```xml
   <Button guid="guidPackageCmdSet" id="CommandId" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <!-- Replace this KnownMoniker with your desired ImageMoniker -->
     <Icon guid="ImageCatalogGuid" id="Blank" />
     <!-- Add this -->
     <CommandFlag>IconIsMoniker</CommandFlag>
     <Strings>
       <ButtonText>MyToolWindow</ButtonText>
     </Strings>
   </Button>
   ```

   **Comment puis-je utiliser des surnoms d’image dans une fenêtre d’outils existante ?**

   La mise à jour d’une fenêtre d’outil existante pour utiliser des surnoms d’image est similaire aux étapes pour créer une nouvelle fenêtre d’outil.

   Ce sont les endroits clés pour utiliser des surnoms dans une fenêtre d’outils. Suivez les instructions pour chacun :

3. L’onglet fenêtre d’outil lorsque les onglets deviennent assez petits (également utilisés dans le commutateur de fenêtre **Ctrl**+**Tab).**

   1. Supprimer ces lignes (si elles existent) dans le constructeur pour la classe qui dérive du type **ToolWindowPane:**

       ```csharp
       this.BitmapResourceID = <Value>;
       this.BitmapIndex = <Value>;
       ```

   2. Voir l’étape #1 du "Comment puis-je utiliser des surnoms d’image dans une nouvelle fenêtre d’outils?" section ci-dessus.

4. La commande d’ouvrir la fenêtre d’outil.

   - Voir l’étape #2 du "Comment puis-je utiliser des surnoms d’image dans une nouvelle fenêtre d’outils?" section ci-dessus.

## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>Comment puis-je utiliser des surnoms d’image dans un fichier .vsct ?
 Mettez à jour votre fichier *.vsct* comme indiqué par les lignes commentées ci-dessous:

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <!--  Include the definitions for images included in the VS image catalog -->
  <Include href="KnownImageIds.vsct"/>
  <Commands package="guidMyPackage">
    <Buttons>
      <Button guid="guidMyCommandSet" id="cmdidMyCommand" priority="0x0000" type="Button">
        <!-- Add an Icon element, changing the attributes to match the image moniker you want to use.
             In this case, we're using the Guid for the VS image catalog.
             Change the id attribute to be the ID of the desired image moniker. -->
        <Icon guid="ImageCatalogGuid" id="OpenFolder" />
        <CommandFlag>DynamicVisibility</CommandFlag>
        <CommandFlag>DefaultInvisible</CommandFlag>
        <CommandFlag>DefaultDisabled</CommandFlag>
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>IconAndText</CommandFlag>
        <!-- Add the IconIsMoniker CommandFlag -->
        <CommandFlag>IconIsMoniker</CommandFlag>
        <Strings>
          <ButtonText>Quick Fixes...</ButtonText>
          <CommandName>Show Quick Fixes</CommandName>
          <CanonicalName>ShowQuickFixes</CanonicalName>
          <LocCanonicalName>ShowQuickFixes</LocCanonicalName>
        </Strings>
      </Button>
    </Buttons>
  </Commands>
  <!-- It is recommended that you remove <Bitmap> elements that are no longer used in the vsct file -->
  <Symbols>
    <GuidSymbol name="guidMyPackage"    value="{1491e936-6ffe-474e-8371-30e5920d8fdd}" />
    <GuidSymbol name="guidMyCommandSet" value="{10347de4-69a9-47f4-a950-d3301f6d2bc7}">
      <IDSymbol name="cmdidMyCommand" value="0x9437" />
    </GuidSymbol>
  </Symbols>
</CommandTable>
```

 **Que faire si mon fichier .vsct doit également être lu par les anciennes versions de Visual Studio?**

 Les anciennes versions de Visual Studio ne reconnaissent pas le drapeau de commande **IconIsMoniker.** Vous pouvez utiliser des images du service d’image sur des versions de Visual Studio qui le prennent en charge, mais continuer à utiliser des images à l’ancienne sur les anciennes versions de Visual Studio. Pour ce faire, vous laisseriez le fichier *.vsct* inchangé (et donc compatible avec les anciennes versions de Visual Studio), et créer un fichier CSV (valeurs séparées par virgule) que les cartes des paires GUID/ID définies dans bitmaps d’un \<fichier *.vsct*> élément aux paires de paires DE paires GUID/ID.

 Le format du fichier CSV cartographique est :

```
Icon guid, Icon id, Moniker guid, Moniker id
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200
```

 Le fichier CSV est déployé avec le paquet et son emplacement est spécifié par la propriété **IconMappingFilename** de l’attribut du paquet **ProvideMenuResource** :

```csharp
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]
```

 **L’IconMappingFilename** est soit un chemin relatif implicitement enraciné à $PackageFolder$ (comme dans l’exemple ci-dessus), soit un chemin absolu explicitement enraciné dans un répertoire défini par une variable de l’environnement, comme *«%UserProfile% 'dir1'dir2'MyMappingFile.csv"*.

## <a name="how-do-i-port-a-project-system"></a>Comment puis-je porter un système de projet?
 **Comment fournir ImageMonikers pour un projet**

1. Mettre en **œuvre VSHPROPID_SupportsIconMonikers** sur **iVsHierarchy**du projet , et le retour vrai.

2. Implémentez soit **VSHPROPID_IconMonikerImageList** (si le projet initial utilisé **VSHPROPID_IconImgList**) ou **VSHPROPID_IconMonikerGuid**, **VSHPROPID_IconMonikerId**, **VSHPROPID_OpenFolderIconMonikerGuid**, **VSHPROPID_OpenFolderIconMonikerId** (si le projet original utilisé **VSHPROPID_IconHandle** et **VSHPROPID_OpenFolderIconHandle**).

3. Modifier la mise en œuvre des VSHPROPID originaux pour les icônes afin de créer des versions « héritées » des icônes si les points d’extension les demandent. **IVsImageService2** fournit la fonctionnalité nécessaire pour obtenir ces icônes

   **Exigences supplémentaires pour les saveurs du projet VB/C**

   Ne mettez en œuvre **VSHPROPID_SupportsIconMonikers** si vous détectez que votre projet est la saveur la **plus externe**. Sinon, la saveur extérieure réelle peut ne pas soutenir les surnoms d’image en réalité, et votre saveur de base pourrait effectivement "cacher" des images personnalisées.

   **Comment puis-je utiliser des surnoms d’image dans CPS ?**

   La configuration d’images personnalisées dans CPS (Common Project System) peut être effectuée manuellement ou via un modèle d’élément qui vient avec le système de projet Extensibility SDK.

   **Utilisation du système de projet Extensibility SDK**

   Suivez les instructions de [Fournir des icônes personnalisées pour le type de type de projet/élément](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md) pour personnaliser vos images CPS. Plus d’informations sur CPS peuvent être trouvées à [Visual Studio Project Project extensibility documentation](https://github.com/Microsoft/VSProjectSystem)

   **Utiliser manuellement ImageMonikers**

4. Implémentez et exportez l’interface **IProjectTreeModifier** dans votre système de projet.

5. Déterminez **le nom d’image knownMoniker** ou personnalisé que vous souhaitez utiliser.

6. Dans la méthode **ApplyModifications,** faites ce qui suit quelque part dans la méthode avant de retourner le nouvel arbre, semblable à l’exemple ci-dessous :

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());
   ```

7. Si vous créez un nouvel arbre, vous pouvez définir les images personnalisées en passant dans les surnoms souhaités dans la méthode NewTree, similaire à l’exemple ci-dessous:

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   ProjectImageMoniker icon         = KnownMonikers.FolderClosed.ToProjectSystemType();
   ProjectImageMoniker expandedIcon = KnownMonikers.FolderOpened.ToProjectSystemType();

   return this.ProjectTreeFactory.Value.NewTree(/*caption*/<value>,
                                                /*filePath*/<value>,
                                                /*browseObjectProperties*/<value>,
                                                icon,
                                                expandedIcon);
   ```

## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>Comment puis-je passer d’une bande d’image réelle à une bande d’image basée sur le surnom ?
 **J’ai besoin de soutenir HIMAGELISTs**

 S’il existe déjà une bande d’image existante pour votre code que vous souhaitez mettre à jour pour utiliser le service d’image, mais que vous êtes limité par des API qui nécessitent de passer autour des listes d’images, vous pouvez toujours obtenir les avantages du service d’image. Pour créer une bande d’image basée sur le surnom, suivez les étapes ci-dessous pour créer un manifeste à partir de surnoms existants.

1. Exécutez l’outil **ManifestFromResources,** en le passant la bande d’image. Cela générera un manifeste pour la bande.

   - Recommandé: fournir un nom non par défaut pour le manifeste en fonction de son utilisation.

2. Si vous utilisez uniquement **KnownMonikers**, puis faire ce qui suit:

   - Remplacez \<la section Images> du \<manifeste par Images/>.

   - Supprimer tous les ID sous-image (tout ce qui a le \<nom imagestrip>_).

   - Recommandé : renommer le symbole AssetsGuid et le symbole de bande d’image en fonction de son utilisation.

   - Remplacez chaque **GUID de ContainedImage**par $(ImageCatalogGuid), remplacez\<l’ID de chaque Contenu **par**$(> de surnom) et ajoutez l’attribut Externe "vrai" à chaque **ContenuImage**

       - \<surnom> devrait être remplacé par le **KnownMoniker** qui correspond à l’image, mais avec les "KnownMonikers." retiré du nom.

   - Ajoutez <Import ManifestMD"$(ManifestFolder)\\<Relative install dir path\>to 'Microsoft.VisualStudio.ImageCatalog.imagemanifest" /\*> en \<haut de la section Symboles>.

       - Le chemin relatif est déterminé par l’emplacement de déploiement défini dans la configuration de l’auteur pour le manifeste.

3. Exécutez l’outil **ManifestToCode** pour générer des emballages afin que le code existant dispose d’un surnom qu’il peut utiliser pour interroger le service d’image pour la bande d’image.

   - Recommandé : fournir des noms non-responsables pour les emballages et les espaces de nom adaptés à leur utilisation.

4. Faites tous les ajouts, la mise en place de la rédaction / déploiement, et d’autres modifications de code pour travailler avec le service d’image et les nouveaux fichiers.

   Exemple manifeste, y compris les images internes et externes pour voir à quoi il devrait ressembler :

```xml
<?xml version="1.0"?>
<ImageManifest
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">

  <Symbols>
    <!-- This needs to be the relative path from your manifest to the ImageCatalog's manifest
         where $(ManifestFolder) is the deployed location of this manifest. -->
    <Import Manifest="$(ManifestFolder)\<RelPath>\Microsoft.VisualStudio.ImageCatalog.imagemanifest" />

    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" />
    <Guid Name="ImageGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />
    <Guid Name="ImageStripGuid" Value="{9c84a570-d9a7-4052-a340-188fb276f973}" />
    <ID Name="MyImage_0" Value="100" />
    <ID Name="MyImage_1" Value="101" />
    <ID Name="InternalList" Value="1001" />
    <ID Name="ExternalList" Value="1002" />
  </Symbols>

  <Images>
    <Image Guid="$(ImageGuid)" ID="$(MyImage_0)">
      <Source Uri="$(Resources)/MyImage_0.png">
        <Size Value="16" />
      </Source>
    </Image>
    <Image Guid="$(ImageGuid)" ID="$(MyImage_1)">
      <Source Uri="$(Resources)/MyImage_1.png">
        <Size Value="16" />
      </Source>
    </Image>
  </Images>

  <ImageLists>
    <ImageList Guid="$(ImageStripGuid)" ID="$(InternalList)">
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_0)" />
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_1)" />
    </ImageList>
    <ImageList Guid="$(ImageStripGuid)" ID="$(ExternalList)">
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusError)" External="true" />
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusWarning)" External="true" />
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusInformation)" External="true" />
    </ImageList>
  </ImageLists>

</ImageManifest>
```

 **Je n’ai pas besoin de soutenir HIMAGELISTs**

1. Déterminez l’ensemble de **KnownMonikers** qui correspondent aux images dans votre bande d’image, ou créez vos propres surnoms pour les images dans votre bande d’image.

2. Mettez à jour toute cartographie que vous avez utilisée pour obtenir l’image à l’index requis dans la bande d’image pour utiliser les surnoms à la place.

3. Mettez à jour votre code pour utiliser le service d’image pour demander des surnoms via la cartographie mise à jour. (Cela peut signifier la mise à jour de **CrispImages** pour le code géré, ou la demande de HBITMAPs ou HICONs du service d’image et de les transmettre pour le code natif.)

## <a name="testing-your-images"></a>Testez vos images
 Vous pouvez utiliser l’outil Image Library Viewer pour tester vos manifestes d’image pour vous assurer que tout est rédigé correctement. Vous pouvez trouver l’outil dans le [Visual Studio 2015 SDK](visual-studio-sdk.md). La documentation pour cet outil et d’autres peut être trouvée [ici](/visualstudio/extensibility/internals/vssdk-utilities?view=vs-2015).

## <a name="additional-resources"></a>Ressources supplémentaires

### <a name="samples"></a>Exemples
 Plusieurs des échantillons visual Studio sur GitHub ont été mis à jour pour montrer comment utiliser le service d’image dans le cadre de divers points d’extéabilité Visual Studio.

 Vérifiez [http://github.com/Microsoft/VSSDK-Extensibility-Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples) les derniers échantillons.

### <a name="tooling"></a>Outils
 Un ensemble d’outils de support pour le service d’image a été créé pour aider à créer/mettre à jour l’interface utilisateur qui fonctionne avec le service d’image. Pour plus d’informations sur chaque outil, consultez la documentation qui vient avec les outils. Les outils sont inclus dans le cadre du [Visual Studio 2015 SDK](visual-studio-sdk.md).

 **ManifesteDeresources**

 L’outil Manifest from Resources prend une liste de ressources d’image (PNG ou XAML) et génère un fichier manifeste d’image pour l’utilisation de ces images avec le service d’image.

 **ManifestToCode (en)**

 L’outil Manifeste to Code prend un fichier manifeste d’image et génère un fichier d’emballage pour le référencement des valeurs manifestes dans les fichiers de code (C, C ou VB) ou *.vsct.*

 **ImageLibraryViewer**

 L’outil Image Library Viewer peut charger des manifestes d’image et permet à l’utilisateur de les manipuler de la même manière Visual Studio serait pour s’assurer que le manifeste est rédigé correctement. L’utilisateur peut modifier l’arrière-plan, les tailles, le paramètre DPI, le contraste élevé et d’autres paramètres. Il affiche également des informations de chargement pour trouver des erreurs dans les manifestes et affiche des informations source pour chaque image dans le manifeste.

## <a name="faq"></a>Questions fréquentes (FAQ)

- Y a-t-il des dépendances \<que vous devez inclure lors du chargement de référence inclure.Microsoft.VisualStudio. Interop.14.0.DesignTime" />?

  - Set EmbedInteropTypes "vrai" sur tous les DLLs interop.

- Comment déployer un manifeste d’image avec mon extension ?

  - Ajoutez le fichier *.imagemanifest* à votre projet.

  - Définissez «Inclure dans VSIX» à Vrai.

- Je met à jour mon système de projets CPS. Qu’est-il arrivé à **ImageName** et **StockIconService**?

  - Ceux-ci ont été supprimés lorsque CPS a été mis à jour pour utiliser des surnoms. Vous n’avez plus besoin d’appeler le **StockIconService**, il suffit de passer le **KnownMoniker** désiré à la méthode ou la propriété en utilisant la méthode **d’extension ToProjectSystemType()** dans les services publics CPS. Vous pouvez trouver une cartographie de **ImageName** à **KnownMonikers** ci-dessous:

    |||
    |-|-|
    |**ImageName**|**ConnuMoniker**|
    |ImageName.OfflineWebApp|ConnuImageIds.Web|
    |ImageName.WebReferencesFolder|ConnuImageIds.Web|
    |ImageName.OpenReferenceFolder|ConnuImageIds.FolderOpened|
    |ImageName.ReferenceFolder|ConnuImageIds.Reference|
    |ImageName.Référence|ConnuImageIds.Reference|
    |ImageName.SdlWebReference|ConnuImageIds.WebReferenceFolder|
    |ImageName.DiscoWebReference|ConnuImageIds.DynamicDiscoveryDocument|
    |ImageName.Folder (en)|ConnuImageIds.FolderClosed|
    |ImageName.OpenFolder|ConnuImageIds.FolderOpened|
    |ImageName.ExcludFolder|ConnuImageIds.HiddenFolderClosed|
    |ImageName.OpenExcludedFolder|ConnuImageIds.HiddenFolderOpened|
    |ImageName.ExcludFile|ConnuImageIds.HiddenFile|
    |ImageName.DependentFile|ConnuImageIds.GenerateFile|
    |ImageName.MissingFile|ConnuImageIds.DocumentWarning|
    |ImageName.WindowsForm|ConnuImageIds.WindowsForm|
    |ImageName.WindowsUserControl|ConnuImageIds.UserControl|
    |ImageName.WindowsComponent|ConnuImageIds.ComponentFile|
    |ImageName.XmlSchema|ConnuImageIds.XMLSchema|
    |ImageName.XmlFile|ConnuImageIds.XMLFile|
    |ImageName.WebForm|ConnuImageIds.Web|
    |ImageName.WebService|ConnuImageIds.WebService|
    |ImageName.WebUserControl|ConnuImageIds.WebUserControl|
    |ImageName.WebCustomUserControl|ConnuImageIds.WebCustomControl|
    |ImageName.AspPage|ConnuImageIds.ASPFile|
    |ImageName.GlobalApplicationClass (en)|ConnuImageIds.SettingsFile|
    |ImageName.WebConfig|ConnuImageIds.ConfigurationFile|
    |ImageName.HtmlPage|KnownImageIds.HTMLFile|
    |Feuille imageName.Style|KnownImageIds.StyleSheet (en)|
    |ImageName.ScriptFile|ConnuImageIds.JSScript|
    |ImageName.TextFile|ConnuImageIds.Document|
    |ImageName.SettingsFile|ConnuImageIds.Paramètres|
    |ImageName.Ressources|ConnuImageIds.DocumentGroup|
    |ImageName.Bitmap|ConnuImageIds.Image|
    |ImageName.Icône|ConnuImageIds.IconFile|
    |ImageName.Image|ConnuImageIds.Image|
    |ImageName.ImageMap|ConnuImageIds.ImageMapFile|
    |ImageName.XWorld|ConnuImageIds.XWorldFile|
    |ImageName.Audio|ConnuImageIds.Sound|
    |ImageName.Vidéo|ConnuImageIds.Media|
    |ImageName.Cab|ConnuImageIds.CABProject|
    |ImageName.Jar|ConnuImageIds.JARFile|
    |ImageName.DataEnvironment|ConnuImageIds.DataTable|
    |ImageName.PreviewFile|ConnuImageIds.Report|
    |ImageName.DanglingReference|ConnuImageIds.ReferenceWarning|
    |ImageName.XsltFile|ConnuImageIds.XSLTransforme|
    |ImageName.Cursor|ConnuImageIds.CursorFile|
    |ImageName.AppDesignerFolder|ConnuImageIds.Property|
    |ImageName.Data (en)|ConnueImageIds.Database|
    |ImageName.Application|KnownImageIds.Application (en)|
    |ImageName.DataSet (en anglais)|ConnuImageIds.DatabaseGroup|
    |ImageName.Pfx|ConnuImageIds.Certificate|
    |ImageName.Snk|ConnuImageIds.Rule|
    |ImageName.VisualBasicProject|ConnuImageIds.VBProjectNode|
    |ImageName.CSharpProject|ConnuImageIds.CSProjectNode|
    |ImageName.Empty|ConnuImageIds.Blank|
    |ImageName.MissingFolder|ConnuImageIds.FolderOffline|
    |ImageName.SharedImportReference|KnownImageIds.SharedProject|
    |ImageName.SharedProjectCs|KnownImageIds.CSSharedProject|
    |ImageName.SharedProjectVc|KnownImageIds.CPPSharedProject|
    |ImageName.SharedProjectJs|ConnuImageIds.JSSharedProject|
    |ImageName.CSharpCodeFile|ConnuImageIds.CSFileNode|
    |ImageName.VisualBasicCodeFile|ConnuImageIds.VBFileNode|

  - Je met à jour mon fournisseur de liste d’achèvement. Qu’est-ce que **les connaisseurs** correspondent aux anciennes valeurs **StandardGlyphGroup** et **StandardGlyph** ?

    ||||
    |-|-|-|
    |GlyphGroupClass|GlyphItemPublic (en)|ClassPublic|
    |GlyphGroupClass|GlyphItemInternal|ClassInternal|
    |GlyphGroupClass|GlyphItemFriend|ClassInternal|
    |GlyphGroupClass|GlyphItem Protégé|ClasseProtectée|
    |GlyphGroupClass|GlyphItemPrivate|ClassPrivate (ClassPrivate)|
    |GlyphGroupClass|GlyphItemShortcut|ClassShortcut|
    |GlyphGroupConstant|GlyphItemPublic (en)|ConstantPublic (en)|
    |GlyphGroupConstant|GlyphItemInternal|ConstantInternal (constantInternal)|
    |GlyphGroupConstant|GlyphItemFriend|ConstantInternal (constantInternal)|
    |GlyphGroupConstant|GlyphItem Protégé|Constant Protégé|
    |GlyphGroupConstant|GlyphItemPrivate|ConstantPrivate|
    |GlyphGroupConstant|GlyphItemShortcut|ConstantShortcut|
    |GlyphGroupDelegate|GlyphItemPublic (en)|DéléguéPublic|
    |GlyphGroupDelegate|GlyphItemInternal|DéléguéInternal|
    |GlyphGroupDelegate|GlyphItemFriend|DéléguéInternal|
    |GlyphGroupDelegate|GlyphItem Protégé|Délégué Protégé|
    |GlyphGroupDelegate|GlyphItemPrivate|DéléguéPrivate|
    |GlyphGroupDelegate|GlyphItemShortcut|DéléguéShortcut|
    |GlyphGroupEnum|GlyphItemPublic (en)|ÉnumérationPublic|
    |GlyphGroupEnum|GlyphItemInternal|ÉnumérationInternal|
    |GlyphGroupEnum|GlyphItemFriend|ÉnumérationInternal|
    |GlyphGroupEnum|GlyphItem Protégé|ÉnumérationProté|
    |GlyphGroupEnum|GlyphItemPrivate|ÉnumérationPrivate|
    |GlyphGroupEnum|GlyphItemShortcut|ÉnumérationShortcut|
    |GlyphGroupEnumMember|GlyphItemPublic (en)|ÉnumérationItemPublic|
    |GlyphGroupEnumMember|GlyphItemInternal|ÉnumérationItemInternal|
    |GlyphGroupEnumMember|GlyphItemFriend|ÉnumérationItemInternal|
    |GlyphGroupEnumMember|GlyphItem Protégé|ÉnumérationItemProtectée|
    |GlyphGroupEnumMember|GlyphItemPrivate|ÉnumérationItemPrivate|
    |GlyphGroupEnumMember|GlyphItemShortcut|ÉnumérationItemShortcut|
    |GlyphGroupEvent|GlyphItemPublic (en)|ÉvénementPublic|
    |GlyphGroupEvent|GlyphItemInternal|ÉvénementInternal|
    |GlyphGroupEvent|GlyphItemFriend|ÉvénementInternal|
    |GlyphGroupEvent|GlyphItem Protégé|ÉvénementProtecté|
    |GlyphGroupEvent|GlyphItemPrivate|EventPrivate|
    |GlyphGroupEvent|GlyphItemShortcut|EventShortcut|
    |GlyphGroupException|GlyphItemPublic (en)|ExceptionPublic|
    |GlyphGroupException|GlyphItemInternal|ExceptionInternal|
    |GlyphGroupException|GlyphItemFriend|ExceptionInternal|
    |GlyphGroupException|GlyphItem Protégé|ExceptionProtectée|
    |GlyphGroupException|GlyphItemPrivate|ExceptionPrivate|
    |GlyphGroupException|GlyphItemShortcut|ExceptionShortcut|
    |GlyphGroupField (en anglais seulement)|GlyphItemPublic (en)|FieldPublic (fieldPublic)|
    |GlyphGroupField (en anglais seulement)|GlyphItemInternal|FieldInternal (FieldInternal)|
    |GlyphGroupField (en anglais seulement)|GlyphItemFriend|FieldInternal (FieldInternal)|
    |GlyphGroupField (en anglais seulement)|GlyphItem Protégé|FieldProtected FieldProtected FieldProtected FieldProtect|
    |GlyphGroupField (en anglais seulement)|GlyphItemPrivate|FieldPrivate (FieldPrivate)|
    |GlyphGroupField (en anglais seulement)|GlyphItemShortcut|FieldShortcut (FieldShortcut)|
    |GlyphGroupInterface|GlyphItemPublic (en)|InterfacePublic|
    |GlyphGroupInterface|GlyphItemInternal|InterfaceInternal|
    |GlyphGroupInterface|GlyphItemFriend|InterfaceInternal|
    |GlyphGroupInterface|GlyphItem Protégé|InterfaceProtectée|
    |GlyphGroupInterface|GlyphItemPrivate|InterfacePrivate|
    |GlyphGroupInterface|GlyphItemShortcut|InterfaceShortcut|
    |GlyphGroupMacro|GlyphItemPublic (en)|MacroPublic (MacroPublic)|
    |GlyphGroupMacro|GlyphItemInternal|MacroInternal MacroInternal MacroInternal MacroInter|
    |GlyphGroupMacro|GlyphItemFriend|MacroInternal MacroInternal MacroInternal MacroInter|
    |GlyphGroupMacro|GlyphItem Protégé|MacroProtégée|
    |GlyphGroupMacro|GlyphItemPrivate|MacroPrivate MacroPrivate|
    |GlyphGroupMacro|GlyphItemShortcut|MacroShortcut MacroShortcut|
    |GlyphGroupMap|GlyphItemPublic (en)|MapPublic (en)|
    |GlyphGroupMap|GlyphItemInternal|CarteInternal|
    |GlyphGroupMap|GlyphItemFriend|CarteInternal|
    |GlyphGroupMap|GlyphItem Protégé|CarteProtectée|
    |GlyphGroupMap|GlyphItemPrivate|MapPrivate (en)|
    |GlyphGroupMap|GlyphItemShortcut|MapShortcut|
    |GlyphGroupMapItem|GlyphItemPublic (en)|MapItemPublic (en)|
    |GlyphGroupMapItem|GlyphItemInternal|MapItemInternal|
    |GlyphGroupMapItem|GlyphItemFriend|MapItemInternal|
    |GlyphGroupMapItem|GlyphItem Protégé|MapItemProté|
    |GlyphGroupMapItem|GlyphItemPrivate|MapItemPrivate|
    |GlyphGroupMapItem|GlyphItemShortcut|MapItemShortcut|
    |GlyphGroupMethod|GlyphItemPublic (en)|MéthodePublic|
    |GlyphGroupMethod|GlyphItemInternal|MéthodeInternal|
    |GlyphGroupMethod|GlyphItemFriend|MéthodeInternal|
    |GlyphGroupMethod|GlyphItem Protégé|MethodProtected|
    |GlyphGroupMethod|GlyphItemPrivate|MéthodePrivate|
    |GlyphGroupMethod|GlyphItemShortcut|MéthodeShortcut|
    |GlyphGroupOverload (en anglais seulement)|GlyphItemPublic (en)|MéthodePublic|
    |GlyphGroupOverload (en anglais seulement)|GlyphItemInternal|MéthodeInternal|
    |GlyphGroupOverload (en anglais seulement)|GlyphItemFriend|MéthodeInternal|
    |GlyphGroupOverload (en anglais seulement)|GlyphItem Protégé|MethodProtected|
    |GlyphGroupOverload (en anglais seulement)|GlyphItemPrivate|MéthodePrivate|
    |GlyphGroupOverload (en anglais seulement)|GlyphItemShortcut|MéthodeShortcut|
    |GlyphGroupModule|GlyphItemPublic (en)|ModulePublic|
    |GlyphGroupModule|GlyphItemInternal|ModuleInternal|
    |GlyphGroupModule|GlyphItemFriend|ModuleInternal|
    |GlyphGroupModule|GlyphItem Protégé|Module Protégé|
    |GlyphGroupModule|GlyphItemPrivate|ModulePrivate|
    |GlyphGroupModule|GlyphItemShortcut|ModuleShortcut|
    |GlyphGroupNamespace|GlyphItemPublic (en)|NamespacePublic|
    |GlyphGroupNamespace|GlyphItemInternal|NamespaceInternal|
    |GlyphGroupNamespace|GlyphItemFriend|NamespaceInternal|
    |GlyphGroupNamespace|GlyphItem Protégé|NamespaceProtected|
    |GlyphGroupNamespace|GlyphItemPrivate|NamespacePrivate|
    |GlyphGroupNamespace|GlyphItemShortcut|NamespaceShortcut|
    |GlyphGroupOperator GlyphGroupOperator|GlyphItemPublic (en)|OpérateurPublic|
    |GlyphGroupOperator GlyphGroupOperator|GlyphItemInternal|OpérateurInternal|
    |GlyphGroupOperator GlyphGroupOperator|GlyphItemFriend|OpérateurInternal|
    |GlyphGroupOperator GlyphGroupOperator|GlyphItem Protégé|Opérateur Protégé|
    |GlyphGroupOperator GlyphGroupOperator|GlyphItemPrivate|OperatorPrivate (en)|
    |GlyphGroupOperator GlyphGroupOperator|GlyphItemShortcut|OpérateurShortcut|
    |GlyphGroupProperty|GlyphItemPublic (en)|PropriétéPublic|
    |GlyphGroupProperty|GlyphItemInternal|PropriétéInternal|
    |GlyphGroupProperty|GlyphItemFriend|PropriétéInternal|
    |GlyphGroupProperty|GlyphItem Protégé|Propriété Protégée|
    |GlyphGroupProperty|GlyphItemPrivate|PropriétéPrivate|
    |GlyphGroupProperty|GlyphItemShortcut|PropriétéShortcut|
    |GlyphGroupStruct|GlyphItemPublic (en)|StructurePublic|
    |GlyphGroupStruct|GlyphItemInternal|StructureInternal|
    |GlyphGroupStruct|GlyphItemFriend|StructureInternal|
    |GlyphGroupStruct|GlyphItem Protégé|StructureProtectée|
    |GlyphGroupStruct|GlyphItemPrivate|StructurePrivate|
    |GlyphGroupStruct|GlyphItemShortcut|StructureShortcut|
    |GlyphGroupTemplate|GlyphItemPublic (en)|TemplatePublic (en)|
    |GlyphGroupTemplate|GlyphItemInternal|TemplateInternal|
    |GlyphGroupTemplate|GlyphItemFriend|TemplateInternal|
    |GlyphGroupTemplate|GlyphItem Protégé|TemplateProtected|
    |GlyphGroupTemplate|GlyphItemPrivate|TemplatePrivate (templatePrivate)|
    |GlyphGroupTemplate|GlyphItemShortcut|TemplateShortcut|
    |GlyphGroupTypedef|GlyphItemPublic (en)|TypeDefinitionPublic|
    |GlyphGroupTypedef|GlyphItemInternal|TypeDefinitionInternal|
    |GlyphGroupTypedef|GlyphItemFriend|TypeDefinitionInternal|
    |GlyphGroupTypedef|GlyphItem Protégé|TypeDéfinitionProté|
    |GlyphGroupTypedef|GlyphItemPrivate|TypeDefinitionPrivate|
    |GlyphGroupTypedef|GlyphItemShortcut|TypeDefinitionShortcut|
    |GlyphGroupType|GlyphItemPublic (en)|TypePublic|
    |GlyphGroupType|GlyphItemInternal|TypeInternal|
    |GlyphGroupType|GlyphItemFriend|TypeInternal|
    |GlyphGroupType|GlyphItem Protégé|Type Protégé|
    |GlyphGroupType|GlyphItemPrivate|TypePrivate|
    |GlyphGroupType|GlyphItemShortcut|TypeShortcut|
    |GlyphGroupUnion|GlyphItemPublic (en)|UnionPublic (en)|
    |GlyphGroupUnion|GlyphItemInternal|UnionInternal|
    |GlyphGroupUnion|GlyphItemFriend|UnionInternal|
    |GlyphGroupUnion|GlyphItem Protégé|UnionProtected|
    |GlyphGroupUnion|GlyphItemPrivate|UnionPrivate|
    |GlyphGroupUnion|GlyphItemShortcut|UnionShortcut|
    |GlyphGroupVariable|GlyphItemPublic (en)|FieldPublic (fieldPublic)|
    |GlyphGroupVariable|GlyphItemInternal|FieldInternal (FieldInternal)|
    |GlyphGroupVariable|GlyphItemFriend|FieldInternal (FieldInternal)|
    |GlyphGroupVariable|GlyphItem Protégé|FieldProtected FieldProtected FieldProtected FieldProtect|
    |GlyphGroupVariable|GlyphItemPrivate|FieldPrivate (FieldPrivate)|
    |GlyphGroupVariable|GlyphItemShortcut|FieldShortcut (FieldShortcut)|
    |GlyphGroupValueType|GlyphItemPublic (en)|ValueTypePublic|
    |GlyphGroupValueType|GlyphItemInternal|ValueTypeInternal|
    |GlyphGroupValueType|GlyphItemFriend|ValueTypeInternal|
    |GlyphGroupValueType|GlyphItem Protégé|ValueTypeProté|
    |GlyphGroupValueType|GlyphItemPrivate|ValueTypePrivate|
    |GlyphGroupValueType|GlyphItemShortcut|ValueTypeShortcut|
    |GlyphGroupIntrinsic|GlyphItemPublic (en)|ObjetPublic|
    |GlyphGroupIntrinsic|GlyphItemInternal|ObjetInternal|
    |GlyphGroupIntrinsic|GlyphItemFriend|ObjetInternal|
    |GlyphGroupIntrinsic|GlyphItem Protégé|Objet Protégé|
    |GlyphGroupIntrinsic|GlyphItemPrivate|ObjectPrivate|
    |GlyphGroupIntrinsic|GlyphItemShortcut|ObjectShortcut|
    |GlyphGroupJSharpMethod|GlyphItemPublic (en)|MéthodePublic|
    |GlyphGroupJSharpMethod|GlyphItemInternal|MéthodeInternal|
    |GlyphGroupJSharpMethod|GlyphItemFriend|MéthodeInternal|
    |GlyphGroupJSharpMethod|GlyphItem Protégé|MethodProtected|
    |GlyphGroupJSharpMethod|GlyphItemPrivate|MéthodePrivate|
    |GlyphGroupJSharpMethod|GlyphItemShortcut|MéthodeShortcut|
    |GlyphGroupJSharpField|GlyphItemPublic (en)|FieldPublic (fieldPublic)|
    |GlyphGroupJSharpField|GlyphItemInternal|FieldInternal (FieldInternal)|
    |GlyphGroupJSharpField|GlyphItemFriend|FieldInternal (FieldInternal)|
    |GlyphGroupJSharpField|GlyphItem Protégé|FieldProtected FieldProtected FieldProtected FieldProtect|
    |GlyphGroupJSharpField|GlyphItemPrivate|FieldPrivate (FieldPrivate)|
    |GlyphGroupJSharpField|GlyphItemShortcut|FieldShortcut (FieldShortcut)|
    |Classe GlyphGroupJSharp|GlyphItemPublic (en)|ClassPublic|
    |Classe GlyphGroupJSharp|GlyphItemInternal|ClassInternal|
    |Classe GlyphGroupJSharp|GlyphItemFriend|ClassInternal|
    |Classe GlyphGroupJSharp|GlyphItem Protégé|ClasseProtectée|
    |Classe GlyphGroupJSharp|GlyphItemPrivate|ClassPrivate (ClassPrivate)|
    |Classe GlyphGroupJSharp|GlyphItemShortcut|ClassShortcut|
    |GlyphGroupJSharpNamespace|GlyphItemPublic (en)|NamespacePublic|
    |GlyphGroupJSharpNamespace|GlyphItemInternal|NamespaceInternal|
    |GlyphGroupJSharpNamespace|GlyphItemFriend|NamespaceInternal|
    |GlyphGroupJSharpNamespace|GlyphItem Protégé|NamespaceProtected|
    |GlyphGroupJSharpNamespace|GlyphItemPrivate|NamespacePrivate|
    |GlyphGroupJSharpNamespace|GlyphItemShortcut|NamespaceShortcut|
    |GlyphGroupJSharpInterface|GlyphItemPublic (en)|InterfacePublic|
    |GlyphGroupJSharpInterface|GlyphItemInternal|InterfaceInternal|
    |GlyphGroupJSharpInterface|GlyphItemFriend|InterfaceInternal|
    |GlyphGroupJSharpInterface|GlyphItem Protégé|InterfaceProtectée|
    |GlyphGroupJSharpInterface|GlyphItemPrivate|InterfacePrivate|
    |GlyphGroupJSharpInterface|GlyphItemShortcut|InterfaceShortcut|
    |GlyphGroupError||StatusError|
    |GlyphBscFile||ClassFile (ClassFile)|
    |GlyphAssembly||Informations de référence|
    |GlyphLibraire||Bibliothèque|
    |GlyphVBProject||VBProjetNode|
    |GlyphCoolProject||CSProjectNode|
    |GlyphCppProject||CPPProjetNode|
    |GlyphDialogId||Boîte de dialogue|
    |GlyphOpenFolder||FolderOpened|
    |GlyphClosedFolder GlyphClosedFolder||FolderClosed|
    |GlyphArrow||GoToNext GoToNext|
    |GlyphCSharpFile||CSFileNode|
    |GlyphCSharpExpansion||Extrait|
    |GlyphKeyword (en)||IntellisenseKeyword (en anglais seulement)|
    |GlyphInformation||Informations sur l’état|
    |GlyphReference||ClassMethodReference (ClassMethodReference)|
    |GlyphRecursion||Récursivité|
    |GlyphXmlItem||Tag|
    |Projet GlyphJSharp||DocumentCollection|
    |GlyphJSharpDocument||Document|
    |GlyphForwardType||GoToNext GoToNext|
    |GlyphCallersGraph (en)||CallTo|
    |GlyphCallGraph (en)||CallDe|
    |GlyphWarning (en)||StatusWarning|
    |GlyphMaybeReference||Questionmark|
    |GlyphMaybeCaller||CallTo|
    |GlyphMaybeCall||CallDe|
    |GlyphExtensionMethod||ExtensionMethod|
    |GlyphExtensionMethodInternal||ExtensionMethod|
    |GlyphExtensionMethodFriend||ExtensionMethod|
    |GlyphExtensionMethodProécisé||ExtensionMethod|
    |GlyphExtensionMethodPrivate||ExtensionMethod|
    |GlyphExtensionMethodShortcut||ExtensionMethod|
    |GlyphXmlAttribute||XmlAttribute|
    |GlyphXmlChild||XmlElement|
    |GlyphXmlDescendant||XmlDescendant|
    |GlyphXmlNamespace||XmlNamespace|
    |GlyphXmlAttributeQuestion||XmlAttributeLowConfidence|
    |GlyphXmlAttributeCheck||XmlAttributeHighConfidence|
    |GlyphXmlChildQuestion||XmlElementLowConfidence XmlElementLowConfidence|
    |GlyphXmlChildCheck (en anglais seulement)||XmlElementHighConfidence|
    |GlyphXmlDescendantQuestion||XmlDescendantLowConfidence XmlDescendantLowConfidence|
    |GlyphXmlDescendantCheck||XmlDescendantHighConfidence XmlDescendantHighConfidence|
    |GlyphCompletionWarning||IntellisenseWarning (en anglais seulement)|
