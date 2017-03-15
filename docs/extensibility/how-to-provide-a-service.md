---
title: "Comment : fournir un Service | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "services fournissant"
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# Comment : fournir un Service
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un VSPackage peut fournir des services qui utilisent des autres packages VS. Pour fournir un service, un VSPackage doit inscrire le service avec Visual Studio et ajoutez le service.  
  
 La <xref:Microsoft.VisualStudio.Shell.Package> classe implémente à la fois <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> et <xref:System.ComponentModel.Design.IServiceContainer>.<xref:System.ComponentModel.Design.IServiceContainer> contient des méthodes de rappel qui fournissent des services à la demande.  
  
 Pour plus d’informations sur les services, consultez [Service Essentials](../extensibility/internals/service-essentials.md) .  
  
> [!NOTE]
>  Lorsqu’un VSPackage est sur le point d’être déchargé, Visual Studio attend jusqu'à ce que toutes les demandes de services qui fournit un VSPackage qui ont été remis. Il n’autorise pas les nouvelles demandes de ces services. Vous ne devez pas appeler explicitement la <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> méthode révoquer un service lors du déchargement.  
  
#### Implémentation d’un service  
  
1.  Créez un projet VSIX \(**fichier \/ nouveau \/ projet \/ Visual C\# \/ Extensiblity \/ projet VSIX**\).  
  
2.  Ajoutez un VSPackage au projet. Sélectionnez le nœud de projet dans le **l’Explorateur de solutions** et cliquez sur **Ajouter \/ nouvel élément \/ éléments Visual c\# \/ extensibilité \/ Package Visual Studio**.  
  
3.  Pour implémenter un service, vous devez créer trois types :  
  
    -   Interface qui décrit le service. La plupart de ces interfaces sont vides, autrement dit, elles n’ont aucuns méthodes.  
  
    -   Interface qui décrit l’interface de service. Cette interface comprend les méthodes à mettre en oeuvre.  
  
    -   Une classe qui implémente le service et l’interface de service.  
  
     L’exemple suivant montre une implémentation très basique des trois types. Le constructeur de la classe de service doit définir le fournisseur de services.  
  
    ```c#  
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
  
### L’inscription d’un service  
  
1.  Pour enregistrer un service, ajoutez le <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> pour le VSPackage qui fournit le service. Voici un exemple :  
  
    ```c#  
    [ProvideService(typeof(SMyService))]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [Guid(VSPackage1.PackageGuidString)]  
    public sealed class VSPackage1 : Package  
    {. . . }  
    ```  
  
     Cet attribut enregistre `SMyService` avec Visual Studio.  
  
    > [!NOTE]
    >  Pour inscrire un service qui remplace un autre service portant le même nom, utilisez le <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>. Notez que seul le remplacement d’un service est autorisé.  
  
### Ajout d’un Service  
  
1.  1.	Dans l’initialiseur VSPackage, ajoutez le service et ajoutez une méthode de rappel pour créer les services. Voici la modification à apporter à la <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> méthode :  
  
    ```c#  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2.  Implémentez la méthode de rappel qui doit créer et retourner le service ou null s’il ne peut pas être créé.  
  
    ```  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new SMyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    >  Visual Studio peut refuser une demande de fournir un service. Il le fait si un autre package VS fournit déjà le service.  
  
3.  Vous pouvez désormais accéder à un service et utiliser ses méthodes. Nous allons le montrer dans l’initialiseur, mais vous pouvez obtenir le service n’importe où que vous souhaitez utiliser le service.  
  
    ```c#  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
  
        MyService myService = (MyService) this.GetService(typeof(SMyService));  
        myService.Hello();  
        string helloString = myService.myString;  
  
        base.Initialize();  
    }  
    ```  
  
     La valeur de `helloString` doit être « Hello ».  
  
## Voir aussi  
 [Comment : obtenir un Service](../Topic/How%20to:%20Get%20a%20Service.md)   
 [À l'aide et fournir des Services](../extensibility/using-and-providing-services.md)   
 [Service Essentials](../extensibility/internals/service-essentials.md)