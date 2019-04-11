---
title: Prise en charge par moniteur afin que les extendeurs de Visual Studio
titleSuffix: ''
description: Découvrez la nouvelle prise en charge extendeur pour par-monitor-sensibilisation disponible dans Visual Studio 2019.
ms.date: 04/09/2019
helpviewer_keywords:
- Visual Studio, PMA, per-monitor-awareness, extenders, Windows Forms
- Per-Monitor Awareness support for extenders
ms.assetid: ''
author: rub8n
ms.author: rurios
manager: anthc
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: reference
ms.workload:
- multiple
ms.openlocfilehash: 42de73a29e053066c0fbeca72ca3511b58b2fa7e
ms.sourcegitcommit: 0a2fdc23faee77187e10a1c19665ba5a1ac68e72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/10/2019
ms.locfileid: "59477682"
---
# <a name="per-monitor-awareness-support-for-visual-studio-extenders"></a>Prise en charge par moniteur afin que les extendeurs de Visual Studio

Versions antérieures à Visual Studio 2019 était leur contexte de sensibilisation à la résolution définie à système prenant en charge, plutôt qu’à un prenant en charge par moniteur des PPP (AVM). En cours d’exécution dans le système de reconnaissance a généré dans une expérience visuelle détériorée (par exemple, floues polices ou icônes) chaque fois que Visual Studio devaient effectuer le rendu sur plusieurs écrans à des facteurs d’échelle différente ou accédez à distance les ordinateurs avec des configurations d’affichage différent (par exemple, différentes Windows mise à l’échelle).

Le contexte de sensibilisation à la résolution de Visual Studio 2019 est ensemble comme prenant en charge, ce qui permet à Visual Studio pour effectuer le rendu en fonction de la configuration de l’affichage dans lequel il est hébergé par le moniteur plutôt que dans une configuration définie par le système générique. Traduire au final une interface utilisateur clair pour les surfaces d’exposition qui implémentent la prise en charge AVM.

