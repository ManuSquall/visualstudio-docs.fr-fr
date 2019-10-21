---
title: Créer ou mettre à jour des stratégies d’archivage d’analyse du code standard
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e6d502dc75530bb6b95f38b069b9220c5ad54cac
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649474"
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>Comment : créer ou mettre à jour des stratégies d’archivage d’analyse du code standard

Vous pouvez exiger que l’analyse du code soit exécutée sur tous les projets de code dans un projet Azure DevOps à l’aide de la stratégie d’archivage de l’analyse du code. L’exigence de l’analyse du code peut améliorer la qualité du code qui est archivé dans la base de code.

> [!NOTE]
> Cette fonctionnalité n’est disponible que si vous utilisez Team Foundation Server.

Les stratégies d’archivage de l’analyse du code sont définies dans les paramètres du projet et s’appliquent à chaque projet de code. Les exécutions de l’analyse du code sont configurées pour les projets de code dans le fichier projet (. fichier xxproj) du projet de code. Les exécutions de l’analyse du code sont effectuées sur l’ordinateur local. Quand vous activez une stratégie d’archivage de l’analyse du code, les fichiers d’un projet de code qui doivent être archivés doivent être compilés après leur dernière modification et une exécution d’analyse du code qui contient, au minimum, les règles des paramètres du projet doivent être exécutées sur l’ordinateur sur lequel la modification ont été effectués.

- Pour le code managé, vous définissez la stratégie d’archivage en spécifiant un *ensemble de règles* qui contient un sous-ensemble de règles d’analyse du code.

- Pour C/C++ code, dans Visual Studio 2017 version 15,6 et les versions antérieures, la stratégie d’archivage requiert l’exécution de toutes les règles d’analyse du code. Vous pouvez ajouter des directives de préprocesseur pour désactiver des règles spécifiques pour les projets de code individuels dans votre projet Azure DevOps. Dans 15,7 et versions ultérieures, vous pouvez utiliser **/analyze : RuleSet** pour spécifier les règles à exécuter. Pour plus d’informations, consultez [utilisation d’ensembles de règles C++ pour spécifier les règles à exécuter](using-rule-sets-to-specify-the-cpp-rules-to-run.md).

Une fois que vous avez spécifié une stratégie d’archivage pour le code managé, les membres de l’équipe peuvent synchroniser leurs paramètres d’analyse du code pour les projets de code sur les paramètres de stratégie de projet Azure DevOps.

## <a name="to-open-the-check-in-policy-editor"></a>Pour ouvrir l’éditeur de stratégie d’archivage

1. Dans Team Explorer, cliquez avec le bouton droit sur le nom du projet, pointez sur **paramètres du projet**, puis cliquez sur **contrôle de code source**.

1. Dans la boîte de dialogue **contrôle de code source** , sélectionnez l’onglet **stratégie d’archivage** .

1. Effectuez l’une des opérations suivantes :

    - Cliquez sur **Ajouter** pour créer une nouvelle stratégie d’archivage.

    - Double-cliquez sur l’élément **analyse du code** existant dans la liste type de **stratégie** pour modifier la stratégie.

## <a name="to-set-policy-options"></a>Pour définir des options de stratégie

Activez ou désactivez les options suivantes :

|Option|Description|
|------------|-----------------|
|**Appliquer l’archivage pour contenir uniquement les fichiers qui font partie de la solution actuelle.**|L’analyse du code peut s’exécuter uniquement sur les fichiers spécifiés dans les fichiers de configuration de la solution et du projet. Cette stratégie garantit que tout le code qui fait partie d’une solution est analysé.|
|**Appliquer l’analyseC++ C/code (/analyze)**|Requiert que tous les projets C++ C ou soient générés avec l’option de compilateur/analyze pour exécuter l’analyse du code avant de pouvoir être archivées.|
|**Appliquer l’analyse du code managé**|Requiert que tous les projets managés exécutent l’analyse et la génération du code avant de pouvoir être archivés.|

## <a name="to-specify-a-managed-rule-set"></a>Pour spécifier un ensemble de règles géré

Dans la liste **exécuter cet ensemble de règles** , utilisez l’une des méthodes suivantes :

- Sélectionnez un ensemble de règles standard Microsoft.

- Sélectionnez un ensemble de règles personnalisé en cliquant sur **\<Select ensemble de règles à partir du contrôle de code source... >** . Ensuite, tapez le chemin d’accès de contrôle de version de l’ensemble de règles dans le navigateur de contrôle de code source. La syntaxe d’un chemin d’accès de contrôle de version est :

   **$/** `TeamProjectName` **/** `VersionControlPath`

Pour plus d’informations sur la création et l’implémentation d’un ensemble de règles de stratégie d’archivage personnalisé, consultez [implémenter des stratégies d’archivage personnalisées pour le code managé](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).

## <a name="see-also"></a>Voir aussi

- [Créer et utiliser des stratégies d’archivage de l’analyse du code](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)
