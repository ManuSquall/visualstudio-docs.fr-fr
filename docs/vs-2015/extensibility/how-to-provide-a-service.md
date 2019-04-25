---
title: 'Procédure : Fournir un Service | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ba007a8084355445f0404a9b0f7a2c1cee7b2005
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60108181"
---
# <a name="how-to-provide-a-service"></a>Procédure : Fournir un service
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un VSPackage peut fournir des services qui les VSPackages autres peuvent utiliser. Pour fournir un service, un VSPackage doit inscrire le service avec Visual Studio et ajoutez le service.  
  
 Le <xref:Microsoft.VisualStudio.Shell.Package> classe implémente à la fois <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> et <xref:System.ComponentModel.Design.IServiceContainer>. <xref:System.ComponentModel.Design.IServiceContainer> contient des méthodes de rappel qui fournissent des services à la demande.  
  
 Pour plus d’informations sur les services, consultez [éléments fondamentaux du Service](../extensibility/internals/service-essentials.md) .  
  
> [!NOTE]
>  Quand un VSPackage va être déchargé, Visual Studio attend jusqu'à ce que toutes les demandes pour les services fournis par un VSPackage ont été livrés. Il n’autorise pas les nouvelles demandes de ces services. Vous ne devez pas appeler explicitement la <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> méthode révoquer un service lors du déchargement.  
  
#### <a name="implementing-a-service"></a>Implémentation d’un service  
  
1. Créez un projet VSIX (**fichier / nouveau / projet / Visual c# / extensibilité / projet VSIX**).  
  
2. Ajouter un VSPackage au projet. Sélectionnez le nœud de projet dans le **l’Explorateur de solutions** et cliquez sur **Ajouter / nouvel élément / éléments Visual c# / extensibilité / Package Visual Studio**.  
  
3. Pour implémenter un service, vous devez créer trois types :  
  
   - Une interface qui décrit le service. La plupart de ces interfaces sont vides, autrement dit, elles n’ont aucuns méthodes.  
  
   - Interface qui décrit l’interface de service. Cette interface inclut les méthodes à implémenter.  
  
   - Une classe qui implémente le service et l’interface de service.  
  
     L’exemple suivant montre une implémentation très basique des trois types. Le constructeur de la classe de service doit définir le fournisseur de services.  
  
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
  
1. Pour inscrire un service, ajoutez le <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> au VSPackage qui fournit le service. Voici un exemple :  
  
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
  
### <a name="adding-a-service"></a>Ajout d’un Service  
  
1. 1.  Dans l’initialiseur de VSPackage, ajoutez le service et une méthode de rappel pour créer les services. Voici la modification à apporter au <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> méthode :  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2. Implémentez la méthode de rappel qui doit créer et retourner le service ou null s’il ne peut pas être créé.  
  
    ```  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new SMyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    >  Visual Studio peut rejeter une demande de fournir un service. Il le fait si un autre package Visual Studio fournit déjà le service.  
  
3. Vous pouvez maintenant obtenir le service et utiliser ses méthodes. Nous allons le montrer dans l’initialiseur, mais vous pouvez obtenir le service n’importe où que vous souhaitez utiliser le service.  
  
    ```csharp  
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
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour Bénéficiez d’un Service](../extensibility/how-to-get-a-service.md)   
 [À l’aide et fourniture de Services](../extensibility/using-and-providing-services.md)   
 [Éléments fondamentaux du service](../extensibility/internals/service-essentials.md)