Reportez-vous à la [développement d’applications haute résolution bureau sur Windows](https://docs.microsoft.com/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) documentation pour plus d’informations sur les conditions et le scénario global traitées dans ce document.

## <a name="quickstart"></a>Démarrage rapide
- Assurez-vous de Visual Studio s’exécute en mode d’AVM (consultez **AVM activation**)

- Valider votre extension de fonctionne correctement sur un ensemble de scénarios courants (consultez **tester vos extensions pour les problèmes d’AVM**)

- Si vous détectez des problèmes, vous aurez besoin pour ajouter le nouveau package NuGet AVM, diagnostiquer et résoudre les problèmes à l’aide des stratégies et les recommandations présentées dans ce document

## <a name="enabling-pma"></a>L’activation AVM
Pour activer AVM dans Visual Studio, les conditions suivantes doivent être remplies :
1)  Windows 10 avril 2018 mise à jour (v1803, RS4) ou version ultérieure
2)  .NET framework 4.8 RTM ou version ultérieure (actuellement est fourni en tant qu’aperçu autonome ou une offre groupée avec récentes Windows builds Insider)
3)  Visual Studio 2019 avec le [« Optimiser le rendu pour les écrans de densité de pixels différentes »](https://docs.microsoft.com/visualstudio/ide/reference/general-environment-options-dialog-box?view=vs-2019) option est activée

Une fois que ces exigences sont satisfaites, Visual Studio active automatiquement AVM entre les différents processus.

## <a name="testing-your-extensions-for-pma-issues"></a>Test de vos extensions pour les problèmes d’AVM

Visual Studio prend officiellement en charge les infrastructures d’interface utilisateur HTML/JS, Win32, WPF et Windows Forms. Lorsque Visual Studio est placé en mode d’AVM, les différentes couches d’interface utilisateur se comportent différemment. Par conséquent, quel que soit l’infrastructure de l’interface utilisateur, il est recommandé qu’un test est effectué pour vérifier que toute l’interface utilisateur est conforme à AVM.

Quelle que soit l’infrastructure de l’interface utilisateur prend en charge votre extension, il est recommandé de valider les scénarios courants suivants :

1. Modification du facteur de mise à l’échelle d’un environnement d’analyse unique alors que l’application est en cours d’exécution *
    - Ce scénario permet de tester que l’interface utilisateur ne répond à la modification dynamique de la résolution de Windows

2. Connexion/déconnexion un ordinateur portable où une analyse attachée est définie pour le site principal et le moniteur attaché a un facteur d’échelle différente que le réplica principal pendant l’exécution de l’application.
    - Ce scénario permet de tester que l’interface utilisateur ne répond à l’affichage, modification des PPP, ainsi que la gestion des affiche dynamiquement soient ajoutés ou supprimés

3. Avoir plusieurs écrans avec les facteurs d’échelle différente et déplacement de l’application entre eux.
    - Ce scénario permet de tester que l’interface utilisateur ne répond à la modification de PPP d’affichage
    
4. Communication à distance sur un ordinateur lorsque les ordinateurs locaux et distants disposent des facteurs d’échelle différents pour le moniteur principal.
    - Ce scénario permet de tester que l’interface utilisateur ne répond à la modification dynamique de la résolution de Windows

Un bon test préliminaire pour que l’interface utilisateur peut-être avoir des problèmes est ou non le code utilise soit le *Microsoft.VisualStudio.Utilities.Dpi.DpiHelper* ou *Microsoft.VisualStudio.PlatformUI.DpiHelper* classes. Ces classes DpiHelper ancien prennent uniquement en charge la prise en charge DPI de système et ne fonctionnera pas toujours correctement lorsque le processus est AVM.

Une utilisation typique de ces DpiHelpers ressemblera à :

```cs
Point screenTopRight = logicalBounds.TopRight.LogicalToDeviceUnits();

POINT screenIntTopRight = new POINT
{
    x = (int)screenTopRIght.X,
    y = (int)screenTopRIght.Y
}

IntPtr monitor = NativeMethods.MonitorFromPoint(screenIntTopRight, NativeMethods.Monitor_DEFAULTTONEARST);
```

Dans l’exemple précédent, un rectangle qui représente les limites logiques d’une fenêtre est converti en unités de périphérique afin qu’elle peut être passée à la méthode native MonitorFromPoint qui attend des coordonnées de périphérique afin de retourner un pointeur d’analyse précis.

### <a name="classes-of-issues"></a>Classes de problèmes

Lorsqu’AVM est activée pour Visual Studio, l’interface utilisateur peut répliquer des problèmes de plusieurs façons courantes. Plus, si ce n’est pas tout, de ces problèmes peuvent se produire dans des infrastructures d’interface utilisateur prises en charge de Visual Studio. En outre, ces problèmes peuvent se produire même lorsqu’un élément d’interface utilisateur est hébergé dans l’échelle des scénarios de résolution d’en mode mixte (reportez-vous à la Windows [documentation](https://docs.microsoft.com/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) pour en savoir plus). 

#### <a name="win32-window-creation"></a>Création de la fenêtre Win32
Lors de la création de fenêtres avec CreateWindow() ou CreateWindowEx(), un modèle courant est pour créer la fenêtre aux coordonnées 0,0 (haut/gauche de l’écran principal), puis déplacez-le vers sa position finale. Toutefois, cela peut entraîner la fenêtre déclencher un PPP modifiée message ou un événement, ce qui peut redéclencher autres messages d’interface utilisateur ou des événements et finit par entraîner des comportements indésirables ou du rendu.

#### <a name="wpf-element-placement"></a>Emplacement des éléments WPF
Lorsque vous déplacez les éléments WPF à l’aide de l’ancien Microsoft.VisualStudio.Utilities.Dpi.DpiHelper, les coordonnées en haut à gauche ne peuvent pas être calculées correctement chaque fois que les éléments se trouvent dans le cas de PPP non principal.

#### <a name="serialization-of-ui-element-sizes-or-positions"></a>Sérialisation de tailles d’éléments de l’interface utilisateur ou les positions
Chaque fois que la taille de l’interface utilisateur ou la position est restaurée sur ce qui a été stocké dans un contexte PPP différent, il est positionné et dimensionné de façon incorrecte. Cela se produit, car les limites logiques d’une fenêtre sont convertis en unités de périphérique afin qu’elle peut être passée à la méthode Win32 MonitorFromPoint qui attend des coordonnées de périphérique afin de retourner un pointeur d’analyse précis.

#### <a name="incorrect-scaling"></a>Mise à l’échelle incorrect
Éléments d’interface utilisateur créés sur la résolution primaire mettra à l’échelle correctement, mais quand déplacées sur un écran avec une résolution différente, ils ne pas mettre à l’échelle et par conséquent, leur contenu finit par être trop grand ou trop petit.

#### <a name="incorrect-bounding"></a>Délimitation incorrect
De même, le problème de mise à l’échelle, éléments d’interface utilisateur calculera leurs limites correctement sur leur contexte principal de PPP, toutefois, lorsqu’un paramètre PPP non principal, ils ne sont pas calculer correctement les nouvelles limites. Par conséquent, la fenêtre de contenu finit par est trop petite ou trop grande par rapport à l’interface utilisateur hébergement, ce qui se traduit par un espace vide ou de découpage.

#### <a name="drag--drop"></a>Glisser -déplacer
Chaque fois que dans les scénarios de PPP en mode mixte (par exemple, différents éléments d’interface utilisateur rendu dans le contexte de PPP principaux et secondaires), glisser -déplacer coordonnées pourraient être douteuse, ce qui entraîne le dépôt final position finissent incorrect.

#### <a name="out-of-process-ui"></a>Interface utilisateur out-of-process
Une interface utilisateur est créée out-of-process et si la création du processus externe est dans un autre mode de sensibilisation à la résolution que Visual Studio, cela peut introduire un des problèmes de rendu précédent.

#### <a name="windows-forms-controls-images-or-windows-not-displaying"></a>Windows ne s’affichent ne pas, des images ou des contrôles Windows Forms
Une des principales causes de ce problème est de développeurs qui tentent de redéfinir la parenté un contrôle ou une fenêtre avec un seul DpiAwarenessContext vers une autre fenêtre de DpiAwarenessContext. 

Les images ci-dessous montrent les restrictions du système d’exploitation Windows en cours dans le parentage windows, sauf si le thread qui héberge le comportement est modifiée explicitement :

![Une capture d’écran du comportement parentage correct](../../extensibility/ux-guidelines/media/PMA-parenting-behavior.PNG)

Par conséquent, si vous définissez la relation parent-enfant entre les modes non pris en charge, il échoue, et le contrôle ou la fenêtre peut ne pas être restituée comme prévu.

### <a name="diagnosing-issues"></a>Diagnostic des problèmes
Il existe de nombreux facteurs à prendre en compte lors de l’identification des problèmes liés à AVM : 

1. Ne l’interface utilisateur ou l’API attendu logique ou les valeurs de l’appareil.
    - WPF UI et API généralement utilisent des valeurs logiques (mais pas toujours)
    - API et l’interface utilisateur Win32 généralement utiliser des valeurs de l’appareil

2. D'où viennent les valeurs ?
    - Si vous recevez des valeurs à partir d’autres l’interface utilisateur ou d’une API, est-il passage appareil ou des valeurs logiques.
    - Si vous recevez des valeurs provenant de plusieurs sources, tous utiliser/attendent les mêmes types de valeurs ou conversions doivent-ils être combinés et associés ?

3. Sont des constantes de l’interface utilisateur en cours d’utilisation et la forme se trouvent-ils ?

4. Est le thread dans le contexte de résolution approprié pour les valeurs qu’il reçoit ?
    - Les modifications apportées à activer CLMM doivent généralement placer des chemins de code dans le contexte approprié, toutefois, travail effectué en dehors du flux de messages principale boucle ou un événement peut s’exécuter dans le contexte de PPP incorrect.

5. Les valeurs traversent les limites du contexte PPP ?
    - Glisser -déplacer est une situation courante où les coordonnées peuvent traverser les contextes de PPP. Fenêtre essaie d’être adoptent l’attitude, mais dans certains cas, l’interface utilisateur hôte peut-être d’effectuer des tâches de conversion pour garantir la correspondance des limites de contexte.

### <a name="pma-nugget-package"></a>Package Nugget du AVM
Vous trouverez les nouvelles bibliothèques DpiAwarness sur le package NuGet de Microsoft.VisualStudio.DpiAwareness.

### <a name="recommended-tools"></a>Outils recommandés
Les outils suivants peuvent aider à déboguer les problèmes liés à AVM sur certaines des différentes piles de l’interface utilisateur pris en charge par Visual Studio.

#### <a name="snoop"></a>Aller fouiner
Snoop est un outil de débogage de XAML qui a quelques fonctionnalités supplémentaires qui n’a pas les outils de Visual Studio XAML intégrés. En outre, Snoop n’a pas besoin déboguer activement Visual Studio pour pouvoir afficher et modifier son UI WPF. Les deux méthodes principales Snoop peut être utile pour diagnostiquer les problèmes d’AVM est pour la validation des coordonnées de positionnement logique ou les limites de taille, et pour la validation de l’interface utilisateur a la valeur PPP de droite.
 
#### <a name="visual-studio-xaml-tools"></a>Outils de Visual Studio XAML
Comme Snoop, les outils XAML dans Visual Studio peuvent aider à diagnostiquer les problèmes d’AVM. Une fois une cause probable est trouvée, vous pouvez définir des points d’arrêt et utiliser la fenêtre de l’arborescence d’éléments visuels en direct, ainsi que les fenêtres de débogage, d’inspecter les limites de l’interface utilisateur et de résolution en cours.

## <a name="strategies-for-fixing-pma-issues"></a>Stratégies pour la résolution des problèmes d’AVM

### <a name="replacing-dpihelper-calls"></a>En remplaçant les appels DpiHelper
Dans la plupart des cas, résolution des problèmes de l’interface utilisateur dans AVM se résume à remplaçant les appels dans du code managé à l’ancien : *Microsoft.VisualStudio.Utilities.Dpi.DpiHelper* et *Microsoft.VisualStudio.PlatformUI.DpiHelper* classes, avec les appels à la nouvelle *Microsoft.VisualStudio.Utilities.DpiAwareness* classe d’assistance. 

Pour le code natif, il entraînera en remplaçant les appels à l’ancien *VsUI::CDpiHelper* classe avec les appels à la nouvelle *VsUI::CDpiAwareness* classe. Les nouvelles classes DpiAwareness et CDpiAwareness offrent les mêmes applications d’assistance de conversion comme les classes DpiHelper mais ne nécessitent un paramètre d’entrée supplémentaire : l’élément d’interface utilisateur à utiliser comme référence pour l’opération de conversion. 

La classe DpiAwareness managée offre programmes d’assistance pour les éléments visuels WPF, les contrôles Windows Forms et les HWND Win32 et HMONITORs (à la fois sous la forme d’IntPtrs), tout les CDpiAwareness classe offres HWND et HMONITOR des assistances natives.

### <a name="windows-forms-dialogs-windows-or-controls-displayed-in-the-wrong-dpiawarenesscontext"></a>Boîtes de dialogue Windows Forms, windows ou contrôles affichés dans le mauvais DpiAwarenessContext
Même après une réussite parentage de windows avec DpiAwarenessContext différents (en raison de comportement par défaut de windows), les utilisateurs peuvent toujours voir mise à l’échelle des problèmes comme des fenêtres différentes DpiAwarenessContext mettre à l’échelle différemment. Par conséquent, les utilisateurs peuvent voir texte flou/alignement ou des problèmes de l’Image sur l’interface utilisateur.

La solution consiste à définir l’étendue de DpiAwarenessContext correcte pour toutes les fenêtres et les contrôles dans l’application.

### <a name="tlmm-dialogs"></a>Boîtes de dialogue TLMM
Lorsque vous créez des fenêtres de niveau supérieur tels que des boîtes de dialogue modales, il est important de s’assurer que le thread est dans l’état approprié avant le HWND en cours de création. Le thread peut être placé dans la sensibilité au système par à l’aide du programme d’assistance CDpiScope en mode natif ou géré de l’application d’assistance DpiAwareness.EnterDpiScope dans. (TLMM doit généralement être utilisée sur les boîtes de dialogue non-WPF/windows.)

### <a name="child-level-mixed-mode-clmm"></a>En mode mixte au niveau enfant (CLMM)

Par défaut, les fenêtres enfants reçoivent le même mode de reconnaissance des résolutions que leurs parents. Toutefois, vous pouvez utiliser SetThreadDpiHostingBehavior pour remplacer et ont fenêtres enfants exécuté dans un mode de mise à l’échelle différents que leur parent ou l’hôte.


#### <a name="clmm-issues"></a>Problèmes CLMM
L’essentiel du travail de calcul de l’interface utilisateur qui se produit dans le cadre de la chaîne de boucle ou un événement messagerie principale doit déjà être en cours d’exécution dans le bon contexte PPP. Toutefois, si les coordonnées ou les calculs de dimensionnement sont effectuées en dehors de ces flux de travail principal (comme lors d’une tâche de durée d’inactivité, ou désactiver le thread d’interface utilisateur, le contexte actuel de la résolution peut être incorrect, ce qui conduit à dues de l’interface utilisateur ou mal les problèmes de dimensionnement. Mettre le thread dans l’état correct pour l’interface utilisateur travail résout généralement le problème.
 
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
```cplusplus
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

**REMARQUE** : Visual Studio prend uniquement en charge la connaissance de PerMonitorV2, donc la valeur d’énumération PerMonitor se traduit par la valeur de Windows de DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE_V2.

## <a name="known-issues"></a>Problèmes connus

### <a name="windows-forms"></a>Windows Forms

Pour optimiser les nouveaux scénarios en mode mixte, Windows Forms modifié la création de contrôles et windows chaque fois que leur parent n’a pas été définie explicitement. Précédemment, les contrôles sans un parent explicite utilisés une interne « stationnement fenêtre » comme parent temporaire pour le contrôle ou la fenêtre en cours de création. 

La « fenêtre de stationnement » obtient son DpiAwarenessContext à partir du processus de que l’application s’exécute sous. Le contrôle hérite de la même DpiAwarenessContext en tant que la fenêtre de stationnement et serait puis être à nouveau apparenté au parent d’origine/attendu par le développeur d’applications.  Cela ne fonctionne pas lorsque le parent souhaité pour le contrôle n’est pas le même DpiAwarenessContext que le contrôle en cours de création.

À compter de .NET 4.8, si le parent n’est pas explicitement défini dans le contrôle ou la fenêtre, Windows Forms interrogera pour une fenêtre de stationnement qui correspond à la DpiAwarenessContext du thread dans lequel la création de contrôle ou une fenêtre est demandée et l’utiliser en tant que temporaire parent. En d’autres termes, lors de la création du contrôle est maintenant créé avec la DpiAwarenessContext prévue. Le contrôle ou la fenêtre sera ensuite être à nouveau apparenté au parent attendu par le développeur d’applications.
