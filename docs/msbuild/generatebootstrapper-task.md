---
title: Tâche GenerateBootstrapper | Microsoft Docs
description: Utilisez la tâche MSBuild GenerateBootstrapper, pour une méthode automatisée de détection, de téléchargement et d’installation d’une application et de ses conditions préalables.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateBootstrapper
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateBootstrapper task
- GenerateBootstrapper task [MSBuild]
ms.assetid: ca3ba2c6-d2ea-41f2-b7e3-0fc2b0730460
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 93dbe9d3bf49118328cb53dcd6602bb5fda77b13
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914871"
---
# <a name="generatebootstrapper-task"></a>GenerateBootstrapper (tâche)

Fournit un moyen automatisé de détecter, télécharger et installer une application et ses composants requis. Elle constitue un seul programme d’installation qui intègre les programmes d’installation distincts de tous les composants d’une application.

## <a name="task-parameters"></a>Paramètres de tâche

Le tableau ci-dessous décrit les paramètres de la tâche `GenerateBootstrapper`.

- `ApplicationFile`

   Paramètre `String` facultatif.

   Spécifie le fichier utilisé par le programme d’amorçage pour commencer l’installation de l’application une fois tous les composants requis installés. Une erreur de build se produit si ni le paramètre `BootstrapperItems` ni le paramètre `ApplicationFile` ne sont spécifiés.

- `ApplicationName`

   Paramètre `String` facultatif.

   Spécifie le nom de l’application installée par le programme d’amorçage. Ce nom est affiché dans l’interface utilisateur du programme d’amorçage pendant l’installation.

- `ApplicationRequiresElevation`

   Paramètre `Boolean` facultatif.

   Si `true`, le composant s’exécute avec des autorisations élevées lorsqu’il est installé sur un ordinateur cible.

- `ApplicationUrl`

   Paramètre `String` facultatif.

   Indique l’emplacement web qui héberge le programme d’installation de l’application.

- `BootstrapperComponentFiles`

   Paramètre de sortie `String[]` facultatif.

   Spécifie l’emplacement généré des fichiers de package du programme d’amorçage.

- `BootstrapperItems`

   Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.

   Indique les produits à générer dans le programme d’amorçage. Les éléments transmis à ce paramètre doivent avoir la syntaxe suivante :

  ```xml
  <BootstrapperItem
      Include="ProductCode">
      <ProductName>
          ProductName
      </ProductName>
  </BootstrapperItem>
  ```

   L’attribut `Include` représente le nom d’un composant requis qui doit être installé. Les métadonnées de l’élément `ProductName` sont facultatives et sont utilisées par le moteur de génération comme nom convivial si le package est introuvable. Ces éléments ne sont pas des paramètres d’entrée MSBuild requis, sauf si aucun `ApplicationFile` n’est spécifié. Vous devez inclure un élément pour chaque composant requis qui doit être installé pour votre application.

   Une erreur de build se produit si ni le paramètre `BootstrapperItems` ni le paramètre `ApplicationFile` ne sont spécifiés.

- `BootstrapperKeyFile`

   Paramètre de sortie `String` facultatif.

   Spécifie l’emplacement de génération de *setup.exe*.

- `ComponentsLocation`

   Paramètre `String` facultatif.

   Indique un emplacement où le programme d’amorçage doit rechercher les composants requis à installer. Ce paramètre peut avoir les valeurs suivantes :

  - `HomeSite` : indique que le composant requis est hébergé par le fournisseur du composant.

  - `Relative` : indique que le composant requis est au même emplacement de l’application.

  - `Absolute` : indique que tous les composants doivent se trouver dans une URL centralisée. Cette valeur doit être utilisée conjointement avec le paramètre d’entrée `ComponentsUrl`.

    Si `ComponentsLocation` n’est pas spécifié, `HomeSite` est utilisé par défaut.

- `ComponentsUrl`

   Paramètre `String` facultatif.

   Spécifie l’URL qui contient les conditions préalables à l’installation.

- `CopyComponents`

   Paramètre `Boolean` facultatif.

   Si `true`, le programme d’amorçage copie tous les fichiers de sortie dans le chemin d’accès spécifié dans le paramètre `OutputPath`. Les valeurs du paramètre `BootstrapperComponentFiles` doivent toutes être basées sur ce chemin d’accès. Si `false`, les fichiers ne sont pas copiés, et les valeurs `BootstrapperComponentFiles` sont basées sur la valeur du paramètre `Path`.  La valeur par défaut de ce paramètre est `true`.

- `Culture`

   Paramètre `String` facultatif.

   Spécifie la culture à utiliser pour l’interface utilisateur du programme d’amorçage et la configuration requise pour l’installation. Si la culture spécifiée n’est pas disponible, la tâche utilise la valeur du paramètre `FallbackCulture`.

- `FallbackCulture`

   Paramètre `String` facultatif.

   Spécifie la culture secondaire à utiliser pour l’interface utilisateur du programme d’amorçage et la configuration requise pour l’installation.

- `OutputPath`

   Paramètre `String` facultatif.

   Indique l’emplacement où copier *setup.exe* et tous les fichiers du package.

- `Path`

   Paramètre `String` facultatif.

   Indique l’emplacement de tous les packages requis disponibles.

- `SupportUrl`

   Paramètre `String` facultatif.

   Spécifie l’URL à fournir en cas d’échec de l’installation du programme d’amorçage.

- `Validate`

   Paramètre `Boolean` facultatif.

   Si `true`, le programme d’amorçage exécute la validation XSD sur les éléments de programme d’amorçage d’entrée spécifiés. La valeur par défaut de ce paramètre est `false`.

## <a name="remarks"></a>Notes

En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension> , qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task> . Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [classe de base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Exemple

L’exemple suivant utilise la tâche `GenerateBootstrapper` pour installer une application qui doit avoir le composant .NET Framework 2.0 installé au titre de prérequis.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <BootstrapperFile Include="Microsoft.Net.Framework.2.0">
            <ProductName>Microsoft .NET Framework 2.0</ProductName>
        </BootstrapperFile>
    </ItemGroup>

    <Target Name="BuildBootstrapper">
        <GenerateBootstrapper
            ApplicationFile="WindowsApplication1.application"
            ApplicationName="WindowsApplication1"
            ApplicationUrl="http://mycomputer"
            BootstrapperItems="@(BootstrapperFile)"
            OutputPath="C:\output" />
    </Target>

</Project>
```

## <a name="see-also"></a>Voir aussi

- [Tâches](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
