---
title: 'Comment : fournir un service | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30bfdd49d871919503be767ea930b3d5f2f0fd95
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905766"
---
# <a name="how-to-provide-a-service"></a>Comment : fournir un service
Un VSPackage peut fournir des services que d’autres VSPackages peuvent utiliser. Pour fournir un service, un VSPackage doit inscrire le service auprès de Visual Studio et ajouter le service.

 La <xref:Microsoft.VisualStudio.Shell.Package> classe implémente à la fois <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> et <xref:System.ComponentModel.Design.IServiceContainer> . <xref:System.ComponentModel.Design.IServiceContainer>contient des méthodes de rappel qui fournissent des services à la demande.

 Pour plus d’informations sur les services, consultez [service Essentials](../extensibility/internals/service-essentials.md) .

> [!NOTE]
> Quand un VSPackage est sur le déchargé, Visual Studio attend que toutes les demandes de services fournies par un VSPackage aient été remises. Elle n’autorise pas les nouvelles demandes pour ces services. Vous ne devez pas appeler explicitement la <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> méthode pour révoquer un service lors du déchargement.

## <a name="implement-a-service"></a>Implémenter un service

1. Créez un projet VSIX (**fichier**  >  **nouveau**  >  **projet**  >  **extension Visual C#** projet  >  **Extensibility**  >  **VSIX**).

2. Ajoutez un VSPackage au projet. Sélectionnez le nœud du projet dans le **Explorateur de solutions** puis cliquez sur **Ajouter**  >  **un nouvel élément**  >  **Visual C#** extensibilité des éléments Visual C#  >  **Extensibility**  >  **package Visual Studio**.

3. Pour implémenter un service, vous devez créer trois types :

   - Interface qui décrit le service. La plupart de ces interfaces sont vides, c’est-à-dire qu’elles n’ont aucune méthode.

   - Interface qui décrit l’interface de service. Cette interface comprend les méthodes à implémenter.

   - Classe qui implémente à la fois le service et l’interface de service.

     L’exemple suivant illustre une implémentation de base des trois types. Le constructeur de la classe de service doit définir le fournisseur de services.

   ```csharp
   public class MyService : SMyService, IMyService
   {
       private Microsoft.VisualStudio.OLE.Interop.IServiceProvider serviceProvider;
       private string myString;
       public MyService(Microsoft.VisualStudio.OLE.Interop.IServiceProvider sp)
       {
           Trace.WriteLine(
                  "Constructing a new instance of MyService");
           serviceProvider = sp;
       }
       public void Hello()
       {
           myString = "hello";
       }
       public string Goodbye()
       {
          return "goodbye";
       }
   }
   public interface SMyService
   {
   }
   public interface IMyService
   {
       void Hello();
       string Goodbye();
   }

   ```

### <a name="register-a-service"></a>Inscrire un service

1. Pour inscrire un service, ajoutez le <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> au VSPackage qui fournit le service. Voici un exemple :

    ```csharp
    [ProvideService(typeof(SMyService))]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [Guid(VSPackage1.PackageGuidString)]
    public sealed class VSPackage1 : Package
    {. . . }
    ```

     Cet attribut s’inscrit `SMyService` auprès de Visual Studio.

    > [!NOTE]
    > Pour inscrire un service qui remplace un autre service portant le même nom, utilisez le <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> . Notez qu’un seul remplacement d’un service est autorisé.

### <a name="add-a-service"></a>Ajouter un service

1. Dans l’initialiseur VSPackage, ajoutez le service et ajoutez une méthode de rappel pour créer les services. Voici la modification à apporter à la <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> méthode :

    ```csharp
    protected override void Initialize()
    {
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);

        ((IServiceContainer)this).AddService(typeof(SMyService), callback);
    . . .
    }
    ```

2. Implémentez la méthode de rappel, qui doit créer et retourner le service, ou la valeur null si elle ne peut pas être créée.

    ```csharp
    private object CreateService(IServiceContainer container, Type serviceType)
    {
        if (typeof(SMyService) == serviceType)
            return new MyService(this);
        return null;
    }
    ```

    > [!NOTE]
    > Visual Studio peut rejeter une demande pour fournir un service. Il le fait si un autre VSPackage fournit déjà le service.

3. Vous pouvez désormais accéder au service et utiliser ses méthodes. L’exemple ci-dessous montre comment utiliser le service dans l’initialiseur, mais vous pouvez obtenir le service partout où vous souhaitez utiliser le service.

    ```csharp
    protected override void Initialize()
    {
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);

        ((IServiceContainer)this).AddService(typeof(SMyService), callback);

        MyService myService = (MyService) this.GetService(typeof(SMyService));
        myService.Hello();
        string helloString = myService.Goodbye();

        base.Initialize();
    }
    ```

     La valeur de `helloString` doit être « Hello ».

## <a name="see-also"></a>Voir aussi
- [Comment : obtenir un service](../extensibility/how-to-get-a-service.md)
- [Utilisez et fournissez des services](../extensibility/using-and-providing-services.md)
- [Notions de service Essentials](../extensibility/internals/service-essentials.md)
