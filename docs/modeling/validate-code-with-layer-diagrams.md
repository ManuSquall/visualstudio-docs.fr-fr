---
title: Valider du code avec des diagrammes de dépendance
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
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 975fe8eac5657e245027a4811e50bbc93528cfe5
ms.sourcegitcommit: 273b657e115c1756adb84e0e56b6f2c709bcee76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80759701"
---
# <a name="validate-code-with-dependency-diagrams"></a>Valider du code avec des diagrammes de dépendance

## <a name="why-use-dependency-diagrams"></a>Pourquoi utiliser des diagrammes de dépendance?

Pour vous assurer que le code n’entre pas en conflit avec sa conception, validez votre code avec des diagrammes de dépendance dans Visual Studio. Cela peut vous aider à :

- Trouvez des conflits entre les dépendances dans votre code et les dépendances sur le diagramme de dépendance.

- Rechercher des dépendances qui peuvent être affectées par les modifications proposées.

   Par exemple, vous pouvez modifier le diagramme de dépendance pour afficher les modifications d’architecture potentielles, puis valider le code pour voir les dépendances affectées.

- Refactoriser ou migrer le code vers une conception différente.

   Recherchez le code ou les dépendances qui requièrent du travail lorsque vous déplacez le code vers une architecture différente.

**Configuration requise**

- Visual Studio

  Pour créer un diagramme de dépendance pour un projet .NET Core, vous devez avoir Visual Studio 2019 version 16.2 ou plus tard.

- Une solution qui a un projet de modélisation avec un diagramme de dépendance. Ce diagramme de dépendance doit être lié à des artefacts dans les projets C ou Visual Basic que vous souhaitez valider. Voir [Créer des diagrammes de dépendance à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md).

