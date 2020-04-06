---
title: 'Comment : Fournir un service de studio visuel asynchrone (en anglais seulement) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65362e465beec5465903083beca069104a48166b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710765"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Comment : Fournir un service de studio visuel asynchrone
Si vous souhaitez obtenir un service sans bloquer le thread d’interface utilisateur, vous devez créer un service asynchrone et charger le paquet sur un thread d’arrière-plan. À cette fin, <xref:Microsoft.VisualStudio.Shell.AsyncPackage> vous pouvez <xref:Microsoft.VisualStudio.Shell.Package>utiliser un plutôt que un , et ajouter le service avec les méthodes asynchrones spéciales du paquet asynchrone.

 Pour plus d’informations sur la fourniture de services synchrones Visual Studio, voir [Comment : Fournir un service](../extensibility/how-to-provide-a-service.md).

## <a name="implement-an-asynchronous-service"></a>Mettre en œuvre un service asynchrone

1. Créer un projet VSIX **(File** > **New** > **Project** > **Visual C '** > **Extensiblity** > **VSIX Project**). Nommez le projet **TestAsync**.

2. Ajoutez un VSPackage au projet. Sélectionnez le nœud de projet dans la **Solution Explorer** et cliquez sur **Ajouter un** > **nouvel article** > **Visual CMD Items** > **Extensibility** > Visual Studio**Package**. Nommez ce fichier *TestAsyncPackage.cs*.

3. En *TestAsyncPackage.cs*, changer le paquet `AsyncPackage` pour `Package`hériter de plutôt que:

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. Pour implémenter un service, vous devez créer trois types :

    - Une interface qui identifie le service. Beaucoup de ces interfaces sont vides, c’est-à-dire qu’elles n’ont pas de méthodes car elles ne sont utilisées que pour interroger le service.

    - Une interface qui décrit l’interface de service. Cette interface comprend les méthodes à implémenter.

    - Une classe qui implémente à la fois le service et l’interface de service.

5. L’exemple suivant montre une mise en œuvre très basique des trois types. Le constructeur de la classe de service doit définir le fournisseur de services. Dans cet exemple, nous allons simplement ajouter le service au fichier de code de paquet.

6. Ajouter les directives suivantes au fichier du paquet :

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    using Microsoft.VisualStudio.Threading;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```

7. Voici la mise en œuvre de service asynchrone. Notez que vous devez définir le fournisseur de services asynchrone plutôt que le fournisseur de services synchrones dans le constructeur:

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

            await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
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

## <a name="register-a-service"></a>Enregistrer un service
 Pour enregistrer un service, ajoutez le <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> forfait qui fournit le service. Différent de l’enregistrement d’un service synchrone, vous devez vous assurer à la fois forfait et support de service chargement async:

- Vous devez ajouter le **permisbackgroundLoading** <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> - véritable champ pour s’assurer que le paquet peut être initialisé asynchronement Pour plus d’informations sur le PackageRegistrationAttribute, voir [Registre et désinscrire VSPackages](../extensibility/registering-and-unregistering-vspackages.md).

- Vous devez ajouter le champ **IsAsyncQueryable - vrai** pour s’assurer que l’instance <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> de service peut être paradé asynchrone.

  Voici un exemple `AsyncPackage` d’inscription à un service asynchrone :

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="add-a-service"></a>Ajouter un service

1. Dans *TestAsyncPackage.cs,* supprimez `Initialize()` la méthode et `InitializeAsync()` remplacez la méthode. Ajoutez le service et ajoutez une méthode de rappel pour créer les services. Voici un exemple de l’initialisateur asynchrone ajoutant un service:

    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }

    ```
    Pour rendre ce service visible en dehors de ce forfait, définissez la valeur du drapeau de promotion pour que le dernier paramètre soit *vrai* :`this.AddService(typeof(STextWriterService), CreateTextWriterService, true);`

2. Ajouter une référence à *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll*.

3. Implémentez la méthode de rappel comme méthode asynchrone qui crée et renvoie le service.

    ```csharp
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        TextWriterService service = new TextWriterService(this);
        await service.InitializeAsync(cancellationToken);
        return service;
    }

    ```

## <a name="use-a-service"></a>Utiliser un service
 Maintenant, vous pouvez obtenir le service et utiliser ses méthodes.

1. Nous allons le montrer dans l’initialisation, mais vous pouvez obtenir le service n’importe où vous voulez utiliser le service.

    ```csharp
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;
        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");
    }

    ```

     N’oubliez pas `userpath` de passer à un nom de fichier et le chemin qui a du sens sur votre machine!

2. Construisez et exécutez le code. Lorsque l’instance expérimentale de Visual Studio apparaît, ouvrez une solution. Cela provoque `AsyncPackage` le chargement automatique. Lorsque l’initialisateur s’exécute, vous devez trouver un fichier à l’endroit où vous avez spécifié.

## <a name="use-an-asynchronous-service-in-a-command-handler"></a>Utiliser un service asynchrone dans un gestionnaire de commande
 Voici un exemple de la façon d’utiliser un service asynchrone dans une commande de menu. Vous pouvez utiliser la procédure montrée ici pour utiliser le service dans d’autres méthodes non asynchrones.

1. Ajoutez une commande de menu à votre projet. (Dans le **Solution Explorer**, sélectionnez le nœud de projet, clic droit, et **sélectionnez Ajouter** > **de nouveaux éléments** > **Extensibility** > **Custom Command**.) Nommez le fichier de commande *TestAsyncCommand.cs*.

2. Le modèle de commande `Initialize()` personnalisé réin ajoute la méthode au fichier *TestAsyncPackage.cs* afin d’initialiser la commande. Dans `Initialize()` la méthode, copiez la ligne qui initialise la commande. Il doit se présenter comme suit :

    ```csharp
    TestAsyncCommand.Initialize(this);
    ```

     Déplacez cette `InitializeAsync()` ligne vers la méthode dans le *fichier AsyncPackageForService.cs.* Comme il s’agit d’une initialisation asynchrone, vous devez passer <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>au fil principal avant de para initialiser la commande en utilisant . Elle doit maintenant ressembler à ceci :

    ```csharp

    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService =
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;
        
        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");

        await this.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
        TestAsyncCommand.Initialize(this);
    }

    ```

3. Supprimer `Initialize()` la méthode.

4. Dans le *fichier TestAsyncCommand.cs,* `MenuItemCallback()` trouvez la méthode. Supprimer le corps de la méthode.

5. Ajouter une directive à l’aide :

    ```csharp
    using System.IO;
    ```

6. Ajoutez une méthode asynchrone nommée `UseTextWriterAsync()`, qui obtient le service et utilise ses méthodes:

    ```csharp
    private async System.Threading.Tasks.Task UseTextWriterAsync()
    {
        // Query text writer service asynchronously to avoid a blocking call.
        ITextWriterService textService =
           await AsyncServiceProvider.GlobalProvider.GetServiceAsync(typeof(STextWriterService))
              as ITextWriterService;

        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");
       }

    ```

7. Appelez cette méthode `MenuItemCallback()` à partir de la méthode:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        UseTextWriterAsync();
    }

    ```

8. Générez la solution et commencez le débogage. Lorsque l’exemple expérimental de Visual Studio apparaît, allez au menu **Tools** et recherchez l’élément de menu **Invoke TestAsyncCommand.** Lorsque vous cliquez dessus, le TextWriterService écrit au fichier que vous avez spécifié. (Vous n’avez pas besoin d’ouvrir une solution, car invoquer la commande provoque également le paquet à charger.)

## <a name="see-also"></a>Voir aussi
- [Utiliser et fournir des services](../extensibility/using-and-providing-services.md)
