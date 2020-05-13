---
title: 'Comment : Obtenir un service Microsoft Docs'
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e8e6f20eaa08d6bb7aaa0cc9e560856daa5959e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710957"
---
# <a name="how-to-get-a-service"></a>Comment : Obtenir un service

Vous avez souvent besoin d’obtenir des services Visual Studio pour accéder à différentes fonctionnalités. En général, un service Visual Studio fournit une ou plusieurs interfaces que vous pouvez utiliser. Vous pouvez obtenir la plupart des services à partir d’un VSPackage.

Tout VSPackage qui <xref:Microsoft.VisualStudio.Shell.Package> dérive et qui a été correctement situé peut demander n’importe quel service global. Parce `Package` que la <xref:System.IServiceProvider>classe met en œuvre , tout VSPackage qui dérive de `Package` est également un fournisseur de services.

Lorsque Visual Studio <xref:Microsoft.VisualStudio.Shell.Package>charge un, <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> passe un objet à la méthode lors de l’initialisation. C’est ce *qu’on appelle l’emplacement* de la VSPackage. La `Package` classe enveloppe ce fournisseur <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> de services et fournit la méthode pour obtenir des services.

## <a name="getting-a-service-from-an-initialized-vspackage"></a>Obtenir un service à partir d’un VSPackage initialisé

1. Chaque extension Visual Studio commence par un projet de déploiement VSIX, qui contiendra les actifs d’extension. Créer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] un projet `GetServiceExtension`VSIX nommé . Vous pouvez trouver le modèle de projet VSIX dans le dialogue **du nouveau projet** en recherchant "vsix".

2. Maintenant, ajoutez un modèle d’élément de commande personnalisé nommé **GetServiceCommand**. Dans le dialogue **Add New Item,** rendez-vous sur **Visual C’Extensibility** > **Extensibility** et **sélectionnez Custom Command**. Dans le champ **nom** au bas de la fenêtre, changer le nom du fichier de commande pour *GetServiceCommand.cs*. Pour plus d’informations sur la façon de créer une commande personnalisée, [créez une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md)

3. Dans *GetServiceCommand.cs*, retirez le `MenuItemCommand` corps de la méthode et ajoutez le code suivant :

   ```csharp
   IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
   if (activityLog == null) return;
   System.Windows.Forms.MessageBox.Show("Found the activity log service.");

   ```

    Ce code obtient un service SVsActivityLog <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> et le jette à une interface, qui peut être utilisé pour écrire au journal d’activité. Par exemple, voir [Comment : Utilisez le journal d’activité](../extensibility/how-to-use-the-activity-log.md).

4. Générez le projet et commencez le débogage. L’instance expérimentale apparaît.

5. Sur le menu **Tools** de l’instance expérimentale, trouvez le bouton **Invoke GetServiceCommand.** Lorsque vous cliquez sur ce bouton, vous devriez voir une boîte de message qui indique **trouvé le service de journal d’activité.**

## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Obtenir un service à partir d’une fenêtre d’outil ou d’un conteneur de contrôle

Parfois, vous pouvez avoir besoin d’obtenir un service à partir d’une fenêtre d’outils ou un conteneur de contrôle qui n’a pas été situé, ou bien a été situé avec un fournisseur de services qui ne sait pas sur le service que vous voulez. Par exemple, vous pouvez écrire au journal d’activité à partir d’un contrôle.

La <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> méthode statique repose sur un fournisseur de services mis en cache <xref:Microsoft.VisualStudio.Shell.Package> qui est initialisé la première fois que tout VSPackage dérivé de est situé.

Étant donné que le constructeur VSPackage est appelé avant le site du VSPackage, les services mondiaux ne sont généralement pas disponibles à l’intérieur du constructeur VSPackage. Voir [comment : Services de dépannage](../extensibility/how-to-troubleshoot-services.md) pour une solution de contournement.

Voici un exemple de la façon d’obtenir un service dans une fenêtre d’outils ou tout autre élément non-VSPackage.

```csharp
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="getting-a-service-from-the-dte-object"></a>Obtenir un service à partir de l’objet DTE

Vous pouvez également <xref:EnvDTE.DTEClass> obtenir des services à partir d’un objet. Cependant, vous devez obtenir l’objet DTE comme un service <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> à partir d’un VSPackage ou en appelant la méthode statique.

L’objet DTE <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>implémente , que vous pouvez <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>utiliser pour interroger pour un service en utilisant .

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

- [Comment : Fournir un service](../extensibility/how-to-provide-a-service.md)
- [Utiliser et fournir des services](../extensibility/using-and-providing-services.md)
- [Essentiels de service](../extensibility/internals/service-essentials.md)
