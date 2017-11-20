---
title: "Adressage « Incidents2 » PPP | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6e944c8a998a3e8bba46d5018faf1b9103a91240
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="addressing-dpi-issues"></a>Résoudre les problèmes de PPP
Un nombre croissant d’appareils fournies dans les écrans « haute résolution ». Ces écrans ont en général plus de 200 pixels par pouce (PPP). Travailler avec une application sur ces ordinateurs nécessitera un contenu à être mis à l’échelle en fonction des besoins de l’affichage du contenu à une distance de l’affichage normal pour le périphérique. À compter de 2014, la cible principale pour les écrans à densité élevée et est (ordinateurs portables de coque, tablettes et téléphones) des appareils mobile.  
  
 Windows 8.1 et versions ultérieures contient plusieurs fonctionnalités qui permettent à ces ordinateurs travailler avec les environnements où l’ordinateur est attaché à la fois à haute densité et densité standard affiche en même temps et les affiche.  
  
-   Windows peut vous permettre à ajuster le contenu à l’appareil à l’aide de « Rendre texte et autres éléments plus ou moins volumineux » configuration (disponible à partir de Windows XP).  
  
-   Windows 8.1 et versions ultérieures, est automatiquement redimensionnés contenu pour la plupart des applications être cohérent lorsque déplacé entre les affichages de différentes densités de pixels. Lorsque l’écran principal est haute densité (200 % mise à l’échelle) et l’affichage secondaire est densité standard (100 %), Windows redimensionne automatiquement le contenu de l’application de la fenêtre vers le bas sur l’affichage secondaire (1 pixel affichée pour chaque 4 pixels restitués par le application).  
  
-   Le droit de mise à l’échelle pour la densité en pixels et à distance pour l’affichage (Windows 7 et versions ultérieures, configurables par l’OEM) d’affichage par défaut est Windows.  
  
-   Windows peut adapter automatiquement le contenu à 250 % sur de nouveaux périphériques qui dépassent 280 PPP (à compter de Windows 8.1 s.14).  
  
 Windows offre un moyen de traitement de mise à l’échelle l’interface utilisateur pour tirer parti des nombres de pixel accrue. Une application a donné son consentement pour ce système en déclarant proprement dit « système reconnaissant les résolutions. » Les applications qui ne le faites pas sont mis à l’échelle par le système. Cela peut entraîner une expérience utilisateur « floue » où l’application entière est uniformément étiré en pixels. Exemple :  
  
 ![Problèmes de PPP floue](../extensibility/media/dpi-issues-fuzzy.png "PPP émet floue")  
  
 Visual Studio a donné son consentement à en cours de mise à l’échelle reconnaissant les résolutions et par conséquent n’est pas « virtualisée. »  
  
 Tirer parti de plusieurs technologies de l’interface utilisateur, qui présentent les différentes méthodes pour traiter avec mise à l’échelle des facteurs définis par le système Windows (et Visual Studio). Exemple :  
  
-   WPF mesure les contrôles d’une manière indépendante du périphérique (unités, et non en pixels). WPF UI s’ajuste automatiquement pour la résolution en cours.  
  
-   Toutes les tailles de texte, quelle que soit l’infrastructure d’interface utilisateur sont exprimées en points et ainsi sont traités par le système comme PPP indépendant. Texte dans Win32, Windows Forms et WPF déjà montée en puissance correctement lorsqu’il est dessiné sur le périphérique d’affichage.  
  
-   Fenêtres et boîtes de dialogue Win32/WinForms ont l’activation de disposition est redimensionné avec text - par exemple, via la grille, le flux et panneaux de disposition de table. Ceux-ci permettent d’éviter les emplacements codés en dur les pixels qui ne sont pas à l’échelle lorsque les tailles de police sont augmentées.  
  
-   Icônes fournies par le système ou des ressources en fonction des métriques du système (par exemple, SM_CXICON et SM_CXSMICON) sont déjà mis à l’échelle.  
  
## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Ancienne Win32 (GDI, GDI +) et l’interface utilisateur basée sur des Windows Forms  
 Alors que WPF est déjà haute PPP prenant en charge, une grande partie de notre code basé sur le GDI Win32 a été pas écrit à l’origine avec une reconnaissance de résolution à l’esprit. Windows a fourni des API de la mise à l’échelle PPP. Résout les problèmes de Win32 doit-elle utiliser régulièrement dans le produit. Visual Studio a fourni une assistance de bibliothèque de classes pour éviter la duplication de fonctionnalité et de garantir la cohérence entre le produit.  
  
## <a name="high-resolution-images"></a>Images en haute résolution  
 Cette section s’adresse principalement aux développeurs de l’extension Visual Studio 2013. Pour Visual Studio 2015, utilisez le service d’images qui est intégré à Visual Studio. Vous souhaiterez peut-être également que vous devez cible/prise en charge de plusieurs versions de Visual Studio et par conséquent, l’utilisation du service d’images dans 2015 n’est pas une option dans la mesure où il n’existe pas dans les versions précédentes. Cette section concerne également vous puis.  
  
## <a name="scaling-up-images-that-are-too-small"></a>Mise à l’échelle des images qui sont trop petits.  
 Les images qui sont trop petits peuvent « puissance » et rendus sur GDI et WPF à l’aide de certaines méthodes courantes. Les classes d’assistance PPP managées sont disponibles pour les intégrateurs de Visual Studio internes et externes à l’adresse mise à l’échelle des icônes, les bitmaps, imagestrips et imagelists. Basée sur Win32 de natif C / C ++ programmes d’assistance sont disponibles pour la mise à l’échelle HICON, HBITMAP, HIMAGELIST et VsUI::GdiplusImage. Mise à l’échelle d’une image bitmap généralement nécessite uniquement une modification d’une ligne après l’inclusion d’une référence à la bibliothèque d’assistance. Exemple :  
  
```cpp  
(Unmanaged)  VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
```  
  
```csharp  
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);  
```  
  
 Mise à l’échelle un imagelist dépend d’imagelist est terminé au moment du chargement, ou est ajouté au moment de l’exécution. Si elle est terminée au moment du chargement, appelez LogicalToDeviceUnits() avec l’imagelist comme vous le feriez pour une image bitmap. Lorsque le code a besoin charger une image bitmap individuelles avant de composer l’imagelist, veillez à mettre à l’échelle de la taille de l’image d’imagelist :  
  
```csharp  
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);  
```  
  
 En code natif, les dimensions peuvent être mis à l’échelle lorsque vous créez l’imagelist comme suit :  
  
```cpp  
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);  
```  
  
 Fonctions de la bibliothèque autorise la spécification de l’algorithme de redimensionnement. Lorsque mise à l’échelle d’images doit être placé dans imagelists, veillez à spécifier la couleur d’arrière-plan qui est utilisée pour la transparence, ou utiliser le mode NearestNeighbor présente l’échelle (ce qui entraîne la distorsion à 125 % et 150 %).  
  
 Consultez le <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> documentation sur MSDN.  
  
 Le tableau suivant présente des exemples de mode images doivent être à l’échelle PPP correspondant facteurs d’échelle. Les images en vert indiquent nos meilleures pratiques à compter de Visual Studio 2013 (100 à 200 % mise à l’échelle PPP) :  
  
 ![Problèmes de PPP mise à l’échelle](../extensibility/media/dpi-issues-scaling.png "mise à l’échelle des problèmes de PPP")  
  
## <a name="layout-issues"></a>Problèmes de mise en page  
 Problèmes courants de mise en page peuvent être évitées principalement en conservant les points dans l’interface utilisateur à l’échelle et par rapport à un autre, plutôt qu’à l’aide d’accès est absolu (en particulier, exprimées en pixels). Exemple :  
  
-   Les positions de mise en page/texte nécessaire d’ajuster au compte pour la mise à l’échelle des images.  
  
-   Colonnes dans les grilles doivent avoir des largeurs ajustées pour le texte de l’échelle.  
  
