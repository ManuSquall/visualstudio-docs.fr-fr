---
title: "Inscription et la désinscription des VSPackages | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: 35
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 312c06295492ac9bd1136ea7de9a0399f247c365
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="registering-and-unregistering-vspackages"></a>Inscription et annulation de l’inscription de VSPackages
Vous utilisez des attributs pour inscrire un VSPackage, mais  
  
## <a name="registering-a-vspackage"></a>L’inscription d’un VSPackage  
 Vous pouvez utiliser des attributs pour contrôler l’inscription de VSPackages gérés. Toutes les informations d’inscription sont contenues dans un fichier .pkgdef. Pour plus d’informations sur l’enregistrement de fichiers, consultez [CreatePkgDef utilitaire](../extensibility/internals/createpkgdef-utility.md).  
  
 Le code suivant montre comment utiliser les attributs standard d’inscription pour inscrire votre VSPackage.  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>Annuler l’inscription d’une Extension  
 Si vous testé avec un grand nombre des différents VSPackages et les supprimer de l’instance expérimentale, vous pouvez simplement exécuter la **réinitialiser** commande. Recherchez **réinitialiser l’Instance expérimentale de Visual Studio** sur la page de démarrage de votre ordinateur, ou exécutez cette commande à partir de la ligne de commande :  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Si vous souhaitez désinstaller une extension que vous avez installés sur votre instance de développement de Visual Studio, accédez à **outils / Extensions et mises à jour**, recherchez l’extension, puis cliquez sur **désinstallation**.  
  
 Si pour une raison quelconque, aucune de ces méthodes aboutit à la désinstallation de l’extension, vous pouvez désinscrire l’assembly VSPackage à partir de la ligne de commande comme suit :  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>  
```  
  
<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>  
  
## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>Utilisez un attribut personnalisé d’inscription pour inscrire une extension  
  
Dans certains cas, vous devrez créer un nouvel attribut de l’inscription de votre extension. Vous pouvez utiliser les attributs d’inscription pour ajouter de nouvelles clés de Registre ou pour ajouter de nouvelles valeurs pour les clés existantes. Le nouvel attribut doit dériver de <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, et il doit remplacer le <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> et <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> méthodes.  
  
### <a name="creating-a-custom-attribute"></a>Création d’un attribut personnalisé  
  
Le code suivant montre comment créer un attribut d’inscription.  
  
```csharp  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
    public class CustomRegistrationAttribute : RegistrationAttribute  
    {  
    }  
```  
  
 Le <xref:System.AttributeUsageAttribute> est utilisé sur les classes d’attributs pour spécifier l’élément de programme (classe, méthode, etc.) à laquelle l’attribut se rapporte, qu’il peut être utilisé plusieurs fois et si elle peut être héritée.  
  
### <a name="creating-a-registry-key"></a>Création d’une clé de Registre  
  
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
  
### <a name="creating-a-new-value-under-an-existing-registry-key"></a>Création d’une valeur sous une clé de Registre existante  
  
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
