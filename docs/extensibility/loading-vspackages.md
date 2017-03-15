---
title: "Chargement des packages VS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Chargement automatique de packages VS"
  - "packages VS, charger"
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Chargement des packages VS
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les VSPackages sont chargés dans Visual Studio uniquement lorsque leur fonctionnalité est requise. Par exemple, un VSPackage est chargé lorsque Visual Studio utilise un factory de projet ou un service qui implémente le VSPackage. Cette fonctionnalité est appelée chargement différé, qui est utilisé chaque fois que possible améliorer les performances.  
  
> [!NOTE]
>  Visual Studio peut déterminer certaines informations VSPackage, telles que les commandes par un VSPackage, sans charger le VSPackage.  
  
 VSPackages peut être définis à chargement automatique dans un contexte d’interface graphique utilisateur particulier, par exemple, lorsqu’une solution est ouverte. Le <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> attribut définit ce contexte.  
  
### Chargement automatique un VSPackage dans un contexte spécifique  
  
-   Ajouter le `ProvideAutoLoad` aux attributs VSPackage d’attribut :  
  
    ```c#  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     Afficher les champs énumérées de <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> pour obtenir la liste des contextes d’interface utilisateur et leurs valeurs GUID.  
  
-   Définir un point d’arrêt dans le <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> \(méthode\).  
  
-   Générez le VSPackage et démarrer le débogage.  
  
-   Chargez une solution ou en créer un.  
  
     Le VSPackage charge et s’arrête au point d’arrêt.  
  
## Forcer un VSPackage à charger  
 Dans certaines circonstances, un VSPackage peut\-être forcer un autre VSPackage à charger. Par exemple, un VSPackage léger peut charger un VSPackage supérieure dans un contexte qui n’est pas disponible comme un CMDUIContext.  
  
 Vous pouvez utiliser la <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> méthode pour forcer un VSPackage à charger.  
  
-   Insérez ce code dans la <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> méthode du VSPackage qui force une autre VSPackage à charger :  
  
    ```c#  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     Lorsque le VSPackage est initialisé, il force `PackageToBeLoaded` à charger.  
  
     Chargement de force ne doit pas servir pour la communication du VSPackage. Utilisez plutôt [À l'aide et fournir des Services](../extensibility/using-and-providing-services.md).  
  
## À l’aide d’un attribut personnalisé à inscrire un VSPackage  
 Dans certains cas, vous devrez créer un nouvel attribut de l’inscription de votre extension. Vous pouvez utiliser les attributs de l’inscription pour ajouter de nouvelles clés de Registre ou pour ajouter de nouvelles valeurs pour les clés existantes. Le nouvel attribut doit dériver de <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, et il doit remplacer le <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> et <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> méthodes.  
  
## Création d’une clé de Registre  
 Dans le code suivant, l’attribut personnalisé crée un **personnalisé** sous\-clé sous la clé pour le VSPackage est en cours d’inscription.  
  
```c#  
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
  
## Création d’une valeur sous une clé de Registre existante  
 Vous pouvez ajouter des valeurs personnalisées à une clé existante. Le code suivant montre comment ajouter une nouvelle valeur à une clé d’inscription VSPackage.  
  
```c#  
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
  
## Voir aussi  
 [Packages VS](../extensibility/internals/vspackages.md)