---
title: 'Comment : utiliser AsyncPackage pour charger des VSPackages en arrière-plan | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
caps.latest.revision: 9
ms.author: gregvanl
ms.openlocfilehash: 4e5ff08c256838626537ae10ede9dffd8aea6b08
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49899628"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Comment : utiliser AsyncPackage pour charger des VSPackages en arrière-plan
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

E/s disque peuvent entraîner le chargement et l’initialisation d’un package VS. Si ces e/s se produit sur le thread d’interface utilisateur, il peut entraîner des problèmes de réactivité. Pour résoudre ce problème, Visual Studio 2015 introduit le <xref:Microsoft.VisualStudio.Shell.AsyncPackage> classe qui permet le chargement de package sur un thread d’arrière-plan.  
  
## <a name="creating-an-asyncpackage"></a>Création d’un AsyncPackage  
 Vous pouvez commencer par créer un projet VSIX (**fichier / nouveau / projet / Visual c# / extensibilité / projet VSIX**) et l’ajout d’un VSPackage au projet (cliquez avec le bouton droit sur le projet et **ajouter/New Item / C# élément/extensibilité/Visual Package Studio**). Vous pouvez créer vos services, puis ajouter ces services à votre package.  
  
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
  
4. Si vous avez un travail de l’initialisation asynchrone à faire, vous devez substituer <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>. Supprimer le **Initialize()** méthode fournie par le modèle VSIX. (Le **Initialize()** méthode dans **AsyncPackage** est sealed). Vous pouvez utiliser toutes les <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> méthodes pour ajouter des services asynchrones à votre package.  
  
    Remarque : Pour appeler **base. InitializeAsync()**, vous pouvez modifier votre code source :  
  
   ```csharp  
   await base.InitializeAsync(cancellationToken, progress);  
   ```  
  
5. Vous devez veiller à ne rend ne pas RPC (supprimer Procedure Call) à partir de votre code d’initialisation asynchrone (dans **InitializeAsync**). Il peuvent se produire lorsque vous appelez <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> directement ou indirectement.  Lorsque les charges de synchronisation sont requis, bloque le thread d’interface utilisateur à l’aide de <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>. Le modèle de blocage par défaut désactive RPC. Cela signifie que si vous essayez d’utiliser un RPC à partir de vos tâches async, vous êtes l’interblocage si le thread d’interface utilisateur est lui-même en attente de votre package à charger. L’alternative général est de marshaler votre code pour le thread d’interface utilisateur si nécessaire à l’aide de quelque chose comme **fabrique de tâches assemblables**de <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> ou tout autre mécanisme qui n’utilise pas un RPC.  N’utilisez pas **ThreadHelper.Generic.Invoke** ou généralement bloque le thread appelant attend d’obtenir le thread d’interface utilisateur.  
  
    Remarque : Vous devez éviter d’utiliser **GetService** ou **QueryService** dans votre **InitializeAsync** (méthode). Si vous devez les utiliser, vous devez basculer vers le thread d’interface utilisateur tout d’abord. L’alternative consiste à utiliser <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> à partir de votre **AsyncPackage** (en le convertissant à <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>.)  
  
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
 La majorité du travail est identique à la création d’un nouveau **AsyncPackage**. Vous devez suivre les étapes 1 à 5 ci-dessus. Vous devez également prendre une attention supplémentaire sur les éléments suivants :  
  
1.  N’oubliez pas de supprimer le **initialiser** remplacement que vous aviez dans votre package.  
  
2.  Éviter les interblocages : il peut être masqué RPC dans votre code qui se produisent maintenant sur un thread d’arrière-plan. Vous devez vous assurer que si vous effectuez un appel RPC (par exemple, **GetService**), vous devez soit (1) Basculer vers le thread principal ou (2) utilisez la version asynchrone de l’API s’il existe (par exemple, **GetServiceAsync**).  
  
3.  Ne basculez pas entre les threads trop fréquemment. Essayez de localiser le travail qui peut se produire dans un thread d’arrière-plan. Cela réduit le temps de chargement.  
  
## <a name="querying-services-from-asyncpackage"></a>Interrogation des Services à partir de AsyncPackage  
 Un **AsyncPackage** peut ou ne peut pas charger de façon asynchrone en fonction de l’appelant. Par exemple,  
  
- Si l’appelant appelé **GetService** ou **QueryService** (ces deux API synchrones) ou  
  
- Si l’appelant appelé **IVsShell::LoadPackage** (ou **IVsShell5::LoadPackageWithContext**) ou  
  
- La charge est déclenchée par un contexte d’interface utilisateur, mais vous n’avez pas spécifié que le mécanisme de contexte de l’interface utilisateur vous charger en mode asynchrone  
  
  puis votre package sera chargée de façon synchrone.  
  
  Notez que votre package a toujours une opportunité (dans sa phase d’initialisation asynchrone) pour effectuer le travail du thread de l’interface utilisateur, bien que le thread d’interface utilisateur sera bloqué pendant la saisie semi-automatique de ce travail. Si l’appelant utilise **IAsyncServiceProvider** à une requête asynchrone pour votre service, puis votre charge et l’initialisation seront effectuées en mode asynchrone en supposant qu’ils ne bloquent pas immédiatement sur l’objet résultant de la tâche.  
  
  C# : Comment interroger le service de façon asynchrone :  
  
```csharp  
using Microsoft.VisualStudio.Shell;   
using Microsoft.VisualStudio.Shell.Interop;   
  
IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;   
IMyTestService testService = await ayncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;  
```

