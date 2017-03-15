---
title: "Comment : obtenir un Service | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f66c7e1f01c8d8eb69c6718314890bfb02cccc17
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-get-a-service"></a>Comment : obtenir un Service
Vous devez souvent obtenir des services de Visual Studio pour accéder aux différentes fonctionnalités. En général, un service de Visual Studio fournit une ou plusieurs interfaces que vous pouvez utiliser. Vous pouvez obtenir la plupart des services à partir d’un VSPackage.  
  
 Un VSPackage qui dérive de <xref:Microsoft.VisualStudio.Shell.Package>et qui a été correctement placé peut demander à n’importe quel service global.</xref:Microsoft.VisualStudio.Shell.Package> Étant donné que la classe de Package implémente <xref:System.IServiceProvider>, un VSPackage qui dérive de Package est également un fournisseur de services.</xref:System.IServiceProvider>  
  
 Lorsque Visual Studio charge un <xref:Microsoft.VisualStudio.Shell.Package>, il passe un <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>de l’objet à le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>méthode lors de l’initialisation.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> </xref:Microsoft.VisualStudio.Shell.Package> Il s’agit *positionnement* le VSPackage. La classe de Package encapsule ce fournisseur de services et fournit la <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>méthode pour obtenir des services.</xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>  
  
## <a name="getting-a-service-from-an-initialized-vspackage"></a>Obtention d’un service à partir d’un VSPackage initialisé  
  
1.  Chaque extension de Visual Studio démarre avec un projet de déploiement VSIX qui contient les composants d’extension. Créer un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projet VSIX nommé `GetServiceExtension`. Vous pouvez trouver le modèle de projet VSIX dans le **nouveau projet** boîte de dialogue sous **Visual C# / extensibilité**.  
  
2.  Ajoutez maintenant un modèle d’élément commande personnalisée nommé **GetServiceCommand**. Dans le **ajouter un nouvel élément** boîte de dialogue, accédez à **Visual C# / extensibilité** et sélectionnez **personnalisée**. Dans le **nom** en bas de la fenêtre, modifiez le nom du fichier de commandes **GetServiceCommand.cs**. Pour plus d’informations sur la création d’une commande personnalisée, [création d’une Extension avec une commande de Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
3.  Dans GetServiceCommand.cs, supprimez le corps de la méthode MenuItemCommand et ajoutez le code suivant :  
  
    ```c#  
    IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (activityLog == null) return;  
    System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
  
    ```  
  
     Ce code obtient un service SVsActivityLog et il effectue un cast en une <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>interface, qui peut être utilisé pour écrire dans le journal d’activité.</xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> Pour obtenir un exemple, consultez [Comment : utiliser le journal d’activité](../extensibility/how-to-use-the-activity-log.md).  
  
4.  Générez le projet et commencez le débogage. L’instance expérimentale s’affiche.  
  
5.  Dans le menu Outils de l’instance expérimentale, trouver la **GetServiceCommand appeler** bouton. Lorsque vous cliquez sur ce bouton, vous devez voir une boîte de message indiquant que **trouvé le service de journal d’activité.**  
  
## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Obtention d’un service à partir d’un conteneur de contrôle ou de la fenêtre outil  
 Parfois, vous devrez peut-être obtenir un service à partir d’une fenêtre outil ou le contrôle conteneur qui n’a pas été installé, ou bien a été installé avec un fournisseur de services qui ne sait pas sur le service. Par exemple, vous souhaiterez écrire dans le journal d’activité à partir d’un contrôle.  
  
 La méthode statique <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>méthode s’appuie sur un fournisseur de services de mise en cache qui est initialisé la première fois un VSPackage dérivé <xref:Microsoft.VisualStudio.Shell.Package>dépend.</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>  
  
 Étant donné que le constructeur VSPackage est appelé avant que le VSPackage est placé, services globaux sont généralement pas disponibles dans le constructeur du package VS. Consultez la page [Comment : résoudre les problèmes des Services](../extensibility/how-to-troubleshoot-services.md) pour une solution de contournement.  
  
 Voici un exemple de la façon d’obtenir un service dans une fenêtre outil ou un autre élément non VSPackage.  
  
```c#  
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
## <a name="getting-a-service-from-the-dte-object"></a>Obtention d’un service à partir de l’objet DTE  
 Vous pouvez également obtenir des services de <xref:EnvDTE.DTEClass>objet.</xref:EnvDTE.DTEClass> Toutefois, vous devez obtenir l’objet DTE en tant que service à partir d’un VSPackage ou en appelant la méthode statique <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>méthode.</xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>  
  
 Implémente l’objet DTE <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>, que vous pouvez utiliser pour interroger un service à l’aide <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>.</xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>  
  
 Voici comment obtenir un service à partir de l’objet DTE.  
  
```c#  
// Start with the DTE object, for example:   
// using EnvDTE;  
// DTE dte = (DTE)GetService(typeof(DTE));  
  
ServiceProvider sp = new ServiceProvider((Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);  
if (sp != null)  
{  
    IVsActivityLog log = sp.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log != null)  
    {   
        System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : fournir un Service](../extensibility/how-to-provide-a-service.md)   
 [À l’aide et fournir des Services](../extensibility/using-and-providing-services.md)   
 [Service Essentials](../extensibility/internals/service-essentials.md)
