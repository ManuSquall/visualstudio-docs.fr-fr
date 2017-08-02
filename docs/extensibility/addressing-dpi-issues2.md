---
title: "Adressage &#171;&#160;Incidents2&#160;&#187; PPP | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# R&#233;solution des probl&#232;mes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Expédiez un nombre croissant de périphériques avec écrans « haute résolution ». Ces écrans ont en général plus de 200 pixels par pouce \(PPP\). Travailler avec une application sur ces ordinateurs nécessitera contenu pour être mis à l'échelle en fonction des besoins de l'affichage du contenu à une distance d'observation normale de l'appareil. À compter de 2014, la cible principale à densité élevée et affiche la valeur est \(tablettes, ordinateurs portables coque et téléphones\) des périphériques mobile.  
  
 Windows 8.1 et versions ultérieures contient plusieurs fonctionnalités pour permettre à ces ordinateurs travailler avec les environnements où l'ordinateur est attaché à la fois à haute densité et densité standard affiche en même temps et les affiche.  
  
-   Windows peut vous permettre à ajuster le contenu à l'appareil à l'aide de la « permettre texte et autres éléments plus ou moins volumineux » paramètre \(disponible depuis Windows XP\).  
  
-   Windows 8.1 et versions ultérieures, sont automatiquement redimensionnés contenu pour la plupart des applications soient cohérents lors du déplacement d'une affiche de différentes densités de pixels. Lorsque l'écran principal est haute densité \(augmentation de 200 %\) et l'affichage secondaire est la densité standard \(100 %\), Windows redimensionner automatiquement le contenu de l'application de la fenêtre vers le bas sur l'affichage secondaire \(1 pixel affichée pour chaque 4 pixels rendus par l'application\).  
  
