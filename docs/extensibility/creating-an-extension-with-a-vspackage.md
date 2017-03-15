---
title: "Cr&#233;ation d&#39;une Extension avec un VSPackage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# Cr&#233;ation d&#39;une Extension avec un VSPackage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette procédure pas à pas vous montre comment créer un projet VSIX et ajouter un élément de projet VSPackage. Nous allons utiliser le VSPackage pour obtenir le service de l'interpréteur de commandes de l'interface utilisateur afin d'afficher une boîte de message.  
  
## Conditions préalables  
 À partir de Visual Studio 2015, vous n'installez pas Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d'installation de Visual Studio. Vous pouvez également installer le Kit de développement logiciel Visual Studio plus tard. Pour plus d'informations, consultez [L'installation du Kit de développement logiciel de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Création d'un VSPackage  
  
1.  Créez un projet VSIX nommé **FirstPackage**. Vous pouvez trouver le modèle de projet VSIX dans le **Nouveau projet** boîte de dialogue sous **Visual C\# \/ extensibilité**.  
  
2.  Lorsque le projet s'ouvre, ajoutez un modèle d'élément de package Visual Studio nommé **FirstPackage**. Dans le **l'Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **Ajouter \/ nouvel élément**. Dans le **Ajouter un nouvel élément** boîte de dialogue, accédez à **Visual C\# \/ extensibilité** et sélectionnez **Package Visual Studio**. Dans le **nom** en bas de la fenêtre, modifiez le nom du fichier de commandes **FirstPackage.cs**.  
  
3.  Générez le projet et commencez le débogage.  
  
     L'instance expérimentale de Visual Studio s'affiche. Pour plus d'informations sur l'instance expérimentale, consultez [L'Instance expérimentale](../extensibility/the-experimental-instance.md).  
  
4.  Dans l'instance expérimentale, ouvrez le **Outils \/ Extensions et mises à jour** fenêtre. Vous devez voir les **FirstPackage** extension ici. \(Si vous ouvrez **Extensions et mises à jour** dans votre instance de travail de Visual Studio, vous ne verrez pas **FirstPackage**\).  
  
## Le chargement du package VS  
 À ce stade l'extension n'est pas chargé car il n'existe rien qui le force à charger. Vous pouvez généralement charger une extension lorsque vous interagissez avec son interface utilisateur \(en cliquant sur une commande de menu, en ouvrant une fenêtre outil\), ou en spécifiant que le VSPackage doit se charger dans un contexte de l'interface utilisateur spécifique. Pour plus d'informations sur le chargement des contextes VSPackages et l'interface utilisateur, consultez la page [Chargement des packages VS](../extensibility/loading-vspackages.md). Pour cette procédure, nous allons vous montrer comment charger un VSPackage lorsqu'une solution est ouverte.  
  
1.  Ouvrez le fichier FirstPackage.cs. Recherchez la déclaration de la classe FirstPackage. Remplacer les attributs existants avec les éléments suivants :  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackageGuids.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2.  Nous allons ajouter un message qui nous permet de savoir que le VSPackage a été chargé. Nous utiliser méthode Initialize\(\) du VSPackage pour ce faire, car vous pouvez obtenir les services de Visual Studio uniquement après que le VSPackage a été installé. \(Pour plus d'informations sur l'obtention de services, consultez [Comment : obtenir un Service](../Topic/How%20to:%20Get%20a%20Service.md).\) Remplacez la méthode Initialize\(\) de FirstPackage avec du code qui obtient le <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> service, obtient le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interface et appelle son <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> \(méthode\).  
  
    ```c#  
    protected override void Initialize()  
    {  
        base.Initialize();  
  
        IVsUIShell uiShell = (IVsUIShell)GetService(typeof(SVsUIShell));  
        Guid clsid = Guid.Empty;  
        int result;  
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(uiShell.ShowMessageBox(  
            0,  
            ref clsid,  
            "FirstPackage",  
             string.Format(CultureInfo.CurrentCulture, "Inside {0}.Initialize()", this.GetType().FullName),  
            string.Empty,  
            0,  
            OLEMSGBUTTON.OLEMSGBUTTON_OK,  
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
            OLEMSGICON.OLEMSGICON_INFO,  
            0,  
            out result));  
    }  
    ```  
  
3.  Générez le projet et commencez le débogage. L'instance expérimentale s'affiche.  
  
4.  Ouvrez une solution dans l'instance expérimentale. Vous devez voir une boîte de message indiquant que **premier Package dans Initialize\(\)**.