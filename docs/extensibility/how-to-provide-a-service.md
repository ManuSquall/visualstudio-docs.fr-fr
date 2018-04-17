---
title: 'Comment : fournir un Service | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 70d16085bc6cbc7f01a991a1eca731b8abed2b0f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-provide-a-service"></a>Comment : fournir un Service
Un VSPackage peut fournir des services qui permet d’autres packages VS. Pour fournir un service, un VSPackage doit inscrire le service avec Visual Studio et ajoutez le service.  
  
 Le <xref:Microsoft.VisualStudio.Shell.Package> classe implémente à la fois <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> et <xref:System.ComponentModel.Design.IServiceContainer>. <xref:System.ComponentModel.Design.IServiceContainer> contient des méthodes de rappel qui fournissent des services à la demande.  
  
 Pour plus d’informations sur les services, consultez [Service Essentials](../extensibility/internals/service-essentials.md) .  
  
> [!NOTE]
>  Quand un VSPackage va être déchargé, Visual Studio attend jusqu'à ce que toutes les demandes pour les services fournis par un VSPackage ont été remis. Il n’autorise pas les nouvelles demandes de ces services. Vous ne devez pas appeler explicitement la <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> méthode révoquer un service lors du déchargement.  
  
#### <a name="implementing-a-service"></a>Implémentation d’un service  
  
1.  Créez un projet VSIX (**fichier > Nouveau > projet > c# > extensibilité > projet VSIX**).  
  
2.  Ajouter un VSPackage au projet. Sélectionnez le nœud de projet dans le **l’Explorateur de solutions** et cliquez sur **Ajouter > nouvel élément > éléments Visual c# > extensibilité > Package Visual Studio**.  
  
3.  Pour implémenter un service, vous devez créer trois types :  
  
    -   Interface qui décrit le service. La plupart de ces interfaces sont vides, autrement dit, elles n’ont aucuns méthodes.  
  
    -   Interface qui décrit l’interface de service. Cette interface comprend les méthodes à implémenter.  
  
    -   Une classe qui implémente le service et l’interface de service.  
  
     L’exemple suivant montre une implémentation des trois types de base. Le constructeur de la classe de service doit définir le fournisseur de services.  
  
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
  
### <a name="registering-a-service"></a>L’inscription d’un service  
  
1.  Pour inscrire un service, ajoutez le <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> pour le VSPackage qui fournit le service. Voici un exemple :  
  
    ```csharp  
    [ProvideService(typeof(SMyService))]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [Guid(VSPackage1.PackageGuidString)]  
    public sealed class VSPackage1 : Package  
    {. . . }  
    ```  
  
     Cet attribut enregistre `SMyService` avec Visual Studio.  
  
    > [!NOTE]
    >  Pour inscrire un service qui remplace un autre service portant le même nom, utilisez le <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>. Notez que seul remplacement d’un service est autorisé.  
  
### <a name="adding-a-service"></a>Ajout d’un Service  
  
1.  Dans l’initialiseur de VSPackage, ajoutez le service et ajouter une méthode de rappel pour créer les services. Voici la modification à apporter à la <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> méthode :  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2.  Implémentez la méthode de rappel, qui doit créer et retourner le service ou null s’il ne peut pas être créé.  
  
    ```csharp  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new MyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    >  Visual Studio peut rejeter une demande de fournir un service. Il le fait si un autre VSPackage fournit déjà le service.  
  
3.  Vous pouvez désormais obtenir le service et utiliser ses méthodes. L’exemple ci-dessous illustre l’utilisation du service dans l’initialiseur, mais vous pouvez obtenir le service n’importe où que vous souhaitez utiliser le service.  
  
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
 [Comment : obtenir un Service](../extensibility/how-to-get-a-service.md)   
 [À l’aide et fournir des Services](../extensibility/using-and-providing-services.md)   
 [Éléments fondamentaux du service](../extensibility/internals/service-essentials.md)
