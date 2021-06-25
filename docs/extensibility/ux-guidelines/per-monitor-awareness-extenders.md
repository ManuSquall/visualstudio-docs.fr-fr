---
title: Prise en charge de la prise en charge des Per-Monitor pour les extendeurs Visual Studio
titleSuffix: ''
description: En savoir plus sur la nouvelle prise en charge de l’extendeur pour la détection par moniteur disponible dans Visual Studio 2019.
ms.date: 04/10/2019
helpviewer_keywords:
- Visual Studio, PMA, per-monitor-awareness, extenders, Windows Forms
- Per-Monitor Awareness support for extenders
author: rub8n
ms.author: rurios
manager: anthc
monikerRange: vs-2019
ms.topic: reference
dev_langs:
- CSharp
- CPP
ms.openlocfilehash: 90ec038e8f27407ba08633bacbb5576bee2a7883
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902044"
---
# <a name="per-monitor-awareness-support-for-visual-studio-extenders"></a>Prise en charge de la prise en charge des Per-Monitor pour les extendeurs Visual Studio

Les versions antérieures à Visual Studio 2019 avaient un contexte de reconnaissance PPP défini sur la prise en charge du système, plutôt que sur la prise en charge de la résolution par moniteur (PMA). L’exécution dans la reconnaissance du système a entraîné une dégradation de l’expérience visuelle (par exemple, des polices ou des icônes floues) à chaque fois que Visual Studio devait effectuer un rendu sur des moniteurs avec des facteurs d’échelle différents ou à distance sur des ordinateurs avec différentes configurations d’affichage (par exemple, une mise à l’échelle de Windows).

Le contexte de détection PPP de Visual Studio 2019 est défini comme AVM, lorsque l’environnement le prend en charge, ce qui permet à Visual Studio de s’afficher en fonction de la configuration de l’affichage où il est hébergé plutôt que d’une configuration définie par le système. À la fin de la traduction en une interface utilisateur toujours nette pour les zones de surface qui prennent en charge le mode PMA.

Pour plus d’informations sur les conditions générales et le scénario global abordé dans ce document, reportez-vous à la documentation relative au [développement d’applications de bureau haute résolution sur Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) .

## <a name="quickstart"></a>Démarrage rapide

- S’assurer que Visual Studio s’exécute en mode AVM (voir **activation de AVM**)

- Valider le bon fonctionnement de votre extension dans un ensemble de scénarios courants (consultez **test de vos extensions pour les problèmes AVM**)

- Si vous rencontrez des problèmes, vous pouvez utiliser les stratégies/recommandations présentées dans ce document pour diagnostiquer et résoudre ces problèmes. Vous devez également ajouter le nouveau package NuGet [Microsoft. VisualStudio. DpiAwareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) à votre projet pour accéder aux API requises.

## <a name="enable-pma"></a>Activer AVM

Pour activer l’AVM dans Visual Studio, les conditions suivantes doivent être remplies :

- Mise à jour 2018 de Windows 10 avril (v1803, RS4) ou version ultérieure
- .NET Framework 4,8 RTM ou version ultérieure
- L’option [« optimiser le rendu pour les écrans avec des densités de pixels différentes »](../../ide/reference/general-environment-options-dialog-box.md) est activée pour Visual Studio 2019

Une fois ces conditions satisfaites, Visual Studio active automatiquement le mode PMA à travers le processus.

> [!NOTE]
> Le contenu Windows Forms dans Visual Studio (par exemple, l’Explorateur de propriétés) ne prend en charge la validation AVM que si vous disposez de Visual Studio 2019 version 16,1 ou ultérieure.

## <a name="test-your-extensions-for-pma-issues"></a>Tester vos extensions pour les problèmes de AVM

Visual Studio prend officiellement en charge les infrastructures d’interface utilisateur WPF, Windows Forms, Win32 et HTML/JS. Lorsque Visual Studio est placé en mode PMA, chaque pile d’interface utilisateur se comporte différemment. Par conséquent, quelle que soit l’infrastructure de l’interface utilisateur, il est recommandé d’effectuer un test pour vérifier que toute l’interface utilisateur est conforme au mode PMA.

Il est recommandé de valider les scénarios courants suivants :

