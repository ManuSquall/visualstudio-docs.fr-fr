---
title: Prise en charge par moniteur afin que les extendeurs de Visual Studio
titleSuffix: ''
description: Découvrez la nouvelle prise en charge extendeur pour par-monitor-sensibilisation disponible dans Visual Studio 2019.
ms.date: 04/10/2019
helpviewer_keywords:
- Visual Studio, PMA, per-monitor-awareness, extenders, Windows Forms
- Per-Monitor Awareness support for extenders
ms.assetid: ''
author: rub8n
ms.author: rurios
manager: anthc
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.technology: vs-ide-general
ms.topic: reference
ms.workload:
- multiple
ms.openlocfilehash: 44938c5753491521702867398a514f770cf831fb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62793635"
---
# <a name="per-monitor-awareness-support-for-visual-studio-extenders"></a>Prise en charge par moniteur afin que les extendeurs de Visual Studio
Versions antérieures à Visual Studio 2019 eu leur contexte de sensibilisation à la résolution définie sur le système prenant en charge, plutôt que des PPP prenant en charge (AVM) par le moniteur. En cours d’exécution dans la sensibilité au système a entraîné un visuel détérioré expérience (par exemple, floues polices ou icônes) chaque fois que Visual Studio devait restituer sur plusieurs écrans à des facteurs d’échelle différente ou à distance sur des machines avec des configurations d’affichage différent, par exemple (différents Windows mise à l’échelle).

Le contexte de sensibilisation à la résolution de Visual Studio 2019 est défini comme AVM, lorsque l’environnement prend en charge, ce qui permet de Visual Studio pour effectuer le rendu en fonction de la configuration de l’affichage dans lequel il est hébergé plutôt que dans une configuration définie système unique. Traduire au final une interface utilisateur toujours clair pour les surfaces d’exposition qui prennent en charge le mode AVM.

