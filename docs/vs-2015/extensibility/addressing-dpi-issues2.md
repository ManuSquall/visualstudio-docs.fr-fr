---
title: Adressage « Incidents2 » PPP | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3cb14cf601633efa6bbb022d8d1a56e62cc0f9b0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501434"
---
# <a name="addressing-dpi-issues"></a>Résolution des problèmes DPI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [« Incidents2 » du paramètre PPP de l’adressage](https://docs.microsoft.com/visualstudio/extensibility/addressing-dpi-issues2).  
  
Un nombre croissant de périphériques fournies dans les écrans « haute résolution ». Ces écrans ont généralement plus de 200 pixels par pouce (PPP). Travailler avec une application sur ces ordinateurs nécessitera contenu mis à l’échelle pour répondre aux besoins de l’affichage du contenu à une distance de l’affichage normal pour l’appareil. À compter de 2014, la cible principale pour les écrans à haute densité est mobile computing appareils (tablettes, ordinateurs portables coque et téléphones).  
  
 Windows 8.1 et versions ultérieures contient plusieurs fonctionnalités pour activer ces ordinateurs travailler avec les environnements où l’ordinateur est attaché à la fois à haute densité et densité standard affiche en même temps et les affiche.  
  
-   Windows peut vous permettre au contenu de mise à l’échelle à l’appareil à l’aide de la « faire texte et autres éléments supérieure ou inférieure » paramètre (disponible depuis Windows XP).  
  
-   Windows 8.1 et versions ultérieures est automatiquement adapter le contenu pour la plupart des applications être cohérent lorsque déplacées entre affiche de différentes densités de pixel. Lorsque l’écran principal est à haute densité (200 % mise à l’échelle) et l’affichage secondaire est densité standard (100 %), Windows sera automatiquement mise à l’échelle le contenu de la fenêtre application vers le bas sur l’affichage secondaire (1 pixel affichée pour chaque 4 pixels rendus par le application).  
  
-   Windows ne pourra pas le droit de mise à l’échelle pour la densité en pixels et à distance pour l’affichage (Windows 7 et versions ultérieures, configurables par l’OEM) d’affichage.  
  
-   Windows peut adapter automatiquement le contenu de 250 % sur de nouveaux périphériques qui dépassent les 280 PPP (à compter de Windows 8.1 s.14).  
  
 Windows a un moyen de traiter avec montée en charge l’interface utilisateur pour tirer parti des nombres de pixel accrue. Une application adhère à ce système en déclarant elle-même « système reconnaissant les résolutions. » Les applications qui ne le faites pas sont mis à l’échelle par le système. Cela peut entraîner une expérience utilisateur « approximative » où l’application entière est uniformément étiré par pixel. Exemple :  
  
 ![PPP émet floue](../extensibility/media/dpi-issues-fuzzy.png "PPP émet floue")  
  
 Visual Studio adhère à en cours de mise à l’échelle-reconnaissant les résolutions et par conséquent n’est pas « virtualisé. »  
  
 Tirer parti de plusieurs technologies d’interface utilisateur, qui présentent les différentes manières de traiter les facteurs définies par le système de mise à l’échelle Windows (et Visual Studio). Exemple :  
  
-   WPF mesure les contrôles d’une manière indépendante du périphérique (unités, et non en pixels). WPF UI s’ajuste automatiquement pour la résolution actuelle.  
  
-   Toutes les tailles de texte, quel que soit l’infrastructure d’interface utilisateur sont exprimées en points et par conséquent, sont traitées par le système en tant qu’indépendant des PPP. Texte dans Win32, WinForms et WPF déjà montée correctement lorsqu’elle est dessinée sur le périphérique d’affichage.  
  
-   Fenêtres et boîtes de dialogue Win32/WinForms disposent de moyens permettant la disposition est redimensionné avec texte – par exemple, via la grille, les flux et les panneaux de disposition de table. Ces outils permettent en évitant les emplacements de pixel codées en dur qui ne sont pas à l’échelle lorsque les tailles de police sont augmentées.  
  