- Modification du facteur d’échelle d’un seul environnement d’analyse pendant l’exécution de l’application.

  Ce scénario permet de vérifier que l’interface utilisateur répond au changement de PPP Windows dynamique.

- Ancrage/déconnexion d’un ordinateur portable où un moniteur connecté est défini sur le serveur principal et le moniteur attaché a un facteur d’échelle différent de celui de l’ordinateur portable pendant que l’application est en cours d’exécution.

  Ce scénario permet de vérifier que l’interface utilisateur répond à la modification de la résolution d’affichage, ainsi que la gestion des affichages ajoutés ou supprimés de manière dynamique.

- Disposer de plusieurs moniteurs avec différents facteurs d’échelle et déplacer l’application entre eux.

  Ce scénario permet de vérifier que l’interface utilisateur répond à la modification de la résolution d’affichage
    
- Communication à distance sur un ordinateur lorsque les ordinateurs locaux et distants ont des facteurs d’échelle différents pour l’analyse principale.

  Ce scénario permet de vérifier que l’interface utilisateur répond au changement de PPP Windows dynamique.

Un bon test préliminaire indiquant si votre interface utilisateur peut rencontrer des problèmes est que le code utilise les classes *Microsoft. VisualStudio. Utilities. dpi. DpiHelper*, *Microsoft. VisualStudio. PlatformUI. DpiHelper* ou *vsui :: CDpiHelper* . Ces anciennes classes DpiHelper prennent uniquement en charge la prise en charge DPI du système et ne fonctionnent pas toujours correctement lorsque le processus est AVM.

L’utilisation classique de ces DpiHelpers se présente comme suit :

```cs
Point screenTopRight = logicalBounds.TopRight.LogicalToDeviceUnits();

POINT screenIntTopRight = new POINT
{
    x = (int)screenTopRIght.X,
    y = (int)screenTopRIght.Y
}

// Declared via P/Invoke
IntPtr monitor = MonitorFromPoint(screenIntTopRight, MONITOR_DEFAULTTONEARST);
```

Dans l’exemple précédent, un rectangle représentant les limites logiques d’une fenêtre est converti en unités de périphérique afin qu’il puisse être passé à la méthode Native MonitorFromPoint qui attend les coordonnées de l’appareil pour retourner un pointeur d’analyse précis.

### <a name="classes-of-issues"></a>Classes de problèmes
Lorsque le mode PMA est activé pour Visual Studio, l’interface utilisateur peut répliquer des problèmes de plusieurs façons courantes. La plupart de ces problèmes peuvent se produire dans n’importe quelle infrastructure d’interface utilisateur prise en charge par Visual Studio. En outre, ces problèmes peuvent également se produire quand une partie de l’interface utilisateur est hébergée dans des scénarios de mise à l’échelle DPI en mode mixte (reportez-vous à la [documentation](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) de Windows pour en savoir plus). 

#### <a name="win32-window-creation"></a>Création de fenêtres Win32
Lorsque vous créez des fenêtres avec CreateWindow () ou CreateWindowEx (), un modèle courant consiste à créer la fenêtre au niveau des coordonnées (0,0) (angle supérieur/gauche de l’affichage principal), puis à la déplacer vers sa position finale. Toutefois, cette action peut entraîner le déclenchement d’un message ou d’un événement modifié par DPI, qui peut redéclencher d’autres messages ou événements de l’interface utilisateur et aboutir à un comportement ou un rendu indésirable.

#### <a name="wpf-element-placement"></a>Positionnement d’un élément WPF
Lors du déplacement d’éléments WPF à l’aide de l’ancienne version de Microsoft. VisualStudio. Utilities. dpi. DpiHelper, les coordonnées de l’angle supérieur gauche peuvent ne pas être calculées correctement chaque fois que les éléments sont sur une résolution PPP non primaire.

#### <a name="serialization-of-ui-element-sizes-or-positions"></a>Sérialisation de la taille ou de la position des éléments d’interface utilisateur
Lorsque la taille ou la position de l’interface utilisateur (si elle est enregistrée en tant qu’unités de périphérique) est restaurée dans un autre contexte PPP que celui dans lequel elle a été stockée, elle est positionnée et dimensionnée de manière incorrecte. Cela se produit parce que les unités de périphérique ont une relation DPI inhérente.

