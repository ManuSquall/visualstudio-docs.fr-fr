---
title: Inscription et annulation de l’inscription de VSPackages | Microsoft Docs
description: En savoir plus sur l’inscription et l’annulation de l’inscription de vos VSPackages, y compris les attributs que vous utilisez et le fichier. pkgdef.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 48067ed883a44870b3b753cb5e3d6943eca91ca5
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900302"
---
# <a name="register-and-unregister-vspackages"></a>Inscrire et désinscrire des VSPackages
Vous utilisez des attributs pour inscrire un VSPackage, mais

## <a name="register-a-vspackage"></a>Inscrire un VSPackage
 Vous pouvez utiliser des attributs pour contrôler l’inscription des VSPackages managés. Toutes les informations d’inscription sont contenues dans un fichier *. pkgdef* . Pour plus d’informations sur l’inscription basée sur les fichiers, consultez [CreatePkgDef Utility](../extensibility/internals/createpkgdef-utility.md).

 Le code suivant montre comment utiliser les attributs d’inscription standard pour inscrire votre VSPackage.

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]
public sealed class BasicPackage : Package
{
    // ...
}
```

## <a name="unregister-an-extension"></a>Annuler l’enregistrement d’une extension
 Si vous avez fait des essais avec un grand nombre de VSPackages et souhaitez les supprimer de l’instance expérimentale, vous pouvez simplement exécuter la commande de **réinitialisation** . Recherchez **Réinitialiser l’instance expérimentale de Visual Studio** sur la page de démarrage de votre ordinateur, ou exécutez la commande suivante à partir de la ligne de commande :

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp
```

 Si vous souhaitez désinstaller une extension que vous avez installée sur votre instance de développement de Visual Studio, accédez à **Outils**  >  **extensions et mises à jour**, recherchez l’extension, puis cliquez sur **désinstaller**.

 Si, pour une raison quelconque, aucune de ces méthodes ne parvient à désinstaller l’extension, vous pouvez annuler l’inscription de l’assembly VSPackage à partir de la ligne de commande comme suit :

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>
```

<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>

## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>Utiliser un attribut d’inscription personnalisé pour inscrire une extension

Dans certains cas, vous devrez peut-être créer un nouvel attribut d’inscription pour votre extension. Vous pouvez utiliser les attributs d’inscription pour ajouter de nouvelles clés de registre ou pour ajouter de nouvelles valeurs aux clés existantes. Le nouvel attribut doit dériver de <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> , et il doit substituer <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> les <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> méthodes et.

### <a name="create-a-custom-attribute"></a>Création d’un attribut personnalisé

Le code suivant montre comment créer un nouvel attribut d’inscription.

```csharp
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]
public class CustomRegistrationAttribute : RegistrationAttribute
{
}
```

 <xref:System.AttributeUsageAttribute>Est utilisé sur les classes d’attributs pour spécifier l’élément de programme (classe, méthode, etc.) auquel l’attribut se rapporte, s’il peut être utilisé plusieurs fois et s’il peut être hérité.

### <a name="create-a-registry-key"></a>Créer une clé de Registre

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

### <a name="create-a-new-value-under-an-existing-registry-key"></a>Créer une valeur sous une clé de Registre existante

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
- [VSPackages](../extensibility/internals/vspackages.md)
