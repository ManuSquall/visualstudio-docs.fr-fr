---
title: Chargement des VSPackages | Microsoft Docs
description: En savoir plus sur le chargement de VSPackages dans Visual Studio, y compris le chargement différé, qui est utilisé dans la mesure du possible pour améliorer les performances.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 39a58bcbad79191f54a7b4eeb2aa12e90d8a6e44
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073285"
---
# <a name="load-vspackages"></a>Charger les VSPackages
Les VSPackages sont chargés dans Visual Studio uniquement lorsque leurs fonctionnalités sont requises. Par exemple, un VSPackage est chargé quand Visual Studio utilise une fabrique de projet ou un service que le VSPackage implémente. Cette fonctionnalité est appelée chargement différé, qui est utilisée chaque fois que cela est possible pour améliorer les performances.

> [!NOTE]
> Visual Studio peut déterminer certaines informations VSPackage, telles que les commandes qu’un VSPackage offre, sans charger le VSPackage.

 Les VSPackages peuvent être configurés pour se charger dans un contexte d’interface utilisateur (IU) particulier, par exemple lorsqu’une solution est ouverte. L' <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> attribut définit ce contexte.

### <a name="autoload-a-vspackage-in-a-specific-context"></a>Charger un VSPackage dans un contexte spécifique

- Ajoutez l' `ProvideAutoLoad` attribut aux attributs VSPackage :

    ```csharp
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID
    public class MyAutoloadedPackage : Package
    {. . .}
    ```

     Consultez les champs énumérés de <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> pour obtenir la liste des contextes d’interface utilisateur et leurs valeurs GUID.

- Définissez un point d’arrêt dans la <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> méthode.

- Générez le VSPackage et démarrez le débogage.

- Charger une solution ou en créer une.

     Le VSPackage se charge et s’arrête au point d’arrêt.

## <a name="force-a-vspackage-to-load"></a>Forcer le chargement d’un VSPackage
 Dans certains cas, un VSPackage peut être amené à forcer le chargement d’un autre VSPackage. Par exemple, un VSPackage léger peut charger un VSPackage plus volumineux dans un contexte qui n’est pas disponible en tant que CMDUIContext.

 Vous pouvez utiliser la <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> méthode pour forcer le chargement d’un VSPackage.

- Insérez ce code dans la <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> méthode du VSPackage qui force le chargement d’un autre VSPackage :

    ```csharp
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;
    if (shell == null) return;

    IVsPackage package = null;
    Guid PackageToBeLoadedGuid =
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);

    ```

     Lorsque le VSPackage est initialisé, il force le `PackageToBeLoaded` chargement.

     Le chargement forcé ne doit pas être utilisé pour la communication VSPackage. Utilisez à la place [use et fournissez des services](../extensibility/using-and-providing-services.md) .

## <a name="see-also"></a>Voir aussi
- [VSPackages](../extensibility/internals/vspackages.md)
