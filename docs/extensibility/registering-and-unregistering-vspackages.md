---
title: Inscription et la désinscription de VSPackages | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dff8223a95621f353fa57c38e91bf24b6b177f82
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433381"
---
# <a name="register-and-unregister-vspackages"></a>Inscrire et désinscrire des VSPackages
Vous utilisez des attributs pour inscrire un VSPackage, mais

## <a name="register-a-vspackage"></a>Inscrire un VSPackage
 Vous pouvez utiliser des attributs pour contrôler l’inscription de VSPackages gérés. Toutes les informations d’inscription sont contenues dans un *.pkgdef* fichier. Pour plus d’informations sur le fichier d’inscription, consultez [utilitaire CreatePkgDef](../extensibility/internals/createpkgdef-utility.md).

 Le code suivant montre comment utiliser les attributs standard d’inscription pour inscrire votre VSPackage.

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]
public sealed class BasicPackage : Package
{
    // ...
}
```

## <a name="unregister-an-extension"></a>Annuler l’inscription d’une extension
 Si vous avez expérimenté, avec un grand nombre de VSPackages différents et que vous souhaitez les supprimer de l’instance expérimentale, vous pouvez exécuter la **réinitialiser** commande. Recherchez **réinitialiser l’Instance expérimentale de Visual Studio** sur la page de démarrage de votre ordinateur, ou exécutez cette commande à partir de la ligne de commande :

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp
```

 Si vous souhaitez désinstaller une extension que vous avez installée sur votre instance de développement de Visual Studio, accédez à **outils** > **Extensions et mises à jour**, recherchez l’extension et cliquez sur  **Désinstaller**.

 Si pour une raison quelconque, aucune de ces méthodes ne réussit à désinstaller l’extension, vous pouvez désinscrire l’assembly VSPackage à partir de la ligne de commande comme suit :

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>
```

<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>

## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>Utiliser un attribut personnalisé d’inscription pour inscrire une extension

Dans certains cas, vous devrez peut-être créer un nouvel attribut d’inscription pour votre extension. Vous pouvez utiliser les attributs d’inscription pour ajouter de nouvelles clés de Registre ou pour ajouter de nouvelles valeurs pour les clés existantes. Le nouvel attribut doit dériver de <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, et il doit remplacer le <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> et <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> méthodes.

### <a name="create-a-custom-attribute"></a>Créer un attribut personnalisé

Le code suivant montre comment créer un nouvel attribut d’inscription.

```csharp
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]
public class CustomRegistrationAttribute : RegistrationAttribute
{
}
```

 Le <xref:System.AttributeUsageAttribute> est utilisé sur les classes d’attributs pour spécifier l’élément de programme (classe, méthode, etc.) à laquelle l’attribut se rapporte, qu’il peut être utilisé plusieurs fois et si elle peut être héritée.

### <a name="create-a-registry-key"></a>Créer une clé de Registre

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

### <a name="create-a-new-value-under-an-existing-registry-key"></a>Créer une nouvelle valeur sous une clé de Registre existante

Vous pouvez ajouter des valeurs personnalisées à une clé existante. Le code suivant montre comment ajouter une nouvelle valeur à une clé d’inscription de VSPackage.

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
