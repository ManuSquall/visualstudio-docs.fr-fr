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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: ac75be41d547905b122284fa09a654be368d73e7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53907824"
---
# <a name="validate-code-with-dependency-diagrams"></a>Valider du code avec des diagrammes de dépendance

## <a name="why-use-dependency-diagrams"></a>Pourquoi utiliser des diagrammes de dépendance ?

Pour vous assurer que le code n’entre en conflit avec sa conception, validez votre code avec des diagrammes de dépendance dans Visual Studio. Cela peut vous aider à :

- Rechercher des conflits entre les dépendances dans votre code et sur le diagramme de dépendances.

- Rechercher des dépendances qui peuvent être affectées par les modifications proposées.

   Par exemple, vous pouvez modifier le diagramme de dépendances pour afficher les modifications de l’architecture potentielle, puis valider le code pour voir les dépendances concernées.

- Refactoriser ou migrer le code vers une conception différente.

   Rechercher le code ou les dépendances qui requièrent du travail lorsque vous déplacez le code vers une architecture différente.

**Spécifications**

- Visual Studio

- Une solution qui a un projet de modélisation avec un diagramme de dépendances. Ce diagramme de dépendance doit être lié aux artefacts dans les projets c# ou Visual Basic que vous souhaitez valider. Consultez [créer des diagrammes de dépendance à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md).

> [!NOTE]
> Diagrammes de dépendance ne sont pas pris en charge pour les projets .NET Core dans Visual Studio 2017.

