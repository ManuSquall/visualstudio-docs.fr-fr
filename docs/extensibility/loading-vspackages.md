---
title: Chargement des VSPackages | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 008cd31bc3d9f909477089e608393f596bfb0682
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="loading-vspackages"></a>Chargement des VSPackages
Les VSPackages sont chargés dans Visual Studio uniquement lorsque leur fonctionnalité est requise. Par exemple, un VSPackage est chargé lorsque Visual Studio utilise une fabrique de projet ou un service qui le VSPackage implémente. Cette fonctionnalité est appelée chargement différé, qui est utilisé chaque fois que possible améliorer les performances.  
  
> [!NOTE]
>  Visual Studio peut déterminer certaines informations sur le package, telles que les commandes par un VSPackage, sans charger le VSPackage.  
  
 VSPackages peut être définis à autoload dans un contexte d’interface utilisateur utilisateur particulier, par exemple, lorsqu’une solution est ouverte. Le <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> attribut définit ce contexte.  
  
### <a name="autoloading-a-vspackage-in-a-specific-context"></a>Chargement automatique un VSPackage dans un contexte spécifique  
  
-   Ajouter le `ProvideAutoLoad` aux attributs VSPackage d’attribut :  
  
    ```csharp  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     Afficher les champs énumérées de <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> pour obtenir la liste des contextes d’interface utilisateur et leurs valeurs GUID.  
  
-   Définir un point d’arrêt dans le <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> (méthode).  
  
-   Générer le VSPackage et démarrer le débogage.  
  
-   Charger une solution ou créez-en un.  
  
     Le package Visual Studio charge et s’arrête au point d’arrêt.  
  
## <a name="forcing-a-vspackage-to-load"></a>Forcer un VSPackage à charger  
 Dans certaines circonstances un VSPackage peut être amené à forcer un autre VSPackage doit être chargé. Par exemple, un VSPackage léger peut charger un VSPackage plus volumineux dans un contexte qui n’est pas disponible en tant qu’un CMDUIContext.  
  
 Vous pouvez utiliser la <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> méthode pour forcer un VSPackage à charger.  
  
-   Insérez ce code dans la <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> méthode du VSPackage qui force une autre VSPackage à charger :  
  
    ```csharp  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     Lorsque le VSPackage est initialisé, il force `PackageToBeLoaded` à charger.  
  
     Lors du chargement de force ne doit pas être utilisé pour la communication du VSPackage. Utilisez [à l’aide et fourniture de Services](../extensibility/using-and-providing-services.md) à la place.
  
## <a name="see-also"></a>Voir aussi  
 [VSPackages](../extensibility/internals/vspackages.md)
