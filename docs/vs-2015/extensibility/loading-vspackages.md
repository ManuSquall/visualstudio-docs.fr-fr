---
title: Chargement des VSPackages | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e20caff476e116ad59430692719bdbbe22c4914c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839633"
---
# <a name="loading-vspackages"></a>Chargement de VSPackages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les VSPackages sont chargés dans Visual Studio uniquement lorsque leurs fonctionnalités sont requises. Par exemple, un VSPackage est chargé quand Visual Studio utilise une fabrique de projet ou un service que le VSPackage implémente. Cette fonctionnalité est appelée chargement différé, qui est utilisée chaque fois que cela est possible pour améliorer les performances.  
  
> [!NOTE]
> Visual Studio peut déterminer certaines informations VSPackage, telles que les commandes qu’un VSPackage offre, sans charger le VSPackage.  
  
 Les VSPackages peuvent être configurés pour se charger dans un contexte d’interface utilisateur (IU) particulier, par exemple lorsqu’une solution est ouverte. L' <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> attribut définit ce contexte.  
  
### <a name="autoloading-a-vspackage-in-a-specific-context"></a>Chargement automatique d’un VSPackage dans un contexte spécifique  
  
- Ajoutez l' `ProvideAutoLoad` attribut aux attributs VSPackage :  
  
    ```csharp  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     Consultez les champs énumérés de <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> pour obtenir la liste des contextes d’interface utilisateur et leurs valeurs GUID.  
  
- Définissez un point d’arrêt dans la <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> méthode.  
  
- Générez le VSPackage et démarrez le débogage.  
  
- Charger une solution ou en créer une.  
  
     Le VSPackage se charge et s’arrête au point d’arrêt.  
  
## <a name="forcing-a-vspackage-to-load"></a>Forcer le chargement d’un VSPackage  
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
  
     Le chargement forcé ne doit pas être utilisé pour la communication VSPackage. Utilisez [à la place et fournissez des services](../extensibility/using-and-providing-services.md) .  
  
## <a name="using-a-custom-attribute-to-register-a-vspackage"></a>Utilisation d’un attribut personnalisé pour inscrire un VSPackage  
 Dans certains cas, vous devrez peut-être créer un nouvel attribut d’inscription pour votre extension. Vous pouvez utiliser les attributs d’inscription pour ajouter de nouvelles clés de registre ou pour ajouter de nouvelles valeurs aux clés existantes. Le nouvel attribut doit dériver de <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> , et il doit substituer <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> les <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> méthodes et.  
  
## <a name="creating-a-registry-key"></a>Création d’une clé de Registre  
 Dans le code suivant, l’attribut personnalisé crée une sous-clé **personnalisée** sous la clé pour le VSPackage en cours d’inscription.  
  
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
 Vous pouvez ajouter des valeurs personnalisées à une clé existante. Le code suivant montre comment ajouter une nouvelle valeur à une clé d’inscription VSPackage.  
  
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
