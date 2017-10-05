---
title: "Comment : utiliser AsyncPackage pour charger les VSPackages en arrière-plan | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
caps.latest.revision: 8
ms.author: gregvanl
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: cfd99e4926aac1847f6f0397747201cb0e3a74ab
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Comment : utiliser AsyncPackage pour charger les VSPackages en arrière-plan
E/s disque peuvent entraîner le chargement et l’initialisation d’un package Visual Studio. Si ces e/s se produit sur le thread d’interface utilisateur, elle peut entraîner des problèmes de réactivité. Pour résoudre ce problème, Visual Studio 2015 introduit le <xref:Microsoft.VisualStudio.Shell.AsyncPackage> classe qui permet le chargement du package sur un thread d’arrière-plan.  
  
## <a name="creating-an-asyncpackage"></a>Création d’un AsyncPackage  
 Commencez par créer un projet VSIX (**fichier / nouveau / projet / Visual c# / extensibilité / projet VSIX**) et l’ajout d’un VSPackage au projet (cliquez avec le bouton droit sur le projet et **élément d’ajouter un nouveau / C# élément/extensibilité/Visual Package Studio**). Vous pouvez ensuite créer vos services et ajouter ces services à votre package.  
  
1.  Dériver le package à partir de <xref:Microsoft.VisualStudio.Shell.AsyncPackage>.  
  
2.  Si vous fournissez des services dont l’interrogation risque de votre package à charger :  
  
     Pour indiquer à Visual Studio que votre package est sécurisé pour le chargement en arrière-plan et adopter ce comportement, votre <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> doit définir **AllowsBackgroundLoading** true dans le constructeur d’attribut à la propriété.  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]  
  
    ```  
  
     Pour indiquer à Visual Studio qu’il peut instancier votre service sur un thread d’arrière-plan, vous devez définir le <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> propriété à true dans le <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> constructeur.  
  
    ```csharp  
    [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]  
  
    ```  
  
3.  Si vous chargez via les contextes d’interface utilisateur, vous devez spécifier **PackageAutoLoadFlags.BackgroundLoad** pour le <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> ou la valeur (0 x 2) dans les indicateurs écrit sous forme de la valeur d’entrée de charger automatiquement de votre package.  
  
    ```csharp  
    [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]  
  
    ```  
  
4.  Si vous disposez de travail à effectuer l’initialisation asynchrone, vous devez substituer <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>. Supprimer le **Initialize()** méthode fournie par le modèle VSIX. (Le **Initialize()** méthode dans **AsyncPackage** est sealed). Vous pouvez utiliser toutes les <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> méthodes pour ajouter des services asynchrones à votre package.  
  
     Remarque : Pour appeler **base. InitializeAsync()**, vous pouvez modifier votre code source :  
  
    ```csharp  
    await base.InitializeAsync(cancellationToken, progress);  
    ```  
  
5.  Vous devez prendre soin pour ne pas rendre RPC (Remote Procedure Call) à partir de votre code d’initialisation asynchrone (dans **InitializeAsync**). Il peuvent se produire lorsque vous appelez <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> directement ou indirectement.  Lorsque les charges de synchronisation sont requis, bloque le thread d’interface utilisateur à l’aide de <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>. Le modèle de blocage par défaut désactive les appels de procédure distante. Cela signifie que si vous essayez d’utiliser un RPC à partir de vos tâches asynchrones, vous blocage si le thread d’interface utilisateur est lui-même en attente de votre package à charger. L’alternative générale est de marshaler votre code pour le thread d’interface utilisateur si nécessaire en utilisant un nom tel que **joignable fabrique de tâches**de <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> ou tout autre mécanisme qui n’utilise pas un RPC.  N’utilisez pas **ThreadHelper.Generic.Invoke** ou généralement bloquer le thread appelant attend d’obtenir le thread d’interface utilisateur.  
  
     Remarque : Vous devez éviter d’utiliser **GetService** ou **QueryService** dans votre **InitializeAsync** (méthode). Si vous devez les utiliser, vous devrez basculez d’abord vers le thread d’interface utilisateur. L’alternative consiste à utiliser <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> à partir de votre **AsyncPackage** (en effectuant un cast à <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>.)  
  
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
 La plupart du travail est identique à la création d’un **AsyncPackage**. Vous devez suivre les étapes 1 à 5 ci-dessus. Vous devez également prendre la précaution supplémentaire sur les éléments suivants :  
  
1.  N’oubliez pas de supprimer le **initialiser** remplacement que vous aviez dans votre package.  
  
2.  Éviter les blocages : il peut y avoir masqué RPC dans votre code qui désormais se produire sur un thread d’arrière-plan. Vous devez vous assurer que si vous effectuez un appel RPC (par exemple, **GetService**), vous devez soit commutateur (1) sur le thread principal ou (2) utilisez la version asynchrone de l’API s’il existe (par exemple, **GetServiceAsync**).  
  
3.  Ne passez pas de threads trop fréquemment. Essayez de localiser le travail qui peut se produire dans un thread d’arrière-plan. Cela réduit le temps de chargement.  
  
## <a name="querying-services-from-asyncpackage"></a>Interrogation des Services à partir de AsyncPackage  
 Un **AsyncPackage** peut ou ne peut pas charger de façon asynchrone en fonction de l’appelant. Par exemple,  
  
-   Si l’appelant appelé **GetService** ou **QueryService** (les deux API synchrone) ou  
  
-   Si l’appelant appelé **IVsShell::LoadPackage** (ou **IVsShell5::LoadPackageWithContext**) ou  
  
-   La charge est déclenchée par un contexte de l’interface utilisateur, mais vous n’avez pas spécifié que le mécanisme de contexte de l’interface utilisateur vous chargement asynchrone  
  
 puis votre package sera chargée de façon synchrone.  
  
 Notez que votre package a toujours une opportunité (dans sa phase d’initialisation asynchrone) pour effectuer le travail du thread d’interface utilisateur, bien que le thread d’interface utilisateur est bloqué pour l’achèvement de ce travail. Si l’appelant utilise **IAsyncServiceProvider** à une requête asynchrone pour votre service, puis votre charge et initialisation seront effectuées en mode asynchrone en supposant que ne pas bloquer immédiatement sur l’objet de tâche qui en résulte.  
  
 C# : Comment interroger le service de façon asynchrone :  
  
```csharp  
using Microsoft.VisualStudio.Shell;   
using Microsoft.VisualStudio.Shell.Interop;   
  
IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;   
IMyTestService testService = await ayncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;  
```
  