Pour voir quelles éditions de Visual Studio prennent en charge cette fonctionnalité, voir [le support Edition pour l’architecture et les outils de modélisation](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

Vous pouvez valider le code manuellement à partir d’un diagramme de dépendance ouverte dans Visual Studio ou à partir d’une invite de commande. Vous pouvez également valider automatiquement le code lors de l’exécution de builds locaux ou Azure Pipelines construit. Voir [Channel 9 Vidéo: Concevez et validez votre architecture à l’aide de diagrammes de dépendance](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture).

> [!IMPORTANT]
> Si vous souhaitez exécuter la validation de couche à l’aide de Team Foundation Server (TFS), vous devez également installer la même version de Visual Studio sur votre serveur de construction.

## <a name="live-dependency-validation"></a>Validation de dépendance en direct

La validation de la dépendance se produit en temps réel, et les erreurs sont affichées immédiatement dans la **liste d’erreurs**.

* La validation en direct est prise en charge pour le C et Visual Basic.

* Pour activer l’analyse complète des solutions lors de l’utilisation de la validation de la dépendance en direct, ouvrez les paramètres d’options à partir de la barre d’or qui apparaît dans la **liste d’erreurs**.

  - Vous pouvez définitivement rejeter la barre d’or si vous n’êtes pas intéressé à voir tous les problèmes architecturaux dans votre solution.
  - Si vous n’activez pas l’analyse complète des solutions, l’analyse est effectuée uniquement pour les fichiers en cours de modification.

* Lors de la mise à niveau des projets pour permettre la validation en direct, un dialogue montre l’évolution de la conversion.

* Lors de la mise à jour d’un projet de validation de la dépendance en direct, la version du paquet NuGet est mise à niveau pour être la même pour tous les projets, et est la version la plus élevée en cours d’utilisation.

* L’ajout d’un nouveau projet de validation de la dépendance déclenche une mise à jour du projet.

## <a name="see-if-an-item-supports-validation"></a>Voir si un élément prend en charge la validation

Vous pouvez lier des couches à des sites Web, des documents Office, des fichiers texte simple et des fichiers dans des projets qui sont partagés sur plusieurs applications, mais le processus de validation ne les inclura pas. Aucune erreur de validation n’apparaîtra pour des références à des projets ou à des assemblys qui sont liés à des couches distinctes, lorsqu’aucune dépendance n’apparaît entre ces couches. De telles références ne sont pas considérées comme des dépendances à moins que le code utilise ces références.

1. Sur le diagramme de dépendance, sélectionnez une ou plusieurs couches, cliquez à droite sur votre sélection, puis cliquez sur **Voir les liens**.

2. Dans **Layer Explorer**, regardez la colonne de validation des **supports.** Si la valeur faux lui est affectée, l'élément ne peut pas être validé.

## <a name="include-other-net-assemblies-and-projects-for-validation"></a>Inclure d’autres projets et assemblys .NET pour la validation

Lorsque vous faites glisser des éléments vers le diagramme de dépendance, les références aux assemblages ou projets .NET correspondants sont ajoutées automatiquement au dossier **De références de couche** dans le projet de modélisation. Ce dossier contient des références aux assemblys et aux projets analysés pendant la validation. Vous pouvez inclure d’autres assemblages et projets .NET pour validation sans les traîner manuellement vers le diagramme de dépendance.

1. Dans **Solution Explorer**, cliquez à droite sur le projet de modélisation ou le dossier De références de **couche,** puis cliquez sur **Ajouter la référence**.

2. Dans la boîte de dialogue **Add Reference,** sélectionnez les assemblages ou les projets, puis cliquez **sur OK**.

## <a name="validate-code-manually"></a>Valider manuellement le code

Si vous avez un diagramme de dépendance ouverte qui est lié à des éléments de solution, vous pouvez exécuter la commande de raccourci **Valider** à partir du diagramme. Vous pouvez également utiliser l’invite de commande pour exécuter la commande **de msbuild** avec la propriété personnalisée **/p:ValidateArchitecture** réglée à **True**. Par exemple, lorsque vous apportez des modifications dans le code, exécutez la validation de couche régulièrement afin de pouvoir intercepter tôt les conflits de dépendance.

### <a name="validate-code-from-an-open-dependency-diagram"></a>Valider le code à partir d’un diagramme de dépendance ouverte

1. Cliquez à droite sur la surface du diagramme, puis cliquez sur **Validate Architecture**.

    > [!NOTE]
    > Par défaut, la propriété **Build Action** sur le diagramme de dépendance (.layerdiagram) fichier est configuré pour **valider** de sorte que le diagramme est inclus dans le processus de validation.

     La fenêtre **Error List** signale toutes les erreurs qui se produisent. Pour plus d’informations sur les erreurs de validation, voir [problèmes de validation de couche De dépannage](#troubleshoot-layer-validation-issues).

2. Pour afficher la source de chaque erreur, cliquez double sur l’erreur dans la fenêtre **Error List.**

    > [!NOTE]
    > Visual Studio peut afficher une carte de code au lieu de la source de l’erreur. Cela se produit lorsque le code a une dépendance à l’égard d’un assemblage qui n’est pas spécifié par le diagramme de dépendance, ou que le code manque une dépendance spécifiée par le diagramme de dépendance. Examinez la carte de code ou le code pour déterminer si la dépendance doit exister. Pour plus d’informations sur les cartes de code, voir [les dépendances map dans vos solutions](../modeling/map-dependencies-across-your-solutions.md).

3. Pour gérer les erreurs, voir [résoudre les erreurs de validation des couches](#resolve-layer-validation-errors).

### <a name="validate-code-at-the-command-prompt"></a>Valider le code à l’invite de commande

1. Ouvrez l’invite de commande Visual Studio.

2. Choisissez l’un des éléments suivants :

   - Pour valider le code par rapport à un projet de modélisation spécifique dans la solution, exécutez MSBuild avec la propriété personnalisée suivante.

       ```
       msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
       ```

     - ou -

       Naviguez vers le dossier qui contient le fichier du projet de modélisation (.modelproj) et le diagramme de dépendance, puis exécutez MSBuild avec la propriété personnalisée suivante :

       ```
       msbuild /p:ValidateArchitecture=true
       ```

   - Pour valider le code contre tous les projets de modélisation de la solution, exécutez MSBuild avec la propriété personnalisée suivante :

       ```
       msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
       ```

     - ou -

       Naviguez vers le dossier de solution, qui doit contenir un projet de modélisation qui contient un diagramme de dépendance, puis exécutez MSBuild avec la propriété personnalisée suivante:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

     Toutes les erreurs qui ont lieu seront répertoriées. Pour plus d’informations sur MSBuild, voir [MSBuild](../msbuild/msbuild.md) et [MSBuild Task](../msbuild/msbuild-task.md).

   Pour plus d’informations sur les erreurs de validation, voir [problèmes de validation de couche De dépannage](#troubleshoot-layer-validation-issues).

### <a name="manage-validation-errors"></a>Gérer les erreurs de validation

Pendant le processus de développement, vous pouvez supprimer certains conflits signalés pendant la validation. Par exemple, vous pouvez supprimer des erreurs que vous êtes déjà en train de traiter qui ne sont pas pertinentes dans le cadre de votre scénario spécifique. Lorsque vous supprimez une erreur, il est de bonne pratique de enregistrer un élément de travail dans Team Foundation.

> [!WARNING]
> Vous devez être connecté à un contrôle de code source (SSC, Source Code Control) TFS pour créer un élément de travail ou un lien vers celui-ci. Si vous essayez d'ouvrir une connexion à un autre contrôle de code source TFS, Visual Studio ferme automatiquement la solution actuelle. Vérifiez que vous êtes connecté au contrôle de code source TFS approprié avant d’essayer de créer un élément de travail ou un lien vers celui-ci. Dans les versions ultérieures de Visual Studio, les commandes de menu ne sont pas disponibles si vous n'êtes pas connecté à un contrôle de code source.

#### <a name="create-a-work-item-for-a-validation-error"></a>Créer un élément de travail pour une erreur de validation

- Dans la fenêtre **Error List,** cliquez à droite sur l’erreur, pointez-vous pour **créer l’élément de travail,** puis cliquez sur le type d’élément de travail que vous souhaitez créer.

Utilisez ces tâches pour gérer les erreurs de validation dans la fenêtre **Error List** :

|**À**|**Suivez ces étapes**|
|-|-|
|Supprimer des erreurs sélectionnées pendant la validation|Cliquez à droite sur les erreurs sélectionnées, pointez-le pour **gérer les erreurs de validation,** puis cliquez sur Suppress **Errors**.<br /><br /> Les erreurs supprimées apparaissent barrées. Lors de la prochaine validation, ces erreurs ne s’afficheront pas.<br /><br /> Les erreurs supprimées sont suivies dans un fichier .suppressions pour le fichier de diagramme de dépendance correspondant.|
|Cesser de supprimer des erreurs sélectionnées|Cliquez à droite sur l’erreur ou les erreurs supprimées sélectionnées, pointez vers **gérer les erreurs de validation,** puis cliquez sur Stop **Suppressing Errors**.<br /><br /> Les erreurs supprimées qui sont sélectionnées s'afficheront lors de la prochaine validation.|
|Restaurer toutes les erreurs supprimées dans la fenêtre de la **liste d’erreurs**|Cliquez à droite n’importe où dans la fenêtre de la **liste d’erreurs,** pointez pour **gérer les erreurs de validation,** puis cliquez sur **Afficher toutes les erreurs supprimées**.|
|Masquer toutes les erreurs supprimées de la fenêtre de la **liste d’erreurs**|Cliquez à droite n’importe où dans la fenêtre de la **liste d’erreurs,** pointez pour **gérer les erreurs de validation,** puis cliquez sur **Masquer toutes les erreurs supprimées**.|

## <a name="validate-code-automatically"></a>Valider automatiquement le code

Exécutez la validation de couche chaque fois que vous exécutez une build locale. Si votre équipe utilise Azure DevOps, vous pouvez effectuer la validation de la couche avec des check-ins fermés, que vous pouvez spécifier en créant une tâche MSBuild personnalisée, et utiliser des rapports de construction pour collecter des erreurs de validation. Pour créer des builds d’enregistrement fermés, voir [l’enregistrement fermé tfVC](/azure/devops/pipelines/build/triggers).

### <a name="to-validate-code-automatically-during-a-local-build"></a>Pour valider automatiquement le code au cours d'une build locale

Utilisez un éditeur de texte pour ouvrir le fichier projet de modélisation (.modelproj), puis y inclure la propriété suivante :

```xml
<ValidateArchitecture>true</ValidateArchitecture>
```

\- ou -

1. Dans **Solution Explorer**, cliquez à droite sur le projet de modélisation qui contient le diagramme de dépendance ou des diagrammes, puis cliquez sur **Propriétés**.

2. Dans la fenêtre **Propriétés,** définissez la propriété **Validate Architecture** du projet de modélisation à **True**.

    Cela inclut le projet de modélisation dans le processus de validation.

3. Dans **Solution Explorer**, cliquez sur le diagramme de dépendance (.layerdiagram) fichier que vous souhaitez utiliser pour validation.

4. Dans la fenêtre **Propriétés,** assurez-vous que la propriété **Build Action** du diagramme est configuré pour **valider**.

    Cela inclut le diagramme de dépendance dans le processus de validation.

Pour gérer les erreurs dans la fenêtre Error List, voir [les erreurs de validation de la couche Resolve](#resolve-layer-validation-errors).

## <a name="troubleshoot-layer-validation-issues"></a>Résoudre les problèmes de validation de couche

Le tableau suivant décrit les problèmes liés à la validation de couche et propose une résolution. Ces problèmes ne sont pas liés aux erreurs qui résultent de conflits entre le code et la conception. Pour plus d’informations sur ces erreurs, voir [problèmes de validation de couche Deshoot](#troubleshoot-layer-validation-issues).

|**Problème**|**Possible Cause**|**Résolution :**|
|-|-|-|
|Les erreurs de validation ne se produisent pas comme prévu.|La validation ne fonctionne pas sur des diagrammes de dépendance qui sont copiés à partir d’autres diagrammes de dépendance dans Solution Explorer et qui sont dans le même projet de modélisation. les diagrammes de dépendance qui sont copiés de cette façon contiennent les mêmes références que le diagramme de dépendance d’origine.|Ajoutez un nouveau diagramme de dépendance au projet de modélisation.<br /><br /> Copiez les éléments du diagramme de dépendance source au nouveau diagramme.|

## <a name="resolve-layer-validation-errors"></a>Résoudre les erreurs de validation de la couche

Lorsque vous validez le code par rapport à un diagramme de dépendance, des erreurs de validation se produisent lorsque le code entre en conflit avec la conception. Par exemple, les conditions suivantes peuvent provoquer des erreurs de validation :

- Un artefact est assigné à une couche inappropriée. Dans ce cas, déplacez l’artefact.

- Un artefact, tel qu'une classe, utilise une autre classe d'une manière qui génère un conflit avec votre architecture. Dans ce cas, refactorisez le code pour supprimer la dépendance.

Pour résoudre ces erreurs, mettez à jour le code de façon à ce que la validation ne génère plus d’erreur. Vous pouvez effectuer cette tâche de façon itérative.

La section suivante décrit la syntaxe utilisée lors de ces erreurs, explique la signification de ces erreurs, et suggère des opérations pour les résoudre ou les gérer.

|**Syntaxe**|**Description**|
|-|-|
|*ArtifactN*(*ArtifactTypen*)|*ArtifactN* est un artefact qui est associé à une couche sur le diagramme de dépendance.<br /><br /> *ArtifactTypeN* est le type *d’ArtéfactN*, comme une **classe** ou une **méthode**, par exemple:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|
|*NamespaceNameN*|Nom d'un espace de noms.|
|*LayerNameN*|Le nom d’une couche sur le diagramme de dépendance.|
|*DependencyType*|Le type de relation de dépendance entre *Artifact1* et *Artifact2*. Par exemple, *Artifact1* a une relation **Appels** avec *Artifact2*.|

| **Syntaxe de l'erreur** | **Description d’erreur** |
|-|-|
| DV0001: **Dépendance invalide** | Ce problème est signalé lorsqu’un élément de code (namespace, type, membre) cartographié à une couche fait référence à un élément de code cartographié sur une autre couche, mais il n’y a pas de flèche de dépendance entre ces couches dans le diagramme de validation de dépendance contenant ces couches. Il s’agit d’une violation de la contrainte de dépendance. |
| DV1001: **Nom invalide de l’espace de nom** | Ce problème est rapporté sur un élément de code associé à une couche qui "Noms de nom autorisés" propriété ne contient pas l’espace nom dans lequel cet élément de code est défini. Il s’agit d’une violation de la contrainte de nommage. Notez que la syntaxe de "Noms De Nom autorisés" doit être une liste semi-colon des espaces de nom dans lequel les éléments de code associés sont couche sont autorisés à être définis. |
| DV1002: **Dépendance à l’espace de nom indéfférencé** | Ce problème est rapporté sur un élément de code associé à une couche et faisant référence à un autre élément de code défini dans un espace de nom qui est défini dans la propriété "Unreferenceable Namespace" de la couche. Il s’agit d’une violation de la contrainte de nommage. Notez que la propriété "Unreferenceable Namespaces" est définie comme une liste séparée semi-colon des espaces de nom qui ne devraient pas être référencés dans les éléments de code associés à cette couche. |
| DV1003: **Nom de namespace refusé** | Ce problème est rapporté sur un élément de code associé à une couche qui "Noms de nom refusés" propriété contient l’espace nom dans lequel cet élément de code est défini. Il s’agit d’une violation de la contrainte de nommage. Notez que la propriété " Nom de namespace refusé " est définie comme une liste séparée semi-colon des espaces de nom dans lequel les éléments de code associés à cette couche ne doivent pas être définis. |
| DV2001: **Présence de diagramme de couche** | Ce problème est rapporté sur un projet qui n’inclut pas un fichier de diagramme de dépendance, mais se réfère aux analyseurs de validation de dépendance. Si la validation de dépendance n’a pas été utilisée, vous pouvez supprimer "Microsoft.DependencyValidation.Analyzers" directement de Solution Explorer ou supprimer cet avertissement. Pour ajouter un diagramme de dépendance voir [Créer des diagrammes de dépendance à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md). |
| DV2002: **Base de types non cartographiés** | Ce problème est signalé lorsqu’un élément de code n’est cartographié à aucune couche. |
| DV3001: **Lien manquant** | Couche '*LayerName*' liens vers '*Artifact*' qui ne peuvent pas être trouvés. Vérifiez qu'il ne manque aucune référence d'assembly. |
| DV9001 : **Une analyse architecturale a révélé des erreurs internes** | Il est possible que les résultats ne soient pas complets. Pour plus d'informations, consultez le journal des événements de build ou la fenêtre Sortie. |

## <a name="see-also"></a>Voir aussi

- [Validation de dépendance en direct dans Visual Studio](https://devblogs.microsoft.com/devops/live-dependency-validation-in-visual-studio-2017/)
- [Validation de votre système pendant le développement](../modeling/validate-your-system-during-development.md)
- [Vidéo : Validez vos dépendances d’architecture en temps réel](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
