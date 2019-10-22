---
title: Implémentation de stratégies d’archivage d’analyse du code personnalisées pour le code managé | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.code.analysis.selecttfsrulesets
- vs.code.analysis.browsefortfsruleset
- vs.code.analysis.policyeditor
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1cf759e01e5f152f2220124c90f145bfbbe3c01d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651591"
---
# <a name="implementing-custom-code-analysis-check-in-policies-for-managed-code"></a>Implémentation de stratégies d'archivage de l'analyse du code personnalisées pour le code managé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Une stratégie d’archivage de l’analyse du code spécifie un ensemble de règles que les membres d’un projet d’équipe doivent exécuter sur le code source avant qu’il ne soit archivé dans le contrôle de version. Microsoft fournit un ensemble d' *ensembles de règles* standard qui regroupent les règles d’analyse du code dans des zones fonctionnelles. Les *ensembles de règles de stratégie d’archivage personnalisés* spécifient un ensemble de règles d’analyse du code spécifiques à un projet d’équipe. Un ensemble de règles est stocké dans un fichier. RuleSet.

 Les stratégies d’archivage sont définies au niveau du projet d’équipe et spécifiées par l’emplacement d’un fichier. RuleSet dans l’arborescence de contrôle de version. Il n’existe aucune restriction sur l’emplacement de contrôle de version de l’ensemble de règles personnalisées de stratégie d’équipe.

 L’analyse du code est configurée pour les projets de code individuels dans la fenêtre Propriétés de chaque projet. Un ensemble de règles personnalisé pour un projet de code est spécifié par l’emplacement physique du fichier. RuleSet sur l’ordinateur local. Lorsqu’un fichier. RuleSet est spécifié et qu’il se trouve sur le même lecteur que le projet de code, Visual Studio utilise un chemin d’accès relatif au fichier dans la configuration du projet.

 Une pratique recommandée pour la création d’un ensemble de règles personnalisé de projet d’équipe consiste à stocker le fichier de stratégie d’archivage. RuleSet dans un dossier spécial qui ne fait partie d’aucun projet de code. Si vous stockez le fichier dans un dossier dédié, vous pouvez appliquer des autorisations qui limitent les personnes autorisées à modifier le fichier de règles, et vous pouvez facilement déplacer la structure de répertoires qui contient le projet vers un autre répertoire ou ordinateur.

## <a name="creating-the-team-project-custom-check-in-rule-set"></a>Création de l’ensemble de règles d’archivage personnalisé du projet d’équipe
 Pour créer un ensemble de règles personnalisé pour un projet d’équipe, vous devez d’abord créer un dossier spécial pour l’ensemble de règles de stratégie d’archivage dans **Explorateur du contrôle de code source**. Ensuite, vous créez le fichier d’ensemble de règles et ajoutez le fichier au contrôle de version. Enfin, vous spécifiez l’ensemble de règles en tant que stratégie d’archivage de l’analyse du code pour le projet d’équipe.

