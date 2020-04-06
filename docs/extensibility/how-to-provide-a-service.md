---
title: 'Comment : Fournir un service Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60cae5e8048a0234114e1f9e7d97728e26ee40f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710774"
---
# <a name="how-to-provide-a-service"></a>Comment : Fournir un service
Un VSPackage peut fournir des services que d’autres VSPackages peuvent utiliser. Pour fournir un service, un VSPackage doit enregistrer le service auprès de Visual Studio et ajouter le service.

 La <xref:Microsoft.VisualStudio.Shell.Package> classe met <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> <xref:System.ComponentModel.Design.IServiceContainer>en œuvre à la fois et . <xref:System.ComponentModel.Design.IServiceContainer>contient des méthodes de rappel qui fournissent des services à la demande.

 Pour plus d’informations sur les services, voir [Services essentiels](../extensibility/internals/service-essentials.md) .

> [!NOTE]
> Lorsqu’un VSPackage est sur le point d’être déchargé, Visual Studio attend que toutes les demandes de services qu’un VSPackage fournit aient été livrées. Il n’autorise pas les nouvelles demandes de ces services. Vous ne devez <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> pas explicitement appeler la méthode pour révoquer un service lors du déchargement.

## <a name="implement-a-service"></a>Mettre en œuvre un service

1. Créer un projet VSIX **(File** > **New** > **Project** > **Visual C '** > **Extensibility** > **VSIX Project**).

2. Ajoutez un VSPackage au projet. Sélectionnez le nœud de projet dans la **Solution Explorer** et cliquez sur **Ajouter un** > **nouvel article** > **Visual CMD Items** > **Extensibility** > Visual Studio**Package**.

3. Pour implémenter un service, vous devez créer trois types :

   - Une interface qui décrit le service. Beaucoup de ces interfaces sont vides, c’est-à-dire qu’elles n’ont pas de méthodes.

   - Une interface qui décrit l’interface de service. Cette interface comprend les méthodes à implémenter.

   - Une classe qui implémente à la fois le service et l’interface de service.

     L’exemple suivant montre une mise en œuvre de base des trois types. Le constructeur de la classe de service doit définir le fournisseur de services.

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

### <a name="register-a-service"></a>Enregistrer un service

1. Pour enregistrer un service, ajoutez le <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> VSPackage qui fournit le service. Voici un exemple :

    ```csharp
    [ProvideService(typeof(SMyService))]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [Guid(VSPackage1.PackageGuidString)]
    public sealed class VSPackage1 : Package
    {. . . }
    ```

     Cet attribut `SMyService` s’inscrit auprès de Visual Studio.

    > [!NOTE]
    > Pour enregistrer un service qui remplace un autre <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>service du même nom, utilisez le . Notez qu’un seul remplacement d’un service est autorisé.

### <a name="add-a-service"></a>Ajouter un service

1. Dans l’initialisateur VSPackage, ajoutez le service et ajoutez une méthode de rappel pour créer les services. Voici le changement à <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> apporter à la méthode :

    ```csharp
    protected override void Initialize()
    {
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);

        ((IServiceContainer)this).AddService(typeof(SMyService), callback);
    . . .
    }
    ```

2. Implémentez la méthode de rappel, qui doit créer et retourner le service, ou nulle si elle ne peut pas être créée.

    ```csharp
    private object CreateService(IServiceContainer container, Type serviceType)
    {
        if (typeof(SMyService) == serviceType)
            return new MyService(this);
        return null;
    }
    ```

    > [!NOTE]
    > Visual Studio peut rejeter une demande de fournir un service. Il le fait si un autre VSPackage fournit déjà le service.

3. Maintenant, vous pouvez obtenir le service et utiliser ses méthodes. L’exemple ci-dessous montre l’utilisation du service dans l’initialisateur, mais vous pouvez obtenir le service n’importe où vous voulez utiliser le service.

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

     La valeur `helloString` de devrait être "Bonjour".

## <a name="see-also"></a>Voir aussi
- [Comment : Obtenir un service](../extensibility/how-to-get-a-service.md)
- [Utiliser et fournir des services](../extensibility/using-and-providing-services.md)
- [Essentiels de service](../extensibility/internals/service-essentials.md)
