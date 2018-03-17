---
title: "Comment : fournir un Service asynchrone Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4aac446e9ed71b6e6b0c86ea64068af7a6184767
ms.sourcegitcommit: 236c250bb97abdab99d00c6525d106fc0035d7d0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2018
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Comment : fournir un Service asynchrone Visual Studio
Si vous souhaitez obtenir un service sans bloquer le thread d’interface utilisateur, vous créez un service asynchrone et charger le package sur un thread d’arrière-plan. Pour cela, vous pouvez utiliser un <xref:Microsoft.VisualStudio.Shell.AsyncPackage> plutôt qu’un <xref:Microsoft.VisualStudio.Shell.Package>, ajoutez le service avec des méthodes asynchrones du package asynchrone spéciales.
  
 Pour plus d’informations sur la fourniture des services Visual Studio synchrones, consultez [Comment : fournir un Service](../extensibility/how-to-provide-a-service.md).  
  
## <a name="implementing-an-asynchronous-service"></a>Implémentation d’un Service asynchrone  
  
1.  Créez un projet VSIX (**fichier > Nouveau > projet > c# > Extensiblity > projet VSIX**). Nommez le projet **TestAsync**.  
  
2.  Ajouter un VSPackage au projet. Sélectionnez le nœud de projet dans le **l’Explorateur de solutions** et cliquez sur **Ajouter > nouvel élément > éléments Visual c# > extensibilité > Package Visual Studio**. Nommez ce fichier **TestAsyncPackage.cs**.  
  
3.  Dans TestAsyncPackage.cs, modifiez le package d’hériter de AsyncPackage au lieu de Package :  
  
    ```csharp  
    public sealed class TestAsyncPackage : AsyncPackage  
    ```  
  
4.  Pour implémenter un service, vous devez créer trois types :  
  
    -   Interface qui décrit le service. La plupart de ces interfaces sont vides, autrement dit, elles n’ont aucuns méthodes.  
  
    -   Interface qui décrit l’interface de service. Cette interface comprend les méthodes à implémenter.  
  
    -   Une classe qui implémente le service et l’interface de service.  
  
5.  L’exemple suivant montre une implémentation de base des trois types. Le constructeur de la classe de service doit définir le fournisseur de services. Dans cet exemple, nous allons simplement ajouter le service dans le fichier de code du package.  
  
6.  Ajoutez le code suivant à l’aide des instructions pour le fichier de package :  
  
    ```csharp  
    using System.Threading;  
    using System.Threading.Tasks;  
    using System.Runtime.CompilerServices;  
    using System.IO;  
    ```  
  
7.  Voici l’implémentation de service asynchrone. Notez que vous devez définir le fournisseur de service asynchrone plutôt que le fournisseur de service synchrones dans le constructeur :  
  
    ```csharp
    public class TextWriterService : STextWriterService, ITextWriterService  
    {  
        private Microsoft.VisualStudio.Shell.IAsyncServiceProvider serviceProvider;  
        public TextWriterService(Microsoft.VisualStudio.Shell.IAsyncServiceProvider provider)  
        {  
            serviceProvider = provider;  
        }  
        public async System.Threading.Tasks.Task WriteLineAsync(string path, string line)  
        {  
            StreamWriter writer = new StreamWriter(path);  
            await writer.WriteLineAsync(line);  
            writer.Close();  
        }  
        public TaskAwaiter GetAwaiter()  
        {  
            return new TaskAwaiter();  
        }  
    }  
    public interface STextWriterService  
    {  
    }  
    public interface ITextWriterService   
    {  
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);  
        TaskAwaiter GetAwaiter();  
    }  
    ```  
  
## <a name="registering-a-service"></a>L’inscription d’un Service  
 Pour inscrire un service, ajoutez le <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> au package qui fournit le service. Il existe deux différences lors de l’inscription d’un service synchrone :  
  
-   Si vous êtes le chargement automatique du package, vous devez ajouter le <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> valeur BackgroundLoad à l’attribut. Pour plus d’informations sur les VSPackages chargement automatique, consultez [le chargement des VSPackages](../extensibility/loading-vspackages.md).  
  
-   Vous devez ajouter le **AllowsBackgroundLoading = true** au champ la <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>. Pour plus d’informations sur la PackageRegistrationAttribute, consultez [inscription et annulation de l’inscription de VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
 Voici un exemple d’un AsyncPackage avec une inscription de service asynchrone :
  
```csharp  
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]  
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]   
[Guid(TestAsyncPackage.PackageGuidString)]  
public sealed class TestAsyncPackage : AsyncPackage  
{. . . }  
```  
  
## <a name="adding-a-service"></a>Ajout d’un service  
  
1.  Dans TestAsyncPackage.cs, supprimez le `Initialize()` (méthode) et que vous remplacez le `InitializeAsync()` (méthode). Ajoutez le service et ajoutez une méthode de rappel pour créer les services. Voici un exemple de l’initialiseur asynchrone Ajout d’un service :  
  
    ```csharp
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
2.  Ajoutez une référence à Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll.  
  
3.  Implémentez la méthode de rappel comme une méthode asynchrone qui crée et retourne le service.  
  
    ```csharp  
    public async System.Threading.Tasks.Task<object> CreateService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)  
    {  
        STextWriterService service = null;  
        await System.Threading.Tasks.Task.Run(() => {  
                    service = new TextWriterService(this);  
             });  
  
        return service;  
    }  
  
    ```  
  
## <a name="using-a-service"></a>À l’aide d’un Service  
 Vous pouvez désormais obtenir le service et utiliser ses méthodes.  
  
1.  Nous allons montrer ce dans l’initialiseur, mais vous pouvez obtenir le service n’importe où que vous souhaitez utiliser le service.  
  
    ```csharp  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await textService.WriteLineAsync(<userpath>), "this is a test");  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
     N’oubliez pas de modifier  *\<userpath >* à un nom de fichier et le chemin d’accès logique sur votre ordinateur.  
  