> [!NOTE]
> Pour créer un dossier dans un projet d’équipe, vous devez d’abord mapper la racine du projet d’équipe à un emplacement sur l’ordinateur local. Pour plus d’informations, consultez [créer et utiliser des espaces de travail (ancien)](https://msdn.microsoft.com/db4d5692-179a-44fe-ad31-0c1c900c9cb2).

#### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>Pour créer le dossier de contrôle de version pour l’ensemble de règles de stratégie d’archivage

1. Dans [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], développez le nœud du projet d’équipe, puis cliquez sur **contrôle de code source**.

2. Dans le volet **dossiers** , cliquez avec le bouton droit sur le projet d’équipe, puis cliquez sur **nouveau dossier**.

3. Dans le volet principal du contrôle de code source, cliquez avec le bouton droit sur **nouveau dossier**, cliquez sur **Renommer**, puis tapez un nom pour le dossier de l’ensemble de règles.

#### <a name="to-create-the-check-in-policy-rule-set"></a>Pour créer l’ensemble de règles de stratégie d’archivage

1. Dans le menu **fichier** , pointez sur **nouveau**, puis cliquez sur **fichier**.

2. Dans la liste **catégories** , cliquez sur **général**.

3. Dans la liste **modèles** , double-cliquez sur **ensemble de règles d’analyse du code**.

4. Spécifiez les règles à inclure dans l’ensemble de règles, puis enregistrez le fichier de l’ensemble de règles dans le dossier de l’ensemble de règles que vous avez créé.

     Pour plus d’informations, consultez [création d’ensembles de règles personnalisées](../code-quality/creating-custom-code-analysis-rule-sets.md) .

#### <a name="to-add-the-rule-set-file-to-version-control"></a>Pour ajouter le fichier d’ensemble de règles au contrôle de version

1. Dans **Explorateur du contrôle de code source**, cliquez avec le bouton droit sur le nouveau dossier, puis cliquez sur **Ajouter des éléments au dossier**.

     Pour plus d’informations, consultez [utiliser le contrôle de version](https://msdn.microsoft.com/library/33267cee-fe5f-4aa3-b2cd-6d22ceace314).

2. Cliquez sur le fichier d’ensemble de règles que vous avez créé, puis cliquez sur **Terminer**.

     Le fichier est ajouté au contrôle de code source et extrait pour vous.

3. Dans la fenêtre Détails du **Explorateur du contrôle de code source** , cliquez avec le bouton droit sur le nom du fichier, puis cliquez sur **archiver les modifications en attente**.

4. Dans la boîte de dialogue **archivage** , vous avez la possibilité d’ajouter un commentaire, puis de cliquer sur **Archiver**.

    > [!NOTE]
    > Si vous avez déjà configuré une stratégie d’archivage de l’analyse du code pour votre projet d’équipe et que vous avez sélectionné l’option **appliquer l’archivage pour contenir uniquement les fichiers qui font partie de la solution actuelle**, vous déclenchez un avertissement d’échec de stratégie. Dans la boîte de dialogue échec de la stratégie, sélectionnez **remplacer échec de stratégie et poursuivre l’archivage**. Ajoutez un commentaire obligatoire, puis cliquez sur **OK**.

#### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>Pour spécifier le fichier d’ensemble de règles comme stratégie d’archivage

1. Dans le menu **équipe** , pointez sur **paramètres du projet d’équipe**, puis cliquez sur contrôle de **code source**.

2. Cliquez sur **stratégie d’archivage**, puis sur **Ajouter**.

3. Dans la liste des **stratégies d’archivage** , double-cliquez sur **analyse du code**et assurez-vous que la case à cocher **appliquer l’analyse du code pour le code managé** est activée.

4. Dans la liste **exécuter cet ensemble de règles** , cliquez sur **\<Select ensemble de règles à partir du contrôle de code source >** .

5. Tapez le chemin d’accès du fichier d’ensemble de règles de stratégie d’archivage dans le contrôle de version.

     Le chemin d’accès doit être conforme à la syntaxe suivante :

     **$/** `TeamProjectName` **/** `VersionControlPath`

    > [!NOTE]
    > Vous pouvez copier le chemin d’accès à l’aide de l’une des procédures suivantes dans **Explorateur du contrôle de code source**:

    - Dans le volet **dossiers** , cliquez sur le dossier qui contient le fichier d’ensemble de règles. Copiez le chemin d’accès du contrôle de version du dossier qui apparaît dans la zone **source** , puis tapez manuellement le nom du fichier d’ensemble de règles.

    - Dans la fenêtre Détails, cliquez avec le bouton droit sur le fichier de l’ensemble de règles, puis cliquez sur **Propriétés**. Sous l’onglet **général** , copiez la valeur dans **nom du serveur**.

## <a name="synchronizing-code-projects-to-the-check-in-policy-rule-set"></a>Synchronisation des projets de code avec l’ensemble de règles de stratégie d’archivage
 Vous spécifiez une règle de stratégie d’archivage de projet d’équipe comme ensemble de règles d’analyse du code d’une configuration de projet de code dans la boîte de dialogue Propriétés du projet de code. Si l’ensemble de règles se trouve sur le même lecteur que le projet de code, un chemin d’accès relatif est utilisé pour spécifier l’ensemble de règles lorsque le chemin d’accès est sélectionné dans la boîte de dialogue fichier. Le chemin d’accès relatif permet aux paramètres des propriétés du projet d’être portables vers d’autres ordinateurs qui utilisent des structures de contrôle de version locales similaires.

#### <a name="to-specify-a-team-project-rule-set-as-the-rule-set-of-a-code-project"></a>Pour spécifier un ensemble de règles de projet d’équipe en tant qu’ensemble de règles d’un projet de code

1. Si nécessaire, récupérez le dossier et le fichier de l’ensemble de règles de stratégie d’archivage à partir du contrôle de version.

     Vous pouvez effectuer cette étape dans **Explorateur du contrôle de code source** en cliquant avec le bouton droit sur le dossier de l’ensemble de règles, puis en cliquant sur **obtenir la dernière version**.

2. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet de code, puis cliquez sur **Propriétés**.

3. **Cliquez sur analyse du code**.

4. Si nécessaire, cliquez sur les options appropriées dans les listes **configuration** et **plateforme** .

5. Pour exécuter l’analyse du code chaque fois que le projet de code est généré à l’aide de la configuration spécifiée, activez la case à cocher **activer l’analyse du code sur la build (définit la constante CODE_ANALYSIS)** .

6. Pour ignorer le code dans les composants d’autres sociétés, activez la case à cocher **Supprimer les résultats du code généré** .

7. Dans la liste **exécuter cet ensemble de règles** , cliquez sur **\<Browse... >** .

8. Spécifiez la version locale du fichier d’ensemble de règles de stratégie d’archivage.
