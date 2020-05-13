---
title: Aborder les questions de l’IDD2 (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80f16c5b17a41d1f95b9bcb70e90eb8de46ad69d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740109"
---
# <a name="address-dpi-issues"></a>Résoudre les problèmes de l’IDD
Un nombre croissant d’appareils sont livrés avec des écrans « haute résolution ». Ces écrans ont généralement plus de 200 pixels par pouce (ppi). En travaillant avec une application sur ces ordinateurs, il faudra que le contenu soit mis à l’échelle pour répondre aux besoins de visualisation du contenu à une distance normale de visionnement de l’appareil. En 2014, l’objectif principal pour les écrans à haute densité est les appareils informatiques mobiles (tablettes, ordinateurs portables à clapet et téléphones).

Windows 8.1 et plus contient plusieurs fonctionnalités pour permettre à ces machines de fonctionner avec des écrans et des environnements où la machine est attachée à la fois à haute densité et à des écrans de densité standard en même temps.

- Windows peut vous permettre d’étendre le contenu à l’appareil à l’aide du paramètre " Faire du texte et d’autres éléments plus grand ou plus petit " (disponible depuis Windows XP).

- Windows 8.1 et plus échelle automatiquement le contenu pour la plupart des applications à être cohérente lorsqu’il est déplacé entre les écrans de densités de pixels différentes. Lorsque l’écran primaire est de haute densité (200% de mise à l’échelle) et que l’écran secondaire est de densité standard (100%), Windows échelle automatiquement le contenu de la fenêtre d’application vers le bas sur l’écran secondaire (1 pixel affiché pour chaque 4 pixels rendus par l’application).

- Windows sera par défaut à la bonne échelle pour la densité de pixels et la distance de visualisation pour l’affichage (Windows 7 et plus, OEM-configurable).

- Windows peut automatiquement mettre à l’échelle le contenu jusqu’à 250% sur les nouveaux appareils qui dépassent 280 ppi (à partir de Windows 8.1 S14).

  Windows a une façon de faire face à l’augmentation de l’interface utilisateur pour profiter de l’augmentation du nombre de pixels. Une application s’y attède en se déclarant « DPI système au courant ». Les applications qui ne le font pas sont augmentées par le système. Cela peut entraîner une expérience utilisateur "floue" où l’application entière est uniformément pixel-étiré. Par exemple :

  ![Problèmes de PPP - Flou](../extensibility/media/dpi-issues-fuzzy.png "Problèmes de PPP - Flou")

  Visual Studio opte pour être DPI mise à l’échelle-conscient, et n’est donc pas "virtualisé."

  Windows (et Visual Studio) exploitent plusieurs technologies d’interface utilisateur, qui ont des façons différentes de traiter les facteurs d’échelle définis par le système. Par exemple :

- WPF mesure les contrôles d’une manière indépendante de l’appareil (unités, pas pixels). L’interface utilisateur WPF s’intensifie automatiquement pour le DPI actuel.

- Toutes les tailles de texte, quel que soit le cadre de l’interface utilisateur, sont exprimées en points, et sont donc traitées par le système comme DPI-indépendante. Texte dans Win32, WinForms, et WPF déjà à l’échelle correctement lorsqu’il est attiré sur le dispositif d’affichage.

- Les dialogues et les fenêtres Win32/WinForms ont des moyens d’activer la mise en page qui resize avec du texte (par exemple, à travers la grille, le débit et les panneaux de disposition de table). Ceux-ci permettent d’éviter les emplacements de pixels codés durs qui ne sont pas mis à l’échelle lorsque la taille des polices est augmentée.

- Les icônes fournies par le système ou les ressources basées sur des mesures du système (par exemple, SM_CXICON et SM_CXSMICON) sont déjà mises à l’échelle.

## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Older Win32 (GDI, GDIMD) et WinForms-based UI
Bien que WPF soit déjà très conscient de l’ID, une grande partie de notre code basé sur Win32/GDI n’a pas été écrit à l’origine avec la sensibilisation d’IDD à l’esprit. Windows a fourni des API évolutifs DPI. Les correctifs aux problèmes de Win32 devraient les utiliser uniformément sur l’ensemble du produit. Visual Studio a fourni une bibliothèque de classe d’aide pour éviter de dupliquer les fonctionnalités et d’assurer la cohérence à travers le produit.

## <a name="high-resolution-images"></a>Images haute résolution
Cette section s’adresse principalement aux développeurs qui prolongent Visual Studio 2013. Pour Visual Studio 2015, utilisez le service d’image intégré à Visual Studio. Vous pouvez également constater que vous devez prendre en charge / cibler de nombreuses versions de Visual Studio et donc l’utilisation du service d’image en 2015 n’est pas une option car il n’existe pas dans les versions précédentes. Cette section est également pour vous alors.

## <a name="scaling-up-images-that-are-too-small"></a>Mise à l’échelle des images trop petites
Les images trop petites peuvent être augmentées et rendues sur GDI et WPF en utilisant certaines méthodes courantes. Des cours d’aide DPI gérés sont disponibles pour les intégrateurs internes et externes Visual Studio pour traiter les icônes de mise à l’échelle, les bitmaps, les imagestrips et les listes d’images. Les C/C-helpers natifs de Win32 sont disponibles pour l’échelle HICON, HBITMAP, HIMAGELIST et VsUI ::GdiplusImage. L’échelle d’un bitmap ne nécessite généralement qu’un changement d’une seule ligne après avoir inclus une référence à la bibliothèque d’aide. Par exemple :

```cpp
(Unmanaged) VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);
```

```csharp
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);
```

L’échelle d’une liste d’images dépend si la liste d’images est complète au moment de la charge, ou est annexée au moment de l’exécution. Si vous êtes terminé `LogicalToDeviceUnits()` au moment de la charge, appelez avec la liste d’images comme vous le feriez un bitmap. Lorsque le code doit charger une bitmap individuelle avant de composer la liste d’images, assurez-vous d’établir à l’échelle la taille de l’image de la liste d’images :

```csharp
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);
```

Dans le code natif, les dimensions peuvent être réduites lors de la création de la liste d’images comme suit :

```cpp
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);
```

Les fonctions dans la bibliothèque permettent de spécifier l’algorithme de resizing. Lors de l’échelle des images à placer dans les listes d’images, assurez-vous de spécifier la couleur de fond qui est utilisé pour la transparence, ou utiliser l’échelle NearestNeighbor (qui causera des distorsions à 125% et 150%).

Consultez <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> la documentation sur MSDN.

Le tableau suivant montre des exemples de la façon dont les images doivent être réduites aux facteurs de mise à l’échelle DPI correspondants. Les images décrites en orange dénotent notre meilleure pratique en tant que Visual Studio 2013 (100%-200% DPI mise à l’échelle):

![Problèmes de PPP lors de la mise à l’échelle](../extensibility/media/dpi-issues-scaling.png "Problèmes de PPP lors de la mise à l’échelle")

## <a name="layout-issues"></a>Problèmes de mise en page
Les problèmes de mise en page courants peuvent être évités principalement en gardant des points dans l’interface utilisateur à l’échelle et par rapport à l’autre plutôt que d’utiliser des emplacements absolus (en particulier, dans les unités de pixels). Par exemple :

- Les positions de mise en page/texte doivent s’ajuster pour tenir compte des images à grande échelle.

- Les colonnes dans les grilles doivent avoir des largeurs ajustées pour le texte à l’échelle.

- Les tailles codées dures ou l’espace entre les éléments devront également être mis à l’échelle. Les tailles qui ne sont basées que sur les dimensions du texte sont généralement fines, car les polices sont automatiquement réduites.

  Les fonctions d’assistance <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> sont disponibles dans la classe pour permettre la mise à l’échelle sur les axes X et Y :

- LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (fonctions permettent la mise à l’échelle sur l’axe X/Y)

- espace int - DpiHelper.LogicalToDeviceUnitsX (10);

- int hauteur - VsUI::DpiHelper::LogicalToDeviceUnitsY(5);

  Il existe des surcharges LogicalToDeviceUnits pour permettre la mise à l’échelle d’objets tels que Rect, Point et Size.

## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>Utilisation de la bibliothèque/classe DPIHelper pour mettre à l’échelle des images et de la mise en page
La bibliothèque d’aide Visual Studio DPI est disponible dans des formes indigènes et gérées et peut être utilisée en dehors de la coque Visual Studio par d’autres applications.

Pour utiliser la bibliothèque, rendez-vous sur les [échantillons d’extéabilité du Visual Studio VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) et clonez l’échantillon High-DPI_Images_Icons.

Dans les fichiers sources, inclure *VsUIDpiHelper.h* `VsUI::DpiHelper` et appeler les fonctions statiques de la classe:

```cpp
#include "VsUIDpiHelper.h"

int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);

```

> [!NOTE]
> N’utilisez pas les fonctions d’aide dans des variables statiques de niveau module ou de classe. La bibliothèque utilise également des statiques pour la synchronisation des fils et vous pourriez rencontrer des problèmes d’initialisation des commandes. Convertissez ces statiques en variables non statistiques des membres, soit enveloppez-les en fonction (afin qu’elles soient construites en premier accès).

Pour accéder aux fonctions d’assistance DPI à partir de code géré qui s’exécutera à l’intérieur de l’environnement Visual Studio :

- Le projet de consommation doit faire référence à la dernière version de Shell MPF. Par exemple :

    ```csharp
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />
    ```

- Assurez-vous que le projet a des références à **System.Windows.Forms**, **PresentationCore**, et **PresentationUI**.

- Dans le code, utilisez le **namespace Microsoft.VisualStudio.PlatformUI** et appelez les fonctions statiques de la classe DpiHelper. Pour les types pris en charge (points, tailles, rectangles, etc.), il existe des fonctions d’extension fournies qui renvoient de nouveaux objets à échelle. Par exemple :

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();
    DpiHelper.LogicalToDeviceUnits(ref bitmap);

    ```

## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Faire face au flou de l’image WPF dans l’interface utilisateur zoomable
Dans WPF, les bitmaps sont redimensionné automatiquement par WPF pour le niveau de zoom DPI actuel à l’aide d’un algorithme bicube de haute qualité (par défaut), qui fonctionne bien pour les photos ou de grandes captures d’écran, mais est inapproprié pour les icônes d’élément de menu car il introduit le flou perçu.

Recommandations :

- Pour l’image de logo <xref:System.Windows.Media.BitmapScalingMode> et les bannières d’art, le mode de resizing par défaut pourrait être utilisé.

- Pour les éléments de menu <xref:System.Windows.Media.BitmapScalingMode> et les images iconiques, il faut l’utiliser lorsqu’il ne provoque pas d’autres artefacts de distorsion pour éliminer le flou (à 200% et 300%).

- Pour les grands niveaux de zoom pas multiples de 100% (par exemple, 250% ou 350%), l’échelle des images d’iconographie avec des résultats bicubes dans floue, washed-out interface utilisateur. Un meilleur résultat est obtenu en évoluant d’abord l’image avec NearestNeighbor au plus grand multiple de 100% (par exemple, 200% ou 300%) et l’échelle avec bicube à partir de là. Voir cas spécial: pré-échelle des images WPF pour les grands niveaux DPI pour plus d’informations.

  La classe DpiHelper dans le namespace Microsoft.VisualStudio.PlatformUI fournit un membre <xref:System.Windows.Media.BitmapScalingMode> qui peut être utilisé pour la liaison. Il permettra à la coque Visual Studio de contrôler le mode de mise à l’échelle de bitmap à travers le produit uniformément, en fonction du facteur de mise à l’échelle DPI.

  Pour l’utiliser dans XAML, ajoutez :

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"

<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />

```

La coque Visual Studio place déjà cette propriété sur des fenêtres et des dialogues de haut niveau. L’interface utilisateur basée sur WPF en cours d’exécution dans Visual Studio en héritera déjà. Si le paramètre ne se propage pas à vos pièces particulières d’interface utilisateur, il peut être réglé sur l’élément racine de l’interface utilisateur XAML/WPF. Les endroits où cela se produit comprennent pop-ups, sur les éléments avec les parents Win32, et les fenêtres de concepteur qui sont à court de processus, tels que Blend.

Une certaine interface utilisateur peut évoluer indépendamment du niveau de zoom DPI défini par le système, comme l’éditeur de texte Visual Studio et les concepteurs basés sur WPF (WPF Desktop et Windows Store). Dans ces cas, DpiHelper.BitmapScalingMode ne doit pas être utilisé. Pour résoudre ce problème dans l’éditeur, l’équipe IDE a créé une propriété personnalisée intitulée RenderOptions.BitmapScalingMode. Définissez cette valeur de propriété à HighQuality ou NearestNeighbor en fonction du niveau de zoom combiné du système et de votre interface utilisateur.

## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Cas spécial : pré-échelle des images WPF pour les grands niveaux d’IDD
Pour les très grands niveaux de zoom qui ne sont pas des multiples de 100% (par exemple, 250%, 350%, et ainsi de suite), l’échelle des images d’iconographie avec des résultats bicubes dans floue, washed-out interface utilisateur. L’impression de ces images à côté d’un texte croustillant est presque comme celle d’une illusion d’optique. Les images semblent être plus proches de l’œil et floues par rapport au texte. Le résultat d’échelle à cette taille agrandie peut être amélioré en évoluant d’abord l’image avec NearestNeighbor au plus grand multiple de 100% (par exemple, 200% ou 300%) et l’échelle avec bicube au reste (un supplément de 50%).

Ce qui suit est un exemple des différences dans les résultats, où la première image est mise à l’échelle avec l’algorithme amélioré à double échelle de 100%->200%->250%, et la seconde juste avec bicube 100%->250%.

![DPI issues Double Scaling Exemple](../extensibility/media/dpi-issues-double-scaling-example.png "DPI issues Double Scaling Exemple")

Afin de permettre à l’interface utilisateur d’utiliser cette double échelle, la balisage XAML pour l’affichage de chaque élément Image devra être modifiée. Les exemples suivants montrent comment utiliser le double-échelle dans WPF dans Visual Studio en utilisant la bibliothèque DpiHelper et Shell.12/14.

Étape 1 : Prédimensionner l’image à 200 %, 300 %, etc. en utilisant NearestNeighbor.

Prédimensionner l’image à l’aide d’un convertisseur appliqué sur une fixation, ou avec une extension de balisage XAML. Par exemple :

```xaml
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />

<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />

<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />

```

Si l’image doit également être thématique (la plupart, sinon la totalité, devrait), la balisage peut utiliser un convertisseur différent qui fait d’abord le thème de l’image, puis la pré-mise à l’échelle. La balisage <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> peut <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>utiliser soit ou , en fonction de la sortie de conversion souhaitée.

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

Étape 2 : Assurez-vous que la taille finale est correcte pour l’IDD actuel.

Parce que WPF va mettre à l’échelle l’interface utilisateur pour le DPI actuel en utilisant la propriété BitmapScalingMode fixé sur l’UIElement, un contrôle d’image en utilisant une image prédimensionnée que sa source aura l’air deux ou trois fois plus grande qu’elle ne le devrait. Voici quelques façons de contrer cet effet :

- Si vous connaissez la dimension de l’image originale à 100%, vous pouvez spécifier la taille exacte du contrôle d’image. Ces tailles refléteront la taille de l’interface utilisateur avant l’application de l’échelle.

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />
    ```

- Si la taille de l’image originale n’est pas connue, une layoutTransforme peut être utilisée pour réduire l’objet Image final. Par exemple :

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >
        <Image.LayoutTransform>
            <ScaleTransform
                ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"
                ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />
        </Image.LayoutTransform>
    </Image>
    ```

## <a name="enabling-hdpi-support-to-the-weboc"></a>Permettre le support HDPI au WebOC
Par défaut, les contrôles WebOC (tels que le contrôle WebBrowser dans WPF, ou l’interface IWebBrowser2) n’activent pas la détection et le support HDPI. Le résultat sera un contrôle intégré avec un contenu d’affichage trop petit sur un écran haute résolution. Ce qui suit décrit comment activer le support de haute DPI dans une instance WebOC spécifique.

Implémentez l’interface IDocHostUIHandler (voir l’article MSDN sur [l’IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260(v=vs.85)):

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

Optionnellement, implémenter l’interface ICustomDoc (voir l’article MSDN sur [l’ICustomDoc](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753272(v=vs.85)):

```idl
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]
public interface ICustomDoc
{
    void SetUIHandler(IDocHostUIHandler pUIHandler);
}
```

Associez la classe qui implémente IDocHostUIHandler au document du WebOC. Si vous avez implémenté l’interface ICustomDoc ci-dessus, dès que la propriété de document webOC est valide, jetez-la à un ICustomDoc et appelez la méthode SetUIHandler, en passant la classe qui implémente IDocHostUIHandler.

```csharp
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;
customDoc.SetUIHandler(this);

```

Si vous n’avez PAS implémenté l’interface ICustomDoc, alors dès que la propriété de document webOC est `SetClientSite` valide, vous aurez besoin de le jeter à un IOleObject, et appeler la méthode, en passant dans la classe qui implémente IDocHostUIHandler. Réglez le drapeau DOCHOSTUIFLAG_DPI_AWARE sur le DOCHOSTUIINFO passé à l’appel `GetHostInfo` de méthode :

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

Cela devrait être tout ce dont vous avez besoin pour obtenir votre contrôle WebOC pour prendre en charge HPDI.

## <a name="tips"></a>Conseils

1. Si la propriété de document sur le contrôle WebOC change, vous devrez peut-être réassocier le document avec la classe IDocHostUIHandler.

2. Si ce qui précède ne fonctionne pas, il ya un problème connu avec le WebOC ne pas ramasser le changement de drapeau DPI. La façon la plus fiable de résoudre ce problème est de basculer le zoom optique du WebOC, ce qui signifie deux appels avec deux valeurs différentes pour le pourcentage de zoom. En outre, si cette solution de contournement est nécessaire, il pourrait être nécessaire de l’exécuter sur chaque appel de navigation.

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
