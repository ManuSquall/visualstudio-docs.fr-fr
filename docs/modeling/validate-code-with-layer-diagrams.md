---
title: Valider le code avec des diagrammes de dépendance
ms.date: 11/04/2016
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
ms.technology: vs-ide-modeling
ms.openlocfilehash: 63dc6c6b1307ae5d8b8be880815f5de5e782c6f5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31953644"
---
# <a name="validate-code-with-dependency-diagrams"></a>Valider le code avec des diagrammes de dépendance

**Dernières informations**: consultez [ce billet de blog](https://blogs.msdn.microsoft.com/visualstudioalm/2016/11/30/live-dependency-validation-in-visual-studio-2017/).

[Vidéo : Valider des dépendances de votre architecture en temps réel](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)

## <a name="why-use-dependency-diagrams"></a>Pourquoi utiliser des diagrammes de dépendance ?

Pour vous assurer que le code ne sont en conflit avec sa conception, validez votre code avec des diagrammes de dépendance dans Visual Studio. Cela peut vous aider à :

-   Recherchez des conflits entre les dépendances dans votre code et sur le diagramme de dépendances.

-   Rechercher des dépendances qui peuvent être affectées par les modifications proposées.

     Par exemple, vous pouvez modifier le diagramme de dépendances pour afficher les modifications de l’architecture potentielle, puis valider le code pour consulter les dépendances concernées.

-   Refactoriser ou migrer le code vers une conception différente.

     Rechercher le code ou les dépendances qui requièrent du travail lorsque vous déplacez le code vers une architecture différente.

 **Spécifications**

-   Visual Studio

-   Visual Studio sur votre serveur Team Foundation Build pour valider le code automatiquement avec Team Foundation Build

-   Une solution qui contient un projet de modélisation avec un diagramme de dépendances. Ce diagramme de dépendance doit être lié aux artefacts dans les projets c# ou Visual Basic que vous souhaitez valider. Consultez [créer des diagrammes de dépendance à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md).

 Pour connaître les versions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [Prise en charge des versions pour les outils d'architecture et de modélisation](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Vous pouvez valider le code manuellement à partir d’un diagramme de dépendances ouvert dans Visual Studio ou à partir d’une invite de commandes. Vous pouvez également valider le code automatiquement en exécutant des builds locales ou Team Foundation Build. Consultez [vidéo Channel 9 : création et valider votre architecture à l’aide de diagrammes de dépendance](http://go.microsoft.com/fwlink/?LinkID=252073).

> [!IMPORTANT]
>  Si vous souhaitez effectuer la validation de couche à l’aide de Team Foundation Build, vous devez aussi installer la même version de Visual Studio sur votre serveur de builds.

-   [Si un élément prend en charge la validation](#SupportsValidation)

-   [Inclure d’autres assemblys .NET et les projets pour la validation](#IncludeReferences)

-   [Valider manuellement le code](#ValidateManually)

-   [Valider automatiquement le code](#ValidateAuto)

-   [Résoudre les problèmes de validation de couche](#TroubleshootingValidation)

-   [Comprendre et résoudre les erreurs de validation de couche](#UnderstandingValidationErrors)

## <a name="live-dependency-validation"></a>Validation de dépendance dynamique

Dans cette version de Visual Studio, validation de dépendance se produit en temps réel, et les erreurs sont affichées immédiatement dans la fenêtre liste d’erreurs Visual Studio.

* La validation dynamique est pris en charge pour c# et Visual Basic.NET.

* Pour activer l’analyse de la solution complète lors de l’utilisation de la validation de dépendance dynamique, ouvrez les paramètres des options de la barre jaune s’affiche dans la liste d’erreurs.
 - Vous pouvez fermer définitivement de cette barre jaune si vous n’êtes pas intéressé de voir tous les problèmes d’architecture de votre solution.
 - Si vous n’activez pas l’analyse complète de la solution, l’analyse est effectuée uniquement pour les fichiers en cours de modification.<p />

* Lors de la mise à niveau des projets pour activer la validation dynamique, une boîte de dialogue affiche la progression de la conversion.

* Lors de la mise à jour un projet pour la validation de dépendance dynamique, la version du package NuGet est mis à niveau et la même pour tous les projets et est la version la plus récente en cours d’utilisation.

* Ajout d’un nouveau déclencheur de projet de validation dépendance une mise à jour du projet.

##  <a name="SupportsValidation"></a> Si un élément prend en charge la validation
 Vous pouvez lier des couches à des sites web, des documents Office, des fichiers texte brut et des fichiers de projets partagés entre plusieurs applications, mais le processus de validation ne les inclura pas. Aucune erreur de validation n'apparaîtra pour des références à des projets ou à des assemblys qui sont liés à des couches distinctes, lorsqu'aucune dépendance n'apparaît entre ces couches. De telles références ne sont pas considérées comme des dépendances à moins que le code utilise ces références.

1.  Dans le diagramme de dépendances, sélectionnez une ou plusieurs couches, cliquez sur votre sélection, puis cliquez sur **afficher les liens**.

2.  Dans **Explorateur de couches**, examinez le **prend en charge la Validation** colonne. Si la valeur faux lui est affectée, l’élément ne peut pas être validé.

##  <a name="IncludeReferences"></a> Inclure d’autres assemblys .NET et les projets pour la validation
 Lorsque vous faites glisser des éléments vers le diagramme de dépendances, les références aux assemblys .NET correspondants ou les projets sont ajoutés automatiquement à la **références de couche** dossier dans le projet de modélisation. Ce dossier contient des références aux assemblys et aux projets analysés pendant la validation. Vous pouvez inclure des autres assemblys .NET et des projets pour la validation sans manuellement les faire glisser vers le diagramme de dépendance.

1.  Dans **l’Explorateur de solutions**, cliquez sur le projet de modélisation ou **références de couche** dossier, puis cliquez sur **ajouter une référence**.

2.  Dans le **ajouter une référence** boîte de dialogue, sélectionnez les assemblys ou projets, puis cliquez sur **OK**.

##  <a name="ValidateManually"></a> Valider manuellement le code
 Si vous avez un diagramme de dépendances ouvert qui est lié à des éléments de solution, vous pouvez exécuter la **Validate** commande de raccourci à partir du diagramme. Vous pouvez également utiliser l’invite de commandes pour exécuter le **msbuild** avec la **/p: ValidateArchitecture** la valeur de propriété personnalisée **True**. Par exemple, lorsque vous apportez des modifications dans le code, exécutez la validation de couche régulièrement afin de pouvoir intercepter tôt les conflits de dépendance.

#### <a name="to-validate-code-from-an-open-dependency-diagram"></a>Pour valider le code à partir d’un diagramme ouvert de dépendance

1.  Avec le bouton droit de la surface du diagramme, puis cliquez sur **valider l’Architecture**.

    > [!NOTE]
    >  Par défaut, le **Action de génération** sur le fichier de diagramme (.layerdiagram) de dépendance est définie sur **Validate** afin que le diagramme soit inclus dans le processus de validation.

     Le **liste d’erreurs** fenêtre signale des erreurs qui se produisent. Pour plus d’informations sur les erreurs de validation, consultez [comprendre et résoudre les erreurs de validation de couche](#UnderstandingValidationErrors).

2.  Pour afficher la source de chaque erreur, double-cliquez sur l’erreur dans le **liste d’erreurs** fenêtre.

    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] peut afficher une carte de code à la place de la source de l'erreur. Cela se produit lorsque le code a une dépendance sur un assembly qui n’est pas spécifié par le diagramme de dépendance ou le code il manque une dépendance spécifiée par le diagramme de dépendances. Examinez la carte de code ou le code pour déterminer si la dépendance doit exister. Pour plus d’informations sur les cartes de code, consultez [mapper les dépendances dans vos solutions](../modeling/map-dependencies-across-your-solutions.md).

3.  Pour gérer les erreurs, consultez [gérer les erreurs de validation](#ManageErrors).

#### <a name="to-validate-code-at-the-command-prompt"></a>Pour valider le code à l'invite de commandes

1.  Ouvrez l'invite de commandes [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

2.  Choisissez l'une des valeurs suivantes :

    -   Pour valider le code par rapport à un projet de modélisation spécifique dans la solution, exécutez [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] avec la propriété personnalisée ci-dessous.

        ```
        msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
        ```

         - ou

         Accédez au dossier qui contient la modélisation (.modelproj) fichier projet et le diagramme de dépendances, puis exécutez [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] avec la propriété personnalisée suivante :

        ```
        msbuild /p:ValidateArchitecture=true
        ```

    -   Pour valider le code par rapport à tous les projets de modélisation dans la solution, exécutez [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] avec la propriété personnalisée suivante :

        ```
        msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
        ```

         - ou

         Accédez au dossier de solution, qui doit contenir un projet de modélisation contenant un diagramme de dépendances, puis exécutez [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] avec la propriété personnalisée suivante :

        ```
        msbuild /p:ValidateArchitecture=true
        ```

     Toutes les erreurs qui ont lieu seront répertoriées. Pour plus d’informations sur [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], consultez [MSBuild](../msbuild/msbuild.md) et [tâche MSBuild](../msbuild/msbuild-task.md).

 Pour plus d’informations sur les erreurs de validation, consultez [comprendre et résoudre les erreurs de validation de couche](#UnderstandingValidationErrors).

###  <a name="ManageErrors"></a> Gérer les erreurs de validation
 Pendant le processus de développement, vous pouvez supprimer certains conflits signalés pendant la validation. Par exemple, vous pouvez supprimer des erreurs que vous êtes déjà en train de traiter qui ne sont pas pertinentes dans le cadre de votre scénario spécifique. Lorsque vous supprimez une erreur, il est conseillé d'entrer un élément de travail dans [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)].

> [!WARNING]
>  Vous devez être connecté à un contrôle de code source (SSC, Source Code Control) TFS pour créer un élément de travail ou un lien vers celui-ci. Si vous essayez d'ouvrir une connexion à un autre contrôle de code source TFS, Visual Studio ferme automatiquement la solution actuelle. Vérifiez que vous êtes connecté au contrôle de code source TFS approprié avant d'essayer de créer un élément de travail ou un lien vers celui-ci. Dans les versions ultérieures de Visual Studio, les commandes de menu ne sont pas disponibles si vous n'êtes pas connecté à un contrôle de code source.

##### <a name="to-create-a-work-item-for-a-validation-error"></a>Pour créer un élément de travail pour une erreur de validation

-   Dans le **liste d’erreurs** fenêtre, cliquez sur l’erreur, pointez sur **créer un élément de travail**, puis cliquez sur le type d’élément de travail que vous souhaitez créer.

 Utilisez les tâches suivantes pour gérer les erreurs de validation dans le **liste d’erreurs** fenêtre :

|**To**|**Procédez comme suit**|
|------------|----------------------------|
|Supprimer des erreurs sélectionnées pendant la validation|Cliquez sur l’une ou plusieurs erreurs sélectionnées, pointez sur **gérer les erreurs de Validation**, puis cliquez sur **supprimer les erreurs**.<br /><br /> Les erreurs supprimées apparaissent barrées. Lors de la prochaine validation, ces erreurs ne s’afficheront pas.<br /><br /> Les erreurs supprimées sont suivies dans un fichier .suppressions pour le fichier de diagramme de dépendance correspondante.|
|Cesser de supprimer des erreurs sélectionnées|Cliquez sur l’ou les erreurs supprimées sélectionnées, pointez sur **gérer les erreurs de Validation**, puis cliquez sur **arrêter la suppression des erreurs**.<br /><br /> Les erreurs supprimées qui sont sélectionnées s’afficheront lors de la prochaine validation.|
|Restaurer toutes les erreurs supprimées dans le **liste d’erreurs** fenêtre|Avec le bouton droit n’importe où dans le **liste d’erreurs** fenêtre, pointez sur **gérer les erreurs de Validation**, puis cliquez sur **afficher les erreurs supprimées**.|
|Masquer toutes les erreurs supprimées à partir de la **liste d’erreurs** fenêtre|Avec le bouton droit n’importe où dans le **liste d’erreurs** fenêtre, pointez sur **gérer les erreurs de Validation**, puis cliquez sur **masquer les erreurs supprimées**.|

##  <a name="ValidateAuto"></a> Valider automatiquement le code
 Exécutez la validation de couche chaque fois que vous exécutez une build locale. Si votre équipe utilise Team Foundation Build, vous pouvez exécuter la validation de couche avec les archivages contrôlés que vous spécifiez en créant une tâche personnalisée MSBuild, puis utilisez les rapports de build pour collecter les erreurs de validation. Pour créer des builds d’archivage contrôlé, consultez [utiliser un processus de build d’archivage contrôlé pour valider les modifications](http://msdn.microsoft.com/Library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec).

#### <a name="to-validate-code-automatically-during-a-local-build"></a>Pour valider automatiquement le code au cours d'une build locale

-   Utilisez un éditeur de texte pour ouvrir le fichier projet de modélisation (.modelproj), puis y inclure la propriété suivante :

```
<ValidateArchitecture>true</ValidateArchitecture>
```

 \- ou -

1.  Dans **l’Explorateur de solutions**, cliquez sur le projet de modélisation qui contient le diagramme de dépendances ou des diagrammes, puis cliquez sur **propriétés**.

2.  Dans le **propriétés** fenêtre, définissez le projet de modélisation **valider l’Architecture** propriété **True**.

     Cela inclut le projet de modélisation dans le processus de validation.

3.  Dans **l’Explorateur de solutions**, cliquez sur le fichier de diagramme (.layerdiagram) de dépendances que vous souhaitez utiliser pour la validation.

4.  Dans le **propriétés** fenêtre, assurez-vous que du diagramme **Action de génération** est définie sur **Validate**.

     Cela inclut le diagramme de dépendances dans le processus de validation.

 Pour gérer les erreurs dans la fenêtre liste d’erreurs, consultez [gérer les erreurs de Validation](#ManageErrors).

#### <a name="to-validate-code-automatically-during-a-team-foundation-build"></a>Pour valider automatiquement le code au cours d’une build Team Foundation

1.  Dans **Team Explorer**, double-cliquez sur la définition de build, puis cliquez sur **processus**.

2.  Sous **paramètres du processus de génération**, développez **Compilation**et tapez la commande suivante dans le **Arguments MSBuild** paramètre :

     `/p:ValidateArchitecture=true`

 Pour plus d’informations sur les erreurs de validation, consultez [comprendre et résoudre les erreurs de validation de couche](#UnderstandingValidationErrors). Pour plus d'informations sur [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)], consultez :

-   [Build et release](/vsts/build-release/index)

-   [Utilisez le modèle par défaut pour votre processus de génération](http://msdn.microsoft.com/Library/43930b12-c21b-4599-a980-2995e3d16e31)

-   [Modifier une Build hérité qui est basé sur UpgradeTemplate.xaml](http://msdn.microsoft.com/Library/ee1a8259-1dd1-4a10-9563-66c5446ef41c)

-   [Personnaliser votre modèle de processus de génération](http://msdn.microsoft.com/Library/b94c58f2-ae6f-4245-bedb-82cd114f6039)

-   [Surveiller la progression d’une Build en cours d’exécution](http://msdn.microsoft.com/Library/e51e3bad-2d1d-4b7b-bfcc-c43439c6c8ef)

##  <a name="TroubleshootingValidation"></a> Résoudre les problèmes de validation de couche
 Le tableau suivant décrit les problèmes liés à la validation de couche et propose une résolution. Ces problèmes ne sont pas liés aux erreurs qui résultent de conflits entre le code et la conception. Pour plus d’informations sur ces erreurs, consultez [comprendre et résoudre les erreurs de validation de couche](#UnderstandingValidationErrors).

|**Problème**|**Cause possible**|**Résolution**|
|---------------|------------------------|--------------------|
|Les erreurs de validation ne se produisent pas comme prévu.|La validation ne fonctionne pas sur les diagrammes de dépendance qui sont copiés à partir d’autres diagrammes de dépendance dans l’Explorateur de solutions et qui se trouvent dans le même projet de modélisation. les diagrammes de dépendance qui sont copiés de cette façon contiennent les mêmes références que le diagramme d’origine de la dépendance.|Ajoutez un nouveau diagramme de dépendance pour le projet de modélisation.<br /><br /> Copier les éléments du diagramme de dépendance source vers le nouveau diagramme.|

##  <a name="UnderstandingValidationErrors"></a> Compréhension et résolution des erreurs de Validation de couche
 Lorsque vous validez du code par rapport à un diagramme de dépendances, les erreurs de validation se produisent lorsque le code est en conflit avec la conception. Par exemple, les conditions suivantes peuvent provoquer des erreurs de validation :

-   Un artefact est assigné à une couche inappropriée. Dans ce cas, déplacez l'artefact.

-   Un artefact, tel qu'une classe, utilise une autre classe d'une manière qui génère un conflit avec votre architecture. Dans ce cas, refactorisez le code pour supprimer la dépendance.

 Pour résoudre ces erreurs, mettez à jour le code de façon à ce que la validation ne génère plus d'erreur. Vous pouvez effectuer cette tâche de façon itérative.

 La section suivante décrit la syntaxe utilisée lors de ces erreurs, explique la signification de ces erreurs, et suggère des opérations pour les résoudre ou les gérer.

|**Syntaxe**|**Description**|
|----------------|---------------------|
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN* est un artefact associé à une couche sur le diagramme de dépendances.<br /><br /> *ArtifactTypeN* est le type de *ArtifactN*, comme un **classe** ou **méthode**, par exemple :<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|
|*NamespaceNameN*|Nom d'un espace de noms.|
|*LayerNameN*|Le nom d’une couche sur le diagramme de dépendances.|
|*DependencyType*|Le type de relation de dépendance entre *Artifact1* et *Artifact2*. Par exemple, *Artifact1* a un **appelle** relation avec *Artifact2*.|

|**Syntaxe de l’erreur**|**Description de l’erreur**|
|----------------------|---------------------------|
|DV0001 : **dépendance non valide**|Ce problème est signalé lorsqu’un élément de code (espace de noms, type, membre) est mappée vers des références de couche un élément de code mappé à une autre couche, mais il n’existe aucune flèche de dépendance entre ces couches dans le schéma de validation de dépendance contenant cette couches. Il s’agit d’une violation de contrainte de dépendance.|
|DV1001 : **nom de l’espace de noms non valide**|Ce problème est signalé dans un élément de code associé à une couche de propriété « Autorisé Namespace Names » ne contient pas l’espace de noms dans lequel cet élément de code est défini. Il s’agit d’une violation de contrainte d’attribution de noms. Notez que la syntaxe des « Noms de Namespace autorisé » est soit une liste de points-virgules, des espaces de noms dans le code associés à des éléments sont couche ne peuvent pas être définies.|
|DV1002 : **dépendance sur l’espace de noms unreferenceable**|Ce problème est signalé dans un élément de code associé à une couche et faisant référence à un autre élément de code défini dans un espace de noms qui est défini dans la propriété « Namespace Unreferenceable » de la couche. Il s’agit d’une violation de contrainte d’attribution de noms. Notez que la propriété « Espaces de noms Unreferenceable » est définie sous forme de liste séparés par des points-virgules des espaces de noms qui ne doivent pas être référencés dans les éléments de code associés à cette couche.|
|DV1003 : **nom d’espace de noms non autorisé**|Ce problème est signalé dans un élément de code associé à une couche de propriété « Interdits Namespace Names » contient l’espace de noms dans lequel cet élément de code est défini. Il s’agit d’une violation de contrainte d’attribution de noms. Notez que la propriété « Nom d’espace de noms non autorisé » est définie sous forme de liste séparés par des points-virgules des espaces de noms dans le code les éléments associés à cette couche ne doivent pas être définies.|
|DV3001 : **lien manquant**|Couche '*LayerName*'est liée à'*artefact*' qui est introuvable. Vérifiez qu'il ne manque aucune référence d'assembly.|*LayerName* lié à un artefact qui est introuvable. Par exemple, il manque peut-être un lien vers une classe car le projet de modélisation ne comporte pas de référence à l'assembly contenant la classe.|
|DV9001 : **l’analyse des erreurs internes détectées**|Il est possible que les résultats ne soient pas complets. Pour plus d'informations, consultez le journal des événements de build ou la fenêtre Sortie.|Consultez le journal détaillé des événements de build ou la fenêtre Sortie pour plus de détails.|


## <a name="see-also"></a>Voir aussi

- [Valider votre système pendant le développement](../modeling/validate-your-system-during-development.md)
- [Vidéo : Valider des dépendances de votre architecture en temps réel](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
