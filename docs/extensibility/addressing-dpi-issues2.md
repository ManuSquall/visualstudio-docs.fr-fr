---
title: Adressage DPI Issues2 | Microsoft Docs
description: Découvrez les problèmes liés à la programmation des écrans haute résolution, tels que la mise à l’échelle du contenu, les problèmes de mise en page et l’utilisation des API de mise à l’échelle DPI.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9cf7b4fe19cdefe11b77de1418b16454089f45c6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097511"
---
# <a name="address-dpi-issues"></a>Problèmes d’adresse DPI
Un nombre grandissant d’appareils sont fournis avec des écrans « haute résolution ». Ces écrans ont généralement plus de 200 pixels par pouce (PPP). L’utilisation d’une application sur ces ordinateurs nécessite que le contenu soit mis à l’échelle pour répondre aux besoins de l’affichage du contenu à une distance d’affichage normale pour l’appareil. À partir de 2014, la cible principale pour les affichages à haute densité est celle des appareils informatiques mobiles (tablettes, ordinateurs portables à ouverture latérale et téléphones).

Windows 8.1 et versions ultérieures contiennent plusieurs fonctionnalités permettant à ces machines de fonctionner avec des écrans et des environnements où l’ordinateur est attaché à des affichages à haute densité et à densité standard en même temps.

- Windows peut vous permettre de mettre à l’échelle le contenu sur l’appareil à l’aide du paramètre « rendre le texte et d’autres éléments plus grands ou plus petits » (disponible depuis Windows XP).

- Windows 8.1 et versions ultérieures met automatiquement à l’échelle le contenu pour que la plupart des applications soient cohérentes lorsqu’elles sont déplacées entre des affichages de densités de pixels différentes. Lorsque l’affichage principal est haute densité (200% de mise à l’échelle) et que l’affichage secondaire est une densité standard (100%), Windows met automatiquement à l’échelle le contenu de la fenêtre d’application sur l’affichage secondaire (1 pixel affiché pour chaque 4 pixels rendu par l’application).

- Par défaut, Windows passera à la mise à l’échelle appropriée pour la densité de pixels et la distance d’affichage pour l’affichage (Windows 7 et versions ultérieures, configurable par l’OEM).

- Windows peut automatiquement mettre à l’échelle le contenu jusqu’à 250% sur les nouveaux appareils qui dépassent 280 PPP (à partir de Windows 8.1 S14).

  Windows dispose d’un moyen de faire face à la mise à l’échelle de l’interface utilisateur pour tirer parti de l’augmentation du nombre de pixels. Une application choisit dans ce système en déclarant elle-même « prise en charge de la résolution du système ». Les applications qui ne le font pas sont mises à l’échelle par le système. Cela peut se traduire par une expérience utilisateur « floue » dans laquelle l’application entière est étirée uniformément par pixel. Par exemple :

  ![Problèmes de PPP - Flou](../extensibility/media/dpi-issues-fuzzy.png "Problèmes de PPP - Flou")

  Visual Studio opte pour la prise en charge de la mise à l’échelle DPI et n’est donc pas « virtualisé ».

  Windows (et Visual Studio) tirent parti de plusieurs technologies d’interface utilisateur, qui présentent des méthodes différentes pour traiter les facteurs de mise à l’échelle définis par le système. Par exemple :

- WPF mesure les contrôles de façon indépendante du périphérique (unités, et non pixels). L’interface utilisateur de WPF est automatiquement mise à l’échelle pour la résolution actuelle.

- Toutes les tailles de texte, quelle que soit l’infrastructure de l’interface utilisateur, sont exprimées en points, et sont donc traitées par le système comme étant indépendantes des DPI. Le texte dans Win32, WinForms et WPF est déjà mis à l’échelle correctement lorsqu’il est dessiné sur le périphérique d’affichage.

