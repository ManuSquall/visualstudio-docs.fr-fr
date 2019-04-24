---
title: 'Procédure : Utiliser AsyncPackage pour charger des VSPackages en arrière-plan | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
author: gregvanl
ms.author: gregvanl
ms.workload:
- vssdk
ms.openlocfilehash: 99b23c223d91678f03a52910ed4516be0839a338
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60113961"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Procédure : Utiliser AsyncPackage pour charger des VSPackages en arrière-plan
E/s disque peuvent entraîner le chargement et l’initialisation d’un package VS. Si ces e/s se produit sur le thread d’interface utilisateur, il peut entraîner des problèmes de réactivité. Pour résoudre ce problème, Visual Studio 2015 introduit le <xref:Microsoft.VisualStudio.Shell.AsyncPackage> classe qui permet le chargement de package sur un thread d’arrière-plan.

## <a name="create-an-asyncpackage"></a>Créer un AsyncPackage
 Vous pouvez commencer par créer un projet VSIX (**fichier** > **New** > **projet** > **Visual C#**   >  **Extensibilité** > **projet VSIX**) et l’ajout d’un VSPackage au projet (avec le bouton droit sur le projet et **ajouter**  >  **Un nouvel élément**  >   **C# élément** > **extensibilité**  >   **Package Visual Studio**). Vous pouvez créer vos services, puis ajouter ces services à votre package.

1. Dériver le package à partir de <xref:Microsoft.VisualStudio.Shell.AsyncPackage>.

2. Si vous fournissez des services dont l’interrogation risque de votre package à charger :

    Pour indiquer à Visual Studio que votre package est sécurisé pour le chargement en arrière-plan et à adopter ce comportement, votre <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> doit définir **AllowsBackgroundLoading** propriété sur true dans le constructeur d’attribut.

   ```csharp
   [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]

   ```

    Pour indiquer à Visual Studio qu’il est sûr instancier votre service sur un thread d’arrière-plan, vous devez définir le <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> propriété sur true dans le <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> constructeur.

   ```csharp
   [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]

   ```

3. Si vous chargez par le biais de contextes d’interface utilisateur, vous devez spécifier **PackageAutoLoadFlags.BackgroundLoad** pour le <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> ou la valeur (0 x 2) dans les indicateurs écrite en tant que la valeur d’entrée de charger automatiquement de votre package.

   ```csharp
   [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]

   ```

4. Si vous avez un travail de l’initialisation asynchrone à faire, vous devez substituer <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>. Supprimer le `Initialize()` méthode fournie par le modèle VSIX. (Le `Initialize()` méthode dans **AsyncPackage** est sealed). Vous pouvez utiliser toutes les <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> méthodes pour ajouter des services asynchrones à votre package.

    REMARQUE : Pour appeler `base.InitializeAsync()`, vous pouvez modifier votre code source :

   ```csharp
   await base.InitializeAsync(cancellationToken, progress);
   ```

5. Vous devez veiller à ne rend ne pas RPC (Remote Procedure Call) à partir de votre code d’initialisation asynchrone (dans **InitializeAsync**). Il peuvent se produire lorsque vous appelez <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> directement ou indirectement.  Lorsque les charges de synchronisation sont requis, bloque le thread d’interface utilisateur à l’aide de <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>. Le modèle de blocage par défaut désactive RPC. Cela signifie que si vous essayez d’utiliser un RPC à partir de vos tâches async, vous êtes l’interblocage si le thread d’interface utilisateur est lui-même en attente de votre package à charger. L’alternative général est de marshaler votre code pour le thread d’interface utilisateur si nécessaire à l’aide de quelque chose comme **fabrique de tâches assemblables**de <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> ou tout autre mécanisme qui n’utilise pas un RPC.  N’utilisez pas **ThreadHelper.Generic.Invoke** ou généralement bloque le thread appelant attend d’obtenir le thread d’interface utilisateur.

    REMARQUE : Évitez d’utiliser **GetService** ou **QueryService** dans votre `InitializeAsync` (méthode). Si vous devez les utiliser, vous devez basculer vers le thread d’interface utilisateur tout d’abord. L’alternative consiste à utiliser <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> à partir de votre **AsyncPackage** (en le convertissant à <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>.)

   C# : Créer un AsyncPackage :

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

## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>Convertir un VSPackage existant AsyncPackage
 La majorité du travail est identique à la création d’un nouveau **AsyncPackage**. Suivez les étapes 1 à 5 ci-dessus. Vous devez également prendre des précautions supplémentaires avec les recommandations suivantes :

1. N’oubliez pas de supprimer le `Initialize` remplacement que vous aviez dans votre package.

2. Éviter les blocages : Il peut être masqué RPC dans votre code. ce qui se produire maintenant sur un thread d’arrière-plan. Assurez-vous que si vous effectuez un appel RPC (par exemple, **GetService**), vous devez soit (1) Basculer vers le thread principal ou (2) utilisez la version asynchrone de l’API s’il existe (par exemple, **GetServiceAsync**).

3. Ne basculez pas entre les threads trop fréquemment. Essayez de localiser le travail qui peut se produire dans un thread d’arrière-plan afin de réduire le temps de chargement.

## <a name="querying-services-from-asyncpackage"></a>Interrogation des services à partir de AsyncPackage
 Un **AsyncPackage** peut ou ne peut pas charger de façon asynchrone en fonction de l’appelant. Par exemple,

- Si l’appelant appelé **GetService** ou **QueryService** (ces deux API synchrones) ou

- Si l’appelant appelé **IVsShell::LoadPackage** (ou **IVsShell5::LoadPackageWithContext**) ou

- La charge est déclenchée par un contexte d’interface utilisateur, mais vous n’avez pas spécifié que le mécanisme de contexte de l’interface utilisateur vous charger en mode asynchrone

  puis votre package sera chargée de façon synchrone.

  Votre package a toujours une opportunité (dans sa phase d’initialisation asynchrone) pour effectuer le travail du thread de l’interface utilisateur, bien que le thread d’interface utilisateur sera bloqué pendant la saisie semi-automatique de ce travail. Si l’appelant utilise **IAsyncServiceProvider** à une requête asynchrone pour votre service, puis votre charge et l’initialisation seront effectuées en mode asynchrone en supposant qu’ils ne bloquent pas immédiatement sur l’objet résultant de la tâche.

  C# : Guide pratique pour interroger le service de façon asynchrone

```csharp
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;

IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;
IMyTestService testService = await asyncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;
```
