---
title: Valider du code avec des diagrammes de couche | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, validating
- validation, layer diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, layer diagrams
- MSBuild, validating code
ms.assetid: 70cbe55d-4b33-4355-b0a7-88c770a6f75c
caps.latest.revision: 84
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 45b82ece15cfef4d313764027c0220453a6d4849
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75845437"
---
# <a name="validate-code-with-layer-diagrams"></a>Valider du code avec des diagrammes de couche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour vous assurer que le code n'est pas en conflit avec sa conception, validez votre code avec des diagrammes de couche dans Visual Studio. Cela peut vous aider à :

- Rechercher des conflits entre des dépendances dans votre code et des dépendances sur le diagramme de couche.

- Rechercher des dépendances qui peuvent être affectées par les modifications proposées.

   Par exemple, vous pouvez modifier le diagramme de couche pour afficher les modifications apportées à l'architecture potentielle, puis valider le code afin de consulter les dépendances concernées.

- Refactoriser ou migrer le code vers une conception différente.

   Recherchez le code ou les dépendances qui requièrent du travail lorsque vous déplacez le code vers une architecture différente.

  **Configuration requise**

- Visual Studio

- Visual Studio sur votre serveur Team Foundation Build pour valider le code automatiquement avec Team Foundation Build

- Une solution qui inclut un projet de modélisation avec un diagramme de couche. Ce diagramme de couche doit être lié aux artefacts dans les projets Visual C# .NET ou Visual Basic .NET que vous souhaitez valider. Consultez [créer des diagrammes de couche à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md).

  Pour connaître les versions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

  Vous pouvez valider manuellement le code depuis un diagramme de couche ouvert dans Visual Studio ou depuis une invite de commandes. Vous pouvez également valider le code automatiquement en exécutant des builds locales ou Team Foundation Build. Voir [vidéo Channel 9 : concevoir et valider votre architecture à l’aide de diagrammes de couche](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture).

> [!IMPORTANT]
> Si vous souhaitez effectuer la validation de couche à l'aide de Team Foundation Build, vous devez aussi installer la même version de Visual Studio sur votre serveur de builds.

