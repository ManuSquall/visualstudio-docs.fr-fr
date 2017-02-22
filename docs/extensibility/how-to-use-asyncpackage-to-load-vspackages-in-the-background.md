---
title: "Comment&#160;: utiliser AsyncPackage pour charger les VSPackages en arri&#232;re-plan | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
caps.latest.revision: 8
ms.author: "gregvanl"
caps.handback.revision: 8
---
# Comment&#160;: utiliser AsyncPackage pour charger les VSPackages en arri&#232;re-plan
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

E\/s disque peuvent entraîner le chargement et l’initialisation d’un package VS. Si ces e\/s se produit sur le thread d’interface utilisateur, il peut provoquer des problèmes de réactivité. Pour résoudre ce problème, Visual Studio 2015 introduit la <xref:Microsoft.VisualStudio.Shell.AsyncPackage> classe permettant le chargement du package sur un thread d’arrière\-plan.  
  
## Création d’un AsyncPackage  
 Vous pouvez commencer par créer un projet VSIX \(**fichier \/ nouveau \/ projet \/ Visual C\# \/ extensibilité \/ projet VSIX**\) et en ajoutant un VSPackage au projet \(cliquez avec le bouton droit sur le projet et **Ajouter un nouveau élément \/ C\# élément\/extensibilité\/Visual Studio Package**\). Vous pouvez créer vos services, puis ajouter ces services à votre package.  
  
1.  Dériver le package à partir de <xref:Microsoft.VisualStudio.Shell.AsyncPackage>.  
  
2.  Si vous fournissez des services dont l’interrogation risque de votre package à charger :  
  
     Pour indiquer à Visual Studio que votre package est sécurisé pour le chargement en arrière\-plan et s’abonner à ce problème, votre <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> doit définir **AllowsBackgroundLoading** propriété la valeur true dans le constructeur d’attribut.  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]  
  
    ```  
  
     Pour indiquer à Visual Studio qu’il est sûr instancier votre service sur un thread d’arrière\-plan, vous devez définir le <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> propriété à true dans le <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> constructeur.  
  
    ```c#  
    [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]  
  
    ```  
  
3.  Si vous chargez via des contextes d’interface utilisateur, vous devez spécifier **PackageAutoLoadFlags.BackgroundLoad** pour le <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> ou la valeur \(0 x 2\) dans les indicateurs écrite en tant que la valeur d’entrée de chargement automatique de votre package.  
  
    ```c#  
    [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]  
  
    ```  
  
4.  Si vous disposez d’un travail d’initialisation asynchrone à faire, vous devez substituer <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>. Supprimer le **Initialize\(\)** méthode fournie par le modèle VSIX. \(Le **Initialize\(\)** méthode **AsyncPackage** est sealed\). Vous pouvez utiliser toutes les <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> méthodes pour ajouter des services asynchrones à votre package.  
  
     Remarque : Pour appeler **base. InitializeAsync\(\)**, vous pouvez modifier votre code source :  
  
    ```c#  
    await base.InitializeAsync(cancellationToken, progress);  
    ```  
  
5.  Vous devez veiller à ne rend ne pas RPC \(supprimer Procedure Call\) à partir de votre code d’initialisation asynchrone \(dans **InitializeAsync**\). Il peuvent se produire lorsque vous appelez <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> directement ou indirectement.  Lorsque les charges de synchronisation sont requis, bloque le thread d’interface utilisateur à l’aide de <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>. Le modèle de blocage par défaut désactive RPC. Cela signifie que si vous essayez d’utiliser un RPC à partir de vos tâches asynchrones, vous blocage si le thread d’interface utilisateur est en attente de votre package à charger. L’alternative général est de marshaler votre code pour le thread d’interface utilisateur si nécessaire à l’aide de quelque chose comme **joignable fabrique de tâches**de <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> ou un autre mécanisme qui n’utilise pas un RPC.  N’utilisez pas **ThreadHelper.Generic.Invoke** ou généralement bloque le thread appelant attend d’obtenir le thread d’interface utilisateur.  
  
     Remarque : Vous devez éviter d’utiliser **GetService** ou **QueryService** dans votre **InitializeAsync** \(méthode\). Si vous devez les utiliser, vous devrez basculez d’abord vers le thread d’interface utilisateur. L’alternative consiste à utiliser <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> à partir de votre **AsyncPackage** \(en le convertissant au <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>.\)  
  
 C\# : Créer un AsyncPackage :  
  
```c#  
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
  
## Convertir un VSPackage existant AsyncPackage  
 La majeure partie du travail est identique à la création d’un **AsyncPackage**. Vous devez suivre les étapes 1 à 5 ci\-dessus. Vous devez également prendre très attention sur les éléments suivants :  
  
1.  N’oubliez pas de supprimer le **initialiser** remplacement que vous aviez dans votre package.  
  
2.  Éviter les blocages : il peut être masqué RPC dans votre code qui se produisent maintenant sur un thread d’arrière\-plan. Vous devez vous assurer que si vous effectuez un appel RPC \(par exemple, **GetService**\), vous devez vous passez par le thread principal \(1\) ou \(2\) utilisez la version asynchrone de l’API s’il existe \(par exemple, **GetServiceAsync**\).  
  
3.  Ne passez pas de threads trop fréquemment. Essayez de localiser le travail qui peut se produire dans un thread d’arrière\-plan. Cela réduit le temps de chargement.  
  
## Interrogation des Services de AsyncPackage  
 Un **AsyncPackage** peut ou ne peut pas charger asynchrone en fonction de l’appelant. Par exemple,  
  
-   Si l’appelant appelé **GetService** ou **QueryService** \(les deux API synchrone\) ou  
  
-   Si l’appelant appelé **IVsShell::LoadPackage** \(ou **IVsShell5::LoadPackageWithContext**\) ou  
  
-   La charge est déclenchée par un contexte de l’interface utilisateur, mais vous n’avez pas spécifié que le mécanisme de contexte de l’interface utilisateur vous charger en mode asynchrone  
  
 puis votre package sera chargé de façon synchrone.  
  
 Notez que votre package a toujours une opportunité \(dans sa phase d’initialisation asynchrone\) pour effectuer le travail du thread d’interface utilisateur, bien que le thread d’interface utilisateur sera bloquée pour la saisie semi\-automatique de ce travail. Si l’appelant utilise **IAsyncServiceProvider** à une requête asynchrone pour votre service, puis votre charge et l’initialisation seront effectuées en mode asynchrone en supposant qu’ils ne bloquent immédiatement sur l’objet de tâche qui en résulte.  
  
 C\# : Comment faire pour interroger le service de manière asynchrone :  
  
```c#  
using Microsoft.VisualStudio.Shell;   
using Microsoft.VisualStudio.Shell.Interop;   
  
IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;   
IMyTestService testService = await ayncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;  
```