-   Codé en dur les tailles ou espace entre les éléments devrez également être mis à l’échelle. Tailles qui sont basées sur les dimensions de texte sont généralement bien, car les polices sont automatiquement mis à l’échelle.  
  
 Fonctions d’assistance sont disponibles dans la <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> classe permettant d’autoriser la mise à l’échelle sur l’axe des X et Y :  
  
-   LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (fonctions autoriser la mise à l’échelle sur X / axe des Y)  
  
-   espace d’int = DpiHelper.LogicalToDeviceUnitsX (10) ;  
  
-   hauteur d’int = VsUI::DpiHelper::LogicalToDeviceUnitsY(5) ;  
  
 Il existe des surcharges de LogicalToDeviceUnits pour permettre la mise à l’échelle des objets tels que Rect, Point et la taille.  
  
## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>À l’aide de la bibliothèque DPIHelper/la classe à l’échelle des images et la disposition  
 La bibliothèque d’assistance de Visual Studio PPP est disponible dans les formulaires natifs et managés et peut être utilisée par d’autres applications en dehors de l’interpréteur de commandes de Visual Studio.  
  
 Pour utiliser la bibliothèque, rendez-vous sur le [exemples d’extensibilité de Visual Studio extensibilité Visual Studio](https://github.com/Microsoft/VSSDK-Extensibility-Samples) et cloner l’exemple haute-DPI_Images_Icons  
  
 Dans les fichiers sources, inclure VsUIDpiHelper.h et appeler les fonctions statiques de classe de VsUI::DpiHelper :  
  
```cpp  
#include "VsUIDpiHelper.h"  
  
int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);  
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
  
```  
  
> [!NOTE]
>  N’utilisez pas les fonctions d’assistance dans des variables statiques au niveau du module ou au niveau de la classe. La bibliothèque utilise également des variables statiques pour la synchronisation de threads et susceptible de rencontrer des problèmes d’initialisation de la commande. Convertir les données statiques à des variables de membre non statiques, ou les encapsuler dans une fonction (afin qu’ils obtient construits lors du premier accès).  
  
 Pour accéder aux fonctions d’assistance PPP du code managé qui s’exécute à l’intérieur de l’environnement Visual Studio :  
  
-   Le projet de consommation doit faire référence à la dernière version de l’interpréteur de commandes MPF. Exemple :  
  
    ```csharp  
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />  
    ```  
  
-   Vérifiez le projet comporte des références à **System.Windows.Forms**, **PresentationCore**, et **PresentationUI**.  
  
-   Dans le code, utilisez la **Microsoft.VisualStudio.PlatformUI** espace de noms et l’appel de fonctions statiques de classe de DpiHelper. Pour les types pris en charge (points, des tailles, rectangles et ainsi de suite), sont fournies à l’échelle de fonctions d’extension qui retournent des nouveaux objets. Exemple :  
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);  
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();  
    DpiHelper.LogicalToDeviceUnits(ref bitmap);  
  
    ```  
  
## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Traitement de tolérance d’image WPF dans l’interface utilisateur zoomable  
 Dans WPF, les bitmaps sont redimensionnées automatiquement par WPF pour le niveau de zoom actuel PPP en utilisant un algorithme de haute qualité bicubique (par défaut), qui fonctionne bien pour les images ou des captures d’écran de grande taille, mais ne convient pour les icônes d’élément de menu, car elle introduit une tolérance perçue .  
  
 Recommandations :  
  
-   Pour le logo image et les bannières une illustration, la valeur par défaut <xref:System.Windows.Media.BitmapScalingMode> utilisable en mode de redimensionnement.  
  
-   Pour les éléments de menu et les images d’iconographie, la <xref:System.Windows.Media.BitmapScalingMode> doit être utilisé quand il ne peut entraîner d’autres artefacts de distorsion éliminer la tolérance (à 200 et 300 %).  
  
-   Pour les grandes zoom ne niveaux pas les multiples de 100 % (par exemple, 250 % ou % de 350), mise à l’échelle des images iconographie avec bicubique entraîne l’interface utilisateur floue, filigrane. Un meilleur résultat est obtenu par la première mise à l’échelle de l’image avec le mode NearestNeighbor présente au multiple plus grand de 100 % (par exemple, 200 % ou 300 %) et de la mise à l’échelle avec bicubique à partir de là. Consultez le cas particulier : prescaling des images WPF pour PPP volumineux niveaux pour plus d’informations.  
  
 La classe DpiHelper dans l’espace de noms Microsoft.VisualStudio.PlatformUI fournit un membre <xref:System.Windows.Media.BitmapScalingMode> qui peut être utilisé pour la liaison. Cela permet de l’interpréteur de commandes de Visual Studio contrôler la bitmap de montée en charge le mode sur le produit de manière uniforme, selon le facteur d’échelle PPP.  
  
 Pour l’utiliser en XAML, ajoutez :  
  
```xaml  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />  
  
