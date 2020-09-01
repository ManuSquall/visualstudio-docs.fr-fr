---
title: Service d’images et catalogue | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
caps.latest.revision: 38
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 102e41e45caac8d0567786579130e0953ec68b30
ms.sourcegitcommit: 26178b116cbf7353fee6ca989b8d872114f7b405
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89284355"
---
# <a name="image-service-and-catalog"></a>Catalogue et service d’images
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ce livre de recettes contient des conseils et des pratiques recommandées pour l’adoption du service d’images Visual Studio et du catalogue d’images introduit dans Visual Studio 2015.  

 Le service d’images introduit dans Visual Studio 2015 permet aux développeurs d’obtenir les images les plus appropriées pour l’appareil et le thème choisi par l’utilisateur pour afficher l’image, y compris des corrections pour le contexte dans lequel elles sont affichées. L’adoption du service d’images permet d’éliminer les principales difficultés liées à la maintenance des actifs, à la mise à l’échelle des HDPI et à leur gestion.  

|**Problèmes aujourd’hui**|**Solutions**|  
|-|-|  
|Fusion des couleurs d’arrière-plan|Fusion alpha intégrée|  
|Thèmes (certaines) images|Métadonnées du thème|  
|Mode de contraste élevé|Autres ressources de contraste élevé|  
|Ressources multiples nécessaires pour différents modes PPP|Ressources sélectionnables avec un secours vectoriel|  
|Dupliquer les images|Un seul identificateur par concept d’image|  

 Pourquoi adopter le service image ?  

- Procurez-vous toujours la dernière image « pixel-Perfect » dans Visual Studio  

- Vous pouvez envoyer et utiliser vos propres images  

- Vous n’avez pas besoin de tester vos images lorsque Windows ajoute une nouvelle mise à l’échelle PPP  

- Résoudre les anciens obstacles architecturaux dans vos implémentations  

  La barre d’outils de l’interpréteur de commandes Visual Studio avant et après l’utilisation du service d’images :  

  ![Service d’images avant et après](../extensibility/media/image-service-before-and-after.png "Service d’images avant et après")  

## <a name="how-it-works"></a>Fonctionnement  
 Le service image peut fournir une image bitmap adaptée à toute infrastructure d’interface utilisateur prise en charge :  

- WPF : BitmapSource  

- WinForms : System. Drawing. Bitmap  

- Win32 : HBITMAP  

  Diagramme du workflow de service d’images  

  ![Diagramme de flux du service d’images](../extensibility/media/image-service-flow-diagram.png "Diagramme de flux du service d’images")  

  **Monikers d’image**  

  Un moniker d’image (ou moniker pour Short) est une paire GUID/ID qui identifie de façon unique une ressource d’image ou une ressource de liste d’images dans la bibliothèque d’images.  

  **Monikers connus**  

  Ensemble des monikers d’image contenus dans le catalogue d’images Visual Studio et consommables publiquement par n’importe quel composant ou extension Visual Studio.  

  **Fichiers manifeste de l’image**  

  Les fichiers manifeste d’image (. imagemanifest) sont des fichiers XML qui définissent un ensemble de ressources d’image, les monikers qui représentent ces ressources, ainsi que l’image réelle ou les images qui représentent chaque élément multimédia. Les manifestes d’image peuvent définir des images autonomes ou des listes d’images pour la prise en charge des IU héritées. En outre, il existe des attributs qui peuvent être définis sur l’élément multimédia ou sur les images individuelles derrière chaque ressource pour changer quand et comment ces ressources sont affichées.  

  **Schéma du manifeste d’image**  

  Un manifeste d’image complet se présente comme suit :  

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

 Pour faciliter la lecture et l’aide à la maintenance, le manifeste d’image peut utiliser des symboles pour les valeurs d’attribut. Les symboles sont définis comme suit :  

```xml  
<Symbols>  
      <Import Manifest="manifest" />  
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />  
      <ID Name="cmdidSaveAll" Value="1000" />  
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />  
</Symbols>  
```  

|**Sous-élément**|**Définition**|  
|-|-|  
|Importer|Importe les symboles du fichier manifeste donné pour une utilisation dans le manifeste actuel|  
|Guid|Le symbole représente un GUID et doit correspondre à la mise en forme du GUID|  
|ID|Le symbole représente un ID et doit être un entier non négatif|  
|Chaîne|Le symbole représente une valeur de chaîne arbitraire|  

 Les symboles respectent la casse et sont référencés à l’aide de la syntaxe $ (Symbol-Name) :  

```xml  
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >  
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />  
</Image>  
```  

 Certains symboles sont prédéfinis pour tous les manifestes. Ils peuvent être utilisés dans l’attribut URI de l' \<Source> \<Import> élément ou pour référencer des chemins d’accès sur l’ordinateur local.  

|**Symbole**|**Description**|  
|-|-|  
|CommonProgramFiles|La valeur de la variable d’environnement% CommonProgramFiles%|  
|LocalAppData|Valeur de la variable d’environnement% LocalAppData%|  
|ManifestFolder|Dossier contenant le fichier manifeste|  
|MyDocuments|Chemin d’accès complet du dossier Mes documents de l’utilisateur actuel|  
|ProgramFiles|La valeur de la variable d’environnement% ProgramFiles%|  
|Système|Dossier Windows\System32|  
|RépWin|La valeur de la variable d’environnement% WinDir%|  

 **Image**  

 L' \<Image> élément définit une image qui peut être référencée par un moniker. Le GUID et l’ID pris ensemble forment le moniker d’image. Le moniker de l’image doit être unique dans l’ensemble de la bibliothèque d’images. Si plusieurs images ont un moniker donné, la première rencontrée lors de la génération de la bibliothèque est celle qui est conservée.  

 Il doit contenir au moins une source. Les sources de taille neutre offrent les meilleurs résultats dans un large éventail de tailles, mais elles ne sont pas requises. Si le service est invité à fournir une image d’une taille non définie dans l' \<Image> élément et qu’il n’y a aucune source neutre pour la taille, le service choisit la source de taille optimale et la met à l’échelle à la taille demandée.  

```xml  
<Image Guid="guid" ID="int" AllowColorInversion="true/false">  
      <Source ... />  
      <!-- optional additional Source elements -->  
</Image>  
```  

|**Attribut**|**Définition**|  
|-|-|  
|Guid|Souhaitée La partie GUID du moniker d’image|  
|ID|Souhaitée La partie ID du moniker d’image|  
|AllowColorInversion|[Facultatif, valeur par défaut true] Indique si les couleurs de l’image peuvent être inversées par programmation lorsqu’elles sont utilisées sur un arrière-plan sombre.|  

 **Source**  

 L' \<Source> élément définit une ressource source d’image unique (XAML et png).  

```xml  
<Source Uri="uri" Background="background">  
      <!-- optional NativeResource element -->  
 </Source>  
```  

