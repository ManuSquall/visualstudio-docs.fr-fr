---
title: Création d’une Extension avec un VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0077c891a300d81f05aec32930cb1ffda82c8d5d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58949904"
---
# <a name="creating-an-extension-with-a-vspackage"></a>Création d’une extension avec un package VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette procédure pas à pas vous montre comment créer un projet VSIX et ajouter un élément de projet VSPackage. Nous allons utiliser le VSPackage pour obtenir le service de l’interpréteur de commandes de l’interface utilisateur pour afficher une boîte de message.  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-vspackage"></a>Création d’un VSPackage  
  
1.  Créez un projet VSIX nommé **FirstPackage**. Vous pouvez trouver le modèle de projet VSIX dans le **nouveau projet** boîte de dialogue sous **Visual c# / extensibilité**.  
  
2.  Quand le projet s’ouvre, ajoutez un modèle d’élément de package Visual Studio nommé **FirstPackage**. Dans le **l’Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **Ajouter / nouvel élément**. Dans le **ajouter un nouvel élément** boîte de dialogue, accédez à **Visual c# / extensibilité** et sélectionnez **Package Visual Studio**. Dans le **nom** en bas de la fenêtre, modifiez le nom de fichier de commande pour **FirstPackage.cs**.  
  
3.  Générez le projet et commencez le débogage.  
  
     L’instance expérimentale de Visual Studio s’affiche. Pour plus d’informations sur l’instance expérimentale, consultez [l’Instance expérimentale](../extensibility/the-experimental-instance.md).  
  
4.  Dans l’instance expérimentale, ouvrez le **outils / Extensions et mises à jour** fenêtre. Vous devez voir le **FirstPackage** extension ici. (Si vous ouvrez **Extensions et mises à jour** dans votre instance de travail de Visual Studio, vous ne verrez pas **FirstPackage**).  
  
## <a name="loading-the-vspackage"></a>Charger le VSPackage  
 À ce stade l’extension ne se charge pas, car il n’a rien qui oblige ce dernier à charger. Vous pouvez généralement charger une extension lorsque vous interagissez avec son interface utilisateur (en cliquant sur une commande de menu, en ouvrant une fenêtre outil), ou en spécifiant que le VSPackage doit se charger dans un contexte de l’interface utilisateur spécifique. Pour plus d’informations sur le chargement des contextes de VSPackages et l’interface utilisateur, consultez [le chargement de VSPackages](../extensibility/loading-vspackages.md). Pour cette procédure, nous allons vous montrer comment charger un VSPackage lorsqu’une solution est ouverte.  
  
1.  Ouvrez le fichier FirstPackage.cs. Recherchez la déclaration de la classe FirstPackage. Remplacez les attributs existants avec les éléments suivants :  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackageGuids.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2.  Nous allons ajouter un message qui nous permet de savoir que le VSPackage a été chargé. Nous utilisons une méthode Initialize() du VSPackage pour ce faire, car vous pouvez obtenir des services de Visual Studio uniquement une fois que le VSPackage a été placé. (Pour plus d’informations sur l’obtention de services, consultez [Comment : Obtenir un Service](../extensibility/how-to-get-a-service.md).) Remplacez la méthode Initialize() de FirstPackage avec du code qui obtient le <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> de service, obtient le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interface et appelle son <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> (méthode).  
  
    ```csharp  
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
  
3.  Générez le projet et commencez le débogage. L’instance expérimentale s’affiche.  
  
4.  Ouvrez une solution dans l’instance expérimentale. Vous devez voir une boîte de message indiquant que **premier Package à l’intérieur Initialize()**.
