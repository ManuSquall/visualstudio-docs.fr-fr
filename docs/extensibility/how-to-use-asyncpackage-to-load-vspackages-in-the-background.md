---
title: 'Comment: Utilisez AsyncPackage pour charger VSPackages en arrière-plan (fr) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: 77690a1947f82f97c4aa12809a80ea61335d216d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710615"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Comment: Utilisez AsyncPackage pour charger VSPackages en arrière-plan
Le chargement et l’initialisation d’un paquet VS peuvent entraîner le disque I/O. Si un tel I /O se produit sur le thread d’interface utilisateur, il peut conduire à des problèmes de réactivité. Pour remédier à cette situation, Visual <xref:Microsoft.VisualStudio.Shell.AsyncPackage> Studio 2015 a introduit la classe qui permet le chargement des paquets sur un thread de fond.

## <a name="create-an-asyncpackage"></a>Créer un AsyncPackage
 Vous pouvez commencer par créer un projet VSIX **(File** > **New** > **Project** > **Visual C '** > **Extensibility** > **VSIX Project**) et en ajoutant un VSPackage au projet (cliquez à droite sur le projet et **ajouter** > **le nouvel** > **article** > C '**Extensibility** > **Visual Studio Package**). Vous pouvez ensuite créer vos services et ajouter ces services à votre forfait.

1. Dérivez le <xref:Microsoft.VisualStudio.Shell.AsyncPackage>paquet de .

2. Si vous fournissez des services dont la requête peut entraîner la charge de votre colis :

    Pour indiquer à Visual Studio que votre colis est sûr pour <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> le chargement de fond et d’opter dans ce comportement, votre devrait définir La propriété **AllowsBackgroundLoading** à vrai dans le constructeur d’attributs.

   ```csharp
   [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]

   ```

    Pour indiquer à Visual Studio qu’il est sûr d’instantanéiser votre <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> service sur <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> un thread de fond, vous devez définir la propriété pour vrai dans le constructeur.

   ```csharp
   [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]

   ```

3. Si vous chargez via des contextes d’interface utilisateur, vous devez <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> spécifier **PackageAutoLoadFlags.BackgroundLoad** pour la RO la valeur (0x2) dans les drapeaux écrits comme la valeur de l’entrée de votre colis auto-charge.

   ```csharp
   [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]

   ```

4. Si vous avez un travail d’initialisation asynchrone à faire, vous devriez l’emporter <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>. Supprimer `Initialize()` la méthode fournie par le modèle VSIX. (La `Initialize()` méthode dans **AsyncPackage** est scellée). Vous pouvez utiliser <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> l’une des méthodes pour ajouter des services asynchrones à votre forfait.

    REMARQUE : `base.InitializeAsync()`Pour appeler, vous pouvez modifier votre code source pour :

   ```csharp
   await base.InitializeAsync(cancellationToken, progress);
   ```

5. Vous devez prendre soin de ne PAS faire de RPC (Remote Procedure Call) à partir de votre code d’initialisation asynchrone (dans **InitializeAsync**). Ceux-ci peuvent <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> se produire lorsque vous appelez directement ou indirectement.  Lorsque des charges de synchronisation sont nécessaires, <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>le thread d’interface utilisateur bloque à l’aide . Le modèle de blocage par défaut désactive les RPC. Cela signifie que si vous essayez d’utiliser un RPC à partir de vos tâches async, vous serez dans l’impasse si le thread d’interface utilisateur est lui-même en attente de votre paquet à charger. L’alternative générale est de mobiliser votre code au thread d’interface <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> utilisateur si nécessaire en utilisant quelque chose comme **Joinable Task Factory**ou un autre mécanisme qui n’utilise pas un RPC.  Ne pas utiliser **ThreadHelper.Generic.Invoke** ou bloquez généralement le fil d’appel en attente d’obtenir le thread d’interface utilisateur.

    REMARQUE : Vous devriez éviter d’utiliser `InitializeAsync` **GetService** ou **QueryService** dans votre méthode. Si vous devez les utiliser, vous devrez passer d’abord au thread d’interface utilisateur. L’alternative est <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> d’utiliser à partir de votre <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider> **AsyncPackage** (en le jetant à .)

   C : Créez un AsyncPackage :

```csharp
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]
public sealed class TestPackage : AsyncPackage
{
    protected override Task InitializeAsync(System.Threading.CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(SMyTestService), CreateService, true);
        return Task.FromResult<object>(null);
    }
}
```

## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>Convertir un VSPackage existant en AsyncPackage
 La majorité du travail est la même que la création d’un nouvel **AsyncPackage**. Suivez les étapes 1 à 5 ci-dessus. Vous devez également faire preuve de prudence avec les recommandations suivantes :

1. N’oubliez `Initialize` pas de supprimer le remplacement que vous aviez dans votre colis.

2. Évitez les blocages : il pourrait y avoir des RPC cachés dans votre code. qui se produisent maintenant sur un fil de fond. Assurez-vous que si vous faites un RPC (par exemple, **GetService**), vous devez soit (1) passer au fil principal ou (2) utiliser la version asynchrone de l’API si l’on existe (par exemple, **GetServiceAsync**).

3. Ne pas basculer entre les threads trop fréquemment. Essayez de localiser le travail qui peut se produire dans un thread d’arrière-plan pour réduire le temps de charge.

## <a name="querying-services-from-asyncpackage"></a>Services de requête d’AsyncPackage
 Un **AsyncPackage** peut ou non charger asynchronement selon l’appelant. Par exemple,

- Si l’appelant appelé **GetService** ou **QueryService** (deux API synchrones) ou

- Si l’appelant a appelé **IVsShell::LoadPackage** (ou **IVsShell5::LoadPackageWithContext**) ou

- La charge est déclenchée par un contexte d’interface utilisateur, mais vous n’avez pas spécifier le mécanisme de contexte d’interface utilisateur peut vous charger asynchroneously

  puis votre paquet se chargera de façon synchrone.

  Votre paquet a toujours une occasion (dans sa phase d’initialisation asynchrone) de faire le travail sur le fil d’interface utilisateur, bien que le fil d’interface utilisateur sera bloqué pour l’achèvement de ce travail. Si l’appelant utilise **IAsyncServiceProvider** pour interroger asynchronement pour votre service, alors votre charge et l’initialisation seront faites asynchronement en supposant qu’ils ne bloquent pas immédiatement sur l’objet de tâche résultant.

  C : Comment interroger le service asynchrone :

```csharp
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;

IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;
IMyTestService testService = await asyncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;
```
