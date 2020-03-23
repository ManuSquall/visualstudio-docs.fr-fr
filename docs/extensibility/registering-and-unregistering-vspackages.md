---
title: Enregistrement et non-enregistrement VSPackages (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 701700ba9d5c6db1e5858a2419e1b2c0fa950ae5
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303182"
---
# <a name="register-and-unregister-vspackages"></a>Inscrivez-vous et enregistrez VSPackages
Vous utilisez des attributs pour enregistrer un VSPackage, mais

## <a name="register-a-vspackage"></a>Enregistrez un VSPackage
 Vous pouvez utiliser des attributs pour contrôler l’enregistrement des VSPackages gérés. Toutes les informations d’enregistrement sont contenues dans un fichier *.pkgdef.* Pour plus d’informations sur l’enregistrement basé sur les fichiers, voir [CreatePkgDef utilitaire](../extensibility/internals/createpkgdef-utility.md).

 Le code suivant montre comment utiliser les attributs d’enregistrement standard pour enregistrer votre VSPackage.

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]
public sealed class BasicPackage : Package
{
    // ...
}
```

## <a name="unregister-an-extension"></a>Annuler l’enregistrement d’une extension
 Si vous avez expérimenté avec un grand nombre de VSPackages différents et que vous voulez les supprimer de l’instance expérimentale, vous pouvez simplement exécuter la commande **Reset.** Recherchez **Réinitialiser l’instance expérimentale Visual Studio** sur la page de départ de votre ordinateur, ou exécutez cette commande à partir de la ligne de commande :

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp
```

 Si vous souhaitez désinstaller une extension que vous avez installée sur votre instance de développement de Visual Studio, allez à **Tools** > **Extensions and Updates**, trouver l’extension, et cliquez sur **Uninstall**.

 Si, pour une raison quelconque, aucune de ces méthodes ne réussit à désinstaller l’extension, vous pouvez désenregistrer l’assemblage VSPackage de la ligne de commande comme suit :

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>
```

<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>

## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>Utilisez un attribut d’enregistrement personnalisé pour enregistrer une extension

Dans certains cas, vous devrez peut-être créer un nouvel attribut d’enregistrement pour votre extension. Vous pouvez utiliser des attributs d’enregistrement pour ajouter de nouvelles clés de registre ou pour ajouter de nouvelles valeurs aux clés existantes. Le nouvel attribut <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>doit dériver de <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> , <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> et il doit l’emporter sur les méthodes et les méthodes.

### <a name="create-a-custom-attribute"></a>Création d’un attribut personnalisé

Le code suivant montre comment créer un nouvel attribut d’enregistrement.

```csharp
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]
public class CustomRegistrationAttribute : RegistrationAttribute
{
}
```

 L’est <xref:System.AttributeUsageAttribute> utilisé sur les classes d’attributs pour spécifier l’élément du programme (classe, méthode, etc.) auquel l’attribut se rapporte, s’il peut être utilisé plus d’une fois, et s’il peut être hérité.

### <a name="create-a-registry-key"></a>Créer une clé de registre

Dans le code suivant, l’attribut personnalisé crée un sous-clé **personnalisé** sous la clé pour le VSPackage qui est enregistré.

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

### <a name="create-a-new-value-under-an-existing-registry-key"></a>Créer une nouvelle valeur en vertu d’une clé de registre existante

Vous pouvez ajouter des valeurs personnalisées à une clé existante. Le code suivant montre comment ajouter une nouvelle valeur à une clé d’enregistrement VSPackage.

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