#### <a name="incorrect-scaling"></a>Mise à l’échelle incorrecte
Les éléments d’interface utilisateur créés sur le PPP principal sont mis à l’échelle correctement, mais lorsqu’ils sont déplacés vers un affichage avec une résolution différente, ils ne sont pas redimensionnés et leur contenu est trop grand ou trop petit.

#### <a name="incorrect-bounding"></a>Limite incorrecte
Comme pour le problème de mise à l’échelle, les éléments d’interface utilisateur calculent correctement leurs limites sur leur contexte PPP principal. Toutefois, lorsqu’ils sont déplacés vers une résolution non principale, ils ne calculent pas correctement les nouvelles limites. Par conséquent, la fenêtre de contenu est trop petite ou trop grande comparée à l’interface utilisateur d’hébergement, ce qui se traduit par un espace vide ou un découpage.

#### <a name="drag--drop"></a>Glisser & déposer
À chaque fois qu’il s’agit de scénarios en mode mixte (par exemple, différents éléments d’interface utilisateur qui restituent les différents modes de reconnaissance PPP), les coordonnées de glisser-déplacer peuvent être mal calculées, ce qui entraîne la fin incorrecte de la position de dépôt finale.

#### <a name="out-of-process-ui"></a>Interface utilisateur hors processus
Une interface utilisateur est créée hors processus et si le processus de création externe est dans un mode de reconnaissance PPP différent de Visual Studio, cela peut introduire l’un des problèmes de rendu précédents.