- Les boîtes de dialogue Win32/WinForms et Windows ont des moyens d’activer la disposition qui est redimensionnée avec du texte (par exemple, via des panneaux de disposition de grille, de fluide et de tableau). Celles-ci permettent d’éviter les emplacements de pixels codés en dur qui ne sont pas mis à l’échelle lorsque les tailles de police sont augmentées.

- Les icônes fournies par le système ou les ressources basées sur les métriques du système (par exemple, SM_CXICON et SM_CXSMICON) sont déjà mises à l’échelle.

## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Interface utilisateur Win32 (GDI, GDI+) et WinForms plus ancienne
Bien que WPF prenne déjà en charge la résolution PPP, une grande partie de notre code Win32/GDI n’était pas à l’origine écrit avec la prise en compte de la résolution PPP. Windows a fourni des API de mise à l’échelle DPI. Les correctifs pour les problèmes Win32 doivent les utiliser de manière cohérente dans le produit. Visual Studio a fourni une bibliothèque de classes d’assistance pour éviter la duplication des fonctionnalités et garantir la cohérence au sein du produit.

## <a name="high-resolution-images"></a>Images haute résolution
Cette section s’adresse principalement aux développeurs qui étendent Visual Studio 2013. Pour Visual Studio 2015, utilisez le service d’images qui est intégré à Visual Studio. Vous constaterez peut-être également que vous devez prendre en charge/cibler de nombreuses versions de Visual Studio. par conséquent, l’utilisation du service d’images dans 2015 n’est pas une option, car elle n’existe pas dans les versions précédentes. Cette section est également pour vous.

## <a name="scaling-up-images-that-are-too-small"></a>Mise à l’échelle des images trop petites
Les images qui sont trop petites peuvent être mises à l’échelle et rendues sur GDI et WPF à l’aide de méthodes courantes. Les classes d’assistance DPI managées sont disponibles pour les intégrateurs Visual Studio internes et externes pour traiter les icônes de mise à l’échelle, les bitmaps, imagestrips et imagelists. Les applications auxiliaires Win32 natives C/C + + sont disponibles pour la mise à l’échelle de HICON, HBITMAP, HIMAGELIST et VsUI :: GdiplusImage. En général, la mise à l’échelle d’une image bitmap nécessite uniquement une modification d’une seule ligne après l’inclusion d’une référence à la bibliothèque d’assistance. Par exemple :

```cpp
(Unmanaged) VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);
```

```csharp
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);
```

La mise à l’échelle d’un ImageList varie selon que le ImageList est terminé au moment du chargement ou qu’il est ajouté au moment de l’exécution. S’il est terminé au moment du chargement, appelez `LogicalToDeviceUnits()` avec ImageList comme vous le feriez pour une image bitmap. Lorsque le code doit charger une image bitmap individuelle avant de composer ImageList, veillez à mettre à l’échelle la taille de l’image du ImageList :

```csharp
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);
```

En code natif, les dimensions peuvent être mises à l’échelle lors de la création du ImageList comme suit :

```cpp
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);
```

Les fonctions de la bibliothèque autorisent la spécification de l’algorithme de redimensionnement. Lors de la mise à l’échelle des images à placer dans imagelists, veillez à spécifier la couleur d’arrière-plan utilisée pour la transparence ou utilisez la mise à l’échelle NearestNeighbor (ce qui entraîne des distorsions à 125% et 150%).

Consultez la <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> documentation sur MSDN.

Le tableau suivant présente des exemples de mise à l’échelle des images aux facteurs de mise à l’échelle DPI correspondants. Les images présentées en orange dénotent nos meilleures pratiques en matière de Visual Studio 2013 (mise à l’échelle de 100%-200% ppp) :

![Problèmes de PPP lors de la mise à l’échelle](../extensibility/media/dpi-issues-scaling.png "Problèmes de PPP lors de la mise à l’échelle")

