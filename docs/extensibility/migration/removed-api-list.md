---
title: API supprimées dans Visual Studio 2022 preview
description: En savoir plus sur les API VS SDK supprimées dans Visual Studio 2022 Preview, afin que les auteurs d’extension mettent à jour leurs extensions pour qu’elles fonctionnent avec Visual Studio 2022 preview.
ms.date: 06/08/2021
ms.topic: reference
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: bed8d0a261f70acb5e842ebeaf0059faae3fc478
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308722"
---
# <a name="visual-studio-2022-sdk-removed-apis"></a>API supprimées du kit de développement logiciel (SDK) Visual Studio 2022

[!INCLUDE [preview-note](../includes/preview-note.md)]

Les API ci-dessous ont été supprimées du kit de développement logiciel (SDK) Visual Studio et ne peuvent plus être utilisées, consultez chaque section pour plus d’informations sur la mise à jour de votre code.

* [`IVsImageService`](#ivsimageservice)
* [`IBlockContextProvider`](#iblockcontextprovider)
* [`IToolTipProvider`](#itooltipprovider)
* [`IVsTextScanner` les `IVsFullTextScanner`](#ivstextscanner-and-ivsfulltextscanner)
* [Chargement de solution asynchrone et chargement de solution allégé](#asynchronous-solution-load-and-lightweight-solution-load)
* [`IVsDummy`](#ivsdummy)
* [`Microsoft.VisualStudio.Shell.Task`](#microsoftvisualstudioshelltask)
* [Ouvrir à partir de la source Safe](#open-from-source-safe)
* [Nouvelle Concepteur XAML WPF pour .NET Framework](#new-wpf-xaml-designer-for-net-framework)

## <a name="ivsimageservice"></a>IVsImageService

`IVsImageService`Est en cours de suppression dans Visual Studio 2022. Tous les utilisateurs de `IVsImageService` doivent se déplacer vers à la `IVsImageService2` place.

### <a name="recommended-updates"></a>Mises à jour recommandées

Si vous utilisez `IVsImageService` , remplacez les appels à ses méthodes par des appels à des méthodes équivalentes sur `IVsImageService2` :

| **Méthode IVsImageService** | **Méthode IVsImageService2 équivalente** |
|----------------------------|----------------------------------------|
| Ajouter                        | AddCustomImage                         |
| Obtenir                        | GetImage                               |
| GetIconForFile             | GetImageMonikerForFile                 |
| GetIconForFileEx           | GetImageMonikerForFile                 |

`IVsImageService`Méthodes d’ajout et d’extraction d’images référencées par nom (une chaîne), plutôt que par un moniker.  Il est préférable que vous basculiez votre code pour utiliser uniquement des monikers pour faire référence à des images personnalisées, mais si cela prouve que cela peut `IVsImageService2` vous permettre d’associer un nom à un moniker :

* `TryAssociateNameWithMoniker`
* `GetImageMonikerForName`

À l’aide de ces deux méthodes, vous pouvez continuer à référencer les images par nom.

## <a name="iblockcontextprovider"></a>IBlockContextProvider

Les `IBlockContextProvider` types associés à et sont en cours de suppression dans Visual Studio 2022. Tous les utilisateurs de `IBlockContextProvider` doivent se déplacer vers à la `IStructureContextSourceProvider` place.

### <a name="recommended-updates"></a>Mises à jour recommandées

Les utilisateurs de `IBlockContextProvider` doivent utiliser à `IStructureContextSourceProvider` [la](/dotnet/api/microsoft.visualstudio.text.adornments.istructurecontextsourceprovider)place (documentation).

## <a name="itooltipprovider"></a>IToolTipProvider

Les `IToolTipProvider` types associés à et sont en cours de suppression dans Visual Studio 2022. Tous les utilisateurs de `IToolTipProvider` doivent se déplacer vers à la `IToolTipService` place.

### <a name="recommended-updates"></a>Mises à jour recommandées

Les utilisateurs de `IToolTipProvider` doivent utiliser à `IToolTipService` [la](/dotnet/api/microsoft.visualstudio.text.adornments.itooltipservice)place (documentation).

## <a name="ivstextscanner-and-ivsfulltextscanner"></a>IVsTextScanner et IVsFullTextScanner

Les éléments `IVsTextScanner` et `IVsFullTextScanner` sont en cours de suppression dans Visual Studio 2022. Tous les utilisateurs de `IVsTextScanner` ou `IVsFullTextScanner` doivent se déplacer vers à la `IVsTextLines` place.

### <a name="recommended-updates"></a>Mises à jour recommandées

Les utilisateurs de `IVsTextScanner` ou `IVsFullTextScanner` doivent utiliser à `IVsTextLines` la place ([documentation](/dotnet/apimicrosoft.visualstudio.textmanager.interop.ivstextlines.getlinetext)).

## <a name="asynchronous-solution-load-and-lightweight-solution-load"></a>Chargement de solution asynchrone et chargement de solution allégé

Les fonctionnalités de chargement de solution asynchrone (ASL) et de chargement de solution allégé (LSL) sont supprimées dans Visual Studio 2022, car les méthodes suivantes sont supprimées :

### <a name="interfaces"></a>Interfaces

* `IVsSolution4` -Méthodes : `IsBackgroundSolutionLoadEnabled` , `EnsureProjectsAreLoaded` , `EnsureProjectIsLoaded` , `EnsureSolutionIsLoaded`
* `IVsSolutionLoadEvents` -Méthodes : `OnBeforeBackgroundSolutionLoadBegins` , `OnQueryBackgroundLoadProjectBatch` , `OnBeforeLoadProjectBatch` , `OnAfterLoadProjectBatch`
* `IVsSolutionLoadManagerSupport` -Interface entière
* `IVsSolutionLoadManager` -Interface entière
* `IVsSccManager3`  -Interface entière
* `IVsAsynchronousProjectCreate` -Interface entière
* `IVsAsynchronousProjectCreateUI` -Interface entière

### <a name="enums-properties-and-ui-contexts"></a>Enums, propriétés et contextes d’interface utilisateur

* `VSHPROPID_ProjectUnloadStatus` Variables `UNLOADSTATUS_LoadPendingIfNeeded`
* `VSHPROPID_DemandLoadDependencies`
* `VSHPROPID_IsProjectProvisioned`
* `VSPROPID_IsInBackgroundIdleLoadProjectBatch`
* `VSPROPID_IsInSyncDemandLoadProjectBatch`
* `VSPROPID_ActiveSolutionLoadManager`
* `UICONTEXT_BackgroundProjectLoad`

### <a name="recommended-updates"></a>Mises à jour recommandées

Aucun.

## <a name="ivsdummy"></a>IVsDummy

Le `IVsDummy` est en cours de suppression dans Visual Studio 2022 et ne sera pas remplacé. 

### <a name="recommended-updates"></a>Mises à jour recommandées

Aucun. Mais cela ne devrait avoir aucun impact, car l’API n’a rien fait.

## <a name="microsoftvisualstudioshelltask"></a>Microsoft. VisualStudio. Shell. Task

La `Microsoft.VisualStudio.Shell.Task` classe a été renommée pour `Microsoft.VisualStudio.Shell.TaskListItem` ne pas entrer en conflit avec la classe très populaire `System.Threading.Tasks.Task` .

## <a name="open-from-source-safe"></a>Ouvrir à partir de la source Safe

La prise en charge de l’ouverture d’une solution à partir de la sécurité source est en cours de suppression, car les méthodes, événements et constantes suivants sont en cours de suppression.

## <a name="interfaces"></a>Interfaces

* `IVsSCCProvider3` -Interface entière

### <a name="recommended-updates"></a>Mises à jour recommandées

Aucun.

## <a name="new-wpf-xaml-designer-for-net-framework"></a>Nouvelle Concepteur XAML WPF pour .NET Framework

La Concepteur XAML WPF actuelle pour .NET Framework a été dépréciée et sera remplacée par une nouvelle Concepteur XAML WPF pour .NET Framework, en fonction de la même architecture que celle utilisée pour la Concepteur XAML WPF pour .NET (.NET Core). Cela signifie également que le modèle d’extensibilité de contrôle .NET Framework WPF basé sur .design.dll et Microsoft. Windows. Design. Extensibility n’est plus pris en charge. Le nouveau Concepteur XAML WPF pour .NET Framework fournira le même modèle d’extensibilité que le Concepteur XAML WPF pour .NET (.NET Core). Si vous avez déjà créé une extension de .designtools.dll pour .NET (.NET Core), cette même extension fonctionnera pour le nouveau Concepteur XAML WPF pour .NET Framework. Pour plus d’informations sur la migration vers le nouveau modèle d’extensibilité pour les plateformes WPF (.NET Framework et .NET Core) et les plateformes UWP, reportez-vous au lien de migration ci-dessous. 

### <a name="recommended-updates"></a>Mises à jour recommandées

Consultez [migration de l’extensibilité du concepteur XAML](https://github.com/microsoft/xaml-designer-extensibility/blob/main/documents/xaml-designer-extensibility-migration.md).
