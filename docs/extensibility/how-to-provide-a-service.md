---
title: 'Comment : fournir un Service | Microsoft Docs'
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
ms.openlocfilehash: 2408eace3ecea447c9b49ff17c729e3f4661b5d6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942547"
---
# <a name="how-to-provide-a-service"></a>Comment : fournir un service
Un VSPackage peut fournir des services qui les VSPackages autres peuvent utiliser. Pour fournir un service, un VSPackage doit inscrire le service avec Visual Studio et ajoutez le service.  
  
 Le <xref:Microsoft.VisualStudio.Shell.Package> classe implémente à la fois <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> et <xref:System.ComponentModel.Design.IServiceContainer>. <xref:System.ComponentModel.Design.IServiceContainer> contient des méthodes de rappel qui fournissent des services à la demande.  
  
 Pour plus d’informations sur les services, consultez [Service essentials](../extensibility/internals/service-essentials.md) .  
  
> [!NOTE]
>  Quand un VSPackage va être déchargé, Visual Studio attend jusqu'à ce que toutes les demandes pour les services fournis par un VSPackage ont été livrés. Il n’autorise pas les nouvelles demandes de ces services. Vous ne devez pas appeler explicitement la <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> méthode révoquer un service lors du déchargement.  
  
## <a name="implement-a-service"></a>Implémenter un service  
  
1. Créez un projet VSIX (**fichier** > **New** > **projet** > **Visual C#**  >  **Extensibilité** > **projet VSIX**).  
  
2. Ajouter un VSPackage au projet. Sélectionnez le nœud de projet dans le **l’Explorateur de solutions** et cliquez sur **ajouter** > **un nouvel élément** > **éléments Visual c#**  >  **Extensibilité** > **Package Visual Studio**.  
  
3. Pour implémenter un service, vous devez créer trois types :  
  
   - Une interface qui décrit le service. La plupart de ces interfaces sont vides, autrement dit, elles n’ont aucuns méthodes.  
  
   - Interface qui décrit l’interface de service. Cette interface inclut les méthodes à implémenter.  
  
   - Une classe qui implémente le service et l’interface de service.  
  
     L’exemple suivant montre une implémentation de base des trois types. Le constructeur de la classe de service doit définir le fournisseur de services.  
  
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
  
1.  Pour inscrire un service, ajoutez le <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> au VSPackage qui fournit le service. Voici un exemple :  
  
    ```csharp  
    [ProvideService(typeof(SMyService))]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [Guid(VSPackage1.PackageGuidString)]  
    public sealed class VSPackage1 : Package  
    {. . . }  
    ```  
  
     Inscrit cet attribut `SMyService` avec Visual Studio.  
  
    > [!NOTE]
    >  Pour inscrire un service qui remplace un autre service portant le même nom, utilisez le <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>. Remarque qui substituent qu’une seule d’un service est autorisée.  
  
### <a name="add-a-service"></a>Ajouter un service  
  
1.  Dans l’initialiseur de VSPackage, ajoutez le service et une méthode de rappel pour créer les services. Voici la modification à apporter au <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> méthode :  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2.  Implémentez la méthode de rappel qui doit créer et retourner le service ou null s’il ne peut pas être créé.  
  
    ```csharp  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new MyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    >  Visual Studio peut rejeter une demande de fournir un service. Il le fait si un autre package Visual Studio fournit déjà le service.  
  
3.  Vous pouvez maintenant obtenir le service et utiliser ses méthodes. L’exemple ci-dessous montre l’utilisation du service dans l’initialiseur, mais vous pouvez obtenir le service n’importe où que vous souhaitez utiliser le service.  
  
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
 [Comment : obtenir un service](../extensibility/how-to-get-a-service.md)   
 [Utilisez et fournir des services](../extensibility/using-and-providing-services.md)   
 [Éléments fondamentaux du service](../extensibility/internals/service-essentials.md)