-   Le droit de mise à l'échelle de la densité en pixels et à distance pour l'affichage \(Windows 7 et versions ultérieures, configurables par l'OEM\) d'affichage par défaut est Windows.  
  
-   Windows peut automatiquement ajuster le contenu de 250 % sur les nouveaux périphériques qui dépassent 280 PPP \(depuis Windows 8.1 s.14\).  
  
 Windows a une méthode de traitement mise à l'échelle de l'interface utilisateur pour tirer parti des nombres de pixel accrue. Une application de participer à ce système en déclarant proprement dit « système PPP prenant en charge. » Les applications qui ne le faites pas sont mis à l'échelle par le système. Cela peut entraîner une expérience utilisateur « floue » où l'application entière est uniformément étiré par pixel. Exemple :  
  
 ![Problèmes de PPP &#45; Flou](../extensibility/media/dpi-issues-fuzzy.png "DPI Issues Fuzzy")  
  
 Visual Studio indique l'inclusion d'en cours de mise à l'échelle prenant en charge DPI et par conséquent n'est pas « virtualisée. »  
  
 Tirer parti de plusieurs technologies d'interface utilisateur, qui présentent les différentes manières de traiter par le système de facteurs d'échelle Windows \(et Visual Studio\). Exemple :  
  
-   WPF mesure les contrôles d'une manière indépendante du périphérique \(unités, et non en pixels\). WPF UI s'adapte automatiquement à la résolution actuelle.  
  
-   Toutes les tailles de texte, quelle que soit l'infrastructure d'interface utilisateur sont exprimées en points et sont donc traités par le système comme indépendant des PPP. Texte dans WPF, WinForms et Win32 déjà montée correctement lorsqu'il est dessiné sur le périphérique d'affichage.  
  
-   Fenêtres et boîtes de dialogue Win32\/WinForms disposent de moyens permettant de disposition est redimensionné avec texte – par exemple, via la grille, le flux et les panneaux de disposition de table. Ces outils permettent d'éviter les emplacements codés en dur les pixels qui ne sont pas ajustées lorsque les tailles de police sont augmentées.  
  
-   Icônes fournies par le système ou ressources en fonction des métriques du système \(par exemple, SM\_CXICON et SM\_CXSMICON\) sont déjà mis à l'échelle.  
  
## Ancienne Win32 \(GDI, GDI \+\) et l'interface utilisateur WinForms  
 Alors que WPF est déjà en reconnaissant les résolutions élevées, beaucoup de notre code basé sur Win32\/GDI initialement écrite avec prise en charge DPI à l'esprit. Windows fournit des API de mise à l'échelle PPP. Résout les problèmes de Win32 doit utiliser régulièrement dans le produit. Visual Studio offre une assistance de bibliothèque de classes afin d'éviter dupliquent des fonctionnalités et de garantir la cohérence entre le produit.  
  
## Images haute résolution  
 Cette section est principalement utilisée pour les développeurs qui étendent Visual Studio 2013. Pour Visual Studio 2015, utilisez le service d'images qui est intégré à Visual Studio. Vous pouvez également trouver que vous devez cible\/prise en charge de nombreuses versions de Visual Studio et par conséquent, l'utilisation du service d'images en 2015 n'est pas une option dans la mesure où il n'existe pas dans les versions précédentes. Cette section est également puis.  
  
## Mise à l'échelle des images qui sont trop petits  
 Les images qui sont trop petits « mis à l'échelle » et rendus sur GDI et WPF à l'aide de certaines méthodes courantes. Les classes d'assistance PPP managées sont disponibles pour les intégrateurs de systèmes internes et externes Visual Studio à l'adresse mise à l'échelle des icônes, bitmaps, imagestrips et imagelists. Basé sur Win32 de natif C \/ C \+\+ « Helpers » est disponibles pour la mise à l'échelle HICON, HBITMAP, HIMAGELIST et VsUI::GdiplusImage. Mise à l'échelle d'une bitmap généralement requiert uniquement une modification d'une ligne après l'ajout d'une référence à la bibliothèque d'assistance. Exemple :  
  
```cpp  
(Unmanaged)  VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
```  
  
```c#  
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);  
```  
  
 Mise à l'échelle d'un objet imagelist dépend imagelist est terminé au moment du chargement, ou est ajouté au moment de l'exécution. Si elle est terminée au moment du chargement, appelez LogicalToDeviceUnits\(\) avec imagelist comme vous le feriez pour une image bitmap. Lorsque le code doit charger une bitmap individuel avant le composant imagelist, veillez à mettre à l'échelle de la taille de l'image d'imagelist :  
  
```c#  
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);  
```  
  
 En code natif, les dimensions peuvent être mis à l'échelle lors de la création d'imagelist comme suit :  
  
```cpp  
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);  
```  
  
 Fonctions de la bibliothèque autorise la spécification de l'algorithme de redimensionnement. Lorsque mise à l'échelle d'images à placer dans imagelists, assurez\-vous de spécifier la couleur d'arrière\-plan qui est utilisée pour la transparence ou utilisez le mode NearestNeighbor présente l'échelle \(ce qui provoque les distorsions à 125 % et 150 %\).  
  
 Consultez le <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> documentation sur MSDN.  
  
 Le tableau suivant présente des exemples de comment images doivent être mis à l'échelle PPP correspondant facteurs d'échelle. Les images en vert indiquent nos meilleures pratiques à partir de Visual Studio 2013 \(échelle en PPP 100 à 200 %\) :  
  
 ![Problèmes de PPP lors de la mise à l’échelle](~/extensibility/media/dpi-issues-scaling.png "DPI Issues Scaling")  
  
## Problèmes de mise en page  
 Problèmes de mise en page peuvent être évités principalement en conservant des points dans l'interface utilisateur à l'échelle et par rapport à l'autre au lieu d'utiliser des emplacements absolus \(plus précisément, exprimées en pixels\). Exemple :  
  
-   Les positions de mise en page\/texte nécessaire d'ajuster au compte pour la mise à l'échelle des images.  
  
-   Colonnes dans les grilles doivent avoir largeurs ajustées pour le texte mis à l'échelle.  
  
-   Tailles codées en dur ou espace entre les éléments devez également être mis à l'échelle. Tailles qui sont basées sur les dimensions de texte sont en général bien, car les polices sont automatiquement mis à l'échelle.  
  
 Fonctions d'assistance sont disponibles dans la <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> classe pour autoriser la mise à l'échelle de l'axe des X et Y :  
  
-   LogicalToDeviceUnitsX\/LogicalToDeviceUnitsY \(fonctions permettent la mise à l'échelle sur X \/ axe des Y\)  
  
-   int espace \= DpiHelper.LogicalToDeviceUnitsX \(10\) ;  
  
-   int hauteur \= VsUI::DpiHelper::LogicalToDeviceUnitsY\(5\) ;  
  
 Il existe des surcharges de LogicalToDeviceUnits pour permettre la mise à l'échelle des objets tels que Rect, Point et Size.  
  
## À l'aide de la bibliothèque\/classe DPIHelper à l'échelle des images et la disposition  
 La bibliothèque d'assistance de Visual Studio PPP est disponible dans les formulaires natifs et managés et peut être utilisée en dehors de l'interpréteur de commandes de Visual Studio par d'autres applications.  
  
 Pour utiliser la bibliothèque, accédez à la [exemples d'extensibilité de Visual Studio VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) et cloner l'exemple haute\-DPI\_Images\_Icons  
  
 Dans les fichiers source, incluez VsUIDpiHelper.h et appeler les fonctions statiques de classe de VsUI::DpiHelper :  
  
```cpp  
#include "VsUIDpiHelper.h"  
  
int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);  
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
  
```  
  
> [!NOTE]
>  N'utilisez pas les fonctions d'assistance dans des variables statiques au niveau du module ou au niveau de la classe. La bibliothèque utilise également des variables statiques pour la synchronisation des threads, et vous pouvez rencontrer des problèmes d'initialisation de la commande. Convertissez les données statiques à des variables de membres non statiques, ou les encapsuler dans une fonction \(afin qu'ils être construites lors du premier accès\).  
  
 Pour accéder aux fonctions d'assistance PPP du code managé qui s'exécute dans l'environnement Visual Studio :  
  
-   Le projet consommateur doit faire référence à la dernière version de MPF de Shell. Exemple :  
  
    ```c#  
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />  
    ```  
  
-   Vérifiez le projet comporte des références à **System.Windows.Forms**, **PresentationCore**, et **PresentationUI**.  
  
-   Dans le code, utilisez la **Microsoft.VisualStudio.PlatformUI** espace de noms et l'appel des fonctions statiques de la classe de DpiHelper. Pour les types pris en charge \(points, tailles, rectangles et ainsi de suite\), sont fournies à l'échelle de fonctions d'extension qui retournent des nouveaux objets. Exemple :  
  
    ```c#  
    using Microsoft.VisualStudio.PlatformUI;  
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);  
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();  
    DpiHelper.LogicalToDeviceUnits(ref bitmap);  
  
    ```  
  
## Affaire à tolérance d'image WPF dans l'interface utilisateur zoomable  
 Dans WPF, les bitmaps sont redimensionnées automatiquement par WPF pour le niveau de zoom actuel PPP en utilisant un algorithme de haute qualité bicubique \(par défaut\), qui fonctionne bien pour les images ou les captures d'écran de grande taille, mais est inapproprié pour les icônes d'élément de menu, car il implique de tolérance perçue.  
  
 Recommandations :  
  
-   Pour un logo image et bannières illustration, la valeur par défaut <xref:System.Windows.Media.BitmapScalingMode> utilisable en mode de redimensionnement.  
  
-   Pour les éléments de menu et les images de l'iconographie, la <xref:System.Windows.Media.BitmapScalingMode> doit être utilisée lorsqu'elle n'entraîne pas autres artefacts de distorsion éliminer la tolérance \(à 200 et 300 %\).  
  
-   •	Pour les niveaux de zoom élevé pas un multiple de 100 % \(par exemple, 250 % 350 %\), mise à l'échelle des images iconographie bicubique entraîne l'interface utilisateur floue, filigrane. Un meilleur résultat est obtenu par la première mise à l'échelle de l'image avec le mode NearestNeighbor présente au multiple plus grand de 100 % \(par exemple, 200 % ou 300 %\) et la mise à l'échelle avec bicubique à partir de là. Consultez les cas spécial : prescaling des images WPF pour PPP grand niveaux pour plus d'informations.  
  
 La classe DpiHelper dans l'espace de noms Microsoft.VisualStudio.PlatformUI fournit un membre <xref:System.Windows.Media.BitmapScalingMode> qui peut être utilisé pour la liaison. Elle permet au shell Visual Studio contrôler le mode d'ajustement sur le produit de manière uniforme, selon le facteur d'échelle PPP de bitmap.  
  
 Pour l'utiliser en XAML, ajoutez :  
  
```xaml  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />  
  
```  
  
 Le shell Visual Studio définit déjà cette propriété sur les boîtes de dialogue et fenêtres de niveau supérieur. WPF l'interface utilisateur en cours d'exécution dans Visual Studio est déjà hériter. Si le paramètre n'est pas propagée aux vos éléments d'interface utilisateur particuliers, elle peut être définie sur l'élément racine de l'interface utilisateur WPF\/XAML. Cette situation parmi les fenêtres contextuelles, sur les éléments dont les parents de Win32, et concepteurs windows qui s'exécutent hors processus, tels que Blend.  
  
 Une interface utilisateur peut évoluer indépendamment le niveau de zoom de PPP système\-set, telles que l'éditeur de texte Visual Studio et les concepteurs basés sur WPF \(WPF de bureau et du Windows Store\). Dans ce cas, DpiHelper.BitmapScalingMode ne doit pas être utilisé. Pour résoudre ce problème dans l'éditeur, l'équipe de l'IDE a créé une propriété personnalisée intitulée RenderOptions.BitmapScalingMode. Définissez cette valeur de propriété téléconsultations ou mode NearestNeighbor présente en fonction du niveau de zoom combinée du système et de votre interface utilisateur.  
  
## Cas particulier : prescaling images WPF pour les grands niveaux PPP  
 Pour les niveaux de zoom très volumineux qui ne sont pas un multiple de 100 % \(par exemple, 250 %, 350 % et ainsi de suite\), dimensionner des images iconographie bicubique aboutit à l'interface utilisateur floue, filigrane. L'impression de ces images en même temps que le texte est presque similaire à celui d'une illusion optique. Les images apparaissent à être plus proche à le œil et par rapport au texte. Le résultat de mise à l'échelle avec cette taille agrandie peut être amélioré par la première mise à l'échelle de l'image avec le mode NearestNeighbor présente au multiple plus grand de 100 % \(par exemple, 200 % ou 300 %\) et la mise à l'échelle avec bicubique pour le reste \(50 pour cent supplémentaires\).  
  
 Voici un exemple des différences de résultats, où la première image est mise à l'échelle avec l'algorithme de mise à l'échelle double améliorée \-\> 100 %, 200 % \-\> 250 %, et l'autre avec des bicubique 100 % \-\> 250 %.  
  
 ![DPI Issues Double Scaling Example](../extensibility/media/dpi-issues-double-scaling-example.png "DPI Issues Double Scaling Example")  
  
 Pour activer l'interface utilisateur à utiliser cette mise à l'échelle double, le balisage XAML pour l'affichage de chaque élément Image doit être modifiée. Les exemples suivants montrent comment utiliser la double mise à l'échelle dans WPF dans Visual Studio à l'aide de la bibliothèque de DpiHelper et Shell.12\/14.  
  
 Étape 1: Prescale l'image à 200 %, 300 % et ainsi de suite à l'aide du mode NearestNeighbor présente.  
  
 Prescale l'image à l'aide du convertisseur appliqué sur une liaison, ou avec une extension de balisage XAML. Exemple :  
  
```xaml  
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />  
  
<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
  
<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />  
  
```  
  
 Si l'image doit également être à thème \(la plupart, sinon tous, devrait\), le balisage peut utiliser un autre convertisseur qui effectue tout d'abord les thèmes de l'image et puis préalablement mise à l'échelle. Le balisage peut utiliser <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> ou <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>, selon le résultat de la conversion souhaitée.  
  
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
  
 Étape 2: Vérifiez que la taille finale est correcte pour la résolution actuelle.  
  
 Étant donné que WPF étendra l'interface utilisateur pour la résolution actuelle à l'aide de la propriété BitmapScalingMode sur UIElement, un contrôle Image à l'aide d'une image prescaled comme sa source ressemblera à deux ou trois fois plus grand que devez. Voici deux façons pour contrer cet effet :  
  
-   Si vous connaissez la dimension de l'image d'origine à 100 %, vous pouvez spécifier la taille exacte du contrôle Image. Ces tailles reflètent que la taille de l'interface utilisateur avant la mise à l'échelle est appliquée.  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
    ```  
  
-   Si la taille de l'image d'origine n'est pas connue, une propriété LayoutTransform peut servir à l'échelle de l'objet Image finale. Exemple :  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >  
        <Image.LayoutTransform>  
         <ScaleTransform  
             ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"  
             ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />  
        </Image.LayoutTransform>  
    </Image>  
    ```  
  
## Prise en charge de HDPI pour le WebOC  
 Par défaut, les contrôles WebOC \(par exemple, le contrôle WebBrowser dans WPF, ou l'interface IWebBrowser2\) n'activent pas la prise en charge et détection de HDPI. Le résultat sera un contrôle incorporé avec affichage du contenu qui est trop petit sur un affichage haute résolution. Ce qui suit décrit comment activer la prise en charge de haute résolution dans une instance de WebOC web spécifique.  
  
 Implémenter l'interface IDocHostUIHandler \(consultez l'article MSDN sur le [IDocHostUIHandler](http://msdn.microsoft.com/library/aa753260.aspx) interface\) :  
  
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
  
 Vous pouvez également implémenter l'interface de ICustomDoc \(consultez l'article MSDN sur le [ICustomDoc](http://msdn.microsoft.com/library/aa753272.aspx) interface\) :  
  
```idl  
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]  
public interface ICustomDoc  
{  
    void SetUIHandler(IDocHostUIHandler pUIHandler);  
}   
```  
  
 Associer la classe qui implémente IDocHostUIHandler avec les documents de WebOC. Si vous avez implémenté l'interface ICustomDoc ci\-dessus, dès que la propriété de document du WebOC est valide, le convertir en un ICustomDoc et appelez la méthode SetUIHandler, la classe qui implémente IDocHostUIHandler.  
  
```c#  
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface  
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;  
customDoc.SetUIHandler(this);  
  
```  
  
 Si vous n'avez pas implémenté l'interface ICustomDoc, puis dès que la propriété de document du WebOC est valide, vous devez effectuer un cast vers un objet IOleObject et appelez la méthode SetClientSite, en passant dans la classe qui implémente IDocHostUIHandler. Définir l'indicateur DOCHOSTUIFLAG\_DPI\_AWARE sur la DOCHOSTUIINFO transmis à l'appel de méthode GetHostInfo :  
  
```c#  
public int GetHostInfo(DOCHOSTUIINFO info)  
{  
    // This is what the default site provides.  
    info.dwFlags = (DOCHOSTUIFLAG)0x5a74012;  
    // Add the DPI flag to the defaults  
    info.dwFlags |=.DOCHOSTUIFLAG.DOCHOSTUIFLAG_DPI_AWARE;  
    return S_OK;  
}  
```  
  
 Il doit s'agir de tout ce que vous devez obtenir votre contrôle WebOC pour prendre en charge HPDI.  
  
## Conseils  
  
1.  Si la propriété de document sur le contrôle WebOC change, vous devrez peut\-être réassocier le document avec la classe IDocHostUIHandler.  
  
2.  Si les éléments ci\-dessus ne fonctionnent pas, il est un problème connu avec le WebOC ne choisissaient pas la modification de l'indicateur de PPP. La méthode la plus fiable de résolution de ce fait basculer le zoom optique WebOC, deux appels de sens avec deux valeurs différentes pour le pourcentage de zoom. En outre, si cette solution de contournement est nécessaire, il peut être nécessaire effectuer cette opération à chaque appel navigate.  
  
    ```c#  
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