#### <a name="windows-forms-controls-images-or-layouts-rendered-incorrectly"></a>Les contrôles, les images ou les dispositions de Windows Forms restitués de manière incorrecte
Tout le contenu Windows Forms prend pas en charge le mode PMA. Par conséquent, vous pouvez voir un problème de rendu avec des dispositions incorrectes ou une mise à l’échelle. Dans ce cas, une solution possible est de restituer explicitement le contenu Windows Forms dans le DpiAwarenessContext « sensible au système » (consultez [forcer un contrôle dans un DpiAwarenessContext spécifique](#force-a-control-into-a-specific-dpiawarenesscontext)).

#### <a name="windows-forms-controls-or-windows-not-displaying"></a>Contrôles de Windows Forms ou fenêtres non affichées
L’une des principales causes de ce problème est que les développeurs essaient de redéfinir la parente d’un contrôle ou d’une fenêtre avec une DpiAwarenessContext à une fenêtre avec un DpiAwarenessContext différent.

Les images suivantes montrent les restrictions actuelles du système d’exploitation Windows **par défaut** dans les fenêtres de parentage :

![Capture d’écran du comportement de parent correct](media/PMA-parenting-behavior.PNG)

> [!Note]
> Vous pouvez modifier ce comportement en définissant le comportement d’hébergement des threads (reportez-vous à [Dpi_Hosting_Behavior énumération](/windows/desktop/api/windef/ne-windef-dpi_hosting_behavior)).

Par conséquent, si vous définissez une relation parent-enfant entre des modes non pris en charge, elle échoue et le contrôle ou la fenêtre peut ne pas être rendu comme prévu.

### <a name="diagnose-issues"></a>Diagnostiquer les problèmes

Il existe de nombreux facteurs à prendre en compte lors de l’identification des problèmes liés à PMA : 

- L’interface utilisateur ou l’API attend-t-elle des valeurs logiques ou d’appareil ?
    - L’interface utilisateur et les API WPF utilisent généralement des valeurs logiques (mais pas toujours)
    - L’interface utilisateur et les API Win32 utilisent généralement des valeurs d’appareil

- Où les valeurs proviennent-elles ?
    - Si vous recevez des valeurs à partir d’une autre interface utilisateur ou API, c’est qu’il passe des valeurs d’appareil ou logique.
    - Si vous recevez des valeurs à partir de plusieurs sources, les mêmes types de valeurs sont-ils utilisés/attendus, ou les conversions doivent être mélangées et mises en correspondance ?

- Les constantes d’interface utilisateur sont-elles en cours d’utilisation ?

- Le thread se trouve-t-il dans le contexte PPP approprié pour les valeurs qu’il reçoit ?

  Les modifications apportées à activer l’hébergement PPP mixte doivent généralement placer les chemins de code dans le contexte approprié, mais le travail effectué en dehors de la boucle de message principale ou du workflow peut s’exécuter dans un contexte PPP incorrect.

- Les valeurs sont-elles des limites de contexte croisées PPP ?

  Faire glisser & déplacement est une situation courante dans laquelle les coordonnées peuvent traverser des contextes PPP. La fenêtre tente d’effectuer la bonne chose, mais dans certains cas, l’interface utilisateur de l’hôte peut nécessiter un travail de conversion pour garantir la correspondance des limites de contexte.

### <a name="pma-nuget-package"></a>Package NuGet AVM
Les nouvelles bibliothèques DpiAwarness se trouvent sur le package NuGet [Microsoft. VisualStudio. DpiAwareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) .

### <a name="recommended-tools"></a>Outils recommandés
Les outils suivants peuvent vous aider à déboguer les problèmes liés à PMA sur certaines des piles d’interface utilisateur prises en charge par Visual Studio.

#### <a name="snoop"></a>Fouiner
Snoop est un outil de débogage XAML qui offre des fonctionnalités supplémentaires que les outils Visual Studio XAML intégrés n’ont pas. En outre, Snoop n’a pas besoin de déboguer activement Visual Studio pour pouvoir afficher et modifier son interface utilisateur WPF. Les deux principales façons d’utiliser la fonctionnalité Snoop pour diagnostiquer les problèmes d’AVM sont la validation des limites d’emplacement logique ou des limites de taille, et pour la validation de l’interface utilisateur avec la bonne résolution.
 
#### <a name="visual-studio-xaml-tools"></a>Outils XAML Visual Studio
Comme Snoop, les outils XAML de Visual Studio peuvent vous aider à diagnostiquer les problèmes de AVM. Une fois qu’une cause probable est trouvée, vous pouvez définir des points d’arrêt et utiliser la fenêtre arborescence d’éléments visuels dynamique, ainsi que les fenêtres de débogage, pour inspecter les limites de l’interface utilisateur et la valeur PPP actuelle.

## <a name="strategies-for-fixing-pma-issues"></a>Stratégies de résolution des problèmes d’AVM

### <a name="replace-dpihelper-calls"></a>Remplacer les appels DpiHelper

Dans la plupart des cas, la résolution des problèmes d’interface utilisateur en mode PMA revient au remplacement des appels dans le code managé par les anciennes classes *Microsoft. VisualStudio. Utilities. dpi. DpiHelper* et *Microsoft. VisualStudio. PlatformUI. DpiHelper* , avec des appels à la nouvelle classe d’assistance *Microsoft. VisualStudio. Utilities. DpiAwareness* . 

```cs
// Remove this kind of use:
Point deviceTopLeft = new Point(window.Left, window.Top).LogicalToDeviceUnits();

// Replace with this use:
Point deviceTopLeft = window.LogicalToDevicePoint(new Point(window.Left, window.Top));
```

Pour le code natif, elle implique le remplacement des appels à l’ancienne classe *vsui :: CDpiHelper* par des appels à la nouvelle classe *vsui :: CDpiAwareness* . 

```cpp
// Remove this kind of use:
int cx = VsUI::DpiHelper::LogicalToDeviceUnitsX(m_cxS);
int cy = VsUI::DpiHelper::LogicalToDeviceUnitsY(m_cyS);

// Replace with this use:
int cx = m_cxS;
int cy = m_cyS;
VsUI::CDpiAwareness::LogicalToDeviceUnitsX(m_hwnd, &cx);
VsUI::CDpiAwareness::LogicalToDeviceUnitsY(m_hwnd, &cy);
```

Les nouvelles classes DpiAwareness et CDpiAwareness offrent les mêmes assistances de conversion d’unités que les classes DpiHelper, mais requièrent un paramètre d’entrée supplémentaire : l’élément d’interface utilisateur à utiliser comme référence pour l’opération de conversion. Il est important de noter que les assistances de mise à l’échelle des images n’existent pas dans les nouvelles applications d’assistance DpiAwareness/CDpiAwareness, et si nécessaire, le [ImageService](../image-service-and-catalog.md) doit être utilisé à la place.

La classe managée DpiAwareness offre des assistances pour les visuels WPF, les contrôles de Windows Forms et les HWND Win32 et HMONITORs (sous la forme de IntPtrs), tandis que la classe CDpiAwareness Native offre des applications auxiliaires HWND et HMONITOR.

### <a name="windows-forms-dialogs-windows-or-controls-displayed-in-the-wrong-dpiawarenesscontext"></a>Windows Forms les boîtes de dialogue, fenêtres ou contrôles affichés dans le mauvais DpiAwarenessContext
Même après un parent réussi de Windows avec des DpiAwarenessContexts différents (en raison du comportement par défaut de Windows), les utilisateurs peuvent toujours voir des problèmes de mise à l’échelle, car Windows avec différentes échelles de DpiAwarenessContexts diffèrent différemment. Par conséquent, les utilisateurs peuvent voir des problèmes d’alignement/de texte flou ou d’image sur l’interface utilisateur.

La solution consiste à définir l’étendue DpiAwarenessContext appropriée pour toutes les fenêtres et tous les contrôles de l’application.

### <a name="top-level-mixed-mode-tlmm-dialogs"></a>Boîtes de dialogue en mode mixte (TLMM) de niveau supérieur
Lors de la création de fenêtres de niveau supérieur telles que des boîtes de dialogue modales, il est important de s’assurer que le thread est dans l’état approprié avant la création de la fenêtre (et de son descripteur). Le thread peut être mis en connaissance du système à l’aide de l’application auxiliaire CDpiScope dans Native ou de l’application auxiliaire DpiAwareness. EnterDpiScope dans géré. (TLMM doit généralement être utilisé dans les boîtes de dialogue/fenêtres non-WPF.)

### <a name="child-level-mixed-mode-clmm"></a>Mode mixte au niveau de l’enfant (CLMM)
Par défaut, les fenêtres enfants reçoivent le contexte de détection PPP du thread actuel si elles sont créées sans parent, ou le contexte de détection PPP du parent lorsqu’elles sont créées avec un parent. Pour créer un enfant avec un autre contexte de détection PPP que son parent, le thread peut être placé dans le contexte de détection PPP souhaité. L’enfant peut ensuite être créé sans parent et manuellement apparenté à la fenêtre parente.

#### <a name="clmm-issues"></a>Problèmes CLMM
La majeure partie du travail de calcul de l’interface utilisateur qui se produit dans le cadre de la boucle de messagerie principale ou de la chaîne d’événements doit déjà s’exécuter dans le contexte de détection DPI approprié. Toutefois, si les calculs de coordonnées ou de redimensionnement sont effectués en dehors de ces flux de travail principaux (par exemple, pendant une tâche de temps d’inactivité ou en dehors du thread d’interface utilisateur), le contexte de détection PPP actuel peut être incorrect, entraînant des problèmes de mauvais positionnement ou de dimensionnement de l’interface utilisateur. Le fait de placer le thread dans un état correct pour le travail de l’interface utilisateur résout généralement le problème.
 
#### <a name="opt-out-of-clmm"></a>Refuser CLMM
Si une fenêtre outil non WPF est migrée pour prendre entièrement en charge AVM, elle doit refuser l’CLMM. Pour ce faire, une nouvelle interface doit être implémentée : IVsDpiAware.

```cs
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
public interface IVsDpiAware
{
    [ComAliasName("Microsoft.VisualStudio.Shell.Interop.VSDPIMode")]
    uint Mode {get;}
}
```

```cpp
IVsDpiAware : public IUnknown
{
    public:
        HRRESULT STDMETHODCALLTYPE get_Mode(__RCP__out VSDPIMODE *dwMode);
};
```

Pour les langages managés, le meilleur endroit pour implémenter cette interface se trouve dans la même classe qui dérive de *Microsoft. VisualStudio. Shell. ToolWindowPane*. Pour C++, le meilleur emplacement pour implémenter cette interface se trouve dans la même classe qui implémente *IVsWindowPane* à partir de vsshell. h.

La valeur retournée par la propriété mode sur l’interface est une __VSDPIMODE (et castée en uint en managé) :

```cs
enum __VSDPIMODE
{
    VSDM_Unaware    = 0x01,
    VSDM_System     = 0x02,
    VSDM_PerMonitor = 0x03,
}
```

- Si vous ne savez pas que la fenêtre outil doit gérer 96 ppp, Windows gérera sa mise à l’échelle pour tous les autres DPI. Entraînant un léger flou du contenu.
- System signifie que la fenêtre outil doit gérer la résolution PPP pour la résolution d’affichage principale. Tout affichage avec une résolution de PPP correspondante est plus clair, mais si la résolution est différente ou change au cours de la session, Windows gère la mise à l’échelle et est légèrement flou.
- Permonitor signifie que la fenêtre outil doit gérer toutes les DPI sur tous les affichages et chaque fois que la valeur PPP change.

> [!NOTE]
> Visual Studio ne prend en charge que la reconnaissance de PerMonitorV2, donc la valeur de l’enum de persurveillance se traduit par la valeur Windows de DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE_V2.

#### <a name="force-a-control-into-a-specific-dpiawarenesscontext"></a>Forcer un contrôle dans un DpiAwarenessContext spécifique

L’interface utilisateur héritée qui n’est pas mise à jour pour prendre en charge le mode PMA peut encore nécessiter des ajustements mineurs pour fonctionner pendant que Visual Studio s’exécute en mode AVM. L’un de ces correctifs consiste à s’assurer que l’interface utilisateur est créée dans le bon DpiAwarenessContext. Pour forcer votre interface utilisateur dans un DpiAwarenessContext particulier, vous pouvez entrer une étendue ppp avec le code suivant :

```cs
using (DpiAwareness.EnterDpiScope(DpiAwarenessContext.SystemAware))
{
    Form form = new MyForm();
    form.ShowDialog();
}
```

```cpp
void MyClass::ShowDialog()
{
    VsUI::CDpiScope dpiScope(DPI_AWARENESS_CONTEXT_SYSTEM_AWARE);
    HWND hwnd = ::CreateWindow(...);
}
```

> [!NOTE]
> Forcer le DpiAwarenessContext fonctionne uniquement sur l’interface utilisateur non-WPF et les boîtes de dialogue WPF de niveau supérieur. Lors de la création de l’interface utilisateur WPF qui doit être hébergée dans les fenêtres outil ou les concepteurs, dès que le contenu est inséré dans l’arborescence de l’interface utilisateur WPF, il est converti en processus DpiAwarenessContext actuel.

## <a name="known-issues"></a>Problèmes connus

### <a name="windows-forms"></a>Windows Forms

Pour optimiser les nouveaux scénarios en mode mixte, Windows Forms modifié la manière dont il crée les contrôles et Windows chaque fois que leur parent n’a pas été défini explicitement. Précédemment, les contrôles sans parent explicite utilisaient une « fenêtre de parking » interne en tant que parent temporaire du contrôle ou de la fenêtre en cours de création. 

Avant .NET 4,8, il existait une seule « fenêtre de parking » qui obtient son DpiAwarenessContext à partir du contexte de détection de la résolution des PPP du thread en cours au moment de la création de la fenêtre. Tout contrôle non apparenté hérite du même DpiAwarenessContext que la fenêtre de parking lorsque le handle du contrôle est créé et est reapparenté au parent final/attendu par le développeur de l’application. Cela entraînerait des échecs basés sur la temporisation si la « fenêtre de parking » avait un DpiAwarenessContext plus élevé que la fenêtre parente finale.

À compter de .NET 4,8, il existe désormais une « fenêtre de parking » pour chaque DpiAwarenessContext rencontrée. L’autre différence majeure réside dans le fait que le DpiAwarenessContext utilisé pour le contrôle est mis en cache lorsque le contrôle est créé, et non lors de la création du handle. Cela signifie que le comportement final global est le même, mais peut transformer ce qui était un problème basé sur le minutage en un problème cohérent. Il donne également au développeur d’applications un comportement plus déterministe pour l’écriture de son code d’interface utilisateur et son étendue correcte.
