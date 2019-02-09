---
title: Créer ou mettre à jour des stratégies d’archivage d’analyse du code standard
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 768efb3e874f6427cd23f63f14671aa2db1bea71
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55917075"
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>Procédure : Créer ou mettre à jour des stratégies d’archivage d’analyse du code standard

Vous pouvez exiger que l’analyse de code est exécutée sur tous les projets de code dans un projet Azure DevOps à l’aide de la stratégie d’archivage de l’analyse du code. Nécessitant une analyse du code peut améliorer la qualité du code archivé dans la base de code.

> [!NOTE]
> Cette fonctionnalité est disponible uniquement si vous utilisez Team Foundation Server.

Stratégies d’archivage de l’analyse du code sont définies dans les paramètres du projet et s’appliquent à chaque projet de code. Exécutions d’analyse du code sont configurées pour les projets de code dans le fichier projet (.xxproj) pour le projet de code. Exécutions d’analyse du code sont effectuées sur l’ordinateur local. Lorsque vous activez une stratégie d’archivage de l’analyse du code, les fichiers dans un projet de code qui doivent être vérifiées doivent être compilés après leur dernière modification et une analyse du code qui contienne, au minimum, les règles dans les paramètres du projet doivent être effectuées sur l’ordinateur où la modification s ont été apportées.

- Pour le code managé, vous définissez la stratégie d’archivage en spécifiant un *ensemble de règles* qui contient un sous-ensemble de règles d’analyse du code.

- Pour le code C/C++, dans Visual Studio 2017 version 15.6 et versions antérieure, la stratégie d’archivage nécessite que toutes les règles d’analyse du code sont exécutés. Vous pouvez ajouter des directives du préprocesseur pour désactiver des règles spécifiques pour les projets de code individuels de votre projet Azure DevOps. Dans 15.7 et versions ultérieures, vous pouvez utiliser **/ analyze : ruleset** pour spécifier les règles à exécuter. Pour plus d’informations, consultez [à l’aide des ensembles de règles pour spécifier les règles C++ à exécuter](using-rule-sets-to-specify-the-cpp-rules-to-run.md).

Après avoir spécifié une stratégie d’archivage pour le code managé, les membres de l’équipe peuvent synchroniser leurs paramètres d’analyse de code pour les projets de code pour les paramètres de stratégie du projet Azure DevOps.

## <a name="to-open-the-check-in-policy-editor"></a>Pour ouvrir l’éditeur de stratégie d’archivage

1. Dans Team Explorer, cliquez sur le nom du projet, pointez sur **paramètres du projet**, puis cliquez sur **contrôle de code Source**.

1. Dans le **contrôle de code Source** boîte de dialogue, sélectionnez le **stratégie d’archivage** onglet.

1. Effectuez l’une des opérations suivantes :

    - Cliquez sur **ajouter** pour créer une nouvelle stratégie d’archivage.

    - Double-cliquez sur existant **analyse du Code** d’élément dans le **Type de stratégie** liste pour modifier la stratégie.

## <a name="to-set-policy-options"></a>Pour définir les options de stratégie

Activez ou désactivez les options suivantes :

|Option|Description|
|------------|-----------------|
|**Appliquer l’archivage pour qu’il contienne uniquement les fichiers qui font partie de la solution actuelle.**|Analyse du code peut exécuter uniquement sur les fichiers spécifiés dans les fichiers de configuration de solution et projet. Cette stratégie garantit que tout le code qui fait partie d’une solution est analysé.|
|**Appliquer l’analyse du Code C/C++ (/analyze)**|Requiert que tous les projets C ou C++ générés avec le / analyze exécuter l’analyse du code avant de pouvoir être archivées l’option du compilateur.|
|**Appliquer l’analyse du Code pour le Code managé**|Requiert que tous les projets managés exécuter l’analyse du code et générer avant de pouvoir être archivées.|

## <a name="to-specify-a-managed-rule-set"></a>Pour spécifier un ensemble de règles managé

À partir de la **exécuter cet ensemble de règles** liste, utilisez une des méthodes suivantes :

- Sélectionnez un ensemble de règles standard de Microsoft.

- Sélectionnez une règle personnalisée définie en cliquant sur  **\<sélectionner l’ensemble de règle de contrôle de code Source... >**. Ensuite, tapez le chemin d’accès du contrôle de version de l’ensemble de règles dans l’Explorateur de contrôle source. La syntaxe d’un chemin d’accès du contrôle de version est :

   **$/** `TeamProjectName` **/** `VersionControlPath`

Pour plus d’informations sur la façon de créer et implémenter une règle de stratégie d’archivage personnalisées, consultez [implémenter vérification des stratégies personnalisées pour le Code managé](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).

## <a name="see-also"></a>Voir aussi

- [Créer et utiliser des stratégies d’archivage de l’analyse du code](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)