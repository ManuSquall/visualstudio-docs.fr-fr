---
title: Stratégies d’archivage de l’analyse du code personnalisées pour le code managé
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.code.analysis.selecttfsrulesets
- vs.code.analysis.browsefortfsruleset
- vs.code.analysis.policyeditor
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 55294f7418de085cb4ceccd4063a4b2b55cbc6c4
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2019
ms.locfileid: "71975036"
---
# <a name="implement-custom-code-analysis-check-in-policies-for-managed-code"></a>Implémenter des stratégies d’archivage d’analyse du code personnalisées pour le code managé

Une stratégie d’archivage de l’analyse du code spécifie un ensemble de règles que les membres d’un projet Azure DevOps doivent exécuter sur le code source avant qu’il soit archivé pour contrôle de version. Microsoft fournit un ensemble de la norme *ensembles de règles* cette analyse de code de groupe de règles dans des zones fonctionnelles. *Ensembles de règles de stratégie d’archivage personnalisée* spécifier un ensemble de règles d’analyse du code qui sont spécifiques à un projet. Un ensemble de règles est stocké dans un fichier .ruleset.

Stratégies d’archivage sont définies au niveau du projet d’Azure DevOps et spécifiées par l’emplacement d’un fichier .ruleset dans l’arborescence de contrôle de version. Il n’existe aucune restriction sur l’emplacement du contrôle de version de l’ensemble de règles personnalisé de stratégie team.

Analyse du code est configurée pour les projets de code individuels dans la fenêtre Propriétés pour chaque projet. Une règle personnalisée définie pour un projet de code est spécifiée par l’emplacement physique du fichier .ruleset sur l’ordinateur local. Lorsqu’un fichier .ruleset est spécifié qui se trouve sur le même lecteur que le projet de code, Visual Studio utilise un chemin d’accès relatif au fichier dans la configuration de projet.

Une pratique suggérée pour la création d’un ensemble de règles personnalisé de projet consiste à stocker le fichier .ruleset de stratégie d’archivage dans un dossier spécial qui ne fait pas partie d’un projet de code de Azure DevOps. Si vous stockez le fichier dans un dossier dédié, vous pouvez appliquer des autorisations qui limitent ce qui peuvent modifier le fichier de règles, et vous pouvez déplacer facilement la structure de répertoire qui contient le projet vers un autre répertoire ou ordinateur.

## <a name="create-the-project-custom-check-in-rule-set"></a>Créer le jeu de règles d’archivage personnalisées de projet

Pour créer une règle personnalisée définie pour un projet Azure DevOps, vous créez tout d’abord un dossier spécial pour la règle de stratégie d’archivage **Explorateur du contrôle de Source**. Ensuite, vous créez le fichier d’ensemble de règles et ajoutez le fichier au contrôle de version. Enfin, vous spécifiez la règle définie en tant que la stratégie de vérification d’analyse du code pour le projet.

> [!NOTE]
> Pour créer un dossier dans un projet Azure DevOps, vous devez d’abord mapper la racine du projet vers un emplacement sur l’ordinateur local.

### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>Pour créer le dossier de contrôle de version pour l’ensemble de règles de stratégie d’archivage

1. Dans Team Explorer, développez le nœud du projet, puis cliquez sur **contrôle de code Source**.

2. Dans le **dossiers** volet, cliquez sur le projet, puis **nouveau dossier**.

3. Dans le volet principal de contrôle de code Source, cliquez sur **nouveau dossier**, cliquez sur **renommer**et tapez un nom pour l’ensemble de règles dossier.

### <a name="to-create-the-check-in-policy-rule-set"></a>Pour créer l’ensemble de règles de stratégie d’archivage

1. Sur le **fichier** menu, pointez sur **New**, puis cliquez sur **fichier**.

2. Dans le **catégories** , cliquez sur **général**.

3. Dans le **modèles** , double-cliquez sur **ensemble de règles d’analyse de Code**.

4. [Spécifier les règles](../code-quality/how-to-create-a-custom-rule-set.md) à inclure dans l’ensemble de règles, puis enregistrez la règle définie fichier dans le dossier de jeu de règle que vous avez créé.

### <a name="to-add-the-rule-set-file-to-version-control"></a>Pour ajouter la règle de définie le fichier de contrôle de version

1. Dans **Explorateur du contrôle de Source**, cliquez sur le nouveau dossier, puis cliquez sur **ajouter des éléments au dossier**.

     Pour plus d’informations, consultez [Git et les référentiels Azure](/azure/devops/repos/git/overview?view=vsts).

2. Cliquez sur l’ensemble de règles fichier que vous avez créé, puis cliquez sur **Terminer**.

     Le fichier est ajouté au contrôle de code source et extrait pour vous.