-   Icônes fournies par le système ou des ressources en fonction des métriques du système (par exemple, SM_CXICON et SM_CXSMICON) sont déjà mis à l’échelle.  
  
## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Win32 plus anciens (GDI, GDI +) et l’interface utilisateur basée sur WinForms  
 Bien que WPF est déjà en reconnaissant les résolutions élevées, une grande partie de notre code basé sur Win32/GDI initialement écrite avec prise en charge DPI à l’esprit. Windows a fourni les API de mise à l’échelle PPP. Résout les problèmes de Win32 doit les utiliser régulièrement sur le produit. Visual Studio a fourni une assistance de bibliothèque de classes afin d’éviter les dupliquent des fonctionnalités et de garantir la cohérence générale du produit.  
  
## <a name="high-resolution-images"></a>Images haute résolution  
 Cette section s’applique principalement aux développeurs de l’extension de Visual Studio 2013. Pour Visual Studio 2015, utilisez le service d’images qui est intégré à Visual Studio. Vous pouvez également trouver que vous devez cible/prise en charge de nombreuses versions de Visual Studio et par conséquent, l’utilisation du service d’images en 2015 n’est pas une option dans la mesure où il n’existe pas dans les versions précédentes. Cette section concerne également vous puis.  
  
## <a name="scaling-up-images-that-are-too-small"></a>Mise à l’échelle des images qui sont trop petits.  
 Les images qui sont trop petits peuvent être « mis à l’échelle » et rendus sur GDI et WPF à l’aide de certaines méthodes courantes. Les classes d’assistance PPP managées sont disponibles pour les intégrateurs de systèmes internes et externes Visual Studio à l’adresse mise à l’échelle des icônes, bitmaps, imagestrips et imagelists. Basées sur Win32 de natif C / C ++ helpers sont disponibles pour la mise à l’échelle HICON, HBITMAP, HIMAGELIST et VsUI::GdiplusImage. Mise à l’échelle d’une image bitmap généralement nécessite uniquement une modification d’une ligne après l’ajout d’une référence à la bibliothèque d’assistance. Exemple :  
  
```cpp  
(Unmanaged)  VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
```  
  
```csharp  
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);  
```  
  
 Mise à l’échelle un objet imagelist varie selon qu’imagelist est terminé au moment du chargement, ou est ajouté au moment de l’exécution. Si elle est terminée au moment du chargement, appelez LogicalToDeviceUnits() avec imagelist comme vous le feriez pour une image bitmap. Lorsque le code a besoin charger une bitmap individuel avant de composer imagelist, veillez à mettre à l’échelle la taille de l’image d’imagelist :  
  
```csharp  
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);  
```  
  
 En code natif, les dimensions peuvent être mis à l’échelle lors de la création imagelist comme suit :  
  
```cpp  
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);  
```  
  
 Fonctions de la bibliothèque autorisent la spécification de l’algorithme de redimensionnement. Lorsque mise à l’échelle d’images à placer dans imagelists, veillez à spécifier la couleur d’arrière-plan qui est utilisée pour la transparence ou mode NearestNeighbor présente à l’échelle (ce qui entraîne des distorsions à 125 % et 150 %).  
  
 Consultez le <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> documentation sur MSDN.  
  
 Le tableau suivant présente des exemples de comment images doivent être à l’échelle PPP correspondante facteurs d’échelle. Les images en vert indiquent nos meilleures pratiques à compter de Visual Studio 2013 (100 à 200 % mise à l’échelle PPP) :  
  
 ![Problèmes de PPP mise à l’échelle](../extensibility/media/dpi-issues-scaling.png "les problèmes de PPP mise à l’échelle")  
  
## <a name="layout-issues"></a>Problèmes de mise en page  
 Problèmes courants de mise en page peuvent être évités principalement en conservant des points dans l’interface utilisateur à l’échelle et par rapport à l’autre plutôt qu’en utilisant les emplacements absolus (plus précisément, exprimées en pixels). Exemple :  
  
