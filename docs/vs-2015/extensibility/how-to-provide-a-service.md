---
title: 'Comment : fournir un service | Microsoft Docs'
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
ms.openlocfilehash: 565a8a91797c826b6419dc5a8488d7d3baf9cddc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839649"
---
# <a name="how-to-provide-a-service"></a>Guide pratique pour fournir un service
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un VSPackage peut fournir des services que d’autres VSPackages peuvent utiliser. Pour fournir un service, un VSPackage doit inscrire le service auprès de Visual Studio et ajouter le service.  
  
 La <xref:Microsoft.VisualStudio.Shell.Package> classe implémente à la fois <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> et <xref:System.ComponentModel.Design.IServiceContainer> . <xref:System.ComponentModel.Design.IServiceContainer> contient des méthodes de rappel qui fournissent des services à la demande.  
  
 Pour plus d’informations sur les services, consultez [service Essentials](../extensibility/internals/service-essentials.md) .  
  
> [!NOTE]
> Quand un VSPackage est sur le déchargé, Visual Studio attend que toutes les demandes de services fournies par un VSPackage aient été remises. Elle n’autorise pas les nouvelles demandes pour ces services. Vous ne devez pas appeler explicitement la <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> méthode pour révoquer un service lors du déchargement.  
  
#### <a name="implementing-a-service"></a>Implémentation d’un service  
  
1. Créez un projet VSIX (**fichier/nouveau/projet/Visual C#/extensibilité/projet VSIX**).  
  
2. Ajoutez un VSPackage au projet. Sélectionnez le nœud du projet dans le **Explorateur de solutions** puis cliquez sur **Ajouter/nouvel élément/éléments Visual C#/extensibilité/package Visual Studio**.  
  
3. Pour implémenter un service, vous devez créer trois types :  
  
   - Interface qui décrit le service. La plupart de ces interfaces sont vides, c’est-à-dire qu’elles n’ont aucune méthode.  
  
   - Interface qui décrit l’interface de service. Cette interface comprend les méthodes à implémenter.  
  
   - Classe qui implémente à la fois le service et l’interface de service.  
  
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
  
### <a name="registering-a-service"></a>Inscription d’un service  
  
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
  
### <a name="adding-a-service"></a>Ajout d’un service  
  
1. 1.  Dans l’initialiseur VSPackage, ajoutez le service et ajoutez une méthode de rappel pour créer les services. Voici la modification à apporter à la <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> méthode :  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2. Implémentez la méthode de rappel, qui doit créer et retourner le service, ou la valeur null si elle ne peut pas être créée.  
  
    ```  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new SMyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    > Visual Studio peut rejeter une demande pour fournir un service. Il le fait si un autre VSPackage fournit déjà le service.  
  
3. Vous pouvez désormais accéder au service et utiliser ses méthodes. Nous allons l’afficher dans l’initialiseur, mais vous pouvez obtenir le service partout où vous souhaitez utiliser le service.  
  
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
 [Comment : obtenir un service](../extensibility/how-to-get-a-service.md)   
 [Utilisation et fourniture de services](../extensibility/using-and-providing-services.md)   
 [Éléments fondamentaux du service](../extensibility/internals/service-essentials.md)
