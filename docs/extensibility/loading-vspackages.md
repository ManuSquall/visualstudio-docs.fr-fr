---
title: Chargement des VSPackages | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 94db8d3bb95e254a3fa528a424048162916fce99
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
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
  
## <a name="using-a-custom-attribute-to-register-a-vspackage"></a>À l’aide d’un attribut personnalisé à inscrire un VSPackage  
 Dans certains cas, vous devrez créer un nouvel attribut de l’inscription de votre extension. Vous pouvez utiliser les attributs d’inscription pour ajouter de nouvelles clés de Registre ou pour ajouter de nouvelles valeurs pour les clés existantes. Le nouvel attribut doit dériver de <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, et il doit remplacer le <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> et <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> méthodes.  
  
## <a name="creating-a-registry-key"></a>Création d’une clé de Registre  
 Dans le code suivant, l’attribut personnalisé crée un **personnalisé** sous-clé sous la clé pour le VSPackage est en cours d’inscription.  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
    }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");  
}  
  
```  
  
## <a name="creating-a-new-value-under-an-existing-registry-key"></a>Création d’une valeur sous une clé de Registre existante  
 Vous pouvez ajouter des valeurs personnalisées pour une clé existante. Le code suivant montre comment ajouter une nouvelle valeur à une clé d’inscription de VSPackage.  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
                }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [VSPackages](../extensibility/internals/vspackages.md)