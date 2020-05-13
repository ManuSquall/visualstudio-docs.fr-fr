---
title: Création d’une extension avec un VSPackage Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1037ebcc58cc4183e6f02119bc7b46abfc132f52
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739529"
---
# <a name="create-an-extension-with-a-vspackage"></a>Créer une extension avec un VSPackage

Ce pas-là vous montre comment créer un projet VSIX et ajouter un élément de projet VSPackage. Nous utiliserons le VSPackage pour obtenir le service UI Shell afin de montrer une boîte de message.

## <a name="prerequisites"></a>Prérequis

A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-vspackage"></a>Créer un VSPackage

1. Créez un projet VSIX nommé **FirstPackage**. Vous pouvez trouver le modèle de projet VSIX dans le dialogue **du nouveau projet** en recherchant "vsix".

2. Lorsque le projet s’ouvre, ajoutez un modèle d’article visual Studio nommé **FirstPackage**. Dans la **Solution Explorer**, cliquez à droite sur le nœud du projet et sélectionnez **Ajouter** > **un nouvel article**. Dans le dialogue **Add New Item,** rendez-vous sur **Visual C’Extensibility** > **Extensibility** et sélectionnez Visual **Studio Package**. Dans le champ **nom** au bas de la fenêtre, changer le nom du fichier de commande pour *FirstPackage.cs*.

3. Générez le projet et commencez le débogage.

    L’exemple expérimental de Visual Studio apparaît. Pour plus d’informations sur l’instance expérimentale, voir [L’exemple expérimental](../extensibility/the-experimental-instance.md).

4. Dans le cas expérimental, ouvrez la fenêtre **Tools** > **Extensions and Updates.** Vous devriez voir l’extension **FirstPackage** ici. (Si vous ouvrez **extensions et mises à jour** dans votre instance de travail de Visual Studio, vous ne verrez pas **FirstPackage**).

## <a name="load-the-vspackage"></a>Chargez le VSPackage

À ce stade, l’extension ne se charge pas parce qu’il n’y a rien qui la fait charger. Vous pouvez généralement charger une extension lorsque vous interagissez avec son interface utilisateur (en cliquant sur une commande de menu, en ouvrant une fenêtre d’outil), ou en spécifiant que le VSPackage doit charger dans un contexte spécifique d’interface utilisateur. Pour plus d’informations sur le chargement des VSPackages et des contextes d’interface utilisateur, voir [Chargement VSPackages](../extensibility/loading-vspackages.md). Pour cette procédure, nous vous montrerons comment charger un VSPackage lorsqu’une solution est ouverte.

1. Ouvrez le *fichier FirstPackage.cs.* Cherchez la déclaration `FirstPackage` de la classe. Remplacez les attributs existants par les attributs suivants :

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid(FirstPackage.PackageGuidString)]
    public sealed class FirstPackage : Package
    ```

2. Ajoutons un message qui nous permet de savoir que le VSPackage a chargé. Nous utilisons la méthode `Initialize()` du VSPackage pour ce faire, car vous pouvez obtenir des services Visual Studio seulement après que le VSPackage a été mis en place. (Pour plus d’informations sur l’obtention de services, voir [Comment : Obtenir un service](../extensibility/how-to-get-a-service.md).) Remplacez `Initialize()` la `FirstPackage` méthode de <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> code qui <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> obtient le service, obtient l’interface, et appelle sa <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> méthode.

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

3. Générez le projet et commencez le débogage. L’instance expérimentale apparaît.

4. Ouvrez une solution dans le cas expérimental. Vous devriez voir une boîte de message qui dit **Premier paquet à l’intérieur Initialize()**.