## <a name="layout-issues"></a>Problèmes de disposition
Les problèmes de disposition courants peuvent être évités principalement en conservant les points de l’interface utilisateur mis à l’échelle et les uns par rapport aux autres plutôt qu’en utilisant des emplacements absolus (en l’occurrence, en pixels). Par exemple :

- Les positions de disposition/texte doivent être ajustées pour tenir compte des images mises à l’échelle.

- Les colonnes des grilles doivent avoir des largeurs ajustées pour le texte mis à l’échelle.

- Les tailles codées en dur ou l’espace entre les éléments devront également être mis à l’échelle. Les tailles basées uniquement sur les dimensions de texte sont généralement correctes, car les polices sont automatiquement mises à l’échelle.

  Les fonctions d’assistance sont disponibles dans la <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> classe pour permettre la mise à l’échelle sur l’axe X et Y :

- LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (fonctions permettant la mise à l’échelle sur l’axe X/Y)

- int Space = DpiHelper. LogicalToDeviceUnitsX (10);

- int Height = VsUI ::D piHelper :: LogicalToDeviceUnitsY (5);

  Il existe des surcharges LogicalToDeviceUnits pour permettre la mise à l’échelle d’objets tels que Rect, point et Size.

## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>Utilisation de la classe/bibliothèque DPIHelper pour mettre à l’échelle des images et de la disposition
La bibliothèque d’assistance PPP de Visual Studio est disponible sous forme native et managée et peut être utilisée en dehors du shell Visual Studio par d’autres applications.

Pour utiliser la bibliothèque, accédez aux [exemples d’extensibilité de Visual Studio VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) et clonez l’exemple de High-DPI_Images_Icons.

Dans les fichiers sources, incluez *VsUIDpiHelper. h* et appelez les fonctions statiques de la `VsUI::DpiHelper` classe :

```cpp
#include "VsUIDpiHelper.h"

int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);

```

> [!NOTE]
> N’utilisez pas les fonctions d’assistance dans les variables statiques au niveau du module ou au niveau de la classe. La bibliothèque utilise également des variables statiques pour la synchronisation des threads et vous pouvez rencontrer des problèmes d’initialisation de l’ordre. Convertissez ces valeurs statiques en variables membres non statiques, ou encapsulez-les dans une fonction (afin qu’elles soient construites au premier accès).

Pour accéder aux fonctions d’assistance PPP à partir du code managé qui s’exécute dans l’environnement Visual Studio :

- Le projet de consommation doit référencer la dernière version de Shell MPF. Par exemple :

    ```csharp
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />
    ```

- Vérifiez que le projet a des références à **System. Windows. Forms**, **PresentationCore** et **presentationui**.

- Dans le code, utilisez l’espace de noms **Microsoft. VisualStudio. PlatformUI** et appelez les fonctions statiques de la classe DpiHelper. Pour les types pris en charge (points, tailles, rectangles, etc.), des fonctions d’extension sont fournies et retournent de nouveaux objets mis à l’échelle. Par exemple :

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();
    DpiHelper.LogicalToDeviceUnits(ref bitmap);

    ```

## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Gestion de la tolérance d’image WPF dans l’interface utilisateur avec zoom
Dans WPF, les bitmaps sont redimensionnées automatiquement par WPF pour le niveau de zoom PPP actuel à l’aide d’un algorithme bicubique de haute qualité (par défaut), ce qui fonctionne bien pour les images ou les captures d’écran volumineuses, mais il n’est pas approprié pour les icônes d’élément de menu car il présente une tolérance perçue.

Recommandations :

- Pour les images de logos et de bannières, le <xref:System.Windows.Media.BitmapScalingMode> mode de redimensionnement par défaut peut être utilisé.

- Pour les éléments de menu et les images iconographie, <xref:System.Windows.Media.BitmapScalingMode> doit être utilisé lorsqu’il n’entraîne pas d’autres artefacts de distorsion afin d’éliminer la tolérance (à 200% et 300%).

- Pour les grands niveaux de zoom qui ne sont pas des multiples de 100% (par exemple, 250% ou 350%), la mise à l’échelle d’images iconographie avec des résultats bicubiques a une interface utilisateur floue et délavée. Un meilleur résultat est obtenu en mettant d’abord à l’échelle l’image avec NearestNeighbor sur le plus grand multiple de 100% (par exemple, 200% ou 300%). et la mise à l’échelle avec bicubique à partir de là. Pour plus d’informations, consultez cas spéciaux : prédimensionnement d’images WPF pour des niveaux de résolution élevée.

  La classe DpiHelper de l’espace de noms Microsoft. VisualStudio. PlatformUI fournit un membre <xref:System.Windows.Media.BitmapScalingMode> qui peut être utilisé pour la liaison. Cela permet au shell Visual Studio de contrôler le mode de mise à l’échelle des bitmaps sur le produit uniformément, en fonction du facteur d’échelle PPP.

  Pour l’utiliser en XAML, ajoutez :

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"

<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />

```

