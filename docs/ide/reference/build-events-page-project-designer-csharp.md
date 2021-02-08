---
title: Événements de build, page du Concepteur de projets (C#)
description: Découvrez comment spécifier des instructions de configuration de Build. Vous pouvez également spécifier les conditions dans lesquelles les événements post-build sont exécutés.
ms.custom: SEO-VS-2020
ms.date: 10/17/2019
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- Project Designer, Build Events page
- pre-build events
- post-build events
ms.assetid: 3fff9ae5-213c-46ea-a660-1d70acb6c922
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 51b430a18a3d0934c16de19cbde82177a5f21f12
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836460"
---
# <a name="build-events-page-project-designer-c"></a>Événements de build, page du Concepteur de projets (C#)

Utilisez la page **Événements de build** du **Concepteur de projets** pour spécifier des instructions de configuration de build. Vous pouvez également spécifier les conditions dans lesquelles les événements post-build sont exécutés. Pour plus d’informations, consultez [Comment : spécifier des événements de build (C#)](../../ide/how-to-specify-build-events-csharp.md) et [Comment : spécifier des événements de build (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur

**Configuration**

Ce contrôle n’est pas modifiable dans cette page. Pour obtenir une description de ce contrôle, consultez [Générer, page du Concepteur de projets (C#)](../../ide/reference/build-page-project-designer-csharp.md).

**Plateforme**

Ce contrôle n’est pas modifiable dans cette page. Pour obtenir une description de ce contrôle, consultez [Générer, page du Concepteur de projets (C#)](../../ide/reference/build-page-project-designer-csharp.md).

**Ligne de commande de l'événement avant génération**

Spécifie les commandes à exécuter avant le début de la génération. Pour taper de longues commandes, cliquez sur **Modifier pré-build** pour afficher la [boîte de dialogue Ligne de commande de l’événement pré-build/post-build](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

> [!NOTE]
> Les événements pré-build ne fonctionnent pas si le projet est à jour et qu’aucune build n’est déclenchée.

**Ligne de commande d'événement après génération**

Spécifie les commandes à exécuter à l’issue de la génération. Pour taper de longues commandes, cliquez sur **modifier après génération** pour afficher la boîte de **dialogue ligne de commande de l’événement pré-build/après génération**.

> [!NOTE]
> Ajoutez une instruction `call` avant toutes les commandes post-build qui exécutent des fichiers .bat. Par exemple, `call C:\MyFile.bat` ou `call C:\MyFile.bat call C:\MyFile2.bat`.

**Exécuter l'événement post-build**

Spécifie les conditions suivantes pour l’événement post-build à exécuter, comme indiqué dans le tableau ci-dessous.

|Option|Résultats|
|------------|------------|
|**Toujours**|L’événement post-build est exécuté, que la build ait abouti ou échoué.|
|**En cas de build réussie**|L’événement post-build est exécuté si la build réussit. Ainsi, l’événement est exécuté même pour un projet à jour, à condition que la build soit un succès.|
|**Lorsque la build met à jour la sortie du projet**|L’événement post-build n’est exécuté que quand le fichier de sortie du compilateur (.exe ou .dll) est différent du fichier de sortie précédent. Ainsi, un événement post-build n’est pas exécuté si un projet est à jour.|

## <a name="in-the-project-file"></a>Dans le fichier projet

Dans les versions antérieures de Visual Studio, lorsque vous modifiez le paramètre **PreBuildEvent** ou **POSTBUILDEVENT** dans l’IDE, Visual Studio ajoute `PreBuildEvent` une `PostBuildEvent` propriété ou au fichier projet. Par exemple, si votre paramètre de ligne de commande **PreBuildEvent** dans l’IDE est le suivant :

```input
"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"
```

le paramètre du fichier projet est alors :

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)" />
</PropertyGroup>
```

Pour les projets .NET Core, Visual Studio 2019 (et Visual Studio 2017 dans les mises à jour plus récentes) ajoute une cible MSBuild nommée `PreBuild` ou `PostBuild` pour les paramètres **PreBuildEvent** et **PostBuildEvent** . Ces cibles utilisent les attributs **BeforeTargets** et **AfterTargets** , que MSBuild reconnaît. Par exemple, dans l’exemple précédent, Visual Studio génère désormais le code suivant :

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>
```

Pour un événement après génération, utilisez le nom `PostBuild` et affectez à l’attribut la valeur `AfterTargets` `PostBuildEvent` .

```xml
<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
> Ces modifications de fichier projet ont été apportées pour prendre en charge les projets de style SDK. Si vous migrez un fichier projet de l’ancien format vers le format de style SDK manuellement, vous devez supprimer les `PreBuildEvent` `PostBuildEvent` Propriétés et et les remplacer par les `PreBuild` cibles et, `PostBuild` comme indiqué dans le code précédent. Pour savoir comment savoir si votre projet est un projet de type SDK, consultez vérifier le [format du projet](/nuget/resources/check-project-format).

## <a name="see-also"></a>Voir aussi

- [Comment : spécifier des événements de build (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Comment : spécifier des événements de build (C#)](../../ide/how-to-specify-build-events-csharp.md)
- [Informations de référence sur les propriétés de projet](../../ide/reference/project-properties-reference.md)
- [Compilation et génération](../../ide/compiling-and-building-in-visual-studio.md)