```  
  
 Déjà, le shell Visual Studio définit cette propriété sur les boîtes de dialogue et fenêtres de niveau supérieur. WPF l’interface utilisateur en cours d’exécution dans Visual Studio est déjà hériter. Si le paramètre n’est pas propagée aux vos éléments particuliers d’interface utilisateur, elle peut être définie sur l’élément racine de l’interface utilisateur XAML/WPF. Emplacements où cela se produit incluent les fenêtres sur les éléments dont les parents de Win32, et le concepteur windows qui s’exécutent hors processus, tels que Blend.  
  
 Une interface utilisateur peut mettre à l’échelle indépendamment le niveau de zoom PPP système-set, telles que l’éditeur de texte Visual Studio et les concepteurs basées sur WPF (WPF de bureau et du Windows Store). Dans ce cas, DpiHelper.BitmapScalingMode ne doit pas être utilisé. Pour résoudre ce problème dans l’éditeur, l’équipe de l’IDE a créé une propriété personnalisée intitulée RenderOptions.BitmapScalingMode. Définissez cette valeur de propriété téléconsultations ou mode NearestNeighbor présente en fonction du niveau de zoom combinée du système et de votre interface utilisateur.  
  
## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Cas particulier : prescaling images WPF pour les niveaux PPP volumineux  
 Pour les niveaux de zoom très volumineux qui ne sont pas des multiples de 100 % (par exemple, 250 %, 350 % et ainsi de suite), mise à l’échelle des images d’iconographie avec résultats bicubique dans l’interface utilisateur floue, filigrane. L’impression de ces images en même temps que le texte est presque similaire à celle d’une illusion optique. Les images apparaissent à être plus proche à le œil clairs et par rapport au texte. Le résultat de mise à l’échelle à cette taille agrandie peut être amélioré en première mise à l’échelle de l’image avec le mode NearestNeighbor présente au multiple plus grand de 100 % (par exemple, 200 % ou 300 %) et de la mise à l’échelle avec bicubique pour le reste (50 pour cent supplémentaires).  
  
 Voici un exemple des différences de résultats, où la première image est mise à l’échelle avec l’algorithme de mise à l’échelle le double améliorée -> de 100 %, 200 % -> 250 %, et l’autre, avec bicubique 100 % -> 250 %.  
  
 ![Problèmes de PPP Double exemple de mise à l’échelle](../extensibility/media/dpi-issues-double-scaling-example.png "PPP émet Double exemple de mise à l’échelle")  
  
 Afin d’activer l’interface utilisateur à utiliser cette mise à l’échelle le double, le balisage XAML pour l’affichage de chaque élément Image doit être modifiée. Les exemples suivants montrent comment utiliser la double mise à l’échelle dans WPF dans Visual Studio à l’aide de la bibliothèque de DpiHelper et Shell.12/14.  
  
 Étape 1 : Prescale l’image à 200 %, 300 % et ainsi de suite à l’aide du mode NearestNeighbor présente.  
  
 Prescale l’image à l’aide d’un convertisseur de soit appliqué sur une liaison, ou avec une extension de balisage XAML. Exemple :  
  
```xaml  
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />  
  
<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
  
<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />  
  