Le shell Visual Studio définit déjà cette propriété dans les fenêtres et les boîtes de dialogue de niveau supérieur. L’interface utilisateur WPF s’exécutant dans Visual Studio l’hérite déjà. Si le paramètre ne se propage pas à vos éléments d’interface utilisateur spécifiques, il peut être défini sur l’élément racine de l’interface utilisateur XAML/WPF. Les emplacements où cela se produit incluent les fenêtres contextuelles, les éléments avec parents Win32 et les fenêtres de concepteur qui s’exécutent hors processus, telles que Blend.

Certaines interfaces utilisateur peuvent être mises à l’échelle indépendamment du niveau de zoom DPI défini par le système, par exemple l’éditeur de texte Visual Studio et les concepteurs WPF (bureau WPF et Windows Store). Dans ce cas, DpiHelper. BitmapScalingMode ne doit pas être utilisé. Pour résoudre ce problème dans l’éditeur, l’équipe de l’IDE a créé une propriété personnalisée intitulée RenderOptions. BitmapScalingMode. Définissez cette valeur de propriété sur HighQuality ou NearestNeighbor en fonction du niveau de zoom combiné du système et de votre interface utilisateur.

## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Cas particulier : prédimensionnement d’images WPF pour les grands niveaux DPI
Pour les très grands niveaux de zoom qui ne sont pas des multiples de 100% (par exemple, 250%, 350%, etc.), la mise à l’échelle d’images iconographie avec des résultats bicubiques a une interface utilisateur floue et délavée. L’impression de ces images en même temps que du texte clair est quasiment identique à celle d’une illusion optique. Les images semblent être plus proches de l’œil et être désactivées par rapport au texte. Le résultat de la mise à l’échelle à cette taille agrandie peut être amélioré en mettant d’abord à l’échelle l’image avec NearestNeighbor sur le plus grand multiple de 100% (par exemple, 200% ou 300%). et la mise à l’échelle avec bicubique jusqu’au reste (50%) supplémentaires.

Voici un exemple des différences de résultats, où la première image est mise à l’échelle à l’aide de l’algorithme de double mise à l’échelle 100%->200%->250%, et la seconde uniquement avec les 100s bicubiques%->250%.

![Exemple de résolution des problèmes PPP double mise à l’échelle](../extensibility/media/dpi-issues-double-scaling-example.png "Exemple de résolution des problèmes PPP double mise à l’échelle")

Pour permettre à l’interface utilisateur d’utiliser cette double mise à l’échelle, le balisage XAML pour l’affichage de chaque élément image doit être modifié. Les exemples suivants montrent comment utiliser la double mise à l’échelle dans WPF dans Visual Studio à l’aide de la bibliothèque DpiHelper et de Shell. 12/14.

Étape 1 : prémettez l’image à l’échelle 200%, 300%, et ainsi de suite à l’aide de NearestNeighbor.

