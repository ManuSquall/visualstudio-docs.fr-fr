---
title: 'Procédure : Obtenir un Service | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 46ef86b8cde506aad3e00aa6b5dbc6470c0087de
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60052179"
---
# <a name="how-to-get-a-service"></a>Procédure : Obtenir un service
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous devez souvent obtenir des services Visual Studio pour accéder aux différentes fonctionnalités. En règle générale, un service de Visual Studio fournit une ou plusieurs interfaces que vous pouvez utiliser. Vous pouvez obtenir la plupart des services à partir d’un VSPackage.  
  
 N’importe quel package Visual Studio qui dérive de <xref:Microsoft.VisualStudio.Shell.Package> et qui a été correctement dans le site peut poser pour n’importe quel service global. Étant donné que la classe de Package implémente <xref:System.IServiceProvider>, un VSPackage qui dérive de Package est également un fournisseur de services.  
  
 Lorsque Visual Studio charge un <xref:Microsoft.VisualStudio.Shell.Package>, il passe un <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> de l’objet à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> méthode pendant l’initialisation. Il s’agit *positionnement* le VSPackage. La classe de Package encapsule ce fournisseur de services et fournit le <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> méthode pour obtenir des services.  
  
## <a name="getting-a-service-from-an-initialized-vspackage"></a>Obtention d’un service à partir d’un VSPackage initialisé  
  
1. Chaque extension de Visual Studio commence par un projet de déploiement VSIX qui contiendra les ressources de l’extension. Créer un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projet VSIX nommé `GetServiceExtension`. Vous pouvez trouver le modèle de projet VSIX dans le **nouveau projet** boîte de dialogue sous **Visual c# / extensibilité**.  
  
2. Ajoutez maintenant un modèle d’élément de commande personnalisée nommé **GetServiceCommand**. Dans le **ajouter un nouvel élément** boîte de dialogue, accédez à **Visual c# / extensibilité** et sélectionnez **commande personnalisée**. Dans le **nom** en bas de la fenêtre, modifiez le nom de fichier de commande pour **GetServiceCommand.cs**. Pour plus d’informations sur la création d’une commande personnalisée, [création d’une Extension avec une commande de Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
3. Dans GetServiceCommand.cs, supprimez le corps de la méthode MenuItemCommand et ajoutez le code suivant :  
  
    ```csharp  
    IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (activityLog == null) return;  
    System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
  
    ```  
  
     Ce code obtient un service SVsActivityLog et caste vers une <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interface, ce qui peut être utilisé pour écrire dans le journal d’activité. Pour voir un exemple, consultez [Comment : Utiliser le journal d’activité](../extensibility/how-to-use-the-activity-log.md).  
  
4. Générez le projet et commencez le débogage. L’instance expérimentale s’affiche.  
  
5. Dans le menu Outils de l’instance expérimentale, recherchez le **GetServiceCommand appeler** bouton. Lorsque vous cliquez sur ce bouton, vous devez voir une boîte de message indiquant que **trouvé le service de journal d’activité.**  
  
## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Obtention d’un service à partir d’un conteneur de contrôle ou de la fenêtre outil  
 Parfois, vous devrez peut-être obtenir un service à partir d’une fenêtre outil ou le contrôle conteneur qui n’a pas été installé, ou bien a été installé avec un fournisseur de services qui ne sait pas sur le service que vous souhaitez. Par exemple, vous souhaiterez peut-être écrire dans le journal d’activité à partir d’un contrôle.  
  
 La méthode statique <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> méthode s’appuie sur un fournisseur de services de mise en cache qui est initialisé à la première fois qu’un VSPackage dérivé <xref:Microsoft.VisualStudio.Shell.Package> est placé.  
  
 Étant donné que le constructeur de VSPackage est appelé avant le VSPackage est dans le site, les services globaux sont généralement pas disponibles dans le constructeur de VSPackage. Voir [Guide pratique pour Dépanner les Services](../extensibility/how-to-troubleshoot-services.md) pour une solution de contournement.  
  
 Voici un exemple de la façon d’obtenir un service dans une fenêtre outil ou un autre élément non VSPackage.  
  
```csharp  
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
## <a name="getting-a-service-from-the-dte-object"></a>Obtention d’un service à partir de l’objet DTE  
 Vous pouvez également obtenir des services à partir de <xref:EnvDTE.DTEClass> objet. Toutefois, vous devez obtenir l’objet DTE en tant que service à partir d’un VSPackage ou en appelant la méthode statique <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> (méthode).  
  
 Implémente l’objet DTE <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>, que vous pouvez utiliser pour interroger un service à l’aide de <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>.  
  
 Voici comment obtenir un service à partir de l’objet DTE.  
  
```csharp  
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
 [Guide pratique pour Fournir un Service](../extensibility/how-to-provide-a-service.md)   
 [À l’aide et fourniture de Services](../extensibility/using-and-providing-services.md)   
 [Éléments fondamentaux du service](../extensibility/internals/service-essentials.md)