- [Voir si un élément prend en charge la validation](#SupportsValidation)

- [Inclure d’autres projets et assemblys .NET pour la validation](#IncludeReferences)

- [Valider manuellement le code](#ValidateManually)

- [Valider automatiquement le code](#ValidateAuto)

- [Résoudre les problèmes de validation de couche](#TroubleshootingValidation)

- [Comprendre et résoudre des erreurs de validation de couche](#UnderstandingValidationErrors)

## <a name="see-if-an-item-supports-validation"></a><a name="SupportsValidation"></a> Vérifier si un élément prend en charge la validation
 Vous pouvez lier des couches à des sites web, des documents Office, des fichiers texte brut et des fichiers de projets partagés entre plusieurs applications, mais le processus de validation ne les inclura pas. Aucune erreur de validation n’apparaîtra pour des références à des projets ou à des assemblys qui sont liés à des couches distinctes, lorsqu’aucune dépendance n’apparaît entre ces couches. De telles références ne sont pas considérées comme des dépendances à moins que le code utilise ces références.

1. Dans le diagramme de couche, sélectionnez une ou plusieurs couches, cliquez avec le bouton droit sur votre sélection, puis cliquez sur **afficher les liens**.

2. Dans l **'Explorateur de couches**, examinez la colonne **prend en charge la validation** . Si la valeur faux lui est affectée, l'élément ne peut pas être validé.

## <a name="include-other-net-assemblies-and-projects-for-validation"></a><a name="IncludeReferences"></a> Inclure d’autres assemblys .NET et des projets pour la validation
 Lorsque vous faites glisser des éléments vers le diagramme de couche, les références aux assemblys .NET ou aux projets correspondants sont ajoutées automatiquement au dossier **références de couche** dans le projet de modélisation. Ce dossier contient des références aux assemblys et aux projets analysés pendant la validation. Vous pouvez également inclure d'autres assemblys .NET et des projets pour qu'ils soient validés sans les faire glisser manuellement vers le diagramme de couche.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet de modélisation ou le dossier **références de couche** , puis cliquez sur **Ajouter une référence**.

2. Dans la boîte de dialogue **Ajouter une référence** , sélectionnez les assemblys ou les projets, puis cliquez sur **OK**.

## <a name="validate-code-manually"></a><a name="ValidateManually"></a> Valider le code manuellement
 Si vous avez un diagramme de couche ouvert qui est lié aux éléments de solution, vous pouvez exécuter la commande **valider** le raccourci à partir du diagramme. Vous pouvez également utiliser l’invite de commandes pour exécuter la commande **MSBuild** avec la propriété personnalisée **/p : ValidateArchitecture** définie sur **true**. Par exemple, lorsque vous apportez des modifications dans le code, exécutez la validation de couche régulièrement afin de pouvoir intercepter tôt les conflits de dépendance.

#### <a name="to-validate-code-from-an-open-layer-diagram"></a>Pour valider le code à partir d'un diagramme de couche ouvert

1. Cliquez avec le bouton droit sur la surface du diagramme, puis cliquez sur **valider l’architecture**.

    > [!NOTE]
    > Par défaut, la propriété **action de génération** du fichier de diagramme de couche (. layerdiagram) est définie sur **valider** afin que le diagramme soit inclus dans le processus de validation.

     La fenêtre **liste d’erreurs** signale toutes les erreurs qui se produisent. Pour plus d’informations sur les erreurs de validation, consultez [comprendre et résoudre les erreurs de validation de couche](#UnderstandingValidationErrors).

2. Pour afficher la source de chaque erreur, double-cliquez sur l’erreur dans la fenêtre **liste d’erreurs** .

    > [!NOTE]
    > [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] peut afficher une carte de code à la place de la source de l’erreur. Cela se produit lorsque le code a une dépendance sur un assembly qui n'est pas spécifié par le diagramme de couche ou lorsqu'une dépendance spécifiée par le diagramme de couche manque dans le code. Examinez la carte de code ou le code pour déterminer si la dépendance doit exister. Pour plus d’informations sur les cartes de code, consultez [mapper les dépendances entre vos solutions](../modeling/map-dependencies-across-your-solutions.md).

3. Pour gérer les erreurs, consultez [gérer les erreurs de validation](#ManageErrors).

#### <a name="to-validate-code-at-the-command-prompt"></a>Pour valider le code à l'invite de commandes

1. Ouvrez l'invite de commandes [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

2. Choisissez l’un des éléments suivants :

   - Pour valider le code par rapport à un projet de modélisation spécifique dans la solution, exécutez [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] avec la propriété personnalisée ci-dessous.

     ```
     msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
     ```

     - ou -

       Accédez au dossier qui contient le fichier du projet de modélisation (.modelproj) et le diagramme de couche, puis exécutez [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] avec la propriété personnalisée suivante :

     ```
     msbuild /p:ValidateArchitecture=true
     ```

   - Pour valider le code par rapport à tous les projets de modélisation dans la solution, exécutez [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] avec la propriété personnalisée suivante :

     ```
     msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
     ```

     - ou -

       Accédez au dossier de solution, qui doit contenir un projet de modélisation contenant un diagramme de couche, puis exécutez [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] avec la propriété personnalisée suivante :

     ```
     msbuild /p:ValidateArchitecture=true
     ```

     Toutes les erreurs qui ont lieu seront répertoriées. Pour plus d’informations sur [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , consultez [MSBuild](../msbuild/msbuild.md) et [tâche MSBuild](../msbuild/msbuild-task.md).

   Pour plus d’informations sur les erreurs de validation, consultez [comprendre et résoudre les erreurs de validation de couche](#UnderstandingValidationErrors).

### <a name="manage-validation-errors"></a><a name="ManageErrors"></a> Gérer les erreurs de validation
 Pendant le processus de développement, vous pouvez supprimer certains conflits signalés pendant la validation. Par exemple, vous pouvez supprimer des erreurs que vous êtes déjà en train de traiter qui ne sont pas pertinentes dans le cadre de votre scénario spécifique. Lorsque vous supprimez une erreur, il est conseillé d’entrer un élément de travail dans [!INCLUDE[esprfound](../includes/esprfound-md.md)].

> [!WARNING]
> Vous devez être connecté à un contrôle de code source (SSC, Source Code Control) TFS pour créer un élément de travail ou un lien vers celui-ci. Si vous essayez d'ouvrir une connexion à un autre contrôle de code source TFS, Visual Studio ferme automatiquement la solution actuelle. Vérifiez que vous êtes connecté au contrôle de code source TFS approprié avant d’essayer de créer un élément de travail ou un lien vers celui-ci. Dans les versions ultérieures de Visual Studio, les commandes de menu ne sont pas disponibles si vous n'êtes pas connecté à un contrôle de code source.

##### <a name="to-create-a-work-item-for-a-validation-error"></a>Pour créer un élément de travail pour une erreur de validation

- Dans la fenêtre **liste d’erreurs** , cliquez avec le bouton droit sur l’erreur, pointez sur **créer un élément de travail**, puis cliquez sur le type d’élément de travail que vous souhaitez créer.

  Utilisez les tâches suivantes pour gérer les erreurs de validation dans la fenêtre **liste d’erreurs** :

|**To**|**Procédez comme suit**|
|------------|----------------------------|
|Supprimer des erreurs sélectionnées pendant la validation|Cliquez avec le bouton droit sur une ou plusieurs erreurs sélectionnées, pointez sur **gérer les erreurs de validation**, puis cliquez sur supprimer les **Erreurs**.<br /><br /> Les erreurs supprimées apparaissent barrées. Lors de la prochaine validation, ces erreurs ne s’afficheront pas.<br /><br /> Les erreurs supprimées sont suivies dans un fichier .suppressions pour le fichier de diagramme de couche correspondant.|
|Cesser de supprimer des erreurs sélectionnées|Cliquez avec le bouton droit sur l’erreur ou les erreurs supprimées sélectionnées, pointez sur **gérer les erreurs de validation**, puis cliquez sur arrêter la suppression des **Erreurs**.<br /><br /> Les erreurs supprimées qui sont sélectionnées s'afficheront lors de la prochaine validation.|
|Restaurer toutes les erreurs supprimées dans la fenêtre **liste d’erreurs**|Cliquez avec le bouton droit n’importe où dans la fenêtre de **liste d’erreurs** , pointez sur **gérer les erreurs de validation**, puis cliquez sur **afficher toutes les erreurs supprimées**.|
|Masquer toutes les erreurs supprimées de la fenêtre **liste d’erreurs**|Cliquez avec le bouton droit n’importe où dans la fenêtre de **liste d’erreurs** , pointez sur **gérer les erreurs de validation**, puis cliquez sur **Masquer toutes les erreurs supprimées**.|

## <a name="validate-code-automatically"></a><a name="ValidateAuto"></a> Valider automatiquement le code
 Exécutez la validation de couche chaque fois que vous exécutez une build locale. Si votre équipe utilise Team Foundation Build, vous pouvez exécuter la validation de couche avec les archivages contrôlés que vous spécifiez en créant une tâche personnalisée MSBuild, puis utilisez les rapports de build pour collecter les erreurs de validation. Pour créer des builds d’archivage contrôlé, consultez [utiliser un processus de génération d’archivage contrôlé pour valider les modifications](https://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec).

#### <a name="to-validate-code-automatically-during-a-local-build"></a>Pour valider automatiquement le code au cours d'une build locale

- Utilisez un éditeur de texte pour ouvrir le fichier projet de modélisation (.modelproj), puis y inclure la propriété suivante :

```
<ValidateArchitecture>true</ValidateArchitecture>
```

 \- ou -

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet de modélisation qui contient le ou les diagrammes de couche, puis cliquez sur **Propriétés**.

2. Dans la fenêtre **Propriétés** , affectez à la propriété **valider l’architecture** du projet de modélisation la **valeur true**.

    Cela inclut le projet de modélisation dans le processus de validation.

3. Dans **Explorateur de solutions**, cliquez sur le fichier de diagramme de couche (. layerdiagram) que vous souhaitez utiliser pour la validation.

4. Dans la fenêtre **Propriétés** , assurez-vous que la propriété **action de génération** du diagramme est définie sur **valider**.

    Cela inclut le diagramme de couche dans le processus de validation.

   Pour gérer les erreurs dans la fenêtre de Liste d’erreurs, consultez [gérer les erreurs de validation](#ManageErrors).

#### <a name="to-validate-code-automatically-during-a-team-foundation-build"></a>Pour valider automatiquement le code au cours d'une build Team Foundation

1. Dans **Team Explorer**, double-cliquez sur la définition de build, puis cliquez sur **traiter**.

2. Sous **paramètres du processus de génération**, développez **compilation**, puis tapez ce qui suit dans le paramètre **arguments MSBuild** :

    `/p:ValidateArchitecture=true`

   Pour plus d’informations sur les erreurs de validation, consultez [comprendre et résoudre les erreurs de validation de couche](#UnderstandingValidationErrors). Pour plus d’informations sur [!INCLUDE[esprbuild](../includes/esprbuild-md.md)], consultez :

- [Créer l’application](/azure/devops/pipelines/index)

- [Utiliser le modèle par défaut pour un processus de build](https://msdn.microsoft.com/library/43930b12-c21b-4599-a980-2995e3d16e31)

- [Modifier une build héritée basée sur UpgradeTemplate. Xaml](https://msdn.microsoft.com/library/ee1a8259-1dd1-4a10-9563-66c5446ef41c)

- [Personnaliser votre modèle de processus de génération](https://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)

- [Surveiller la progression d'une build en cours d'exécution](https://msdn.microsoft.com/library/e51e3bad-2d1d-4b7b-bfcc-c43439c6c8ef)

## <a name="troubleshoot-layer-validation-issues"></a><a name="TroubleshootingValidation"></a> Résoudre les problèmes de validation de couche
 Le tableau suivant décrit les problèmes liés à la validation de couche et propose une résolution. Ces problèmes ne sont pas liés aux erreurs qui résultent de conflits entre le code et la conception. Pour plus d’informations sur ces erreurs, consultez [comprendre et résoudre les erreurs de validation de couche](#UnderstandingValidationErrors).

|**Problème**|**Cause possible**|**Résolution :**|
|---------------|------------------------|--------------------|
|Les erreurs de validation ne se produisent pas comme prévu.|La validation ne fonctionne pas avec les diagrammes de couche copiés à partir d'autres diagrammes de couche dans l'Explorateur de solutions, et ceux se trouvant dans le même projet de modélisation. Les diagrammes de couche copiés de cette façon contiennent les mêmes références que le diagramme de couche d'origine.|Ajoutez un nouveau diagramme de couche au projet de modélisation.<br /><br /> Copiez les éléments depuis le diagramme de couche source vers le nouveau diagramme.|

## <a name="understanding-and-resolving-layer-validation-errors"></a><a name="UnderstandingValidationErrors"></a> Compréhension et résolution des erreurs de validation de couche
 Lorsque vous validez du code par rapport à un diagramme de couche, des erreurs de validation se produisent si le code est en conflit avec la conception. Par exemple, les conditions suivantes peuvent provoquer des erreurs de validation :

- Un artefact est assigné à une couche inappropriée. Dans ce cas, déplacez l’artefact.

- Un artefact, tel qu'une classe, utilise une autre classe d'une manière qui génère un conflit avec votre architecture. Dans ce cas, refactorisez le code pour supprimer la dépendance.

  Pour résoudre ces erreurs, mettez à jour le code de façon à ce que la validation ne génère plus d’erreur. Vous pouvez effectuer cette tâche de façon itérative.

  La section suivante décrit la syntaxe utilisée lors de ces erreurs, explique la signification de ces erreurs, et suggère des opérations pour les résoudre ou les gérer.

|**Syntaxe**|**Description**|
|----------------|---------------------|
|*Artefactn*(*ArtifactTypeN*)|*Artefactn* est un artefact associé à une couche sur le diagramme de couche.<br /><br /> *ArtifactTypeN* est le type d' *artefactn*, tel qu’une **classe** ou une **méthode**, par exemple :<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|
|*NamespaceNameN*|Nom d'un espace de noms.|
|*LayerNameN*|Nom d'une couche sur le diagramme de couche.|
|*DependencyType*|Type de relation de dépendance entre *artefact 1* et *Artefact2*. Par exemple, *artefact 1* a une relation d' **appels** avec *Artefact2*.|

|**Syntaxe de l'erreur**|**Description de l’erreur**|
|----------------------|---------------------------|
|AV0001 : dépendance non valide : *artefact 1*(*ArtifactType1*)--> *Artefact2*(*ArtifactType2*)<br /><br /> Couches : *LayerName1*, *LayerName2* &#124; Dependencies : *DependencyType*|*Artefact 1* dans *LayerName1* ne doit pas avoir de dépendance sur *Artefact2* dans *LayerName2* , car *LayerName1* n’a pas de dépendance directe sur *LayerName2*.|
|AV1001 : espace de noms non valide : *artefact*<br /><br /> Couche : *nomcouche* &#124; espace de noms requis : *NamespaceName1* &#124; espace de noms actuel : *NamespaceName2*|*NomCouche* requiert que ses artefacts associés appartiennent à *NamespaceName1*. L' *artefact* est dans *NamespaceName2*, et non *NamespaceName1*.|
|AV1002 : dépend de l’espace de noms interdit : *artefact 1*(*ArtifactType1*) &#124; *Artefact2*(*ArtifactType2*)<br /><br /> Couche : *nomcouche* &#124; espace de noms interdit : *NomEspaceNoms* &#124; Dependencies : *DependencyType*|*NomCouche* exige que les artefacts qui lui sont associés ne dépendent pas de *NomEspaceNoms*. *Artefact 1* ne peut pas dépendre de *Artefact2* , car *Artefact2* est dans *NomEspaceNoms*.|
|AV1003 : dans l’espace de noms interdit : *artefact*(*artifactType*)<br /><br /> Couche : *nomcouche* &#124; espace de noms interdit : *NomEspaceNoms*|*NomCouche* exige que les artefacts qui lui sont associés ne puissent pas appartenir à *NomEspaceNoms*. L' *artefact* appartient à *NomEspaceNoms*.|
|AV3001 : lien manquant : la couche'*NomCouche*'est liée à'*artifact*'qui est introuvable. Vérifiez qu'il ne manque aucune référence d'assembly.|*NomCouche* est lié à un artefact qui est introuvable. Par exemple, il manque peut-être un lien vers une classe car le projet de modélisation ne comporte pas de référence à l'assembly contenant la classe.|
|AV9001 : erreurs internes détectées lors de l'analyse de l'architecture. Il est possible que les résultats ne soient pas complets. Pour plus d'informations, consultez le journal des événements de build ou la fenêtre Sortie.|Consultez le journal détaillé des événements de build ou la fenêtre Sortie pour plus de détails.|

## <a name="security"></a>Sécurité

## <a name="see-also"></a>Voir aussi
 [Validation de votre système pendant le développement](../modeling/validate-your-system-during-development.md)
