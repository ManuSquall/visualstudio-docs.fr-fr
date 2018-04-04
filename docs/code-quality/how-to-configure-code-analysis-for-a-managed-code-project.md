---
title: 'Comment : configurer l’analyse du Code pour un projet de Code managé | Documents Microsoft'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: article
f1_keywords:
- vs.codeanalysis.propertypages.csvb
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 46d41b09f0f6639195613c8a4d9a08f952c79525
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2018
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>Procédure : configurer l’analyse du code pour un projet de code managé

Dans Visual Studio, vous pouvez choisir parmi une liste de l’analyse du code *ensembles de règles* à appliquer à un projet de code managé. L’ensemble de règles par défaut est *règles minimales recommandées*. Vous pouvez appliquer un autre ensemble de règles à un projet ou à tous les projets dans une solution.

> [!TIP]
> Pour plus d’informations sur la configuration d’un ensemble de règles pour les applications Web ASP.NET, consultez [Comment : configurer l’analyse du Code pour une Application Web ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).

## <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>Pour configurer un ensemble de règles pour un projet .NET Framework

1. Ouvrez le **l’analyse du Code** onglet sur les pages de propriétés du projet. Pour cela, dans une des manières suivantes :

   - Dans **l’Explorateur de solutions**, sélectionnez le projet. Dans la barre de menus, sélectionnez **analyser** > **configurer l’analyse du Code** > **pour \<projectname >**.

   - Cliquez sur le projet dans **l’Explorateur de solutions** et sélectionnez **propriétés**, puis sélectionnez le **analyse du Code** onglet.

1. Dans le **Configuration** et **plateforme** listes, sélectionnez la plateforme de configuration et la cible de génération.

1. Pour exécuter l’analyse du code chaque fois que le projet est généré à l’aide de la configuration sélectionnée, sélectionnez le **activer l’analyse du Code sur la Build** case à cocher. Vous pouvez également exécuter l’analyse du code manuellement en sélectionnant **analyser** > **exécuter l’analyse du Code** > **exécuter l’analyse du Code sur \<projectname >**.

1. Par défaut, l'analyse du code ne signale pas d'avertissements pour le code généré automatiquement par les outils externes. Pour afficher les avertissements du code généré, désactivez le **supprimer les résultats du code généré** case à cocher.

    > [!NOTE]
    > Cette option ne supprime pas les erreurs d'analyse du code et les avertissements du code généré qui apparaissent dans les formulaires et les modèles. Vous pouvez afficher et mettre à jour le code source pour un formulaire ou un modèle, sans que celle-ci n’est remplacé.

1. Dans le **exécuter cet ensemble de règles** liste, effectuez l’une des opérations suivantes :

    - Sélectionnez l’ensemble de règles que vous souhaitez utiliser.

    - Sélectionnez  **\<Parcourir... >** pour rechercher une règle personnalisée existante définie qui ne figure pas dans la liste.

    - Définissez un ensemble de règles personnalisé. Pour plus d’informations, consultez [création d’ensembles de règles personnalisés](../code-quality/creating-custom-code-analysis-rule-sets.md).

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : configuration et utilisation d’un ensemble de règles personnalisé](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)
- [Guide pratique pour configurer l’analyse du code pour une application web ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)