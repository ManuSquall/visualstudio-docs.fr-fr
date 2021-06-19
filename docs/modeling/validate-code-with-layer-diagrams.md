---
title: Valider du code avec des diagrammes de dépendance
description: Découvrez que pour vous assurer que le code n’est pas en conflit avec sa conception, vous devez valider votre code avec des diagrammes de dépendance dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, validating
- validation, dependency diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, dependency diagrams
- MSBuild, validating code
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1f2d62433d150f61e9a7e21cceb20eb715a0767a
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388358"
---
# <a name="validate-code-with-dependency-diagrams"></a>Valider du code avec des diagrammes de dépendance

## <a name="why-use-dependency-diagrams"></a>Pourquoi utiliser des diagrammes de dépendance ?

Pour vous assurer que le code n’est pas en conflit avec sa conception, validez votre code avec des diagrammes de dépendance dans Visual Studio. Cela peut vous aider à :

- Recherchez les conflits entre les dépendances dans votre code et les dépendances sur le diagramme de dépendance.

- Rechercher des dépendances qui peuvent être affectées par les modifications proposées.

   Par exemple, vous pouvez modifier le diagramme de dépendance pour afficher les modifications d’architecture potentielles, puis valider le code pour voir les dépendances affectées.

- Refactoriser ou migrer le code vers une conception différente.

   Recherchez le code ou les dépendances qui requièrent du travail lorsque vous déplacez le code vers une architecture différente.

**Configuration requise**

- Visual Studio

  Pour créer un diagramme de dépendance pour un projet .NET Core, vous devez disposer de Visual Studio 2019 version 16,2 ou ultérieure.

- Solution avec un projet de modélisation avec un diagramme de dépendance. Ce diagramme de dépendance doit être lié aux artefacts dans les projets C# ou Visual Basic que vous souhaitez valider. Consultez [créer des diagrammes de dépendance à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md).

