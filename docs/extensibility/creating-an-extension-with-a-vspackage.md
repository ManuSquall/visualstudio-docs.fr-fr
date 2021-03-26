---
title: Création d’une extension avec un VSPackage | Microsoft Docs
description: Découvrez comment créer un projet VSIX et ajouter un élément de projet VSPackage à l’aide du VSPackage pour obtenir le service de Shell d’interface utilisateur afin d’afficher une boîte de message.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a6c93d90771eeffbfe28ae91781403019743afa9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089145"
---
# <a name="create-an-extension-with-a-vspackage"></a>Créer une extension avec un VSPackage

Cette procédure pas à pas vous montre comment créer un projet VSIX et ajouter un élément de projet VSPackage. Nous utiliserons le VSPackage pour obtenir le service de Shell d’interface utilisateur afin d’afficher une boîte de message.

## <a name="prerequisites"></a>Prérequis

À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-vspackage"></a>Créer un VSPackage

1. Créez un projet VSIX nommé **FirstPackage**. Vous pouvez trouver le modèle de projet VSIX dans la boîte de dialogue **nouveau projet** en recherchant « VSIX ».

2. Lorsque le projet s’ouvre, ajoutez un modèle d’élément de package Visual Studio nommé **FirstPackage**. Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet et sélectionnez **Ajouter**  >  **un nouvel élément**. Dans la boîte de dialogue **Ajouter un nouvel élément** , accédez à extensibilité **Visual C#**  >   et sélectionnez **package Visual Studio**. Dans le champ **nom** en bas de la fenêtre, remplacez le nom du fichier de commandes par *FirstPackage. cs*.

3. Générez le projet et commencez le débogage.

    L’instance expérimentale de Visual Studio s’affiche. Pour plus d’informations sur l’instance expérimentale, consultez [l’instance expérimentale](../extensibility/the-experimental-instance.md).

4. Dans l’instance expérimentale, ouvrez la   >  fenêtre **extensions et mises à jour** des outils. Vous devez voir l’extension **FirstPackage** ici. (Si vous ouvrez **extensions et mises à jour** dans votre instance de Visual Studio qui fonctionne, vous ne voyez pas **FirstPackage**).

## <a name="load-the-vspackage"></a>Charger le VSPackage

À ce stade, l’extension ne se charge pas, car il n’y a rien qui la force à se charger. Vous pouvez généralement charger une extension quand vous interagissez avec son interface utilisateur (en cliquant sur une commande de menu, en ouvrant une fenêtre outil) ou en spécifiant que le VSPackage doit se charger dans un contexte d’interface utilisateur spécifique. Pour plus d’informations sur le chargement des VSPackages et des contextes d’interface utilisateur, consultez [chargement des VSPackages](../extensibility/loading-vspackages.md). Pour cette procédure, nous allons vous montrer comment charger un VSPackage quand une solution est ouverte.

1. Ouvrez le fichier *FirstPackage. cs* . Recherchez la déclaration de la `FirstPackage` classe. Remplacez les attributs existants par les attributs suivants :

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid(FirstPackage.PackageGuidString)]
    public sealed class FirstPackage : Package
    ```

2. Nous allons ajouter un message qui nous permet de savoir que le VSPackage a été chargé. Nous utilisons la méthode du VSPackage `Initialize()` pour effectuer cette opération, car vous pouvez accéder aux services Visual Studio uniquement une fois que le VSPackage a été mis en place. (Pour plus d’informations sur l’obtention de services, consultez [Comment : obtenir un service](../extensibility/how-to-get-a-service.md).) Remplacez la `Initialize()` méthode de `FirstPackage` par le code qui obtient le <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> service, obtient l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interface et appelle sa <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> méthode.

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

3. Générez le projet et commencez le débogage. L’instance expérimentale s’affiche.

4. Ouvrez une solution dans l’instance expérimentale. Vous devriez voir une boîte de message indiquant le **premier package à l’intérieur d’Initialize ()**.
