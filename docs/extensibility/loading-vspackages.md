---
title: Chargement vsPackages (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1c221bf06ef3b7e37e2afc1856f3e54fe5ad95e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702967"
---
# <a name="load-vspackages"></a>Chargez VSPackages
VSPackages sont chargés dans Visual Studio seulement lorsque leur fonctionnalité est nécessaire. Par exemple, un VSPackage est chargé lorsque Visual Studio utilise une usine de projet ou un service que le VSPackage met en œuvre. Cette fonctionnalité est appelée chargement différé, qui est utilisé dans la mesure du possible pour améliorer les performances.

> [!NOTE]
> Visual Studio peut déterminer certaines informations VSPackage, telles que les commandes qu’un VSPackage offre, sans charger le VSPackage.

 VSPackages peut être réglé pour recharger automatiquement dans un contexte particulier d’interface utilisateur (interface utilisateur), par exemple, lorsqu’une solution est ouverte. L’attribut <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> définit ce contexte.

### <a name="autoload-a-vspackage-in-a-specific-context"></a>Autochargez un VSPackage dans un contexte spécifique

- Ajoutez `ProvideAutoLoad` l’attribut aux attributs VSPackage :

    ```csharp
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID
    public class MyAutoloadedPackage : Package
    {. . .}
    ```

     Voir les champs énumérés pour <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> une liste des contextes d’interface utilisateur et leurs valeurs GUID.

- Définissez un point <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> d’arrêt dans la méthode.

- Construisez le VSPackage et commencez à débogage.

- Chargez une solution ou créez-en une.

     Le VSPackage charge et s’arrête au point d’arrêt.

## <a name="force-a-vspackage-to-load"></a>Forcer un VSPackage à charger
 Dans certaines circonstances, un VSPackage peut avoir à forcer un autre VSPackage à être chargé. Par exemple, un VSPackage léger peut charger un VSPackage plus grand dans un contexte qui n’est pas disponible sous forme de CMDUIContext.

 Vous pouvez <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> utiliser la méthode pour forcer un VSPackage à charger.

- Insérez <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> ce code dans la méthode du VSPackage qui force un autre VSPackage à charger :

    ```csharp
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;
    if (shell == null) return;

    IVsPackage package = null;
    Guid PackageToBeLoadedGuid =
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);

    ```

     Lorsque le VSPackage est parasécé, il force `PackageToBeLoaded` à charger.

     Le chargement de force ne doit pas être utilisé pour la communication VSPackage. Utilisez [et fournissez plutôt des services.](../extensibility/using-and-providing-services.md)

## <a name="see-also"></a>Voir aussi
- [VSPackages](../extensibility/internals/vspackages.md)