Mettre à l’échelle l’image à l’aide d’un convertisseur appliqué sur une liaison, ou avec une extension de balisage XAML. Par exemple :

```xaml
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />

<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />

<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />

```

Si l’image doit également être à thème (la plupart du temps, si ce n’est pas le cas), le balisage peut utiliser un convertisseur différent qui effectue tout d’abord les thèmes de l’image, puis la pré-mise à l’échelle. Le balisage peut utiliser <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> ou <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter> , selon la sortie de conversion souhaitée.

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

Étant donné que WPF met à l’échelle l’interface utilisateur pour la résolution actuelle à l’aide de la propriété BitmapScalingMode définie sur l’UIElement, un contrôle d’image utilisant une image Prémis à l’échelle comme source est à deux ou trois fois plus grand qu’il ne le devrait. Voici quelques méthodes pour contrer cet effet :

- Si vous connaissez la dimension de l’image d’origine à 100%, vous pouvez spécifier la taille exacte du contrôle image. Ces tailles reflètent la taille de l’interface utilisateur avant l’application de la mise à l’échelle.

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />
    ```

- Si la taille de l’image d’origine n’est pas connue, un LayoutTransform peut être utilisé pour réduire l’objet image final. Par exemple :

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >
        <Image.LayoutTransform>
            <ScaleTransform
                ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"
                ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />
        </Image.LayoutTransform>
    </Image>
    ```

## <a name="enabling-hdpi-support-to-the-weboc"></a>Activation de la prise en charge de HDPI sur le WebOC
Par défaut, les contrôles WebOC (tels que le contrôle WebBrowser dans WPF, ou l’interface IWebBrowser2) n’activent pas la détection et la prise en charge de HDPI. Le résultat est un contrôle incorporé dont le contenu d’affichage est trop petit sur un affichage haute résolution. La rubrique suivante décrit comment activer la prise en charge de la haute résolution dans une instance Web WebOC spécifique.

Implémentez l’interface IDocHostUIHandler (consultez l’article MSDN sur le [IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260(v=vs.85)):

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

Si vous le souhaitez, implémentez l’interface ICustomDoc (consultez l’article MSDN sur le [ICustomDoc](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753272(v=vs.85)):

```idl
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]
public interface ICustomDoc
{
    void SetUIHandler(IDocHostUIHandler pUIHandler);
}
```

Associez la classe qui implémente IDocHostUIHandler au document WebOC. Si vous avez implémenté l’interface ICustomDoc ci-dessus, dès que la propriété de document de WebOC est valide, effectuez un cast de celle-ci en ICustomDoc et appelez la méthode SetUIHandler, en passant la classe qui implémente IDocHostUIHandler.

```csharp
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;
customDoc.SetUIHandler(this);

```

Si vous n’avez pas implémenté l’interface ICustomDoc, dès que la propriété de document WebOC est valide, vous devez effectuer un cast de celle-ci en IOleObject, puis appeler la `SetClientSite` méthode, en passant la classe qui implémente IDocHostUIHandler. Définissez l’indicateur DOCHOSTUIFLAG_DPI_AWARE sur le DOCHOSTUIINFO passé à l' `GetHostInfo` appel de la méthode :

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

C’est tout ce dont vous avez besoin pour que votre contrôle WebOC prenne en charge HPDI.

## <a name="tips"></a>Conseils

1. Si la propriété de document sur le contrôle WebOC change, vous devrez peut-être réassocier le document à la classe IDocHostUIHandler.

2. Si la version ci-dessus ne fonctionne pas, il existe un problème connu avec le WebOC qui ne sélectionne pas la modification de l’indicateur PPP. La méthode la plus fiable pour résoudre ce cas consiste à basculer le zoom optique du WebOC, ce qui signifie que deux appels avec deux valeurs différentes pour le pourcentage de zoom. En outre, si cette solution de contournement est requise, il peut être nécessaire de l’exécuter à chaque appel de navigation.

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
