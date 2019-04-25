---
title: Chargement de VSPackages | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ce0f09c1749621838729e1e4f64feb3ca8b07628
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117562"
---
# <a name="load-vspackages"></a>Charger des VSPackages
Les VSPackages sont chargés dans Visual Studio uniquement lorsque leur fonctionnalité est requise. Par exemple, un VSPackage est chargé lorsque Visual Studio utilise une fabrique de projet ou un service qui implémente le VSPackage. Cette fonctionnalité est appelée chargement différé, ce qui est utilisé chaque fois que possible améliorer les performances.

> [!NOTE]
>  Visual Studio peut déterminer certaines informations sur le package, telles que les commandes offertes par un VSPackage, sans charger le VSPackage.

 VSPackages peut être définis à chargement automatique dans un contexte d’interface (UI) utilisateur particulier, par exemple, lorsqu’une solution est ouverte. Le <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> attribut définit ce contexte.

### <a name="autoload-a-vspackage-in-a-specific-context"></a>Charger automatiquement un VSPackage dans un contexte spécifique

- Ajouter le `ProvideAutoLoad` d’attribut pour les attributs de package Visual Studio :

    ```csharp
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID
    public class MyAutoloadedPackage : Package
    {. . .}
    ```

     Afficher les champs énumérées de <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> pour obtenir la liste des contextes d’interface utilisateur et leurs valeurs GUID.

- Définir un point d’arrêt dans le <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> (méthode).

- Générer le VSPackage et démarrer le débogage.

- Chargez une solution, ou créez-en un.

     Le package Visual Studio charge et s’arrête au point d’arrêt.

## <a name="force-a-vspackage-to-load"></a>Force un VSPackage à charger
 Dans certaines circonstances, un VSPackage peut avoir forcer un autre VSPackage à charger. Par exemple, un VSPackage léger peut charger un VSPackage plus volumineux dans un contexte qui n’est pas disponible en tant qu’un CMDUIContext.

 Vous pouvez utiliser la <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> méthode pour forcer un VSPackage à charger.

- Insérez ce code dans le <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> méthode du VSPackage qui force une autre VSPackage à charger :

    ```csharp
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;
    if (shell == null) return;

    IVsPackage package = null;
    Guid PackageToBeLoadedGuid =
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);

    ```

     Lorsque le VSPackage est initialisé, il force `PackageToBeLoaded` à charger.

     Chargement de force n’a pas doit être utilisé pour la communication de VSPackage. Utilisez [utilisez et fournir des services](../extensibility/using-and-providing-services.md) à la place.

## <a name="see-also"></a>Voir aussi
- [VSPackages](../extensibility/internals/vspackages.md)