Reportez-vous à la [développement d’applications haute résolution bureau sur Windows](https://docs.microsoft.com/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) documentation pour plus d’informations sur les conditions et le scénario global traitées dans ce document.

## <a name="quickstart"></a>Démarrage rapide
- Assurez-vous de Visual Studio s’exécute en mode d’AVM (consultez **AVM activation**)

- Valider votre extension de fonctionne correctement sur un ensemble de scénarios courants (consultez **tester vos extensions pour les problèmes d’AVM**)

- Si vous détectez des problèmes, vous pouvez utiliser les stratégies/recommandations présentées dans ce document pour diagnostiquer et résoudre ces problèmes. Vous devrez également ajouter la nouvelle [Microsoft.VisualStudio.DpiAwareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) package NuGet à votre projet pour accéder aux API requis.

## <a name="enabling-pma"></a>L’activation AVM
Pour activer AVM dans Visual Studio, les conditions suivantes doivent être remplies :
1) Windows 10 avril 2018 mise à jour (v1803, RS4) ou version ultérieure
2) .NET framework 4.8 RTM ou version ultérieure
3) Visual Studio 2019 avec le [« Optimiser le rendu pour les écrans de densité de pixels différentes »](https://docs.microsoft.com/visualstudio/ide/reference/general-environment-options-dialog-box?view=vs-2019) option est activée

Une fois que ces exigences sont satisfaites, Visual Studio active automatiquement le mode AVM entre les différents processus.

> [!NOTE]
> Contenu de Windows Forms dans Visual Studio (par exemple Explorateur de propriétés) prendra en charge AVM uniquement lorsque vous avez Visual Studio 2019 Update #1.

## <a name="testing-your-extensions-for-pma-issues"></a>Test de vos extensions pour les problèmes d’AVM

Visual Studio prend officiellement en charge les infrastructures d’interface utilisateur HTML/JS, Win32, WPF et Windows Forms. Lorsque Visual Studio est placé en mode d’AVM, chaque pile de l’interface utilisateur se comporte différemment. Par conséquent, quel que soit l’infrastructure de l’interface utilisateur, il est recommandé qu’un test est effectué pour vérifier que toute l’interface utilisateur est compatible avec le mode AVM.

Il est recommandé de que valider les scénarios courants suivants :

1. Modification du facteur de mise à l’échelle d’un environnement d’analyse unique alors que l’application est en cours d’exécution *
    - Ce scénario permet de tester que l’interface utilisateur ne répond à la modification dynamique de la résolution de Windows

2. Connexion/déconnexion un ordinateur portable où un moniteur connecté est défini sur le serveur principal et le moniteur attaché a un facteur d’échelle différente que l’ordinateur portable pendant l’exécution de l’application.
    - Ce scénario permet de tester que l’interface utilisateur ne répond à l’affichage, modification des PPP, ainsi que la gestion des affiche dynamiquement soient ajoutés ou supprimés

3. Avoir plusieurs écrans avec les facteurs d’échelle différente et déplacement de l’application entre eux.
    - Ce scénario permet de tester que l’interface utilisateur ne répond à la modification de PPP d’affichage
    
4. Communication à distance sur un ordinateur lorsque les ordinateurs locaux et distants disposent des facteurs d’échelle différents pour le moniteur principal.
    - Ce scénario permet de tester que l’interface utilisateur ne répond à la modification dynamique de la résolution de Windows

Un bon test préliminaire pour que votre interface utilisateur peut-être avoir des problèmes est que le code utilise le *Microsoft.VisualStudio.Utilities.Dpi.DpiHelper*, *Microsoft.VisualStudio.PlatformUI.DpiHelper*, ou *VsUI::CDpiHelper* classes. Ces classes DpiHelper ancien prennent uniquement en charge la prise en charge DPI de système et ne fonctionnera pas toujours correctement lorsque le processus est AVM.

Une utilisation typique de ces DpiHelpers ressemblera à :

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

Dans l’exemple précédent, un rectangle qui représente les limites logiques d’une fenêtre est converti en unités de périphérique afin qu’elle peut être passée à la méthode native MonitorFromPoint qui attend des coordonnées de périphérique afin de retourner un pointeur d’analyse précis.

### <a name="classes-of-issues"></a>Classes de problèmes
Lorsque le mode AVM est activé pour Visual Studio, l’interface utilisateur peut répliquer des problèmes de plusieurs façons courantes. Plus, si ce n’est pas tout, de ces problèmes peuvent se produire dans des infrastructures d’interface utilisateur prises en charge de Visual Studio. En outre, ces problèmes peuvent également se produire lorsqu’un élément d’interface utilisateur est hébergé dans l’échelle des scénarios de résolution d’en mode mixte (reportez-vous à la Windows [documentation](https://docs.microsoft.com/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) pour en savoir plus). 

#### <a name="win32-window-creation"></a>Création de la fenêtre Win32
Lors de la création de fenêtres avec CreateWindow() ou CreateWindowEx(), un modèle courant consiste à créer la fenêtre aux coordonnées (0,0) (haut/gauche de l’écran principal), puis déplacez-le vers sa position finale. Toutefois, cela peut entraîner la fenêtre déclencher un PPP modifiée message ou un événement, ce qui peut redéclencher autres messages d’interface utilisateur ou des événements et finit par entraîner des comportements indésirables ou du rendu.

#### <a name="wpf-element-placement"></a>Emplacement des éléments WPF
Lorsque vous déplacez les éléments WPF à l’aide de l’ancien Microsoft.VisualStudio.Utilities.Dpi.DpiHelper, les coordonnées en haut à gauche ne peuvent pas être calculées correctement chaque fois que les éléments se trouvent sur un paramètre PPP non principal.

#### <a name="serialization-of-ui-element-sizes-or-positions"></a>Sérialisation de tailles d’éléments de l’interface utilisateur ou les positions
Lors de la taille de l’interface utilisateur ou la position (s’il est enregistré en tant qu’unités de périphérique) est restaurée sur ce qui a été stocké dans un contexte PPP différent, il est positionné et dimensionné de façon incorrecte. Cela se produit, car les unités de périphérique ont une relation de PPP inhérente.

#### <a name="incorrect-scaling"></a>Mise à l’échelle incorrect
Éléments d’interface utilisateur créés sur la résolution primaire mettra à l’échelle correctement, mais quand déplacées sur un écran avec une résolution différente, ils ne pas mettre à l’échelle et par conséquent, leur contenu finit par être trop grand ou trop petit.

#### <a name="incorrect-bounding"></a>Délimitation incorrect
De même, le problème de mise à l’échelle, éléments d’interface utilisateur calculera leurs limites correctement sur leur contexte principal de PPP, toutefois, lorsqu’un paramètre PPP non principal, ils ne sont pas calculer correctement les nouvelles limites. Par conséquent, la fenêtre de contenu finit par est trop petite ou trop grande par rapport à l’interface utilisateur hébergement, ce qui se traduit par un espace vide ou de découpage.

#### <a name="drag--drop"></a>Glisser -déplacer
Chaque fois que dans les scénarios de PPP en mode mixte (par exemple, différents éléments d’interface utilisateur dans différents modes de sensibilisation à la résolution de rendu), glisser -déplacer coordonnées pourraient être douteuse, ce qui entraîne le dépôt final position finissent incorrect.

#### <a name="out-of-process-ui"></a>Interface utilisateur out-of-process
Une interface utilisateur est créée out-of-process et si la création du processus externe est dans un autre mode de sensibilisation à la résolution que Visual Studio, cela peut introduire un des problèmes de rendu précédent.

#### <a name="windows-forms-controls-images-or-layouts-rendered-incorrectly"></a>Contrôles Windows Forms, des images ou des dispositions de rendu de manière incorrecte
Pas tout le contenu de Windows Forms prend en charge le mode AVM. Par conséquent, vous pouvez voir le rendu de problème avec les dispositions incorrectes ou la mise à l’échelle. Une solution possible est dans ce cas consiste à afficher explicitement le contenu de Windows Forms dans DpiAwarenessContext « Prenant en charge de système » (reportez-vous à [forçant un contrôle dans un DpiAwarenessContext spécifique](#forcing-a-control-into-a-specific-dpiawarenesscontext)).

#### <a name="windows-forms-controls-or-windows-not-displaying"></a>Contrôles Windows Forms ou windows s’affichent ne pas
Une des principales causes de ce problème est de développeurs qui tentent de redéfinir la parenté un contrôle ou une fenêtre avec un DpiAwarenessContext à une fenêtre avec un DpiAwarenessContext différent.

Les images suivantes montrent actuel **par défaut** restrictions du système d’exploitation Windows dans apparenter windows :

![Une capture d’écran du comportement parentage correct](../../extensibility/ux-guidelines/media/PMA-parenting-behavior.PNG)

> [!Note]
> Vous pouvez modifier ce comportement en définissant le comportement d’hébergement de Thread (reportez-vous à [DpiHostinBehaviour](https://docs.microsoft.com/windows/desktop/api/windef/ne-windef-dpi_hosting_behavior)).

Par conséquent, si vous définissez la relation parent-enfant entre les modes non pris en charge, il échoue, et le contrôle ou la fenêtre peut ne pas être restituée comme prévu.

### <a name="diagnosing-issues"></a>Diagnostic des problèmes
Il existe de nombreux facteurs à prendre en compte lors de l’identification des problèmes liés à AVM : 

1. Ne l’interface utilisateur ou l’API attendent logique ou les valeurs de l’appareil.
    - WPF UI et API généralement utilisent des valeurs logiques (mais pas toujours)
    - API et l’interface utilisateur Win32 généralement utiliser des valeurs de l’appareil

2. D'où viennent les valeurs ?
    - Si vous recevez des valeurs à partir d’autres l’interface utilisateur ou d’une API, est-il passage appareil ou des valeurs logiques.
    - Si vous recevez des valeurs provenant de plusieurs sources, tous utiliser/attendent les mêmes types de valeurs ou conversions doivent-ils être combinés et associés ?

3. Sont des constantes de l’interface utilisateur en cours d’utilisation et la forme se trouvent-ils ?

4. Est le thread dans le contexte de résolution approprié pour les valeurs qu’il reçoit ?
    - Les modifications pour permettre l’hébergement de PPP mixte doivent généralement placer des chemins de code dans le contexte approprié, toutefois, travail effectué en dehors du flux de messages principale boucle ou un événement peut s’exécuter dans le contexte de PPP incorrect.

5. Les valeurs traversent les limites du contexte PPP ?
    - Glisser -déplacer est une situation courante où les coordonnées peuvent traverser les contextes de PPP. Fenêtre essaie d’être adoptent l’attitude, mais dans certains cas, l’interface utilisateur hôte peut-être d’effectuer des tâches de conversion pour garantir la correspondance des limites de contexte.

### <a name="pma-nuget-package"></a>Package NuGet d’AVM
Vous trouverez les nouvelles bibliothèques DpiAwarness sur le [Microsoft.VisualStudio.DpiAwareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) package NuGet.

### <a name="recommended-tools"></a>Outils recommandés
Les outils suivants peuvent aider à déboguer les problèmes liés à AVM sur certaines des différentes piles de l’interface utilisateur pris en charge par Visual Studio.

#### <a name="snoop"></a>Aller fouiner
Snoop est un outil de débogage de XAML qui a quelques fonctionnalités supplémentaires qui n’a pas les outils de Visual Studio XAML intégrés. En outre, Snoop n’a pas besoin déboguer activement Visual Studio pour pouvoir afficher et modifier son UI WPF. Les deux méthodes principales Snoop peut être utile pour diagnostiquer les problèmes d’AVM est pour la validation des coordonnées de positionnement logique ou les limites de taille, et pour la validation de l’interface utilisateur a la valeur PPP de droite.
 
#### <a name="visual-studio-xaml-tools"></a>Outils de Visual Studio XAML
Comme Snoop, les outils XAML dans Visual Studio peuvent aider à diagnostiquer les problèmes d’AVM. Une fois une cause probable est trouvée, vous pouvez définir des points d’arrêt et utiliser la fenêtre de l’arborescence d’éléments visuels en direct, ainsi que les fenêtres de débogage, d’inspecter les limites de l’interface utilisateur et de résolution en cours.

## <a name="strategies-for-fixing-pma-issues"></a>Stratégies pour la résolution des problèmes d’AVM
### <a name="replacing-dpihelper-calls"></a>En remplaçant les appels DpiHelper
Dans la plupart des cas, résolution des problèmes de l’interface utilisateur en mode d’AVM se résume à remplaçant les appels dans du code managé à l’ancien *Microsoft.VisualStudio.Utilities.Dpi.DpiHelper* et *Microsoft.VisualStudio.PlatformUI.DpiHelper*classes, avec les appels à la nouvelle *Microsoft.VisualStudio.Utilities.DpiAwareness* classe d’assistance. 

```cs
// Remove this kind of use:
Point deviceTopLeft = new Point(window.Left, window.Top).LogicalToDeviceUnits();

// Replace with this use:
Point deviceTopLeft = window.LogicalToDevicePoint(new Point(window.Left, window.Top));
```

Pour le code natif, il entraînera en remplaçant les appels à l’ancien *VsUI::CDpiHelper* classe avec les appels à la nouvelle *VsUI::CDpiAwareness* classe. 

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

Les nouvelles classes DpiAwareness et CDpiAwareness offrent la même unité helpers de conversion comme les classes DpiHelper mais ne nécessitent un paramètre d’entrée supplémentaire : l’élément d’interface utilisateur à utiliser comme référence pour l’opération de conversion. Il est important de noter que les programmes d’assistance image mise à l’échelle n’existent pas dans les nouveaux programmes d’assistance DpiAwareness/CDpiAwareness et si nécessaire, le [ImageService](https://docs.microsoft.com/visualstudio/extensibility/image-service-and-catalog?view=vs-2019) doit être utilisé à la place.

La classe DpiAwareness managée offre programmes d’assistance pour les éléments visuels WPF, les contrôles Windows Forms et les HWND Win32 et HMONITORs (à la fois sous la forme d’IntPtrs), tout les CDpiAwareness classe offres HWND et HMONITOR des assistances natives.

### <a name="windows-forms-dialogs-windows-or-controls-displayed-in-the-wrong-dpiawarenesscontext"></a>Boîtes de dialogue Windows Forms, windows ou contrôles affichés dans le mauvais DpiAwarenessContext
Même après une réussite parentage de windows avec DpiAwarenessContexts différents (en raison de comportement par défaut de Windows), les utilisateurs peuvent toujours voir mise à l’échelle problèmes sous forme de fenêtres avec différents DpiAwarenessContexts mise à l’échelle différemment. Par conséquent, les utilisateurs risquent de voir le texte flou/alignement ou problèmes sur l’interface utilisateur de l’image.

La solution consiste à définir l’étendue de DpiAwarenessContext correcte pour toutes les fenêtres et les contrôles dans l’application.

### <a name="top-level-mixed-mode-tlmm-dialogs"></a>Boîtes de dialogue de niveau supérieur en mode mixte (TLMM)
Lorsque vous créez des fenêtres de niveau supérieur tels que des boîtes de dialogue modales, il est important de s’assurer que le thread est dans l’état approprié avant la fenêtre (et son handle) en cours de création. Le thread peut être placé dans la sensibilité au système par à l’aide du programme d’assistance CDpiScope en mode natif ou géré de l’application d’assistance DpiAwareness.EnterDpiScope dans. (TLMM doit généralement être utilisée sur les boîtes de dialogue non-WPF/windows.)

### <a name="child-level-mixed-mode-clmm"></a>En mode mixte au niveau enfant (CLMM)
Par défaut, les fenêtres enfants reçoivent le contexte actuel du thread PPP sensibilisation si créé sans un parent, ou le contexte de la reconnaissance de PPP du parent lorsque créé avec un parent. Pour créer un enfant avec un contexte différent de sensibilisation à la résolution de son parent, le thread peut être placé dans le contexte de sensibilisation à la résolution souhaité. Puis l’enfant peut être créé sans un parent et reparentage manuellement vers la fenêtre parente.

#### <a name="clmm-issues"></a>Problèmes CLMM
L’essentiel du travail de calcul de l’interface utilisateur qui se produit dans le cadre de la chaîne de boucle ou un événement messagerie principale doit déjà être en cours d’exécution dans le bon contexte de la reconnaissance de PPP. Toutefois, si les coordonnées ou les calculs de dimensionnement sont effectuées en dehors de ces flux de travail principal (comme lors d’une tâche de durée d’inactivité, ou désactiver le thread d’interface utilisateur, le contexte de sensibilisation à la résolution actuels peut être incorrect, ce qui conduit à dues de l’interface utilisateur ou mal les problèmes de dimensionnement. Mettre le thread dans l’état correct pour l’interface utilisateur travail résout généralement le problème.
 
#### <a name="opting-out-of-clmm"></a>Désactivation de la CLMM
Si une fenêtre d’outil non-WPF pour prendre en charge AVM est migrée, il devrez refuser CLMM. Pour ce faire, une nouvelle interface doit être implémentée : IVsDpiAware.

C# :

```cs
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
public interface IVsDpiAeware
{
    [ComAliasName("Microsoft.VisualStudio.Shell.Interop.VSDPIMode")]
    uint Mode {get;}
}
```
 
C++ :

```cpp
IVsDpiAware : public IUnknown
{
    public:
        HRRESULT STDMETHODCALLTYPE get_Mode(__RCP__out VSDPIMODE *dwMode);
};
```

Pour les langages managés, le meilleur endroit pour implémenter cette interface est dans la même classe qui dérive de *Microsoft.VisualStudio.Shell.ToolWindowPane*. Pour C++, le meilleur endroit pour implémenter cette interface est dans la même classe qui implémente *IVsWindowPane* à partir de vsshell.h.

La valeur retournée par la propriété Mode sur l’interface est un __VSDPIMODE (et cast en uint dans gérés) :

```cs
enum __VSDPIMODE
{
    VSDM_Unaware    = 0x01,
    VSDM_System     = 0x02,
    VSDM_PerMonitor = 0x03,
}
```

- Moyens ignore que la fenêtre outil doit gérer 96 PPP, Windows gère l’échelle pour tous les autres résolutions PPP. Résultant sur le contenu qui est légèrement flou.
- Système de que la fenêtre outil doit gérer la résolution pour le serveur principal affiche les PPP. N’importe quel affichage avec une résolution correspondante est nets, mais si la valeur PPP est différente ou change pendant la session, Windows gère la mise à l’échelle et il sera légèrement flou.
- PerMonitor signifie que la fenêtre outil doit gérer toutes les résolutions PPP sur tous les affichages et chaque fois que la valeur PPP change.

> [!NOTE]
> Visual Studio prend uniquement en charge la connaissance de PerMonitorV2, donc la valeur d’énumération PerMonitor se traduit par la valeur de Windows de DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE_V2.

#### <a name="forcing-a-control-into-a-specific-dpiawarenesscontext"></a>Forcer un contrôle dans un DpiAwarenessContext spécifique
L’interface utilisateur hérité qui n’est pas en cours mis à jour pour prendre en charge le mode AVM, peut-être encore des modifications mineures à travailler pendant que Visual Studio s’exécute en mode d’AVM. Un correctif de ce type consiste à s’assurer de que l’interface utilisateur est créé dans le DpiAwarenessContext droite. Pour forcer votre interface utilisateur dans un DpiAwarenessContext particulier, vous pouvez entrer une portée de PPP avec le code suivant :

C# :

```cs
using (DpiAwareness.EnterDpiScope(DpiAwarenessContext.SystemAware))
{
    Form form = new MyForm();
    form.ShowDialog();
}
```

C++ :

```cpp
void MyClass::ShowDialog()
{
    VsUI::CDpiScope dpiScope(DPI_AWARENESS_CONTEXT_SYSTEM_AWARE);
    HWND hwnd = ::CreateWindow(...);
}
```

> [!NOTE]
> Forcer le DpiAwarenessContext fonctionne uniquement sur WPF l’interface utilisateur et les boîtes de dialogue WPF de niveau supérieur. Lors de la création de WPF UI qui est à être hébergés dans des fenêtres Outil ou les concepteurs, dès que le contenu est inséré dans l’arborescence UI de WPF, elles sont converties en DpiAwarenessContext le processus en cours.

## <a name="known-issues"></a>Problèmes connus
### <a name="windows-forms"></a>Windows Forms

Pour optimiser les nouveaux scénarios en mode mixte, Windows Forms modifié la création de contrôles et windows chaque fois que leur parent n’a pas été définie explicitement. Précédemment, les contrôles sans un parent explicite utilisés une interne « stationnement fenêtre » comme parent temporaire pour le contrôle ou la fenêtre en cours de création. 

Avant .NET 4.8, il existait un seul « stationnement » qui obtient ses DpiAwarenessContext à partir du contexte de la reconnaissance de PPP thread actuel lors de la création de la fenêtre. N’importe quel contrôle non apparenté hérite de la même DpiAwarenessContext en tant que la fenêtre de stationnement lorsque le handle du contrôle est créé et qu’il serait être à nouveau apparenté au parent final/attendu par le développeur d’applications. Cela entraînerait des défaillances basées sur le minutage si la « fenêtre de stationnement » avait un DpiAwarenessContext plus élevée que la fenêtre parent final.

À compter de .NET 4.8, il existe désormais une « fenêtre de stationnement » pour chaque DpiAwarenessContext est rencontrée. La principale différence est que le DpiAwarenessContext utilisé pour le contrôle est mis en cache lorsque le contrôle est créé, pas quand le handle est créé. Cela signifie que le comportement général de fin est identique, mais peut activer ce qui était un problème en fonction de minutage dans un problème de cohérence. Il donne également le développeur d’applications un comportement plus déterministe pour écrire leur code d’interface utilisateur et en étendant sa portée correctement.