-   Les positions de disposition/texte amené à ajuster au compte pour la mise à l’échelle des images.  
  
-   Colonnes dans les grilles doivent avoir des largeurs ajustées pour le texte mis à l’échelle.  
  
-   Tailles codées en dur ou espace entre les éléments devez également être mis à l’échelle. Les tailles sont basés uniquement sur les dimensions de texte sont en général bien, étant donné que les polices sont automatiquement mis à l’échelle.  
  
 Fonctions d’assistance sont disponibles dans le <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> classe permettant d’autoriser la mise à l’échelle sur l’axe des X et Y :  
  
-   LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (fonctions permettent la mise à l’échelle sur X / axe des Y)  
  
-   int espace = DpiHelper.LogicalToDeviceUnitsX (10) ;  
  
-   int hauteur = VsUI::DpiHelper::LogicalToDeviceUnitsY(5) ;  
  
 Il existe des surcharges de LogicalToDeviceUnits pour permettre la mise à l’échelle des objets tels que Rect, Point et Size.  
  
## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>À l’aide de la bibliothèque/classe DPIHelper à l’échelle des images et la disposition  
 La bibliothèque d’assistance de Visual Studio PPP est disponible dans les formulaires natifs et managés et peut être utilisée par d’autres applications en dehors de l’interpréteur de commandes de Visual Studio.  
  
 Pour utiliser la bibliothèque, accédez à la [exemples d’extensibilité de Visual Studio VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) et clonez l’exemple de haute-DPI_Images_Icons  
  
 Dans les fichiers sources, inclure VsUIDpiHelper.h et appeler les fonctions statiques de classe de VsUI::DpiHelper :  
  
```cpp  
#include "VsUIDpiHelper.h"  
  
int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);  
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
  
```  
  
> [!NOTE]
>  N’utilisez pas les fonctions d’assistance dans des variables statiques au niveau du module ou de niveau classe. La bibliothèque utilise également des variables statiques pour la synchronisation de thread et que vous pouvez rencontrer des problèmes d’initialisation de la commande. Convertir ces variables statiques aux variables de membre non statiques, soit les encapsuler dans une fonction (afin qu’ils être construites lors du premier accès).  
  
 Pour accéder aux fonctions d’assistance de PPP à partir de code managé qui s’exécute à l’intérieur de l’environnement Visual Studio :  
  
-   Le projet de consommation doit faire référence à la dernière version de l’interpréteur de commandes MPF. Exemple :  
  
    ```csharp  
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />  
    ```  
  
-   Vérifiez que le projet dispose des références à **System.Windows.Forms**, **PresentationCore**, et **PresentationUI**.  
  
-   Dans le code, utilisez le **Microsoft.VisualStudio.PlatformUI** espace de noms et l’appel de fonctions statiques de classe de DpiHelper. Pour les types pris en charge (points, tailles, rectangles et ainsi de suite), sont fournies à l’échelle de fonctions d’extension qui retournent de nouveaux objets. Exemple :  
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);  
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();  
    DpiHelper.LogicalToDeviceUnits(ref bitmap);  
  
    ```  
  
## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Affaire à tolérance d’image WPF dans l’interface utilisateur zoomable  
 Dans WPF, les bitmaps sont redimensionnées automatiquement par WPF pour le niveau de zoom actuel PPP à l’aide d’un algorithme de haute qualité bicubique (valeur par défaut), qui fonctionne bien pour les images ou des captures d’écran de grande taille, mais ne convient pas pour les icônes d’élément de menu, car elle introduit une tolérance perçue .  
  
 Recommandations :  
  
-   Pour le logo image et les bannières illustration, la valeur par défaut <xref:System.Windows.Media.BitmapScalingMode> mode de redimensionnement peut être utilisé.  
  
-   Pour les éléments de menu et les images de l’iconographie, la <xref:System.Windows.Media.BitmapScalingMode> doit être utilisée quand elle n’entraîne pas autres artefacts de distorsion éliminer la tolérance (à 200 et 300 %).  
  
-   • Pour zoom grand ne niveaux pas des multiples de 100 % (par exemple, 250 % ou % de 350), mise à l’échelle des images iconographie avec bicubique résultats dans l’interface utilisateur floue, filigrane. Un meilleur résultat est obtenu par la première mise à l’échelle de l’image avec le mode NearestNeighbor présente au multiple plus grand de 100 % (par exemple, 200 % ou 300 %) et la mise à l’échelle avec bicubique à partir de là. Consultez des cas spéciaux : prescaling des images WPF pour grandes PPP niveaux pour plus d’informations.  
  
 La classe DpiHelper dans l’espace de noms Microsoft.VisualStudio.PlatformUI fournit un membre <xref:System.Windows.Media.BitmapScalingMode> qui peut être utilisé pour la liaison. Il permettra de l’interpréteur de commandes de Visual Studio contrôler l’image bitmap mise à l’échelle en mode sur le produit de manière uniforme, selon le facteur d’échelle PPP.  
  
 Pour l’utiliser dans XAML, ajoutez :  
  
```xaml  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />  
  