Pour voir quelles éditions de Visual Studio prennent en charge cette fonctionnalité, consultez [prise en charge de l’édition pour l’architecture et les outils de modélisation](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

Vous pouvez valider le code manuellement à partir d’un diagramme de dépendances ouvert dans Visual Studio ou à partir d’une invite de commandes. Vous pouvez également valider le code automatiquement lors de l’exécution de builds locales ou les Pipelines Azure génère. Consultez [vidéo Channel 9 : Concevoir et valider votre architecture à l’aide de diagrammes de dépendance](http://go.microsoft.com/fwlink/?LinkID=252073).

> [!IMPORTANT]
> Si vous souhaitez exécuter la validation de couche à l’aide de Team Foundation Server (TFS), vous devez également installer la même version de Visual Studio sur votre serveur de builds.

## <a name="live-dependency-validation"></a>Validation des dépendances en direct

Validation de dépendance se produit en temps réel et les erreurs sont affichées immédiatement dans le **liste d’erreurs**.

* Validation en direct est pris en charge pour c# et Visual Basic.

* Pour activer l’analyse complète de la solution lors de l’utilisation de validation des dépendances en direct, ouvrez les paramètres des options à partir de la barre jaune s’affiche dans le **liste d’erreurs**.

   - Vous pouvez fermer définitivement de la barre jaune si vous n’êtes pas intéressé de voir tous les problèmes d’architecture dans votre solution.
   - Si vous n’activez pas l’analyse complète de la solution, l’analyse est effectuée uniquement pour les fichiers en cours de modification.

* Lors de la mise à niveau de projets pour activer la validation en direct, une boîte de dialogue affiche la progression de la conversion.

* Lors de la mise à jour un projet pour la validation de dépendance en direct, la version du package NuGet est mis à niveau pour être la même pour tous les projets et est la version la plus récente en cours d’utilisation.

* Ajout d’une mise à jour du projet un nouveaux déclencheurs de projet de validation de dépendance.

## <a name="see-if-an-item-supports-validation"></a>Voir si un élément prend en charge la validation

Vous pouvez lier des couches à des sites Web, les documents Office, les fichiers de texte brut et les fichiers dans les projets qui sont partagés entre plusieurs applications, mais le processus de validation ne les inclut pas. Aucune erreur de validation n’apparaîtra pour des références à des projets ou à des assemblys qui sont liés à des couches distinctes, lorsqu’aucune dépendance n’apparaît entre ces couches. De telles références ne sont pas considérées comme des dépendances à moins que le code utilise ces références.

1.  Sur le diagramme de la dépendance, sélectionnez une ou plusieurs couches, cliquez sur votre sélection et puis cliquez sur **afficher les liens**.

2.  Dans **Explorateur de couches**, examinez le **prend en charge la Validation** colonne. Si la valeur faux lui est affectée, l’élément ne peut pas être validé.

## <a name="include-other-net-assemblies-and-projects-for-validation"></a>Inclure d’autres projets et assemblys .NET pour la validation

Lorsque vous faites glisser des éléments vers le diagramme de dépendance, les références aux projets ou assemblys .NET correspondants sont ajoutés automatiquement à la **références de couche** dossier dans le projet de modélisation. Ce dossier contient des références aux assemblys et aux projets analysés pendant la validation. Vous pouvez inclure des autres assemblys .NET et les projets pour la validation sans manuellement en faisant glisser vers le diagramme de dépendance.

1.  Dans **l’Explorateur de solutions**, cliquez sur le projet de modélisation ou **références de couche** dossier, puis cliquez sur **ajouter une référence**.

2.  Dans le **ajouter une référence** boîte de dialogue, sélectionnez les assemblys ou les projets, puis cliquez sur **OK**.

## <a name="validate-code-manually"></a>Valider manuellement le code

Si vous disposez d’un diagramme de dépendance ouvert qui est lié aux éléments de solution, vous pouvez exécuter la **Validate** commande de raccourci à partir du diagramme. Vous pouvez également utiliser l’invite de commandes pour exécuter le **msbuild** commande avec le **ValidateArchitecture** la valeur de propriété personnalisée **True**. Par exemple, lorsque vous apportez des modifications dans le code, exécutez la validation de couche régulièrement afin de pouvoir intercepter tôt les conflits de dépendance.

### <a name="validate-code-from-an-open-dependency-diagram"></a>Valider le code à partir d’un diagramme de dépendances open

1.  Avec le bouton droit de la surface du diagramme, puis cliquez sur **valider l’Architecture**.

    > [!NOTE]
    > Par défaut, le **Action de génération** propriété sur le fichier de diagramme (.layerdiagram) de dépendance est définie sur **Validate** afin que le diagramme soit inclus dans le processus de validation.

     Le **liste d’erreurs** fenêtre signale les erreurs qui surviennent. Pour plus d’informations sur les erreurs de validation, consultez [comprendre et résoudre les erreurs de validation de couche](#UnderstandingValidationErrors).

2.  Pour afficher la source de chaque erreur, double-cliquez sur l’erreur dans le **liste d’erreurs** fenêtre.

    > [!NOTE]
    > Visual Studio peut afficher une carte de code au lieu de la source de l’erreur. Cela se produit lorsque le code a une dépendance sur un assembly qui n’est pas spécifié par le diagramme de dépendance ou le code, il manque une dépendance qui est spécifiée par le diagramme de dépendances. Examinez la carte de code ou le code pour déterminer si la dépendance doit exister. Pour plus d’informations sur les cartes de code, consultez [mapper les dépendances dans vos solutions](../modeling/map-dependencies-across-your-solutions.md).

3.  Pour gérer les erreurs, consultez [gérer les erreurs de validation](#ManageErrors).

### <a name="validate-code-at-the-command-prompt"></a>Valider le code à l’invite de commandes

1. Ouvrez l’invite de commandes de Visual Studio.

2. Choisissez l'une des valeurs suivantes :

   - Pour valider le code par rapport à un projet de modélisation spécifique dans la solution, exécutez MSBuild avec la propriété personnalisée suivante.

       ```
       msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
       ```

     - ou

       Accédez au dossier qui contient le projet de modélisation (.modelproj) de fichiers et la dépendance de diagramme et puis exécutez MSBuild avec la propriété personnalisée suivante :

       ```
       msbuild /p:ValidateArchitecture=true
       ```

   - Pour valider le code par rapport à tous les projets de modélisation dans la solution, exécutez MSBuild avec la propriété personnalisée suivante :

       ```
       msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
       ```

     - ou

       Accédez au dossier de solution, qui doit contenir un projet de modélisation contenant un diagramme de dépendance et puis exécutez MSBuild avec la propriété personnalisée suivante :

       ```
       msbuild /p:ValidateArchitecture=true
       ```

     Toutes les erreurs qui ont lieu seront répertoriées. Pour plus d’informations sur MSBuild, consultez [MSBuild](../msbuild/msbuild.md) et [tâche MSBuild](../msbuild/msbuild-task.md).

   Pour plus d’informations sur les erreurs de validation, consultez [comprendre et résoudre les erreurs de validation de couche](#UnderstandingValidationErrors).

### <a name="manage-validation-errors"></a>Gérer les erreurs de validation

Pendant le processus de développement, vous pouvez supprimer certains conflits signalés pendant la validation. Par exemple, vous pouvez supprimer des erreurs que vous êtes déjà en train de traiter qui ne sont pas pertinentes dans le cadre de votre scénario spécifique. Lorsque vous supprimez une erreur, il est conseillé de connecter un élément de travail dans Team Foundation.

> [!WARNING]
> Vous devez être connecté à un contrôle de code source (SSC, Source Code Control) TFS pour créer un élément de travail ou un lien vers celui-ci. Si vous essayez d'ouvrir une connexion à un autre contrôle de code source TFS, Visual Studio ferme automatiquement la solution actuelle. Vérifiez que vous êtes connecté au contrôle de code source TFS approprié avant d'essayer de créer un élément de travail ou un lien vers celui-ci. Dans les versions ultérieures de Visual Studio, les commandes de menu ne sont pas disponibles si vous n'êtes pas connecté à un contrôle de code source.

#### <a name="create-a-work-item-for-a-validation-error"></a>Créer un élément de travail pour une erreur de validation

- Dans le **liste d’erreurs** fenêtre, cliquez sur l’erreur, pointez sur **créer un élément de travail**, puis cliquez sur le type d’élément de travail que vous souhaitez créer.

Utilisez ces tâches pour gérer les erreurs de validation dans le **liste d’erreurs** fenêtre :

|**To**|**Procédez comme suit**|
|-|-|
|Supprimer des erreurs sélectionnées pendant la validation|Avec le bouton droit à un ou plusieurs erreurs sélectionnées, pointez sur **gérer les erreurs de Validation**, puis cliquez sur **supprimer les erreurs**.<br /><br /> Les erreurs supprimées apparaissent barrées. Lors de la prochaine validation, ces erreurs ne s’afficheront pas.<br /><br /> Les erreurs supprimées sont suivies dans un fichier .suppressions pour le fichier de diagramme de dépendance correspondante.|
|Cesser de supprimer des erreurs sélectionnées|Avec le bouton droit de l’ou les erreurs supprimées sélectionnées, pointez sur **gérer les erreurs de Validation**, puis cliquez sur **arrêter la suppression des erreurs**.<br /><br /> Les erreurs supprimées qui sont sélectionnées s’afficheront lors de la prochaine validation.|
|Restaurer toutes les erreurs supprimées dans le **liste d’erreurs** fenêtre|Avec le bouton droit n’importe où dans le **liste d’erreurs** fenêtre, pointez sur **gérer les erreurs de Validation**, puis cliquez sur **afficher les erreurs supprimées**.|
|Masquer toutes les erreurs supprimées à partir de la **liste d’erreurs** fenêtre|Avec le bouton droit n’importe où dans le **liste d’erreurs** fenêtre, pointez sur **gérer les erreurs de Validation**, puis cliquez sur **masquer les erreurs supprimées**.|

## <a name="validate-code-automatically"></a>Valider automatiquement le code

Exécutez la validation de couche chaque fois que vous exécutez une build locale. Si votre équipe utilise Azure DevOps, vous pouvez effectuer la validation de couche avec les archivages, que vous pouvez spécifier en créant une tâche MSBuild personnalisée et utiliser les rapports de build pour collecter les erreurs de validation. Pour créer des builds d’archivage contrôlé, consultez [TFVC archivage contrôlé](/azure/devops/pipelines/build/triggers#gated).

### <a name="to-validate-code-automatically-during-a-local-build"></a>Pour valider automatiquement le code au cours d'une build locale

Utilisez un éditeur de texte pour ouvrir le fichier projet de modélisation (.modelproj), puis y inclure la propriété suivante :

```xml
<ValidateArchitecture>true</ValidateArchitecture>
```

\- ou -

1.  Dans **l’Explorateur de solutions**, cliquez sur le projet de modélisation qui contient la dépendance ou les diagrammes, puis cliquez sur **propriétés**.

2.  Dans le **propriétés** fenêtre, définissez le projet de modélisation **valider l’Architecture** propriété **True**.

    Cela inclut le projet de modélisation dans le processus de validation.

3.  Dans **l’Explorateur de solutions**, cliquez sur le fichier de diagramme (.layerdiagram) de dépendance que vous souhaitez utiliser pour la validation.

4.  Dans le **propriétés** fenêtre, assurez-vous que le diagramme **Action de génération** propriété est définie sur **Validate**.

    Cela inclut le diagramme de dépendances dans le processus de validation.

Pour gérer les erreurs dans la fenêtre liste d’erreurs, consultez [gérer les erreurs de Validation](#ManageErrors).

## <a name="troubleshoot-layer-validation-issues"></a>Résoudre les problèmes de validation de couche

Le tableau suivant décrit les problèmes liés à la validation de couche et propose une résolution. Ces problèmes ne sont pas liés aux erreurs qui résultent de conflits entre le code et la conception. Pour plus d’informations sur ces erreurs, consultez [comprendre et résoudre les erreurs de validation de couche](#UnderstandingValidationErrors).

|**Problème**|**Cause possible**|**Résolution**|
|-|-|-|
|Les erreurs de validation ne se produisent pas comme prévu.|La validation ne fonctionne pas sur des diagrammes de dépendance qui sont copiés à partir d’autres diagrammes de dépendance dans l’Explorateur de solutions et qui se trouvent dans le même projet de modélisation. diagrammes de dépendance qui sont copiés de cette façon contiennent les mêmes références que le diagramme de dépendance d’origine.|Ajoutez un nouveau diagramme de dépendances au projet de modélisation.<br /><br /> Copiez les éléments depuis le diagramme de dépendance source vers le nouveau diagramme.|

## <a name="resolve-layer-validation-errors"></a>Résoudre les erreurs de validation de couche

Lorsque vous validez le code par rapport à un diagramme de dépendances, les erreurs de validation se produisent lorsque le code est en conflit avec la conception. Par exemple, les conditions suivantes peuvent provoquer des erreurs de validation :

- Un artefact est assigné à une couche inappropriée. Dans ce cas, déplacez l'artefact.

- Un artefact, tel qu'une classe, utilise une autre classe d'une manière qui génère un conflit avec votre architecture. Dans ce cas, refactorisez le code pour supprimer la dépendance.

Pour résoudre ces erreurs, mettez à jour le code de façon à ce que la validation ne génère plus d'erreur. Vous pouvez effectuer cette tâche de façon itérative.

La section suivante décrit la syntaxe utilisée lors de ces erreurs, explique la signification de ces erreurs, et suggère des opérations pour les résoudre ou les gérer.

|**Syntaxe**|**Description**|
|-|-|
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN* est un artefact associé à une couche sur le diagramme de dépendances.<br /><br /> *ArtifactTypeN* est le type de *ArtifactN*, comme un **classe** ou **méthode**, par exemple :<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|
|*NamespaceNameN*|Nom d'un espace de noms.|
|*LayerNameN*|Le nom d’une couche sur le diagramme de dépendances.|
|*DependencyType*|Le type de relation de dépendance entre *Artifact1* et *Artifact2*. Par exemple, *Artifact1* a un **appels** relation avec *Artifact2*.|

| **Syntaxe de l’erreur** | **Description de l’erreur** |
|-|-|
| DV0001 : **Dépendance non valide** | Ce problème est signalé lorsqu’un élément de code (espace de noms, type, membre) mappée à une référence de couche un élément de code mappé à une autre couche, mais il n’existe aucune flèche de dépendance entre ces couches dans le diagramme de validation de dépendance contenant cette couches. Il s’agit d’une violation de contrainte de dépendance. |
| DV1001 : **Nom de l’espace de noms non valide** | Ce problème est signalé sur un élément de code associé à une couche de propriété de « Autorisé de noms Namespace » ne contienne pas l’espace de noms dans lequel cet élément de code est défini. Il s’agit d’une violation de contrainte d’affectation de noms. Notez que la syntaxe de « Autorisé de noms Namespace » est une liste de point-virgule des espaces de noms dans le code associés à des éléments constituent la couche sont autorisés à être définis. |
| DV1002 : **Dépendance sur l’espace de noms à ne pas référencer** | Ce problème est signalé sur un élément de code associé à une couche et faisant référence à un autre élément de code défini dans un espace de noms qui est défini dans la propriété « À ne pas référencer Namespace » de la couche. Il s’agit d’une violation de contrainte d’affectation de noms. Notez que la propriété « Espaces de noms à ne pas référencer » est définie comme une liste séparée par des points-virgules des espaces de noms qui ne doivent pas être référencés dans les éléments de code associés à cette couche. |
| DV1003 : **Nom de l’espace de noms interdit** | Ce problème est signalé sur un élément de code associé à une couche de propriété de « Interdites des noms Namespace » contient l’espace de noms dans lequel cet élément de code est défini. Il s’agit d’une violation de contrainte d’affectation de noms. Notez que la propriété « Nom d’espace de noms non autorisé » est définie comme une liste séparée par des points-virgules des espaces de noms dans le code les éléments associés à cette couche ne doivent pas être définis. |
| DV3001 : **Lien manquant** | Couche «*LayerName*'établit un lien vers'*artefact*' qui est introuvable. Vérifiez qu'il ne manque aucune référence d'assembly. |
| DV9001 : **Analyse de l’architecture erreurs internes détecté** | Il est possible que les résultats ne soient pas complets. Pour plus d'informations, consultez le journal des événements de build ou la fenêtre Sortie. |

## <a name="see-also"></a>Voir aussi

- [Validation de dépendances dynamique dans Visual Studio 2017](https://blogs.msdn.microsoft.com/devops/2016/11/30/live-dependency-validation-in-visual-studio-2017/)
- [Valider votre système pendant le développement](../modeling/validate-your-system-during-development.md)
- [Vidéo : Valider les dépendances de votre architecture en temps réel](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)