```  
  
 Si l’image doit également être à thème (la plupart, voire la totalité, doit), le balisage peut utiliser un autre convertisseur qui effectue tout d’abord les thèmes de l’image et puis avant mise à l’échelle. Le balisage permet <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> ou <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>, en fonction de la sortie de la conversion souhaitée.  
  
```xaml  
<vsui:DpiPrescaleThemedImageSourceConverter x:Key="DpiPrescaleThemedImageSourceConverter" />  
  
<Image Width="16" Height="16">  
  <Image.Source>  
    <MultiBinding Converter="{StaticResource DpiPrescaleThemedImageSourceConverter}">  
      <Binding Path="Icon" />  
      <Binding Path="(vsui:ImageThemingUtilities.ImageBackgroundColor)"    
               RelativeSource="{RelativeSource Self}" />  
      <Binding Source="{x:Static vsui:Boxes.BooleanTrue}" />  
    </MultiBinding>  
  </Image.Source>  
</Image>  
```  
  
 Étape 2 : Vérifier que la taille finale est correcte pour la résolution en cours.  
  
 Étant donné que WPF évoluera l’interface utilisateur pour la résolution actuelle à l’aide de la propriété BitmapScalingMode sur UIElement, doit être un contrôle Image à l’aide d’une image prescaled comme sa source ressemble à deux ou trois fois supérieure à elle. Voici plusieurs façons de compteur cet effet :  
  
-   Si vous connaissez la dimension de l’image d’origine à 100 %, vous pouvez spécifier la taille exacte du contrôle Image. Ces tailles reflètent que la taille de l’interface utilisateur avant la mise à l’échelle est appliquée.  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
    ```  
  
-   Si la taille de l’image d’origine n’est pas connue, un LayoutTransform peut servir à l’échelle de l’objet Image finale. Exemple :  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >  
        <Image.LayoutTransform>  
         <ScaleTransform  
             ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"  
             ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />  
        </Image.LayoutTransform>  
    </Image>  
    ```  
  
## <a name="enabling-hdpi-support-to-the-weboc"></a>L’activation de la prise en charge HDPI WebOC  
 Par défaut, les contrôles WebOC (par exemple, le contrôle WebBrowser dans WPF, ou l’interface IWebBrowser2) n’activent pas prise en charge et détection de HDPI. Le résultat sera un contrôle incorporé avec l’affichage du contenu qui est trop petit sur un affichage en haute résolution. Voici comment activer la prise en charge de la haute résolution dans une instance de WebOC web spécifique.  
  
 Implémenter l’interface IDocHostUIHandler (consultez l’article MSDN sur le [IDocHostUIHandler](http://msdn.microsoft.com/library/aa753260.aspx) interface) :  
  
```idl  
[ComImport, InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("BD3F23C0-D43E-11CF-893B-00AA00BDCE1A")]  
public interface IDocHostUIHandler  
{  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ShowContextMenu(  
        [In, MarshalAs(UnmanagedType.U4)] int dwID,  
        [In] POINT pt,  
        [In, MarshalAs(UnmanagedType.Interface)] object pcmdtReserved,  
        [In, MarshalAs(UnmanagedType.IDispatch)] object pdispReserved);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetHostInfo([In, Out] DOCHOSTUIINFO info);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ShowUI(  
        [In, MarshalAs(UnmanagedType.I4)] int dwID,  
        [In, MarshalAs(UnmanagedType.Interface)] object activeObject,  
        [In, MarshalAs(UnmanagedType.Interface)] object commandTarget,  
        [In, MarshalAs(UnmanagedType.Interface)] object frame,  
        [In, MarshalAs(UnmanagedType.Interface)] object doc);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int HideUI();  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int UpdateUI();  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int EnableModeless([In, MarshalAs(UnmanagedType.Bool)] bool fEnable);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int OnDocWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int OnFrameWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ResizeBorder(  
        [In] COMRECT rect,  
        [In, MarshalAs(UnmanagedType.Interface)] object doc,  
        bool fFrameWindow);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int TranslateAccelerator(  
        [In] ref MSG msg,  
        [In] ref Guid group,  
        [In, MarshalAs(UnmanagedType.I4)] int nCmdID);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetOptionKeyPath(  
        [Out, MarshalAs(UnmanagedType.LPArray)] string[] pbstrKey,  
        [In, MarshalAs(UnmanagedType.U4)] int dw);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetDropTarget(  
        [In, MarshalAs(UnmanagedType.Interface)] IOleDropTarget pDropTarget,  
        [MarshalAs(UnmanagedType.Interface)] out IOleDropTarget ppDropTarget);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetExternal([MarshalAs(UnmanagedType.IDispatch)] out object ppDispatch);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int TranslateUrl(  
        [In, MarshalAs(UnmanagedType.U4)] int dwTranslate,  
        [In, MarshalAs(UnmanagedType.LPWStr)] string strURLIn,  
        [MarshalAs(UnmanagedType.LPWStr)] out string pstrURLOut);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int FilterDataObject(  
        IDataObject pDO,  
        out IDataObject ppDORet);  
    }   