```  
  
 Le shell Visual Studio définit déjà cette propriété sur les boîtes de dialogue et fenêtres de niveau supérieur. WPF l’interface utilisateur en cours d’exécution dans Visual Studio est déjà hériter. Si le paramètre ne se propage pas à vos éléments de l’interface utilisateur particuliers, elle peut être définie sur l’élément racine de l’interface utilisateur XAML/WPF. Endroits où cela se produit incluent les fenêtres contextuelles, sur les éléments dont les parents de Win32, et les fenêtres du concepteur qui s’exécutent hors processus, tels que Blend.  
  
 Une interface utilisateur peut mettre à l’échelle indépendamment le niveau de zoom de PPP système-set, telles que l’éditeur de texte Visual Studio et les concepteurs WPF (WPF de bureau et Windows Store). Dans ce cas, DpiHelper.BitmapScalingMode ne doit pas être utilisé. Pour résoudre ce problème dans l’éditeur, l’équipe IDE créé une propriété personnalisée intitulée RenderOptions.BitmapScalingMode. Définir cette valeur de propriété téléconsultations ou mode NearestNeighbor présente selon le niveau de zoom combiné du système et de votre interface utilisateur.  
  
## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Cas particulier : prescaling d’images WPF pour les niveaux de PPP volumineux  
 Pour les niveaux de zoom très volumineux qui ne sont pas des multiples de 100 % (par exemple, 250 %, 350 % et ainsi de suite), mise à l’échelle des images d’iconographie avec résultats bicubique dans l’interface utilisateur floue, filigrane. L’impression de ces images en même temps que le texte est presque similaire à celui d’une illusion optique. Les images apparaissent à être plus proches à le œil plus clairs et par rapport au texte. Le résultat de mise à l’échelle au niveau de cette taille agrandie peut être amélioré par la première mise à l’échelle de l’image avec le mode NearestNeighbor présente au multiple plus grand de 100 % (par exemple, 200 % ou 300 %) et la mise à l’échelle avec bicubique le reste (50 pour cent supplémentaires).  
  
 Voici un exemple des différences de résultats, où la première image est mise à l’échelle avec l’algorithme de mise à l’échelle double améliorée -> 100 %, 200 % -> 250 %, et la deuxième identité simplement avec bicubique 100 % -> 250 %.  
  
 ![PPP émet l’exemple de mise à l’échelle Double](../extensibility/media/dpi-issues-double-scaling-example.png "PPP émet Double exemple de mise à l’échelle")  
  
 Pour activer l’interface utilisateur à utiliser cette mise à l’échelle double, le balisage XAML pour l’affichage de chaque élément d’Image devront être modifiées. Les exemples suivants montrent comment utiliser la double mise à l’échelle dans WPF dans Visual Studio à l’aide de la bibliothèque de DpiHelper et Shell.12/14.  
  
 Étape 1 : Prescale l’image à 200 %, 300 % et ainsi de suite à l’aide du mode NearestNeighbor présente.  
  
 Prescale l’image à l’aide d’un convertisseur de soit appliqué sur une liaison, ou avec une extension de balisage XAML. Exemple :  
  
```xaml  
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />  
  
