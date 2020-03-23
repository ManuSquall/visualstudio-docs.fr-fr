---
title: Événements de build, page du Concepteur de projets (C#)
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6629f41657a546ffb5fb48e0b6efb5f4f0dd50cb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596877"
---
# <a name="build-events-page-project-designer-c"></a>Événements de build, page du Concepteur de projets (C#)

Utilisez la page **Événements de build** du **Concepteur de projets** pour spécifier des instructions de configuration de build. Vous pouvez également spécifier les conditions dans lesquelles les événements post-build sont exécutés. Pour plus d’informations, voir [Comment : Spécifier les événements de construction (C)](../../ide/how-to-specify-build-events-csharp.md) et [comment : Spécifier les événements de construction (visual basic)](../../ide/how-to-specify-build-events-visual-basic.md).

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

Spécifie les commandes à exécuter à l’issue de la génération. Pour taper de longues commandes, cliquez sur **Edit Post-build** pour afficher la boîte de **dialogue de la ligne de commandement d’événements pré-construction/post-construction**.

> [!NOTE]
> Ajoutez une instruction `call` avant toutes les commandes post-build qui exécutent des fichiers .bat. Par exemple, `call C:\MyFile.bat` ou `call C:\MyFile.bat call C:\MyFile2.bat`.

**Exécuter l'événement post-build**

Spécifie les conditions suivantes pour l’événement post-build à exécuter, comme indiqué dans le tableau ci-dessous.

|Option|Résultats|
|------------|------------|
|**Toujours**|L’événement post-build est exécuté, que la build ait abouti ou échoué.|
|**En cas de build réussie**|L’événement post-build est exécuté si la build réussit. Ainsi, l’événement est exécuté même pour un projet à jour, à condition que la build soit un succès.|
|**Lorsque la build met à jour la sortie du projet**|L’événement post-build n’est exécuté que quand le fichier de sortie du compilateur (.exe ou .dll) est différent du fichier de sortie précédent. Ainsi, un événement post-build n’est pas exécuté si un projet est à jour.|

## <a name="in-the-project-file"></a>Dans le dossier du projet

Dans les versions précédentes de Visual Studio, lorsque vous modifiez le paramètre **PreBuildEvent** `PostBuildEvent` ou **PostBuildEvent** dans l’IDE, Visual Studio ajoute une propriété ou une `PreBuildEvent` propriété au fichier du projet. Ainsi, par exemple, si votre paramètre de ligne de commande **PreBuildEvent** dans l’IDE est le suivant :

```input
"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"
```

puis le paramètre de fichier de projet est :

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)" />
</PropertyGroup>
```

Pour les projets .NET Core, Visual Studio 2019 (et Visual Studio 2017 `PreBuild` `PostBuild` dans des mises à jour plus récentes) ajoute une cible MSBuild nommée ou pour les paramètres **PreBuildEvent** et **PostBuildEvent.** Ces cibles utilisent les **attributs BeforeTargets** et **AfterTargets,** que MSBuild reconnaît. Par exemple, pour l’exemple précédent, Visual Studio génère maintenant le code suivant :

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>
```

Pour un événement post-construction, `PostBuild` utilisez le `AfterTargets` `PostBuildEvent`nom et définissez l’attribut à .

```xml
<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
> Ces changements de dossiers de projet ont été apportés pour soutenir des projets de type SDK. Si vous migrez manuellement un fichier de projet de l’ancien format au `PreBuildEvent` `PostBuildEvent` format de style `PreBuild` `PostBuild` SDK, vous devez supprimer les propriétés et les remplacer par et les cibles comme indiqué dans le code précédent. Pour savoir comment savoir si votre projet est un projet de style SDK, consultez [le format du projet Check](/nuget/resources/check-project-format).

## <a name="see-also"></a>Voir aussi

- [Comment : Spécifier des événements de construction (visual basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Comment : Spécifier les événements de construction (C)](../../ide/how-to-specify-build-events-csharp.md)
- [Informations de référence sur les propriétés de projet](../../ide/reference/project-properties-reference.md)
- [Compilation et construction](../../ide/compiling-and-building-in-visual-studio.md)