|               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|---------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Attribut** |                                                                                                                                                                                                                                                                                                                                                                                                                                                                            **Définition**                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|      Uri      |                                                                                                                                                                                                                                                                                                               Souhaitée URI qui définit l’emplacement à partir duquel l’image peut être chargée. Les valeurs possibles sont les suivantes :<br /><br /> -Un URI à en- [tête pack](https://msdn.microsoft.com/library/aa970069\(v=vs.100\).aspx) à l’aide de l’autorité application:///<br />-Référence de ressource de composant absolue<br />-Chemin d’accès à un fichier contenant une ressource native                                                                                                                                                                                                                                                                                                               |
|  Arrière-plan   | Facultatif Indique le type d’arrière-plan auquel la source est destinée à être utilisée.<br /><br /> Les valeurs possibles sont les suivantes :<br /><br /> *Clair :* La source peut être utilisée sur un arrière-plan clair.<br /><br /> <em>Foncé :</em> La source peut être utilisée sur un arrière-plan sombre.<br /><br /> *Contraste élevé :* La source peut être utilisée sur n’importe quel arrière-plan en mode contraste élevé.<br /><br /> *HighContrastLight :* La source peut être utilisée sur un arrière-plan clair en mode contraste élevé.<br /><br /> *HighContrastDark :* La source peut être utilisée sur un arrière-plan sombre en mode contraste élevé.<br /><br /> Si l’attribut Background est omis, la source peut être utilisée sur n’importe quel arrière-plan.<br /><br /> Si Background est *clair*, *Dark*, *HighContrastLight*ou *HighContrastDark*, les couleurs de la source ne sont jamais inversées. Si Background est omis ou défini sur *HighContrast*, l’inversion des couleurs de la source est contrôlée par l’attribut **AllowColorInversion** de l’image. |
|               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |

 Un \<Source> élément peut avoir exactement l’un des sous-éléments facultatifs suivants :  

|**Element**|**Attributs (tous obligatoires)**|**Définition**|  
|-|-|-|  
|\<Size>|Valeur|La source sera utilisée pour les images de la taille donnée (en unités de périphérique). L’image sera carrée.|  
|\<SizeRange>|MinSize, MaxSize|La source sera utilisée pour les images comprises entre MinSize et MaxSize (en unités de périphérique). L’image sera carrée.|  
|\<Dimensions>|Width, Height|La source sera utilisée pour les images de la largeur et de la hauteur données (en unités de périphérique).|  
|\<DimensionRange>|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|La source sera utilisée pour les images allant de la largeur/hauteur minimale à la largeur/hauteur maximale (en unités de périphérique).|  

 Un \<Source> élément peut également avoir un sous- \<NativeResource> élément facultatif, qui définit un \<Source> qui est chargé à partir d’un assembly natif plutôt qu’un assembly managé.  

```xml  
<NativeResource Type="type" ID="int" />  
```  

|**Attribut**|**Définition**|  
|-|-|  
|Type|Souhaitée Type de la ressource native (XAML ou PNG)|  
|ID|Souhaitée La partie ID d’entier de la ressource native|  

 **ImageList**  

 L' \<ImageList> élément définit une collection d’images qui peuvent être retournées dans une seule bande. La bande est créée à la demande, selon les besoins.  

```xml  
<ImageList>  
      <ContainedImage Guid="guid" ID="int" External="true/false" />  
      <!-- optional additional ContainedImage elements -->  
 </ImageList>  
```  

|**Attribut**|**Définition**|  
|-|-|  
|Guid|Souhaitée La partie GUID du moniker d’image|  
|ID|Souhaitée La partie ID du moniker d’image|  
|Externe|[Facultatif, valeur par défaut false] Indique si le moniker d’image référence une image dans le manifeste actuel.|  

 Le moniker de l’image contenue n’a pas besoin de référencer une image définie dans le manifeste actuel. Si l’image contenue est introuvable dans la bibliothèque d’images, une image d’espace réservé vide sera utilisée à la place.  

## <a name="using-the-image-service"></a>Utilisation du service d’images  

### <a name="first-steps-managed"></a>Premières étapes (managées)  
 Pour utiliser le service d’images, vous devez ajouter à votre projet des références à certains ou à tous les assemblys suivants :  

- **Microsoft.VisualStudio.ImageCatalog.dll**  

  - Obligatoire si vous utilisez le catalogue d’images intégré KnownMonikers  

- **Microsoft.VisualStudio.Imaging.dll**  

  - Requis si vous utilisez **CrispImage** et **ImageThemingUtilities** dans votre interface utilisateur WPF  

- **Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll**  

  - Obligatoire si vous utilisez les types **ImageMoniker** et **ImageAttributes**  

  - **EmbedInteropTypes** doit avoir la valeur true  

- **Microsoft. VisualStudio. Shell. Interop. 14.0. DesignTime**  

  - Obligatoire si vous utilisez le type **IVsImageService2**  

  - **EmbedInteropTypes** doit avoir la valeur true  

- **Microsoft.VisualStudio.Utilities.dll**  

  - Obligatoire si vous utilisez **BrushToColorConverter** pour ImageThemingUtilities. **ImageBackgroundColor** dans votre interface utilisateur WPF  

- **Microsoft. VisualStudio. Shell. \<VSVersion> . entre**  

  - Obligatoire si vous utilisez le type **IVsUIObject**  

- **Microsoft.VisualStudio.Shell.Interop.10.0.dll**  

  - Obligatoire si vous utilisez les applications d’assistance de l’interface utilisateur liées à WinForms  

  - **EmbedInteropTypes** doit avoir la valeur true  

### <a name="first-steps-native"></a>Premières étapes (natives)  
 Pour utiliser le service d’images, vous devez inclure certains ou l’ensemble des en-têtes suivants dans votre projet :  

- **KnownImageIds. h**  

  - Obligatoire si vous utilisez le catalogue d’images intégré **KnownMonikers**, mais que vous ne pouvez pas utiliser le type **ImageMoniker** , par exemple, pour retourner des valeurs à partir d’appels GetGuidProperty ou **GetProperty** **IVsHierarchy** .  

- **KnownMonikers. h**  

  - Obligatoire si vous utilisez le catalogue d’images intégré **KnownMonikers**.  

- **ImageParameters140. h**  

  - Obligatoire si vous utilisez les types **ImageMoniker** et **ImageAttributes** .  

- **VSShell140. h**  

  - Obligatoire si vous utilisez le type **IVsImageService2** .  

- **ImageThemingUtilities. h**  

  - Obligatoire si vous ne pouvez pas laisser le service d’images les gérer pour vous.  

  - N’utilisez pas cet en-tête si le service d’images peut gérer vos images d’image.  

- **VSUIDPIHelper. h**  

  - Obligatoire si vous utilisez les assistances PPP pour obtenir les PPP actuels.  

## <a name="how-do-i-write-new-wpf-ui"></a>Comment faire écrire une nouvelle interface utilisateur WPF ?  

1. Commencez par ajouter les références d’assembly requises dans la section des premières étapes ci-dessus à votre projet. Vous n’avez pas besoin de les ajouter, par conséquent, ajoutez simplement les références dont vous avez besoin. (Remarque : Si vous utilisez ou avez accès à des **couleurs** au lieu de **pinceaux**, vous pouvez ignorer la référence aux **utilitaires**, car vous n’aurez pas besoin du convertisseur.)  

2. Sélectionnez l’image souhaitée et récupérez son moniker. Utilisez un **KnownMoniker**ou utilisez le vôtre si vous avez vos propres images et monikers personnalisés.  

3. Ajoutez **CrispImages** à votre code XAML. (Voir l’exemple ci-dessous.)  

4. Définissez la propriété **ImageThemingUtilities. ImageBackgroundColor** dans votre hiérarchie d’interface utilisateur. (Cela doit être défini à l’emplacement où la couleur d’arrière-plan est connue, pas nécessairement sur le **CrispImage**.) (Voir l’exemple ci-dessous.)  

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

 **Comment faire mettre à jour l’interface utilisateur WPF existante ?**  

 La mise à jour de l’interface utilisateur WPF existante est un processus relativement simple qui se compose de trois étapes de base :  

1. Remplacer tous les \<Image> éléments de l’interface utilisateur par des \<CrispImage> éléments  

2. Modifier tous les attributs source en attributs de moniker  

    - Si l’image ne change jamais et que vous utilisez **KnownMonikers**, liez de manière statique cette propriété à **KnownMoniker**. (Voir l’exemple ci-dessus.)  

    - Si l’image ne change jamais et que vous utilisez votre propre image personnalisée, effectuez une liaison statique à votre propre moniker.  

    - Si l’image peut changer, liez l’attribut moniker à une propriété de code qui notifie les modifications de propriété.  

3. Quelque part dans la hiérarchie de l’interface utilisateur, définissez **ImageThemingUtilities. ImageBackgroundColor** pour vous assurer que l’inversion des couleurs fonctionne correctement.  

    - Cela peut nécessiter l’utilisation de la classe **BrushToColorConverter** . (Voir l’exemple ci-dessus.)  

## <a name="how-do-i-update-win32-ui"></a>Comment faire mettre à jour l’interface utilisateur Win32 ?  
 Ajoutez ce qui suit à votre code chaque fois qu’il est nécessaire de remplacer le chargement brut des images. Changez les valeurs pour retourner HBITMAPs et HICONs par rapport à HIMAGELIST en fonction des besoins.  

 **Procurez-vous le service image**  

```cpp  
CComPtr<IVsImageService2> spImgSvc;  
CGlobalServiceProvider::HrQueryService(SID_SVsImageService, &spImgSvc);  
```  

 **Demande de l’image**  

```cpp  
ImageAttributes attr = { 0 };  
attr.StructSize      = sizeof(attributes);  
attr.Format          = DF_Win32;  
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST  
attr.ImageType       = IT_Bitmap;  
attr.LogicalWidth    = 16;  
attr.LogicalHeight   = 16;  
attr.Dpi             = VsUI::DpiHelper::GetDeviceDpiX();  
attr.Background      = 0xFFFFFFFF;  
// Desired RGBA color, if you don't use this, don't set IAF_Background below  
attr.Flags           = IAF_RequiredFlags | IAF_Background;  

CComPtr<IVsUIObject> spImg;  
// Replace this KnownMoniker with your desired ImageMoniker  
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);  

```  

## <a name="how-do-i-update-winforms-ui"></a>Comment faire mise à jour de l’interface utilisateur WinForms ?  
 Ajoutez ce qui suit à votre code chaque fois qu’il est nécessaire de remplacer le chargement brut des images. Changez les valeurs pour retourner des bitmaps et des icônes si nécessaire.  

 **Utile avec l’instruction**  

```csharp  
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;  
```  

 **Procurez-vous le service image**  

```csharp  
// This or your preferred way of querying for Visual Studio services  
IVsImageService2 imageService = (IVsImageService2)Package.GetGlobalService(typeof(SVsImageService));  

```  

 **Demander l’image**  

```csharp  
ImageAttributes attributes = new ImageAttributes  
{  
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),  
    // IT_Bitmap for Bitmap, IT_Icon for Icon  
    ImageType     = (uint)_UIImageType.IT_Bitmap,  
    Format        = (uint)_UIDataFormat.DF_WinForms,  
    LogicalWidth  = 16,  
    LogicalHeight = 16,  
    // Desired RGBA color, if you don't use this, don't set IAF_Background below  
    Background    = 0xFFFFFFFF,  
    Flags = (uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background,  
};  

// Replace this KnownMoniker with your desired ImageMoniker  
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);  

Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap  
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj); // Use this if you need an icon  

```  

## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>Comment faire utiliser des monikers d’image dans une nouvelle fenêtre outil ?  
 Le modèle de projet de package VSIX a été mis à jour pour Visual Studio 2015. Pour créer une nouvelle fenêtre outil, cliquez avec le bouton droit sur le projet VSIX, puis sélectionnez « Ajouter un nouvel élément... ». (Ctrl + Maj + A). Sous le nœud extensibilité pour le langage du projet, sélectionnez « fenêtre outil personnalisée », donnez un nom à la fenêtre outil, puis appuyez sur le bouton « Ajouter ».  

 Voici les emplacements clés pour utiliser des monikers dans une fenêtre outil. Suivez les instructions pour chacune d’elles :  

1. Onglet de la fenêtre outil lorsque les onglets sont suffisamment petits (également utilisés dans le sélecteur de fenêtre CTRL + TAB).  

    Ajoutez cette ligne au constructeur pour la classe qui dérive du type **ToolWindowPane** :  

   ```csharp  
   // Replace this KnownMoniker with your desired ImageMoniker  
   this.BitmapImageMoniker = KnownMonikers.Blank;  
   ```  

2. Commande permettant d’ouvrir la fenêtre outil.  

    Dans le fichier. vsct du package, modifiez le bouton de commande de la fenêtre outil :  

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

   **Comment faire utiliser des monikers d’image dans une fenêtre outil existante ?**  

   La mise à jour d’une fenêtre outil existante pour utiliser des monikers d’images est similaire à la procédure de création d’une nouvelle fenêtre d’outils.  

   Voici les emplacements clés pour utiliser des monikers dans une fenêtre outil. Suivez les instructions pour chacune d’elles :  

3. Onglet de la fenêtre outil lorsque les onglets sont suffisamment petits (également utilisés dans le sélecteur de fenêtre CTRL + TAB).  

   1. Supprimez ces lignes (si elles existent) dans le constructeur de la classe qui dérive du type **ToolWindowPane** :  

       ```csharp  
       this.BitmapResourceID = <Value>;  
       this.BitmapIndex = <Value>;  
       ```  

   2. Consultez l’étape #1 de la section « utilisation des monikers d’images dans une nouvelle fenêtre d’outils » ci-dessus.  

4. Commande permettant d’ouvrir la fenêtre outil.  

   - Consultez l’étape #2 de la section « utilisation des monikers d’images dans une nouvelle fenêtre d’outils » ci-dessus.  

## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>Comment faire utiliser des monikers d’image dans un fichier. vsct ?  
 Mettez à jour votre fichier. vsct comme indiqué par les lignes commentées ci-dessous :  

```xml  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <!--  Include the definitions for images included in the VS image catalog -->  
  <Include href="KnownImageIds.vsct"/>  
  <Commands package="guidMyPackage">  
    <Buttons>  
      <Button guid="guidMyCommandSet" id="cmdidMyCommand" priority="0x0000" type="Button">  
        <!-- Add an Icon element, changing the attributes to match the image moniker you want to use.  
             In this case, we’re using the Guid for the VS image catalog.  
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

 **Que se passe-t-il si le fichier. vsct doit également être lu par les anciennes versions de Visual Studio ?**  

 Les versions antérieures de Visual Studio ne reconnaissent pas l’indicateur de commande **IconIsMoniker** . Vous pouvez utiliser des images du service d’images sur les versions de Visual Studio qui la prennent en charge, mais continuer à utiliser des images anciennes sur des versions antérieures de Visual Studio. Pour ce faire, vous ne modifiez pas le fichier. vsct (et, par conséquent, il est compatible avec les versions antérieures de Visual Studio) et vous créez un fichier CSV (valeurs séparées par des virgules) qui mappe des paires GUID/ID définies dans l’élément d’un fichier. vsct \<Bitmaps> aux paires GUID/ID du moniker d’image.  

 Le format du fichier CSV de mappage est le suivant :  

```  
Icon guid, Icon id, Moniker guid, Moniker id  
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100  
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200  
```  

 Le fichier CSV est déployé avec le package et son emplacement est spécifié par la propriété **IconMappingFilename** de l’attribut de package **ProvideMenuResource** :  

```csharp  
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]  
```  

 Le **IconMappingFilename** est un chemin d’accès relatif implicitement enraciné à $PackageFolder $ (comme dans l’exemple ci-dessus), ou un chemin d’accès absolu explicitement enraciné dans un répertoire défini par une variable d’environnement, tel que @ "% UserProfile% \dir1\dir2\MyMappingFile.csv".  

## <a name="how-do-i-port-a-project-system"></a>Comment faire port d’un système de projet ?  
 **Guide pratique pour fournir des ImageMonikers pour un projet**  

1. Implémentez **VSHPROPID_SupportsIconMonikers** sur le **IVsHierarchy**du projet et retourne true.  

2. Implémentez l’un ou l’autre **VSHPROPID_IconMonikerImageList** (si le projet d’origine a utilisé **VSHPROPID_IconImgList**) ou **VSHPROPID_IconMonikerGuid**, **VSHPROPID_IconMonikerId** **VSHPROPID_OpenFolderIconMonikerGuid** **, VSHPROPID_OpenFolderIconMonikerId (si** le projet d’origine a utilisé **VSHPROPID_IconHandle** et **VSHPROPID_OpenFolderIconHandle**).  

3. Modifiez l’implémentation du VSHPROPIDs d’origine pour les icônes afin de créer des versions « héritées » des icônes si les points d’extension les demandent. **IVsImageService2** fournit les fonctionnalités nécessaires à l’extraction de ces icônes  

   **Exigences supplémentaires pour les versions de projet VB/C#**  

   N’implémentez **VSHPROPID_SupportsIconMonikers** que si vous détectez que votre projet est la version la plus à l' **extérieur**. Dans le cas contraire, la version la plus externe réelle peut ne pas prendre en charge les monikers d’image en réalité, et votre version de base peut effectivement « masquer » les images personnalisées.  

   **Comment faire utiliser des monikers d’image dans CPS ?**  

   La définition d’images personnalisées dans CPS (système de projet commun) peut être effectuée manuellement ou via un modèle d’élément fourni avec le kit de développement logiciel (SDK) d’extensibilité du système de projet.  

   **Utilisation du kit de développement logiciel (SDK) extensibilité du système de projet**  

   Suivez les instructions fournies dans [fournir des icônes personnalisées pour le type de projet/type d’élément](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md) afin de personnaliser vos images CPS. Pour plus d’informations sur CPS, consultez [la documentation sur l’extensibilité du système de projet Visual Studio](https://github.com/Microsoft/VSProjectSystem) .  

   **Utiliser manuellement ImageMonikers**  

4. Implémentez et exportez l’interface **IProjectTreeModifier** dans votre système de projet.  

5. Déterminez le **KnownMoniker** ou le moniker d’image personnalisé que vous souhaitez utiliser.  

6. Dans la méthode **ApplyModifications** , procédez comme suit quelque part dans la méthode avant de retourner la nouvelle arborescence, comme dans l’exemple ci-dessous :  

   ```csharp  
   // Replace this KnownMoniker with your desired ImageMoniker  
   tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());  
   ```  

7. Si vous créez une nouvelle arborescence, vous pouvez définir les images personnalisées en passant les monikers souhaités dans la méthode NewTree, comme dans l’exemple ci-dessous :  

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

## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>Comment faire convertir à partir d’une bande d’images réelle en une bande d’images basée sur un moniker ?  
 **Je dois prendre en charge HIMAGELISTs**  

 S’il existe déjà une bande d’images pour votre code que vous souhaitez mettre à jour pour utiliser le service d’images, mais que vous êtes concédés par des API qui nécessitent une transmission autour des listes d’images, vous pouvez toujours bénéficier des avantages du service d’images. Pour créer une bande d’images basée sur un moniker, suivez les étapes ci-dessous pour créer un manifeste à partir de monikers existants.  

1. Exécutez l’outil **ManifestFromResources** en lui transmettant la bande d’images. Cela génère un manifeste pour la bande.  

   - Recommandé : fournissez un nom différent du nom par défaut pour que le manifeste soit adapté à son utilisation.  

2. Si vous utilisez uniquement **KnownMonikers**, procédez comme suit :  

   - Remplacez la \<Images> section du manifeste par \<Images/> .  

   - Supprimez tous les ID de sous-image (tout ce qui est associé à \<imagestrip name> _ # #).  

   - Recommandé : renommez le symbole AssetsGuid et le symbole de la bande d’image en fonction de son utilisation.  

   - Remplacez le GUID de chaque **ContainedImage**par $ (ImageCatalogGuid), remplacez l’ID de chaque **ContainedImage**par $ ( \<moniker> ) et ajoutez l’attribut External = "true" à chaque **ContainedImage**  

       - \<moniker> doit être remplacé par le **KnownMoniker** qui correspond à l’image, mais avec le « KnownMonikers ». supprimé du nom.  

   - Ajoutez <importer manifest = "$ (ManifestFolder) \\<chemin d’accès du répertoire d’installation relatif à \> \Microsoft.VisualStudio.ImageCatalog.imagemanifest"/ \> en haut de la \<Symbols> section.  

       - Le chemin d’accès relatif est déterminé par l’emplacement de déploiement défini dans la création du manifeste du programme d’installation.  

3. Exécutez l’outil **ManifestToCode** pour générer des wrappers afin que le code existant ait un moniker qu’il peut utiliser pour interroger le service d’images pour la bande d’images.  

   - Recommandé : indiquez des noms autres que ceux par défaut pour les wrappers et les espaces de noms pour les adapter à leur utilisation.  

4. Effectuez toutes les opérations d’ajout, de création et de déploiement de l’installation, ainsi que d’autres modifications de code pour utiliser le service d’images et les nouveaux fichiers.  

   Exemple de manifeste incluant des images internes et externes pour voir à quoi ressembler :  

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

 **Je n’ai pas besoin de prendre en charge HIMAGELISTs**  

1. Déterminez l’ensemble des **KnownMonikers** qui correspondent aux images de votre bande d’images, ou créez vos propres monikers pour les images de votre bande d’images.  

2. Mettez à jour le mappage que vous avez utilisé pour récupérer l’image à l’index requis dans la bande d’images pour utiliser les monikers à la place.  

3. Mettez à jour votre code pour utiliser le service d’images pour demander des monikers via le mappage mis à jour. (Cela peut signifier la mise à jour vers **CrispImages** pour le code managé, ou la demande de HBITMAPs ou de HICONs à partir du service d’image et leur transmission pour du code natif.)  

## <a name="testing-your-images"></a>Test de vos images  
 Vous pouvez utiliser l’outil visionneuse de la bibliothèque d’images pour tester vos manifestes d’image afin de vérifier que tout est correctement créé. Vous pouvez trouver cet outil dans le [Kit de développement logiciel (SDK) Visual Studio 2015](visual-studio-sdk.md). Vous trouverez la documentation de cet outil et d’autres informations [ici](internals/vssdk-utilities.md).  

## <a name="additional-resources"></a>Ressources supplémentaires  

### <a name="samples"></a>Exemples  
 Plusieurs exemples Visual Studio sur GitHub ont été mis à jour pour montrer comment utiliser le service d’images dans le cadre de différents points d’extensibilité de Visual Studio.  

 Recherchez [http://github.com/Microsoft/VSSDK-Extensibility-Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples) les exemples les plus récents.  

### <a name="tooling"></a>Outillage  
 Un ensemble d’outils de support pour le service d’images a été créé pour faciliter la création ou la mise à jour de l’interface utilisateur qui fonctionne avec le service d’images. Pour plus d’informations sur chaque outil, consultez la documentation fournie avec les outils. Les outils sont inclus dans le kit de [développement logiciel (SDK) de Visual Studio 2015.](https://msdn.microsoft.com/library/bb166441.aspx)  

 **ManifestFromResources**  

 L’outil Manifest from Resources prend une liste de ressources d’image (PNG ou XAML) et génère un fichier manifeste d’image pour l’utilisation de ces images avec le service image.  

 **ManifestToCode**  

 L’outil Manifest to Code prend un fichier manifeste d’image et génère un fichier de wrapper pour faire référence aux valeurs de manifeste dans du code (C++, C# ou VB) ou des fichiers. vsct.  

 **ImageLibraryViewer**  

 L’outil visionneuse de la bibliothèque d’images peut charger des manifestes d’image et permet à l’utilisateur de les manipuler de la même façon que Visual Studio pour s’assurer que le manifeste est correctement créé. L’utilisateur peut modifier les paramètres de l’arrière-plan, des tailles, du paramètre ppp, du contraste élevé et d’autres paramètres. Il affiche également les informations de chargement pour rechercher les erreurs dans les manifestes et affiche les informations relatives à la source de chaque image dans le manifeste.  

## <a name="faq"></a>Forum aux questions  

- Existe-t-il des dépendances que vous devez inclure lors du chargement \<Reference Include="Microsoft.VisualStudio.*.Interop.14.0.DesignTime" /> ?  

  - Définissez EmbedInteropTypes = "true" sur toutes les dll Interop.  

- Comment faire déployer un manifeste d’image avec mon extension ?  

  - Ajoutez le fichier. imagemanifest à votre projet.  

  - Affectez la valeur true à « include in VSIX ».  

- Je mets à jour mon système de projet CPS. Qu’est-il arrivé à **ImageName** et **StockIconService**?  

  - Celles-ci ont été supprimées lorsque CPS a été mis à jour pour utiliser des monikers. Vous n’avez plus besoin d’appeler **StockIconService**, vous devez simplement transmettre les **KnownMoniker** souhaités à la méthode ou à la propriété à l’aide de la méthode d’extension **ToProjectSystemType ()** dans les utilitaires CPS. Vous pouvez trouver un mappage entre **ImageName** et **KnownMonikers** ci-dessous :  

    |**ImageName**|**KnownMoniker**|  
    |-|-|  
    |ImageName. OfflineWebApp|KnownImageIds. Web|  
    |ImageName. WebReferencesFolder|KnownImageIds. Web|  
    |ImageName. OpenReferenceFolder|KnownImageIds.FolderOpened|  
    |ImageName. ReferenceFolder|KnownImageIds. Reference|  
    |ImageName. Reference|KnownImageIds. Reference|  
    |ImageName. SdlWebReference|KnownImageIds.WebReferenceFolder|  
    |ImageName. DiscoWebReference|KnownImageIds.DynamicDiscoveryDocument|  
    |ImageName. dossier|KnownImageIds.FolderClosed|  
    |ImageName. OpenFolder|KnownImageIds.FolderOpened|  
    |ImageName. ExcludedFolder|KnownImageIds.HiddenFolderClosed|  
    |ImageName. OpenExcludedFolder|KnownImageIds.HiddenFolderOpened|  
    |ImageName. ExcludedFile|KnownImageIds.HiddenFile|  
    |ImageName. DependentFile|KnownImageIds.GenerateFile|  
    |ImageName. MissingFile|KnownImageIds.DocumentWarning|  
    |ImageName. WindowsForm|KnownImageIds.WindowsForm|  
    |ImageName. WindowsUserControl|KnownImageIds. UserControl|  
    |ImageName. WindowsComponent|KnownImageIds.ComponentFile|  
    |Schéma ImageName.Xml|Schéma KnownImageIds.XML|  
    |Fichier ImageName.Xml|Fichier KnownImageIds.XML|  
    |ImageName. WebForm|KnownImageIds. Web|  
    |ImageName. WebService|KnownImageIds. WebService|  
    |ImageName. webusercontrol|KnownImageIds. webusercontrol|  
    |ImageName. WebCustomUserControl|KnownImageIds.WebCustomControl|  
    |ImageName. AspPage|KnownImageIds.ASPFile|  
    |ImageName. GlobalApplicationClass|KnownImageIds. SettingsFile|  
    |ImageName. webconfig|KnownImageIds.ConfigurationFile|  
    |ImageName.HtmlPage|KnownImageIds.HTMLFile|  
    |ImageName. StyleSheet|KnownImageIds. StyleSheet|  
    |ImageName. ScriptFile|Script KnownImageIds.JS|  
    |ImageName. TextFile|KnownImageIds.Document|  
    |ImageName. SettingsFile|KnownImageIds. Settings|  
    |ImageName. Resources|KnownImageIds.DocumentGroup|  
    |ImageName. Bitmap|KnownImageIds. image|  
    |ImageName. Icon|KnownImageIds.IconFile|  
    |ImageName. image|KnownImageIds. image|  
    |ImageName. ImageMap|KnownImageIds.ImageMapFile|  
    |ImageName. XWorld|KnownImageIds.XWorldFile|  
    |ImageName. audio|KnownImageIds. Sound|  
    |ImageName. Video|KnownImageIds. Media|  
    |ImageName.Cab|Projet KnownImageIds.CAB|  
    |ImageName. jar|KnownImageIds. JARFile|  
    |ImageName. DataEnvironment|KnownImageIds. DataTable|  
    |ImageName. PreviewFile|KnownImageIds. Report|  
    |ImageName. DanglingReference|KnownImageIds.ReferenceWarning|  
    |ImageName. XsltFile|KnownImageIds. XSLTransform|  
    |ImageName. Cursor|KnownImageIds.CursorFile|  
    |ImageName. AppDesignerFolder|KnownImageIds. Property|  
    |ImageName. Data|KnownImageIds. base de données|  
    |ImageName. application|KnownImageIds. application|  
    |ImageName. DataSet|KnownImageIds.DatabaseGroup|  
    |ImageName. pfx|KnownImageIds. Certificate|  
    |ImageName. snk|KnownImageIds. Rule|  
    |ImageName. VisualBasicProject|KnownImageIds.VBProjectNode|  
    |ImageName. CSharpProject|KnownImageIds.CSProjectNode|  
    |ImageName. Empty|KnownImageIds. Blank|  
    |ImageName. MissingFolder|KnownImageIds.FolderOffline|  
    |ImageName. SharedImportReference|KnownImageIds.SharedProject|  
    |ImageName. SharedProjectCs|KnownImageIds.CSSharedProject|  
    |ImageName. SharedProjectVc|KnownImageIds.CPPSharedProject|  
    |ImageName. SharedProjectJs|KnownImageIds.JSSharedProject|  
    |ImageName. CSharpCodeFile|KnownImageIds.CSFileNode|  
    |ImageName. VisualBasicCodeFile|KnownImageIds.VBFileNode|  

  - Je mets à jour mon fournisseur de liste de saisie semi-automatique. Qu’est-ce que **KnownMonikers** correspond aux anciennes valeurs **StandardGlyphGroup** et **StandardGlyph** ?  

    |Nom|Nom|Nom|  
    |-|-|-|  
    |GlyphGroupClass|GlyphItemPublic|ClassPublic|  
    |GlyphGroupClass|GlyphItemInternal|ClassInternal|  
    |GlyphGroupClass|GlyphItemFriend|ClassInternal|  
    |GlyphGroupClass|GlyphItemProtected|ClassProtected|  
    |GlyphGroupClass|GlyphItemPrivate|ClassPrivate|  
    |GlyphGroupClass|GlyphItemShortcut|ClassShortcut|  
    |GlyphGroupConstant|GlyphItemPublic|ClassPublic|  
    |GlyphGroupConstant|GlyphItemInternal|ClassInternal|  
    |GlyphGroupConstant|GlyphItemFriend|ClassInternal|  
    |GlyphGroupConstant|GlyphItemProtected|ClassProtected|  
    |GlyphGroupConstant|GlyphItemPrivate|ClassPrivate|  
    |GlyphGroupConstant|GlyphItemShortcut|ClassShortcut|  
    |GlyphGroupDelegate|GlyphItemPublic|DelegatePublic|  
    |GlyphGroupDelegate|GlyphItemInternal|DelegateInternal|  
    |GlyphGroupDelegate|GlyphItemFriend|DelegateInternal|  
    |GlyphGroupDelegate|GlyphItemProtected|DelegateProtected|  
    |GlyphGroupDelegate|GlyphItemPrivate|DelegatePrivate|  
    |GlyphGroupDelegate|GlyphItemShortcut|DelegateShortcut|  
    |GlyphGroupEnum|GlyphItemPublic|EnumerationPublic|  
    |GlyphGroupEnum|GlyphItemInternal|EnumerationInternal|  
    |GlyphGroupEnum|GlyphItemFriend|EnumerationInternal|  
    |GlyphGroupEnum|GlyphItemProtected|EnumerationProtected|  
    |GlyphGroupEnum|GlyphItemPrivate|EnumerationPrivate|  
    |GlyphGroupEnum|GlyphItemShortcut|EnumerationShortcut|  
    |GlyphGroupEnumMember|GlyphItemPublic|EnumerationMemberPublic|  
    |GlyphGroupEnumMember|GlyphItemInternal|EnumerationMemberInternal|  
    |GlyphGroupEnumMember|GlyphItemFriend|EnumerationMemberInternal|  
    |GlyphGroupEnumMember|GlyphItemProtected|EnumerationMemberProtected|  
    |GlyphGroupEnumMember|GlyphItemPrivate|EnumerationMemberPrivate|  
    |GlyphGroupEnumMember|GlyphItemShortcut|EnumerationMemberShortcut|  
    |GlyphGroupEvent|GlyphItemPublic|EventPublic|  
    |GlyphGroupEvent|GlyphItemInternal|EventInternal|  
    |GlyphGroupEvent|GlyphItemFriend|EventInternal|  
    |GlyphGroupEvent|GlyphItemProtected|EventProtected|  
    |GlyphGroupEvent|GlyphItemPrivate|EventPrivate|  
    |GlyphGroupEvent|GlyphItemShortcut|EventShortcut|  
    |GlyphGroupException|GlyphItemPublic|ExceptionPublic|  
    |GlyphGroupException|GlyphItemInternal|ExceptionInternal|  
    |GlyphGroupException|GlyphItemFriend|ExceptionInternal|  
    |GlyphGroupException|GlyphItemProtected|ExceptionProtected|  
    |GlyphGroupException|GlyphItemPrivate|ExceptionPrivate|  
    |GlyphGroupException|GlyphItemShortcut|ExceptionShortcut|  
    |GlyphGroupField|GlyphItemPublic|FieldPublic|  
    |GlyphGroupField|GlyphItemInternal|FieldInternal|  
    |GlyphGroupField|GlyphItemFriend|FieldInternal|  
    |GlyphGroupField|GlyphItemProtected|FieldProtected|  
    |GlyphGroupField|GlyphItemPrivate|FieldPrivate|  
    |GlyphGroupField|GlyphItemShortcut|FieldShortcut|  
    |GlyphGroupInterface|GlyphItemPublic|InterfacePublic|  
    |GlyphGroupInterface|GlyphItemInternal|InterfaceInternal|  
    |GlyphGroupInterface|GlyphItemFriend|InterfaceInternal|  
    |GlyphGroupInterface|GlyphItemProtected|InterfaceProtected|  
    |GlyphGroupInterface|GlyphItemPrivate|InterfacePrivate|  
    |GlyphGroupInterface|GlyphItemShortcut|InterfaceShortcut|  
    |GlyphGroupMacro|GlyphItemPublic|MacroPublic|  
    |GlyphGroupMacro|GlyphItemInternal|MacroInternal|  
    |GlyphGroupMacro|GlyphItemFriend|MacroInternal|  
    |GlyphGroupMacro|GlyphItemProtected|MacroProtected|  
    |GlyphGroupMacro|GlyphItemPrivate|MacroPrivate|  
    |GlyphGroupMacro|GlyphItemShortcut|MacroShortcut|  
    |GlyphGroupMap|GlyphItemPublic|MapPublic|  
    |GlyphGroupMap|GlyphItemInternal|MapInternal|  
    |GlyphGroupMap|GlyphItemFriend|MapInternal|  
    |GlyphGroupMap|GlyphItemProtected|MapProtected|  
    |GlyphGroupMap|GlyphItemPrivate|MapPrivate|  
    |GlyphGroupMap|GlyphItemShortcut|MapShortcut|  
    |GlyphGroupMapItem|GlyphItemPublic|MapItemPublic|  
    |GlyphGroupMapItem|GlyphItemInternal|MapItemInternal|  
    |GlyphGroupMapItem|GlyphItemFriend|MapItemInternal|  
    |GlyphGroupMapItem|GlyphItemProtected|MapItemProtected|  
    |GlyphGroupMapItem|GlyphItemPrivate|MapItemPrivate|  
    |GlyphGroupMapItem|GlyphItemShortcut|MapItemShortcut|  
    |GlyphGroupMethod|GlyphItemPublic|MethodPublic|  
    |GlyphGroupMethod|GlyphItemInternal|MethodInternal|  
    |GlyphGroupMethod|GlyphItemFriend|MethodInternal|  
    |GlyphGroupMethod|GlyphItemProtected|MethodProtected|  
    |GlyphGroupMethod|GlyphItemPrivate|MethodPrivate|  
    |GlyphGroupMethod|GlyphItemShortcut|MethodShortcut|  
    |GlyphGroupOverload|GlyphItemPublic|MethodPublic|  
    |GlyphGroupOverload|GlyphItemInternal|MethodInternal|  
    |GlyphGroupOverload|GlyphItemFriend|MethodInternal|  
    |GlyphGroupOverload|GlyphItemProtected|MethodProtected|  
    |GlyphGroupOverload|GlyphItemPrivate|MethodPrivate|  
    |GlyphGroupOverload|GlyphItemShortcut|MethodShortcut|  
    |GlyphGroupModule|GlyphItemPublic|ModulePublic|  
    |GlyphGroupModule|GlyphItemInternal|ModuleInternal|  
    |GlyphGroupModule|GlyphItemFriend|ModuleInternal|  
    |GlyphGroupModule|GlyphItemProtected|ModuleProtected|  
    |GlyphGroupModule|GlyphItemPrivate|ModulePrivate|  
    |GlyphGroupModule|GlyphItemShortcut|ModuleShortcut|  
    |GlyphGroupNamespace|GlyphItemPublic|NamespacePublic|  
    |GlyphGroupNamespace|GlyphItemInternal|NamespaceInternal|  
    |GlyphGroupNamespace|GlyphItemFriend|NamespaceInternal|  
    |GlyphGroupNamespace|GlyphItemProtected|NamespaceProtected|  
    |GlyphGroupNamespace|GlyphItemPrivate|NamespacePrivate|  
    |GlyphGroupNamespace|GlyphItemShortcut|NamespaceShortcut|  
    |GlyphGroupOperator|GlyphItemPublic|OperatorPublic|  
    |GlyphGroupOperator|GlyphItemInternal|OperatorInternal|  
    |GlyphGroupOperator|GlyphItemFriend|OperatorInternal|  
    |GlyphGroupOperator|GlyphItemProtected|OperatorProtected|  
    |GlyphGroupOperator|GlyphItemPrivate|OperatorPrivate|  
    |GlyphGroupOperator|GlyphItemShortcut|OperatorShortcut|  
    |GlyphGroupProperty|GlyphItemPublic|PropertyPublic|  
    |GlyphGroupProperty|GlyphItemInternal|PropertyInternal|  
    |GlyphGroupProperty|GlyphItemFriend|PropertyInternal|  
    |GlyphGroupProperty|GlyphItemProtected|PropertyProtected|  
    |GlyphGroupProperty|GlyphItemPrivate|PropertyPrivate|  
    |GlyphGroupProperty|GlyphItemShortcut|PropertyShortcut|  
    |GlyphGroupStruct|GlyphItemPublic|StructurePublic|  
    |GlyphGroupStruct|GlyphItemInternal|StructureInternal|  
    |GlyphGroupStruct|GlyphItemFriend|StructureInternal|  
    |GlyphGroupStruct|GlyphItemProtected|StructureProtected|  
    |GlyphGroupStruct|GlyphItemPrivate|StructurePrivate|  
    |GlyphGroupStruct|GlyphItemShortcut|StructureShortcut|  
    |GlyphGroupTemplate|GlyphItemPublic|TemplatePublic|  
    |GlyphGroupTemplate|GlyphItemInternal|TemplateInternal|  
    |GlyphGroupTemplate|GlyphItemFriend|TemplateInternal|  
    |GlyphGroupTemplate|GlyphItemProtected|TemplateProtected|  
    |GlyphGroupTemplate|GlyphItemPrivate|TemplatePrivate|  
    |GlyphGroupTemplate|GlyphItemShortcut|TemplateShortcut|  
    |GlyphGroupTypedef|GlyphItemPublic|TypeDefinitionPublic|  
    |GlyphGroupTypedef|GlyphItemInternal|TypeDefinitionInternal|  
    |GlyphGroupTypedef|GlyphItemFriend|TypeDefinitionInternal|  
    |GlyphGroupTypedef|GlyphItemProtected|TypeDefinitionProtected|  
    |GlyphGroupTypedef|GlyphItemPrivate|TypeDefinitionPrivate|  
    |GlyphGroupTypedef|GlyphItemShortcut|TypeDefinitionShortcut|  
    |GlyphGroupType|GlyphItemPublic|TypePublic|  
    |GlyphGroupType|GlyphItemInternal|TypeInternal|  
    |GlyphGroupType|GlyphItemFriend|TypeInternal|  
    |GlyphGroupType|GlyphItemProtected|TypeProtected|  
    |GlyphGroupType|GlyphItemPrivate|TypePrivate|  
    |GlyphGroupType|GlyphItemShortcut|TypeShortcut|  
    |GlyphGroupUnion|GlyphItemPublic|UnionPublic|  
    |GlyphGroupUnion|GlyphItemInternal|UnionInternal|  
    |GlyphGroupUnion|GlyphItemFriend|UnionInternal|  
    |GlyphGroupUnion|GlyphItemProtected|UnionProtected|  
    |GlyphGroupUnion|GlyphItemPrivate|UnionPrivate|  
    |GlyphGroupUnion|GlyphItemShortcut|UnionShortcut|  
    |GlyphGroupVariable|GlyphItemPublic|FieldPublic|  
    |GlyphGroupVariable|GlyphItemInternal|FieldInternal|  
    |GlyphGroupVariable|GlyphItemFriend|FieldInternal|  
    |GlyphGroupVariable|GlyphItemProtected|FieldProtected|  
    |GlyphGroupVariable|GlyphItemPrivate|FieldPrivate|  
    |GlyphGroupVariable|GlyphItemShortcut|FieldShortcut|  
    |GlyphGroupValueType|GlyphItemPublic|ValueTypePublic|  
    |GlyphGroupValueType|GlyphItemInternal|ValueTypeInternal|  
    |GlyphGroupValueType|GlyphItemFriend|ValueTypeInternal|  
    |GlyphGroupValueType|GlyphItemProtected|ValueTypeProtected|  
    |GlyphGroupValueType|GlyphItemPrivate|ValueTypePrivate|  
    |GlyphGroupValueType|GlyphItemShortcut|ValueTypeShortcut|  
    |GlyphGroupIntrinsic|GlyphItemPublic|ObjectPublic|  
    |GlyphGroupIntrinsic|GlyphItemInternal|ObjectInternal|  
    |GlyphGroupIntrinsic|GlyphItemFriend|ObjectInternal|  
    |GlyphGroupIntrinsic|GlyphItemProtected|ObjectProtected|  
    |GlyphGroupIntrinsic|GlyphItemPrivate|ObjectPrivate|  
    |GlyphGroupIntrinsic|GlyphItemShortcut|ObjectShortcut|  
    |GlyphGroupJSharpMethod|GlyphItemPublic|MethodPublic|  
    |GlyphGroupJSharpMethod|GlyphItemInternal|MethodInternal|  
    |GlyphGroupJSharpMethod|GlyphItemFriend|MethodInternal|  
    |GlyphGroupJSharpMethod|GlyphItemProtected|MethodProtected|  
    |GlyphGroupJSharpMethod|GlyphItemPrivate|MethodPrivate|  
    |GlyphGroupJSharpMethod|GlyphItemShortcut|MethodShortcut|  
    |GlyphGroupJSharpField|GlyphItemPublic|FieldPublic|  
    |GlyphGroupJSharpField|GlyphItemInternal|FieldInternal|  
    |GlyphGroupJSharpField|GlyphItemFriend|FieldInternal|  
    |GlyphGroupJSharpField|GlyphItemProtected|FieldProtected|  
    |GlyphGroupJSharpField|GlyphItemPrivate|FieldPrivate|  
    |GlyphGroupJSharpField|GlyphItemShortcut|FieldShortcut|  
    |GlyphGroupJSharpClass|GlyphItemPublic|ClassPublic|  
    |GlyphGroupJSharpClass|GlyphItemInternal|ClassInternal|  
    |GlyphGroupJSharpClass|GlyphItemFriend|ClassInternal|  
    |GlyphGroupJSharpClass|GlyphItemProtected|ClassProtected|  
    |GlyphGroupJSharpClass|GlyphItemPrivate|ClassPrivate|  
    |GlyphGroupJSharpClass|GlyphItemShortcut|ClassShortcut|  
    |GlyphGroupJSharpNamespace|GlyphItemPublic|NamespacePublic|  
    |GlyphGroupJSharpNamespace|GlyphItemInternal|NamespaceInternal|  
    |GlyphGroupJSharpNamespace|GlyphItemFriend|NamespaceInternal|  
    |GlyphGroupJSharpNamespace|GlyphItemProtected|NamespaceProtected|  
    |GlyphGroupJSharpNamespace|GlyphItemPrivate|NamespacePrivate|  
    |GlyphGroupJSharpNamespace|GlyphItemShortcut|NamespaceShortcut|  
    |GlyphGroupJSharpInterface|GlyphItemPublic|InterfacePublic|  
    |GlyphGroupJSharpInterface|GlyphItemInternal|InterfaceInternal|  
    |GlyphGroupJSharpInterface|GlyphItemFriend|InterfaceInternal|  
    |GlyphGroupJSharpInterface|GlyphItemProtected|InterfaceProtected|  
    |GlyphGroupJSharpInterface|GlyphItemPrivate|InterfacePrivate|  
    |GlyphGroupJSharpInterface|GlyphItemShortcut|InterfaceShortcut|  
    |GlyphGroupError||StatusError|  
    |GlyphBscFile||ClassFile|  
    |GlyphAssembly||Référence|  
    |GlyphLibrary||Bibliothèque|  
    |GlyphVBProject||VBProjectNode|  
    |GlyphCoolProject||CSProjectNode|  
    |GlyphCppProject||CPPProjectNode|  
    |GlyphDialogId||Boîte de dialogue|  
    |GlyphOpenFolder||FolderOpened|  
    |GlyphClosedFolder||FolderClosed|  
    |GlyphArrow||GoToNext|  
    |GlyphCSharpFile||CSFileNode|  
    |GlyphCSharpExpansion||Extrait|  
    |GlyphKeyword||IntellisenseKeyword|  
    |GlyphInformation||StatusInformation|  
    |GlyphReference||ClassMethodReference|  
    |GlyphRecursion||Récursivité|  
    |GlyphXmlItem||Tag|  
    |GlyphJSharpProject||DocumentCollection|  
    |GlyphJSharpDocument||Document|  
    |GlyphForwardType||GoToNext|  
    |GlyphCallersGraph||CallTo|  
    |GlyphCallGraph||CallFrom|  
    |GlyphWarning||StatusWarning|  
    |GlyphMaybeReference||QuestionMark|  
    |GlyphMaybeCaller||CallTo|  
    |GlyphMaybeCall||CallFrom|  
    |GlyphExtensionMethod||ExtensionMethod|  
    |GlyphExtensionMethodInternal||ExtensionMethod|  
    |GlyphExtensionMethodFriend||ExtensionMethod|  
    |GlyphExtensionMethodProtected||ExtensionMethod|  
    |GlyphExtensionMethodPrivate||ExtensionMethod|  
    |GlyphExtensionMethodShortcut||ExtensionMethod|  
    |GlyphXmlAttribute||XmlAttribute|  
    |GlyphXmlChild||XmlElement|  
    |GlyphXmlDescendant||XmlDescendant|  
    |GlyphXmlNamespace||XmlNamespace|  
    |GlyphXmlAttributeQuestion||XmlAttributeLowConfidence|  
    |GlyphXmlAttributeCheck||XmlAttributeHighConfidence|  
    |GlyphXmlChildQuestion||XmlElementLowConfidence|  
    |GlyphXmlChildCheck||XmlElementHighConfidence|  
    |GlyphXmlDescendantQuestion||XmlDescendantLowConfidence|  
    |GlyphXmlDescendantCheck||XmlDescendantHighConfidence|  
    |GlyphCompletionWarning||IntellisenseWarning|