2.  Générez et exécutez le code. Lorsque l’instance expérimentale de Visual Studio s’affiche, ouvrez une solution. Cela entraîne le AsyncPackage à autoload. Lors de l’initialiseur a été exécuté, vous devez rechercher un fichier dans l’emplacement spécifié.  
  
## <a name="using-an-asynchronous-service-in-a-command-handler"></a>À l’aide d’un Service asynchrone dans un gestionnaire de commandes  
 Voici un exemple montrant comment utiliser un service asynchrone dans une commande de menu. Vous pouvez utiliser la procédure ci-après pour utiliser le service dans d’autres méthodes non asynchrone.  
  
1.  Ajouter une commande de menu à votre projet. (Dans le **l’Explorateur de solutions**, sélectionnez le nœud de projet, avec le bouton droit, puis sélectionnez **Ajouter / nouvel élément / extensibilité personnalisée commande**.) Nommez le fichier de commandes **TestAsyncCommand.cs.**  
  
2.  Le modèle de commande personnalisée ajoute de nouveau la `Initialize()` méthode dans le fichier TestAsyncPackage.cs afin d’initialiser la commande. Dans la méthode Initialize(), copiez la ligne qui initialise la commande. Le résultat doit être semblable à ce qui suit :  
  
    ```csharp
    TestAsyncCommand.Initialize(this);  
    ```  
  
     Déplacer cette ligne de la `InitializeAsync()` méthode dans le fichier AsyncPackageForService.cs. Dans la mesure où il s’agit de l’initialisation asynchrone, vous devez basculer vers le thread principal avant d’initialiser l’à l’aide de la commande <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>. Il doit maintenant ressembler à ceci :  
  
    ```csharp  
  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        TestAsyncCommand.Initialize(this);    
  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        ITextWriterService textService =   
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await textService.WriteLineAsync((<userpath>, "this is a test");  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
3.  Supprimer le `Initialize()` (méthode).  
  
4.  Dans le fichier TestAsyncCommand.cs, recherchez le `MenuItemCallback()` (méthode). Supprimer le corps de la méthode.  
  
5.  Ajoutez une instruction using :  
  
    ```csharp 
    using System.IO;  
    ```  
  
6.  Ajouter une méthode asynchrone nommée `GetAsyncService()`, qui obtient le service et utilise ses méthodes :  
  
    ```csharp  
    private async System.Threading.Tasks.Task GetAsyncService()  
    {  
        ITextWriterService textService =   
           this.ServiceProvider.GetService(typeof(STextWriterService))  
              as ITextWriterService;  
        // don't forget to change <userpath> to a local path  
        await textService.WriteLineAsync((<userpath>),"this is a test");  
       }  
  
    ```  
  
7.  Appelez cette méthode à partir de la `MenuItemCallback()` méthode :  
  
    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        GetAsyncService();  
    }  
  
    ```  
  
8.  Générez la solution et commencez le débogage. Lorsque l’instance expérimentale de Visual Studio s’affiche, accédez à la **outils** menu, puis recherchez le **TestAsyncCommand d’appeler** élément de menu. Lorsque vous cliquez dessus, le TextWriterService écrit dans le fichier spécifié. (Vous n’avez pas besoin d’ouvrir une solution, car l’appel de la commande entraîne également le package à charger.)  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation et fourniture de services](../extensibility/using-and-providing-services.md)