<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
  
<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />  
  
```  
  
 Si l’image doit également être à thème (plus, si ce n’est pas tout, des cas), le balisage peut utiliser un autre convertisseur qui effectue tout d’abord les thèmes de l’image et puis préalablement mise à l’échelle. Le balisage peut utiliser <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> ou <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>, en fonction de la sortie de la conversion souhaitée.  
  
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
  
 Étape 2 : Vérifiez que la taille finale est correcte pour la résolution actuelle.  
  
 Étant donné que WPF étendra l’interface utilisateur pour la résolution actuelle à l’aide de la propriété BitmapScalingMode sur UIElement, un contrôle d’Image à l’aide d’une image prescaled comme sa source ressemblera à deux ou trois fois plus volumineux qu’il ne devrait. Voici plusieurs façons de compteur cet effet :  
  
-   Si vous connaissez la dimension de l’image d’origine à 100 %, vous pouvez spécifier la taille exacte du contrôle Image. Ces tailles reflètent que la taille de l’interface utilisateur avant la mise à l’échelle est appliquée.  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
    ```  
  
-   Si la taille de l’image d’origine n’est pas connue, une propriété LayoutTransform peut servir à l’échelle vers le bas de l’objet Image finale. Exemple :  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >  
        <Image.LayoutTransform>  
         <ScaleTransform  
             ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"  
             ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />  
        </Image.LayoutTransform>  
    </Image>  
    ```  
  
## <a name="enabling-hdpi-support-to-the-weboc"></a>L’activation de la prise en charge HDPI pour le WebOC  
 Par défaut, les contrôles WebOC (par exemple, le contrôle WebBrowser dans WPF, ou l’interface IWebBrowser2) n’activent pas prise en charge et détection de HDPI. Le résultat sera un contrôle incorporé avec l’affichage du contenu qui est trop petit pour un affichage haute résolution. La section suivante décrit comment activer la prise en charge de la haute résolution dans une instance de WebOC web spécifique.  
  
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
  
 Associer la classe qui implémente IDocHostUIHandler avec les documents du WebOC. Si vous avez implémenté l’interface ICustomDoc ci-dessus, dès que la propriété de document du WebOC n’est valide, les convertir en un ICustomDoc et appelez la méthode SetUIHandler, en passant de la classe qui implémente IDocHostUIHandler.  
  
```csharp  
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface  
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;  
customDoc.SetUIHandler(this);  
  
```  
  
 Si vous n’avez pas implémenté l’interface ICustomDoc, puis dès que la propriété de document du WebOC n’est valide, vous devez les convertir en un objet IOleObject et appelez la méthode SetClientSite, en passant dans la classe qui implémente IDocHostUIHandler. Définir l’indicateur DOCHOSTUIFLAG_DPI_AWARE sur la DOCHOSTUIINFO passée à l’appel de méthode GetHostInfo :  
  
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
  
 Il doit s’agir de tout ce que vous devez obtenir votre contrôle WebOC pour prendre en charge HPDI.  
  
## <a name="tips"></a>Conseils  
  
1.  Si la propriété de document sur le contrôle WebOC change, vous devrez peut-être réassocier le document à la classe IDocHostUIHandler.  
  
2.  Si la méthode ci-dessus ne fonctionne pas, il est un problème connu avec le WebOC ne collecte ne pas les modifications à l’indicateur de PPP. Le moyen le plus fiable de corriger cela consiste à activer/désactiver le zoom optique WebOC, deux appels de sens avec deux valeurs différentes pour le pourcentage de zoom. En outre, si cette solution de contournement est nécessaire, il peut être nécessaire effectuer cette opération sur chaque appel navigate.  
  
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

