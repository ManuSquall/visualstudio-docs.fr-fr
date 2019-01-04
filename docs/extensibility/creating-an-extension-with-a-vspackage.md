---
title: Création d’une Extension avec un VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1060dda64fc402e69f7f87601a1643fbabed5507
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53838409"
---
# <a name="create-an-extension-with-a-vspackage"></a>Créer une extension avec un VSPackage
Cette procédure pas à pas vous montre comment créer un projet VSIX et ajouter un élément de projet VSPackage. Nous allons utiliser le VSPackage pour obtenir le service de l’interpréteur de commandes de l’interface utilisateur pour afficher une boîte de message.  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [installer le SDK Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-vspackage"></a>Créer un VSPackage  
  
1.  Créez un projet VSIX nommé **FirstPackage**. Vous pouvez trouver le modèle de projet VSIX dans le **nouveau projet** boîte de dialogue sous **Visual C#** > **extensibilité**.  
  
2.  Quand le projet s’ouvre, ajoutez un modèle d’élément de package Visual Studio nommé **FirstPackage**. Dans le **l’Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **ajouter** > **un nouvel élément**. Dans le **ajouter un nouvel élément** boîte de dialogue, accédez à **Visual C#** > **extensibilité** et sélectionnez **Package Visual Studio**. Dans le **nom** en bas de la fenêtre, modifiez le nom de fichier de commande pour *FirstPackage.cs*.  
  
3.  Générez le projet et commencez le débogage.  
  
     L’instance expérimentale de Visual Studio s’affiche. Pour plus d’informations sur l’instance expérimentale, consultez [l’instance expérimentale](../extensibility/the-experimental-instance.md).  
  
4.  Dans l’instance expérimentale, ouvrez le **outils** > **Extensions et mises à jour** fenêtre. Vous devez voir le **FirstPackage** extension ici. (Si vous ouvrez **Extensions et mises à jour** dans votre instance de travail de Visual Studio, vous ne verrez pas **FirstPackage**).  
  
## <a name="load-the-vspackage"></a>Charger le VSPackage  
 À ce stade l’extension ne se charge pas, car il n’a rien qui oblige ce dernier à charger. Vous pouvez généralement charger une extension lorsque vous interagissez avec son interface utilisateur (en cliquant sur une commande de menu, en ouvrant une fenêtre outil), ou en spécifiant que le VSPackage doit se charger dans un contexte de l’interface utilisateur spécifique. Pour plus d’informations sur le chargement des contextes de VSPackages et l’interface utilisateur, consultez [le chargement de VSPackages](../extensibility/loading-vspackages.md). Pour cette procédure, nous allons vous montrer comment charger un VSPackage lorsqu’une solution est ouverte.  
  
1.  Ouvrez le *FirstPackage.cs* fichier. Recherchez la déclaration de la `FirstPackage` classe. Remplacez les attributs existants avec les éléments suivants :  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackage.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2.  Nous allons ajouter un message qui nous permet de savoir que le VSPackage a été chargé. Nous utilisons le VSPackage `Initialize()` méthode pour ce faire, car vous pouvez obtenir Visual Studio services uniquement une fois que le VSPackage a été placé. (Pour plus d’informations sur l’obtention de services, consultez [Comment : Obtenir un service](../extensibility/how-to-get-a-service.md).) Remplacer le `Initialize()` méthode de `FirstPackage` avec du code qui obtient le <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> de service, obtient le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interface et appelle son <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> (méthode).  
  
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