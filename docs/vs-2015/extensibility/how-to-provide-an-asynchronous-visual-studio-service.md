---
title: 'Procédure : Fournir un Service asynchrone | Microsoft Docs'
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3a0bae91d5525de54c967c09e8c4ef130cb85cab
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58950778"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Procédure : Fournir un service Visual Studio asynchrone
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si vous souhaitez obtenir un service sans bloquer le thread d’interface utilisateur, vous devez créer un service asynchrone et charger le package sur un thread d’arrière-plan. Pour cela, vous pouvez utiliser un <xref:Microsoft.VisualStudio.Shell.AsyncPackage> au lieu d’un <xref:Microsoft.VisualStudio.Shell.Package>, ajoutez le service avec des méthodes asynchrones du package asynchrone spéciales

 Pour plus d’informations sur la fourniture des services Visual Studio synchrones, consultez [Comment : Fournir un Service](../extensibility/how-to-provide-a-service.md).

## <a name="implementing-an-asynchronous-service"></a>Implémentation d’un Service asynchrone

1.  Créez un projet VSIX (**fichier / nouveau / projet / Visual C# / extensibilité / projet VSIX**). Nommez le projet **TestAsync**.

2.  Ajouter un VSPackage au projet. Sélectionnez le nœud de projet dans le **l’Explorateur de solutions** et cliquez sur **Ajouter / nouvel élément / éléments Visual C# / extensibilité / Package Visual Studio**. Nommez ce fichier **TestAsyncPackage.cs**.

3.  Dans TestAsyncPackage.cs, modifiez le package d’hériter de AsyncPackage plutôt que de Package :

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4.  Pour implémenter un service, vous devez créer trois types :

    -   Une interface qui décrit le service. La plupart de ces interfaces sont vides, autrement dit, elles n’ont aucuns méthodes.

    -   Interface qui décrit l’interface de service. Cette interface inclut les méthodes à implémenter.

    -   Une classe qui implémente le service et l’interface de service.

5.  L’exemple suivant montre une implémentation très basique des trois types. Le constructeur de la classe de service doit définir le fournisseur de services. Dans cet exemple, nous allons simplement ajouter le service dans le fichier de code de package.

6.  Ajoutez le code suivant à l’aide des instructions pour le fichier de package :

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    ```

7.  Voici l’implémentation de service asynchrone. Notez que vous devez définir le fournisseur de service asynchrone plutôt que le fournisseur de service synchrones dans le constructeur :

    ```
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

- Si vous êtes le chargement automatique du package, vous devez ajouter le <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> valeur BackgroundLoad à l’attribut. Pour plus d’informations sur les VSPackages chargement automatique, consultez [le chargement de VSPackages](../extensibility/loading-vspackages.md).

- Vous devez ajouter le **AllowsBackgroundLoading = true** champ la <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>. Pour plus d’informations sur la PackageRegistrationAttribute, consultez [inscription et annulation de l’inscription de VSPackages](../extensibility/registering-and-unregistering-vspackages.md).

  Voici un exemple d’un AsyncPackage avec une inscription de service asynchrone ::

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

    ```
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
 Vous pouvez maintenant obtenir le service et utiliser ses méthodes.

1.  Nous allons le montrer dans l’initialiseur, mais vous pouvez obtenir le service n’importe où que vous souhaitez utiliser le service.

    ```csharp
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(STextWriterService), CreateService);

        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;

        await writer.WriteLineAsync(<userpath>), "this is a test");

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

     N’oubliez pas de modifier  *\<userpath >* à un nom de fichier et le chemin d’accès qui a du sens sur votre ordinateur !

2.  Générez et exécutez le code. Lorsque l’instance expérimentale de Visual Studio s’affiche, ouvrez une solution. Cela entraîne le AsyncPackage pour charger automatiquement. Lors de l’initialiseur est exécuté, vous devez trouver un fichier dans l’emplacement spécifié.

## <a name="using-an-asynchronous-service-in-a-command-handler"></a>À l’aide d’un Service asynchrone dans un gestionnaire de commandes
 Voici un exemple montrant comment utiliser un service asynchrone dans une commande de menu. Vous pouvez utiliser la procédure présentée ici pour utiliser le service dans d’autres méthodes non asynchrone.

1.  Ajouter une commande de menu à votre projet. (Dans le **l’Explorateur de solutions**, sélectionnez le nœud du projet, avec le bouton droit, puis sélectionnez **Ajouter / nouvel élément / extensibilité / commande personnalisée**.) Nommez le fichier de commandes **TestAsyncCommand.cs.**

2.  Le modèle de commande personnalisée ajoute de nouveau la `Initialize()` méthode au fichier TestAsyncPackage.cs afin d’initialiser la commande. Dans la méthode Initialize(), copiez la ligne qui initialise la commande. Le résultat doit être semblable à ce qui suit :

    ```
    TestAsyncCommand.Initialize(this);
    ```

     Déplacer cette ligne dans le `InitializeAsync()` méthode dans le fichier AsyncPackageForService.cs. Dans la mesure où il s’agit une initialisation asynchrone, vous devez basculer vers le thread principal avant l’initialisation de la commande à l’aide <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>. Il doit maintenant ressembler à ceci :

    ```csharp

    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        TestAsyncCommand.Initialize(this);

        this.AddService(typeof(STextWriterService), CreateService);

        ITextWriterService textService =
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;

        await writer.WriteLineAsync((<userpath>, "this is a test");

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

3.  Supprimer le `Initialize()` (méthode).

4.  Dans le fichier TestAsyncCommand.cs, recherchez le `MenuItemCallback()` (méthode). Supprimer le corps de la méthode.

5.  Ajoutez une instruction using :

    ```
    using System.IO;
    ```

6.  Ajoutez une méthode asynchrone nommée `GetAsyncService()`, qui obtient le service et utilise ses méthodes :

    ```csharp
    private async System.Threading.Tasks.Task GetAsyncService()
    {
        ITextWriterService textService =
           this.ServiceProvider.GetService(typeof(STextWriterService))
              as ITextWriterService;
        // don’t forget to change <userpath> to a local path
        await writer.WriteLineAsync((<userpath>),"this is a test");
       }

    ```

7.  Appelez cette méthode à partir de la `MenuItemCallback()` méthode :

    ```
    private void MenuItemCallback(object sender, EventArgs e)
    {
        GetAsyncService();
    }

    ```

8.  Générez la solution et commencez le débogage. Lorsque l’instance expérimentale de Visual Studio s’affiche, accédez à la **outils** menu et recherchez le **TestAsyncCommand appeler** élément de menu. Lorsque vous cliquez dessus, le TextWriterService écrit dans le fichier spécifié. (Vous n’avez pas besoin d’ouvrir une solution, car l’appel de la commande entraîne également le package à charger.)

## <a name="see-also"></a>Voir aussi
 [Utilisation et fourniture de services](../extensibility/using-and-providing-services.md)