Pour connaître les éditions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [prise en charge d’édition pour les outils d’architecture et de modélisation](../modeling/analyze-and-model-your-architecture.md#VersionSupport).

Vous pouvez valider le code manuellement à partir d’un diagramme de dépendance ouvert dans Visual Studio ou à partir d’une invite de commandes. Vous pouvez également valider le code automatiquement lors de l’exécution de builds locales ou de Azure Pipelines builds. Voir [vidéo Channel 9 : concevoir et valider votre architecture à l’aide de diagrammes de dépendances](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture).

> [!IMPORTANT]
> Si vous souhaitez exécuter la validation de couche à l’aide de Team Foundation Server (TFS), vous devez également installer la même version de Visual Studio sur votre serveur de builds.

## <a name="live-dependency-validation"></a>Validation de dépendances dynamiques

La validation des dépendances se produit en temps réel, et les erreurs sont affichées immédiatement dans le **liste d’erreurs**.

* La validation en direct est prise en charge pour C# et Visual Basic.

* Pour activer l’analyse complète de la solution lors de l’utilisation de la validation de dépendances dynamique, ouvrez les paramètres d’options à partir de la barre dorée qui apparaît dans la **liste d’erreurs**.

  - Vous pouvez ignorer définitivement la barre dorée si vous ne souhaitez pas voir tous les problèmes architecturaux de votre solution.
  - Si vous n’activez pas l’analyse complète de la solution, l’analyse est effectuée uniquement pour les fichiers en cours de modification.

* Lors de la mise à niveau de projets pour activer la validation dynamique, une boîte de dialogue affiche la progression de la conversion.

* Lors de la mise à jour d’un projet pour la validation de dépendances dynamique, la version du package NuGet est mise à niveau pour être la même pour tous les projets, et est la version la plus récente en cours d’utilisation.

* L’ajout d’un nouveau projet de validation de dépendance déclenche une mise à jour de projet.

## <a name="see-if-an-item-supports-validation"></a>Voir si un élément prend en charge la validation

Vous pouvez lier des couches à des sites Web, à des documents Office, à des fichiers texte brut et à des fichiers dans des projets qui sont partagés entre plusieurs applications, mais le processus de validation ne les inclut pas. Aucune erreur de validation n’apparaîtra pour des références à des projets ou à des assemblys qui sont liés à des couches distinctes, lorsqu’aucune dépendance n’apparaît entre ces couches. De telles références ne sont pas considérées comme des dépendances à moins que le code utilise ces références.

1. Dans le diagramme de dépendances, sélectionnez une ou plusieurs couches, cliquez avec le bouton droit sur votre sélection, puis cliquez sur **afficher les liens**.

2. Dans l **'Explorateur de couches**, examinez la colonne **prend en charge la validation** . Si la valeur faux lui est affectée, l'élément ne peut pas être validé.

## <a name="include-other-net-assemblies-and-projects-for-validation"></a>Inclure d’autres projets et assemblys .NET pour la validation

Lorsque vous faites glisser des éléments vers le diagramme de dépendance, les références aux assemblys .NET ou aux projets correspondants sont ajoutées automatiquement au dossier **références de couche** dans le projet de modélisation. Ce dossier contient des références aux assemblys et aux projets analysés pendant la validation. Vous pouvez inclure d’autres assemblys et projets .NET pour la validation sans les faire glisser manuellement vers le diagramme de dépendance.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet de modélisation ou le dossier **références de couche** , puis cliquez sur **Ajouter une référence**.

2. Dans la boîte de dialogue **Ajouter une référence** , sélectionnez les assemblys ou les projets, puis cliquez sur **OK**.

## <a name="validate-code-manually"></a>Valider manuellement le code

Si vous avez un diagramme de dépendance ouvert qui est lié aux éléments de solution, vous pouvez exécuter la commande **valider** le raccourci à partir du diagramme. Vous pouvez également utiliser l’invite de commandes pour exécuter la commande **MSBuild** avec la propriété personnalisée **/p : ValidateArchitecture** définie sur **true**. Par exemple, lorsque vous apportez des modifications dans le code, exécutez la validation de couche régulièrement afin de pouvoir intercepter tôt les conflits de dépendance.

### <a name="validate-code-from-an-open-dependency-diagram"></a>Valider le code à partir d’un diagramme de dépendance ouvert

1. Cliquez avec le bouton droit sur la surface du diagramme, puis cliquez sur **valider l’architecture**.

    > [!NOTE]
    > Par défaut, la propriété **action de génération** sur le fichier du diagramme de dépendance (. layerdiagram) est définie sur **valider** afin que le diagramme soit inclus dans le processus de validation.

     La fenêtre **liste d’erreurs** signale toutes les erreurs qui se produisent. Pour plus d’informations sur les erreurs de validation, consultez [résoudre les problèmes de validation de couche](#troubleshoot-layer-validation-issues).

2. Pour afficher la source de chaque erreur, double-cliquez sur l’erreur dans la fenêtre **liste d’erreurs** .

    > [!NOTE]
    > Visual Studio peut afficher une carte de code à la place de la source de l’erreur. Cela se produit lorsque le code a une dépendance sur un assembly qui n’est pas spécifié par le diagramme de dépendance, ou qu’une dépendance spécifiée par le diagramme de dépendance est manquante dans le code. Examinez la carte de code ou le code pour déterminer si la dépendance doit exister. Pour plus d’informations sur les cartes de code, consultez [mapper les dépendances entre vos solutions](../modeling/map-dependencies-across-your-solutions.md).

3. Pour gérer les erreurs, consultez [résoudre les erreurs de validation de couche](#resolve-layer-validation-errors).

### <a name="validate-code-at-the-command-prompt"></a>Valider le code à l’invite de commandes

1. Ouvrez l’invite de commandes de Visual Studio.

2. Choisissez l’un des éléments suivants :

   - Pour valider le code par rapport à un projet de modélisation spécifique dans la solution, exécutez MSBuild avec la propriété personnalisée suivante.

       ```
       msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
       ```

     - ou -

       Accédez au dossier qui contient le fichier de projet de modélisation (. modelproj) et le diagramme de dépendance, puis exécutez MSBuild avec la propriété personnalisée suivante :

       ```
       msbuild /p:ValidateArchitecture=true
       ```

   - Pour valider le code par rapport à tous les projets de modélisation dans la solution, exécutez MSBuild avec la propriété personnalisée suivante :

       ```
       msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
       ```

     - ou -

       Accédez au dossier de la solution, qui doit contenir un projet de modélisation qui contient un diagramme de dépendance, puis exécutez MSBuild avec la propriété personnalisée suivante :

       ```
       msbuild /p:ValidateArchitecture=true
       ```

     Toutes les erreurs qui ont lieu seront répertoriées. Pour plus d’informations sur MSBuild, consultez [MSBuild](../msbuild/msbuild.md) et [tâche MSBuild](../msbuild/msbuild-task.md).

   Pour plus d’informations sur les erreurs de validation, consultez [résoudre les problèmes de validation de couche](#troubleshoot-layer-validation-issues).

### <a name="manage-validation-errors"></a>Gérer les erreurs de validation

Pendant le processus de développement, vous pouvez supprimer certains conflits signalés pendant la validation. Par exemple, vous pouvez supprimer des erreurs que vous êtes déjà en train de traiter qui ne sont pas pertinentes dans le cadre de votre scénario spécifique. Lorsque vous supprimez une erreur, il est conseillé de consigner un élément de travail dans Team Foundation.

> [!WARNING]
> Vous devez être connecté à un contrôle de code source (SSC, Source Code Control) TFS pour créer un élément de travail ou un lien vers celui-ci. Si vous essayez d'ouvrir une connexion à un autre contrôle de code source TFS, Visual Studio ferme automatiquement la solution actuelle. Vérifiez que vous êtes connecté au contrôle de code source TFS approprié avant d’essayer de créer un élément de travail ou un lien vers celui-ci. Dans les versions ultérieures de Visual Studio, les commandes de menu ne sont pas disponibles si vous n'êtes pas connecté à un contrôle de code source.

#### <a name="create-a-work-item-for-a-validation-error"></a>Créer un élément de travail pour une erreur de validation

- Dans la fenêtre **liste d’erreurs** , cliquez avec le bouton droit sur l’erreur, pointez sur **créer un élément de travail**, puis cliquez sur le type d’élément de travail que vous souhaitez créer.

Utilisez les tâches suivantes pour gérer les erreurs de validation dans la fenêtre **liste d’erreurs** :

|**To**|**Procédez comme suit**|
|-|-|
|Supprimer des erreurs sélectionnées pendant la validation|Cliquez avec le bouton droit sur une ou plusieurs erreurs sélectionnées, pointez sur **gérer les erreurs de validation**, puis cliquez sur supprimer les **Erreurs**.<br /><br /> Les erreurs supprimées apparaissent barrées. Lors de la prochaine validation, ces erreurs ne s’afficheront pas.<br /><br /> Les erreurs supprimées sont suivies dans un fichier. suppressions pour le fichier de diagramme de dépendance correspondant.|
|Cesser de supprimer des erreurs sélectionnées|Cliquez avec le bouton droit sur l’erreur ou les erreurs supprimées sélectionnées, pointez sur **gérer les erreurs de validation**, puis cliquez sur arrêter la suppression des **Erreurs**.<br /><br /> Les erreurs supprimées qui sont sélectionnées s'afficheront lors de la prochaine validation.|
|Restaurer toutes les erreurs supprimées dans la fenêtre **liste d’erreurs**|Cliquez avec le bouton droit n’importe où dans la fenêtre de **liste d’erreurs** , pointez sur **gérer les erreurs de validation**, puis cliquez sur **afficher toutes les erreurs supprimées**.|
|Masquer toutes les erreurs supprimées de la fenêtre **liste d’erreurs**|Cliquez avec le bouton droit n’importe où dans la fenêtre de **liste d’erreurs** , pointez sur **gérer les erreurs de validation**, puis cliquez sur **Masquer toutes les erreurs supprimées**.|

## <a name="validate-code-automatically"></a>Valider automatiquement le code

Exécutez la validation de couche chaque fois que vous exécutez une build locale. Si votre équipe utilise Azure DevOps, vous pouvez effectuer une validation de couche avec des archivages contrôlés, que vous pouvez spécifier en créant une tâche MSBuild personnalisée et utiliser des rapports de build pour collecter les erreurs de validation. Pour créer des builds d’archivage contrôlé, consultez [archivage contrôlé TFVC](/azure/devops/pipelines/build/triggers).

### <a name="to-validate-code-automatically-during-a-local-build"></a>Pour valider automatiquement le code au cours d'une build locale

Utilisez un éditeur de texte pour ouvrir le fichier projet de modélisation (.modelproj), puis y inclure la propriété suivante :

```xml
<ValidateArchitecture>true</ValidateArchitecture>
```

\- ou -

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet de modélisation qui contient le ou les diagrammes de dépendance, puis cliquez sur **Propriétés**.

2. Dans la fenêtre **Propriétés** , affectez à la propriété **valider l’architecture** du projet de modélisation la **valeur true**.

    Cela inclut le projet de modélisation dans le processus de validation.

3. Dans **Explorateur de solutions**, cliquez sur le fichier de diagramme de dépendance (. layerdiagram) que vous souhaitez utiliser pour la validation.

4. Dans la fenêtre **Propriétés** , assurez-vous que la propriété **action de génération** du diagramme est définie sur **valider**.

    Cela comprend le diagramme de dépendance dans le processus de validation.

Pour gérer les erreurs dans la fenêtre de Liste d’erreurs, consultez [résoudre les erreurs de validation de couche](#resolve-layer-validation-errors).

## <a name="troubleshoot-layer-validation-issues"></a>Résoudre les problèmes de validation de couche

Le tableau suivant décrit les problèmes liés à la validation de couche et propose une résolution. Ces problèmes ne sont pas liés aux erreurs qui résultent de conflits entre le code et la conception. Pour plus d’informations sur ces erreurs, consultez [résoudre les problèmes de validation de couche](#troubleshoot-layer-validation-issues).

|**Problème**|**Cause possible**|**Résolution :**|
|-|-|-|
|Les erreurs de validation ne se produisent pas comme prévu.|La validation ne fonctionne pas sur les diagrammes de dépendance qui sont copiés à partir d’autres diagrammes de dépendance dans Explorateur de solutions et qui se trouvent dans le même projet de modélisation. les diagrammes de dépendance copiés de cette façon contiennent les mêmes références que le diagramme de dépendance d’origine.|Ajoutez un nouveau diagramme de dépendance au projet de modélisation.<br /><br /> Copiez les éléments du diagramme de dépendance source vers le nouveau diagramme.|

## <a name="resolve-layer-validation-errors"></a>Résoudre les erreurs de validation de couche

Lorsque vous validez du code par rapport à un diagramme de dépendance, des erreurs de validation se produisent lorsque le code est en conflit avec la conception. Par exemple, les conditions suivantes peuvent provoquer des erreurs de validation :

- Un artefact est assigné à une couche inappropriée. Dans ce cas, déplacez l’artefact.

- Un artefact, tel qu'une classe, utilise une autre classe d'une manière qui génère un conflit avec votre architecture. Dans ce cas, refactorisez le code pour supprimer la dépendance.

Pour résoudre ces erreurs, mettez à jour le code de façon à ce que la validation ne génère plus d’erreur. Vous pouvez effectuer cette tâche de façon itérative.

La section suivante décrit la syntaxe utilisée lors de ces erreurs, explique la signification de ces erreurs, et suggère des opérations pour les résoudre ou les gérer.

|**Syntaxe**|**Description**|
|-|-|
|*Artefactn*(*ArtifactTypeN*)|*Artefactn* est un artefact associé à une couche sur le diagramme de dépendance.<br /><br /> *ArtifactTypeN* est le type d' *artefactn*, tel qu’une **classe** ou une **méthode**, par exemple :<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|
|*NamespaceNameN*|Nom d'un espace de noms.|
|*LayerNameN*|Nom d’une couche sur le diagramme de dépendance.|
|*DependencyType*|Type de relation de dépendance entre *artefact 1* et *Artefact2*. Par exemple, *artefact 1* a une relation d' **appels** avec *Artefact2*.|

| **Syntaxe de l'erreur** | **Description de l’erreur** |
|-|-|
| DV0001 : **dépendance non valide** | Ce problème est signalé lorsqu’un élément de code (espace de noms, type, membre) mappé à une couche fait référence à un élément de code mappé à une autre couche, mais qu’il n’existe aucune flèche de dépendance entre ces couches dans le diagramme de validation des dépendances contenant ces couches. Il s’agit d’une violation de contrainte de dépendance. |
| DV1001 : **nom d’espace de noms non valide** | Ce problème est signalé sur un élément de code associé à une couche dans laquelle la propriété « noms d’espaces de noms autorisés » ne contient pas l’espace de noms dans lequel cet élément de code est défini. Il s’agit d’une violation de contrainte de nom. Notez que la syntaxe de « noms d’espaces de noms autorisés » doit être une liste d’espaces de noms dans laquelle les éléments de code associés à sont des éléments de code autorisés à être définis. |
| DV1002 : **dépendance sur un espace de noms non référencé** | Ce problème est signalé sur un élément de code associé à une couche et référençant un autre élément de code défini dans un espace de noms défini dans la propriété espace de noms non référencé de la couche. Il s’agit d’une violation de contrainte de nom. Notez que la propriété « espaces de noms non référencés » est définie sous la forme d’une liste d’espaces de noms séparés par des points-virgules qui ne doivent pas être référencés dans les éléments de code associés à cette couche. |
| DV1003 : **nom d’espace de noms non autorisé** | Ce problème est signalé sur un élément de code associé à une couche dans laquelle la propriété « noms d’espaces de noms interdits » contient l’espace de noms dans lequel cet élément de code est défini. Il s’agit d’une violation de contrainte de nom. Notez que la propriété « nom d’espace de noms non autorisé » est définie sous la forme d’une liste d’espaces de noms séparés par des points-virgules, dans laquelle les éléments de code associés à cette couche ne doivent pas être définis. |
| DV2001 : **présence du diagramme de couche** | Ce problème est signalé sur un projet qui n’inclut pas de fichier de diagramme de dépendance, mais fait référence aux analyseurs de validation des dépendances. Si la validation de dépendance n’a pas été utilisée, vous pouvez supprimer « Microsoft. DependencyValidation. Analyzers » directement à partir de Explorateur de solutions ou supprimer cet avertissement. Pour ajouter un diagramme de dépendance, consultez [créer des diagrammes de dépendance à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md). |
| DV2002 : **base des types non mappés** | Ce problème est signalé lorsqu’un élément de code n’est mappé à aucune couche. |
| DV3001 : **lien manquant** | La couche «*NomCouche*» est liée à «*artefact*», qui est introuvable. Vérifiez qu'il ne manque aucune référence d'assembly. |
| DV9001 : les **analyses architecturales ont trouvé des erreurs internes** | Il est possible que les résultats ne soient pas complets. Pour plus d'informations, consultez le journal des événements de build ou la fenêtre Sortie. |

## <a name="see-also"></a>Voir aussi

- [Validation de dépendances dynamiques dans Visual Studio](https://devblogs.microsoft.com/devops/live-dependency-validation-in-visual-studio-2017/)
- [Validation de votre système pendant le développement](../modeling/validate-your-system-during-development.md)
- [Vidéo : valider vos dépendances d’architecture en temps réel](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