3. Dans le **Explorateur du contrôle de Source** fenêtre de détails, cliquez sur le nom de fichier, puis **archiver les modifications en attente**.

4. Dans le **archivage** boîte de dialogue, vous pouvez ajouter un commentaire, puis cliquez sur **archiver**.

    > [!NOTE]
    > Si vous avez déjà configuré une stratégie d’archivage de l’analyse du code pour votre projet Azure DevOps et que vous avez sélectionné le **appliquer l’archivage pour qu’il contienne uniquement les fichiers qui font partie de la solution actuelle**, vous déclenchera un avertissement d’échec de stratégie. Dans la boîte de dialogue d’échec de la stratégie, sélectionnez **substituer l’échec de stratégie et poursuivre l’archivage**. Ajouter un commentaire requis, puis cliquez sur **OK**.

### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>Pour spécifier la règle de définie le fichier en tant que la stratégie d’archivage

1. Sur le **équipe** menu, pointez sur **paramètres du projet**, puis cliquez sur **contrôle de code Source**.

2. Cliquez sur **stratégie d’archivage**, puis cliquez sur **ajouter**.

3. Dans le **stratégie d’archivage** , double-cliquez sur **analyse du Code**et vous assurer que le **appliquer l’analyse du Code pour le Code managé** case à cocher est activée.

4. Dans le **exécuter cet ensemble de règles** , cliquez sur  **\<sélectionner l’ensemble de règles de contrôle de code Source >** .

5. Tapez le chemin d’accès du fichier de jeu de règle de stratégie d’archivage dans le contrôle de version.

     Le chemin d’accès doit être conforme à la syntaxe suivante :

     **$/** `TeamProjectName` **/** `VersionControlPath`

    > [!NOTE]
    > Vous pouvez copier le chemin d’accès en utilisant l’une des procédures suivantes dans **Explorateur du contrôle de Source**:

    - Dans le **dossiers** volet, cliquez sur le dossier qui contient le fichier d’ensemble de règles. Copier le chemin d’accès du contrôle de version du dossier qui apparaît dans le **Source** , puis tapez le nom de fichier d’ensemble de la règle manuellement.

    - Dans la fenêtre de détails, cliquez sur le fichier d’ensemble de règles, puis cliquez sur **propriétés**. Sur le **général** onglet, copiez la valeur dans **nom du serveur**.

## <a name="synchronize-code-projects-to-the-check-in-policy-rule-set"></a>Synchroniser les projets de Code à l’ensemble de règles de stratégie d’archivage

Vous spécifiez une règle de stratégie d’archivage de projet est défini comme l’ensemble de règles code analyse d’une configuration de projet de code dans la boîte de dialogue Propriétés du projet de code. Si l’ensemble de règles se trouve sur le même lecteur que le projet de code, un chemin d’accès relatif est utilisé pour spécifier l’ensemble de règles lorsque le chemin d’accès est sélectionné dans la boîte de dialogue de fichier. Structures de contrôle de chemin d’accès relatif permet les paramètres de propriétés de projet soit portable sur d’autres ordinateurs qui utilisent la version locale similaire.

### <a name="to-specify-a-project-rule-set-as-the-rule-set-of-a-code-project"></a>Pour spécifier une règle de projet définie en tant que l’ensemble de règles d’un projet de code

1. Si nécessaire, extrayez le dossier de jeu de règles de stratégie d’archivage et le fichier à partir du contrôle de version.

   Vous pouvez effectuer cette étape dans **Explorateur du contrôle de Source** en double-cliquant sur la règle définie puis cliquer sur **obtenir la dernière Version**.

2. Dans **l’Explorateur de solutions**, cliquez sur le projet de code, puis cliquez sur **propriétés**.

3. **Cliquez sur l’analyse du Code**.

4. Si nécessaire, cliquez sur les options appropriées dans le **Configuration** et **plateforme** répertorie.

::: moniker range="vs-2017"

5. Pour exécuter l’analyse du code chaque fois que le projet de code est généré à l’aide de la configuration spécifiée, sélectionnez **activer l’analyse du code sur la build**.

::: moniker-end

::: moniker range=">=vs-2019"

5. Pour exécuter l’analyse du code chaque fois que le projet de code est généré à l’aide de la configuration spécifiée, sélectionnez **exécuter lors de la génération** dans la section **analyseurs binaires** .

::: moniker-end

6. Dans la liste **exécuter cet ensemble de règles** , cliquez sur **\<Browse >** .

8. Sélectionnez la version locale du fichier d’ensemble de règles de stratégie d’archivage.