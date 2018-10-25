---
title: 'Comment : fournir un Service asynchrone Visual Studio | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c022f1a039aacee3599dd680adfa92a9404b34b8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915670"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Comment : fournir un service de Visual Studio asynchrone
Si vous souhaitez obtenir un service sans bloquer le thread d’interface utilisateur, vous devez créer un service asynchrone et charger le package sur un thread d’arrière-plan. Pour cela, vous pouvez utiliser un <xref:Microsoft.VisualStudio.Shell.AsyncPackage> au lieu d’un <xref:Microsoft.VisualStudio.Shell.Package>, ajoutez le service avec les méthodes asynchrones spéciale du package asynchrone.
  
 Pour plus d’informations sur la fourniture des services Visual Studio synchrones, consultez [Comment : fournir un service](../extensibility/how-to-provide-a-service.md).  
  
## <a name="implement-an-asynchronous-service"></a>Implémenter un service asynchrone  
  
1.  Créez un projet VSIX (**fichier** > **New** > **projet** > **Visual C#**  >  **Extensibilité** > **projet VSIX**). Nommez le projet **TestAsync**.  
  
2.  Ajouter un VSPackage au projet. Sélectionnez le nœud de projet dans le **l’Explorateur de solutions** et cliquez sur **ajouter** > **un nouvel élément** > **éléments Visual c#**  >  **Extensibilité** > **Package Visual Studio**. Nommez ce fichier *TestAsyncPackage.cs*.  
  
3.  Dans *TestAsyncPackage.cs*, modifier le package d’hériter de `AsyncPackage` plutôt que `Package`:  
  
    ```csharp  
    public sealed class TestAsyncPackage : AsyncPackage  
    ```  
  
4.  Pour implémenter un service, vous devez créer trois types :  
  
    -   Une interface qui identifie le service. La plupart de ces interfaces sont vides, autrement dit, ils n’ont aucune méthode car ils sont utilisés uniquement pour l’interrogation du service.
  
    -   Interface qui décrit l’interface de service. Cette interface inclut les méthodes à implémenter.  
  
    -   Une classe qui implémente le service et l’interface de service.  
  
5.  L’exemple suivant montre une implémentation très basique des trois types. Le constructeur de la classe de service doit définir le fournisseur de services. Dans cet exemple, nous allons simplement ajouter le service dans le fichier de code de package.  
  
6.  Ajoutez le code suivant à l’aide des instructions pour le fichier de package :  
  
    ```csharp  
    using System.Threading;  
    using System.Threading.Tasks;  
    using System.Runtime.CompilerServices;  
    using System.IO;
    using Microsoft.VisualStudio.Threading;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```  
  
7.  Voici l’implémentation de service asynchrone. Notez que vous devez définir le fournisseur de service asynchrone plutôt que le fournisseur de service synchrones dans le constructeur :  
  
    ```csharp
    public class TextWriterService : STextWriterService, ITextWriterService  
    {  
        private IAsyncServiceProvider asyncServiceProvider;  
        
        public TextWriterService(IAsyncServiceProvider provider)  
        {
            // constructor should only be used for simple initialization
            // any usage of Visual Studio service, expensive background operations should happen in the
            // asynchronous InitializeAsync method for best performance
            asyncServiceProvider = provider;  
        }
        
        public async Task InitializeAsync(CancellationToken cancellationToken)
        {
            await TaskScheduler.Default;
            // do background operations that involve IO or other async methods

            await this.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);               
            // query Visual Studio services on main thread unless they are documented as free threaded explicitly.
            // The reason for this is the final cast to service interface (such as IVsShell) may involve COM operations to add/release references.

            IVsShell vsShell = this.asyncServiceProvider.GetServiceAsync(typeof(SVsShell)) as IVsShell;
            // use Visual Studio services to continue initialization
        }
        
        public async Task WriteLineAsync(string path, string line)  
        {  
            StreamWriter writer = new StreamWriter(path);  
            await writer.WriteLineAsync(line);  
            writer.Close();  
        }  
    }  

    public interface STextWriterService  
    {  
    }  
    
    public interface ITextWriterService   
    {  
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);  
    }  
    ```  
  
## <a name="register-a-service"></a>Inscrire un service  
 Pour inscrire un service, ajoutez le <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> au package qui fournit le service. Différente de l’inscription d’un service synchrone, vous devez vous assurer que package et le service prend en charge asynchrone du chargement :
  
- Vous devez ajouter le **AllowsBackgroundLoading = true** champ la <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> pour vous assurer de package peut être initialisé de façon asynchrone pour plus d’informations sur la PackageRegistrationAttribute, consultez [inscrire et Annuler l’inscription de VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
- Vous devez ajouter le **IsAsyncQueryable = true** champ la <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> pour garantir l’instance de service peut être initialisée de façon asynchrone.

  Voici un exemple d’un `AsyncPackage` avec une inscription de service asynchrone :
  
```csharp  
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]  
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]   
[Guid(TestAsyncPackage.PackageGuidString)]  
public sealed class TestAsyncPackage : AsyncPackage  
{. . . }  
```  
  
## <a name="add-a-service"></a>Ajouter un service  
  
1.  Dans *TestAsyncPackage.cs*, supprimez le `Initialize()` (méthode) et que vous remplacez le `InitializeAsync()` (méthode). Ajoutez le service et ajoutez une méthode de rappel pour créer les services. Voici un exemple de l’initialiseur asynchrone Ajout d’un service :  
  
    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await base.InitializeAsync(cancellationToken, progress);  
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }  
  
    ```  
  
2.  Ajoutez une référence à *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll*.  
  
3.  Implémentez la méthode de rappel comme une méthode asynchrone qui crée et retourne le service.  
  
    ```csharp  
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)  
    {  
        TextWriterService service = new TextWriterService(this);  
        await service.InitializeAsync(cancellationToken);
        return service;
    }  
  
    ```  
  
## <a name="use-a-service"></a>Utiliser un service  
 Vous pouvez maintenant obtenir le service et utiliser ses méthodes.  
  
1.  Nous allons le montrer dans l’initialiseur, mais vous pouvez obtenir le service n’importe où que vous souhaitez utiliser le service.  
  
    ```csharp  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await base.InitializeAsync(cancellationToken, progress);  
        this.AddService(typeof(STextWriterService), CreateTextWriterService);  
  
        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await textService.WriteLineAsync(<userpath>), "this is a test");  
    }  
  
    ```  
  
     N’oubliez pas de modifier  *\<userpath >* à un nom de fichier et le chemin d’accès qui a du sens sur votre ordinateur !  
  
2.  Générez et exécutez le code. Lorsque l’instance expérimentale de Visual Studio s’affiche, ouvrez une solution. Cela entraîne le `AsyncPackage` pour charger automatiquement. Lors de l’initialiseur est exécuté, vous devez trouver un fichier dans l’emplacement spécifié.  
  
## <a name="use-an-asynchronous-service-in-a-command-handler"></a>Utiliser un service asynchrone dans un gestionnaire de commandes  
 Voici un exemple montrant comment utiliser un service asynchrone dans une commande de menu. Vous pouvez utiliser la procédure présentée ici pour utiliser le service dans d’autres méthodes non asynchrone.  
  
1.  Ajouter une commande de menu à votre projet. (Dans le **l’Explorateur de solutions**, sélectionnez le nœud du projet, avec le bouton droit, puis sélectionnez **ajouter** > **un nouvel élément**  >   **Extensibilité** > **commande personnalisée**.) Nommez le fichier de commandes *TestAsyncCommand.cs*.  
  
2.  Le modèle de commande personnalisée ajoute de nouveau la `Initialize()` méthode à la *TestAsyncPackage.cs* fichier afin d’initialiser la commande. Dans le `Initialize()` (méthode), copiez la ligne qui initialise la commande. Le résultat doit être semblable à ce qui suit :  
  
    ```csharp
    TestAsyncCommand.Initialize(this);  
    ```  
  
     Déplacer cette ligne dans le `InitializeAsync()` méthode dans le *AsyncPackageForService.cs* fichier. Dans la mesure où il s’agit une initialisation asynchrone, vous devez basculer vers le thread principal avant l’initialisation de la commande à l’aide <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>. Il doit maintenant ressembler à ceci :  
  
    ```csharp  
  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await base.InitializeAsync(cancellationToken, progress);  
        this.AddService(typeof(STextWriterService), CreateTextWriterService);  

        ITextWriterService textService =   
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await textService.WriteLineAsync((<userpath>, "this is a test");  
  
        await this.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);  
        TestAsyncCommand.Initialize(this);
    }  
  
    ```  
  
3.  Supprimer le `Initialize()` (méthode).  
  
4.  Dans le *TestAsyncCommand.cs* de fichiers, recherchez le `MenuItemCallback()` (méthode). Supprimer le corps de la méthode.  
  
5.  Ajoutez une instruction using :  
  
    ```csharp 
    using System.IO;  
    ```  
  
6.  Ajoutez une méthode asynchrone nommée `UseTextWriterAsync()`, qui obtient le service et utilise ses méthodes :  
  
    ```csharp  
    private async System.Threading.Tasks.Task UseTextWriterAsync()  
    {  
        // Query text writer service asynchronously to avoid a blocking call.
        ITextWriterService textService =   
           await AsyncServiceProvider.GlobalProvider.GetServiceAsync(typeof(STextWriterService))  
              as ITextWriterService;  

        // don't forget to change <userpath> to a local path  
        await textService.WriteLineAsync((<userpath>),"this is a test");  
       }  
  
    ```  
  
7.  Appelez cette méthode à partir de la `MenuItemCallback()` méthode :  
  
    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        UseTextWriterAsync();  
    }  
  
    ```  
  
8.  Générez la solution et commencez le débogage. Lorsque l’instance expérimentale de Visual Studio s’affiche, accédez à la **outils** menu et recherchez le **TestAsyncCommand appeler** élément de menu. Lorsque vous cliquez dessus, le TextWriterService écrit dans le fichier spécifié. (Vous n’avez pas besoin d’ouvrir une solution, car l’appel de la commande entraîne également le package à charger.)  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisez et fournir des services](../extensibility/using-and-providing-services.md)