```  
  
 Si vous le souhaitez, implémentez l’interface ICustomDoc (consultez l’article MSDN sur le [ICustomDoc](http://msdn.microsoft.com/library/aa753272.aspx) interface) :  
  
```idl  
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]  
public interface ICustomDoc  
{  
    void SetUIHandler(IDocHostUIHandler pUIHandler);  
}   
```  
  
 Associer la classe qui implémente IDocHostUIHandler avec les documents de WebOC. Si vous avez implémenté l’interface ICustomDoc ci-dessus, dès que la propriété de document de WebOC est valide, un cast vers un ICustomDoc et appelez la méthode SetUIHandler, la classe qui implémente IDocHostUIHandler.  
  
```csharp  
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface  
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;  
customDoc.SetUIHandler(this);  
  
```  
  
 Si vous n’avez pas implémenté l’interface ICustomDoc, puis dès que la propriété de document de WebOC est valide, vous devez effectuer un cast vers un objet IOleObject et appelez la méthode SetClientSite, dans la classe qui implémente IDocHostUIHandler. Définir l’indicateur DOCHOSTUIFLAG_DPI_AWARE sur le DOCHOSTUIINFO passé à l’appel de méthode GetHostInfo :  
  
```csharp  
public int GetHostInfo(DOCHOSTUIINFO info)  
{  
    // This is what the default site provides.  
    info.dwFlags = (DOCHOSTUIFLAG)0x5a74012;  
    // Add the DPI flag to the defaults  
    info.dwFlags |=.DOCHOSTUIFLAG.DOCHOSTUIFLAG_DPI_AWARE;  
    return S_OK;  
}  
```  
  
 Il doit s’agir de tout ce dont vous devez obtenir votre contrôle WebOC pour prendre en charge HPDI.  
  
## <a name="tips"></a>Conseils  
  
1.  Si la propriété de document sur le contrôle WebOC change, vous devrez peut-être réassocier le document avec la classe IDocHostUIHandler.  
  
2.  Si la liste ci-dessus ne fonctionne pas, il est un problème connu avec le WebOC ne pas reprenant la modification de l’indicateur PPP. Le moyen le plus fiable de cette résolution est pour activer/désactiver le zoom optique de WebOC, deux appels de sens avec deux valeurs différentes pour le pourcentage de zoom. En outre, si cette solution de contournement est requise, il peut être nécessaire pour l’exécuter sur chaque appel de naviguer.  
  
    ```csharp  
    // browser2 is a SHDocVw.IWebBrowser2 in this case  
    // EX: Call the Exec twice with DPI%-1 and then DPI% as the zoomPercent values  
    IOleCommandTarget cmdTarget = browser2.Document as IOleCommandTarget;  
    if (cmdTarget != null)  
    {  
        object commandInput = zoomPercent;  
        cmdTarget.Exec(IntPtr.Zero,  
                       OLECMDID_OPTICAL_ZOOM,  
                       OLECMDEXECOPT_DONTPROMPTUSER,  
                       ref commandInput,  
                       ref commandOutput);  
    }  
    ```