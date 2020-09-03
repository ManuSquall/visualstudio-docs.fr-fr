---
title: 'Comment : obtenir un service | Microsoft Docs'
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a401103112096a1089b59ba3733d19480f93e891
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905833"
---
# <a name="how-to-get-a-service"></a>Comment : obtenir un service

Vous devez souvent faire en sorte que les services Visual Studio accèdent à différentes fonctionnalités. En général, un service Visual Studio fournit une ou plusieurs interfaces que vous pouvez utiliser. Vous pouvez obtenir la plupart des services à partir d’un VSPackage.

Tout VSPackage qui dérive de <xref:Microsoft.VisualStudio.Shell.Package> et qui a été correctement mis en place peut demander un service global. Étant donné que la `Package` classe implémente <xref:System.IServiceProvider> , tout VSPackage qui dérive de `Package` est également un fournisseur de services.

Lorsque Visual Studio charge un <xref:Microsoft.VisualStudio.Shell.Package> , il passe un <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> objet à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> méthode pendant l’initialisation. C’est ce *que l’on* appelle le VSPackage. La `Package` classe encapsule ce fournisseur de services et fournit la <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> méthode pour obtenir des services.

## <a name="getting-a-service-from-an-initialized-vspackage"></a>Obtention d’un service à partir d’un VSPackage initialisé

1. Chaque extension Visual Studio commence par un projet de déploiement VSIX, qui contient les composants d’extension. Créez un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projet VSIX nommé `GetServiceExtension` . Vous pouvez trouver le modèle de projet VSIX dans la boîte de dialogue **nouveau projet** en recherchant « VSIX ».

2. Ajoutez maintenant un modèle d’élément de commande personnalisé nommé **GetServiceCommand**. Dans la boîte de dialogue **Ajouter un nouvel élément** , accédez à extensibilité **Visual C#**  >  **Extensibility** et sélectionnez **commande personnalisée**. Dans le champ **nom** en bas de la fenêtre, remplacez le nom du fichier de commandes par *GetServiceCommand.cs*. Pour plus d’informations sur la création d’une commande personnalisée, [créez une extension à l’aide d’une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md)

3. Dans *GetServiceCommand.cs*, supprimez le corps de la `MenuItemCommand` méthode et ajoutez le code suivant :

   ```csharp
   IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
   if (activityLog == null) return;
   System.Windows.Forms.MessageBox.Show("Found the activity log service.");

   ```

    Ce code obtient un service SVsActivityLog et le convertit en une <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interface, qui peut être utilisée pour écrire dans le journal d’activité. Pour obtenir un exemple, consultez [procédure : utiliser le journal d’activité](../extensibility/how-to-use-the-activity-log.md).

4. Générez le projet et commencez le débogage. L’instance expérimentale s’affiche.

5. Dans le menu **Outils** de l’instance expérimentale, recherchez le bouton **appeler GetServiceCommand** . Lorsque vous cliquez sur ce bouton, une boîte de message s’affiche, indiquant que **le service Journal d’activité a été trouvé.**

## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Obtention d’un service à partir d’une fenêtre outil ou d’un conteneur de contrôle

Parfois, vous devrez peut-être obtenir un service à partir d’une fenêtre outil ou d’un conteneur de contrôle qui n’a pas été sur site, ou avec un fournisseur de services qui ne connaît pas le service souhaité. Par exemple, vous souhaiterez peut-être écrire dans le journal d’activité à partir d’un contrôle.

La <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> méthode statique s’appuie sur un fournisseur de services mis en cache qui est initialisé la première fois qu’un VSPackage dérivé de est placé dans un <xref:Microsoft.VisualStudio.Shell.Package> site.

Étant donné que le constructeur VSPackage est appelé avant le décompte du VSPackage, les services globaux ne sont généralement pas disponibles dans le constructeur VSPackage. Consultez [Comment : résoudre les problèmes liés aux services](../extensibility/how-to-troubleshoot-services.md) pour une solution de contournement.

Voici un exemple de la façon d’obtenir un service dans une fenêtre outil ou un autre élément non VSPackage.

```csharp
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="getting-a-service-from-the-dte-object"></a>Obtention d’un service à partir de l’objet DTE

Vous pouvez également récupérer des services à partir d’un <xref:EnvDTE.DTEClass> objet. Toutefois, vous devez obtenir l’objet DTE en tant que service à partir d’un VSPackage ou en appelant la <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> méthode statique.

L’objet DTE implémente <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> , que vous pouvez utiliser pour interroger un service à l’aide de <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> .

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

- [Comment : fournir un service](../extensibility/how-to-provide-a-service.md)
- [Utilisez et fournissez des services](../extensibility/using-and-providing-services.md)
- [Notions de service Essentials](../extensibility/internals/service-essentials.md)
